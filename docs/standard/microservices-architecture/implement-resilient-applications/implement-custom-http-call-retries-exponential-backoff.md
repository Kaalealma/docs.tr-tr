---
title: Özel HTTP çağrısı deneme üstel geri alma ile uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Özel HTTP çağrısı deneme üstel geri alma ile uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 10751bb74ed648839fabec67ff7a71e458fb2a44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-custom-http-call-retries-with-exponential-backoff"></a>Özel HTTP çağrısı deneme üstel geri alma ile uygulama

Esnek mikro hizmetler oluşturma için olası HTTP hatası senaryolar ele almanız gerekir. Bu amaçla üstel geri alma ile kendi uygulamanızı yeniden deneme oluşturabilirsiniz.

Zamana bağlı kaynak kullanılamazlık işleme ek olarak, üstel geri alma ayrıca bulut sağlayıcısı kullanım aşırı önlemek için kaynak kullanılabilirliğini kısıtlama dikkate almanız gerekir. Örneğin, çok fazla sayıda bağlantı isteklerini çok hızlı oluşturma bir hizmet reddi görüntülenmesine ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) bulut sağlayıcısı tarafından saldırı. Sonuç olarak, bir kapasite eşiğine karşılaştığında geri bağlantı isteklerini ölçeklendirmek için bir mekanizma sağlamanız gerekir.

İlk incelenmesi kendi kodunuzu olarak üstel geri alma için yardımcı sınıfı ile uygulama [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), aşağıdaki gibi kod artı (olduğu da kullanılabilir bir [GitHub depo ](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).

```csharp
public sealed class RetryWithExponentialBackoff
{
    private readonly int maxRetries, delayMilliseconds, maxDelayMilliseconds;

    public RetryWithExponentialBackoff(int maxRetries = 50,
        int delayMilliseconds = 200,
        int maxDelayMilliseconds = 2000)
    {
        this.maxRetries = maxRetries;
        this.delayMilliseconds = delayMilliseconds;
        this.maxDelayMilliseconds = maxDelayMilliseconds;
    }

    public async Task RunAsync(Func<Task> func)
    {
        ExponentialBackoff backoff = new ExponentialBackoff(this.maxRetries,
            this.delayMilliseconds,
            this.maxDelayMilliseconds);
        retry:
        try
        {
            await func();
        }
        catch (Exception ex) when (ex is TimeoutException ||
            ex is System.Net.Http.HttpRequestException)
        {
            Debug.WriteLine("Exception raised is: " +
                ex.GetType().ToString() +
                " –Message: " + ex.Message +
                " -- Inner Message: " +
                ex.InnerException.Message);
            await backoff.Delay();
            goto retry;
        }
    }
}

public struct ExponentialBackoff
{
    private readonly int m_maxRetries, m_delayMilliseconds, m_maxDelayMilliseconds;
    private int m_retries, m_pow;

    public ExponentialBackoff(int maxRetries, int delayMilliseconds,
        int maxDelayMilliseconds)
    {
        m_maxRetries = maxRetries;
        m_delayMilliseconds = delayMilliseconds;
        m_maxDelayMilliseconds = maxDelayMilliseconds;
        m_retries = 0;
        m_pow = 1;
    }

    public Task Delay()
    {
        if (m_retries == m_maxRetries)
        {
            throw new TimeoutException("Max retry attempts exceeded.");
        }
        ++m_retries;
        if (m_retries < 31)
        {
            m_pow = m_pow << 1; // m_pow = Pow(2, m_retries - 1)
        }
        int delay = Math.Min(m_delayMilliseconds * (m_pow - 1) / 2,
            m_maxDelayMilliseconds);
        return Task.Delay(delay);
    }
}
```

Bu kod bir istemci C kullanarak\# uygulama (başka bir Web API İstemci mikro hizmet, bir ASP.NET MVC uygulaması ya da bile bir C\# Xamarin uygulaması) basittir. Aşağıdaki örnekte gösterildiği nasıl HttpClient sınıfını kullanma.

```csharp
public async Task<Catalog> GetCatalogItems(int page,int take, int? brand, int? type)
{
    _apiClient = new HttpClient();
    var itemsQs = $"items?pageIndex={page}&pageSize={take}";
    var filterQs = "";
    var catalogUrl = $"{_remoteServiceBaseUrl}items{filterQs}?pageIndex={page}&pageSize={take}";
    var dataString = "";
    //
    // Using HttpClient with Retry and Exponential Backoff
    //
    var retry = new RetryWithExponentialBackoff();
    await retry.RunAsync(async () =>
    {
        // work with HttpClient call
        dataString = await _apiClient.GetStringAsync(catalogUrl);
    });
    return JsonConvert.DeserializeObject<Catalog>(dataString);
}
```

Ancak, bu kod yalnızca bir kavram kanıtı uygundur. Sonraki konuyu daha karmaşık ve kanıtlanmış kitaplıkları kullanımı açıklanmaktadır.


>[!div class="step-by-step"]
[Önceki] (implement-resilient-entity-framework-core-sql-connections.md) [sonraki] (implement-http-call-retries-exponential-backoff-polly.md)
