---
title: .NET taşınabilirlik Çözümleyicisi - .NET
description: '.NET Core, .NET standart, UWP ve Xamarin dahil olmak üzere çeşitli .NET uygulamaları arasında nasıl taşınabilir kodunuz: değerlendirilecek .NET taşınabilirlik Çözümleyicisi aracını kullanmayı öğrenin.'
author: blackdwarf
ms.author: mairaw
ms.date: 07/26/2017
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: f310e5fe45315dfa41d596c92d9412dc6b3bc125
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="the-net-portability-analyzer"></a>.NET taşınabilirlik Çözümleyicisi

Birden çok platform Kitaplıklarınızı olmak istersiniz? Ne kadar işin uygulamanızın diğer .NET uygulamaları ve .NET Core, .NET standart, UWP ve Xamarin iOS, Android ve Mac için dahil olmak üzere profillerini uyumlu hale getirmek için gerekli olduğunu görmek mi istiyorsunuz? [.NET taşınabilirlik Çözümleyicisi](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) nasıl programınızı .NET uygulamaları arasında derlemeleri çözümleyerek esnektir üzerinde ayrıntılı bir rapor sağlayan bir araçtır. Taşınabilirlik Çözümleyicisi Visual Studio uzantısı ve bir konsol uygulaması olarak sunulur.

## <a name="new-targets"></a>Yeni hedefler

* [.NET core](../../core/index.md): modüler bir tasarıma sahiptir, yan yana uygular ve platformlar arası senaryolar hedefler. Yan yana diğer uygulamalar bozmadan yeni .NET Core sürümleri benimsemesini sağlar.
* [ASP.NET Core](/aspnet/core): bir çerçevedir modern web-böylece geliştiriciler aynı avantajları vermiş .NET Core üzerinde oluşturulmuştur.
* [Evrensel Windows platformu](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): x64 ve ARM makineler .NET yerel'ın statik derleme kullanarak çalışan Windows mağazası uygulamalarınızı performansını artırma. 
* .NET core + Platform uzantıları: .NET ekosistemi WCF ve ASP.NET Core, FSharp ve Azure gibi diğer API'lerin yanı sıra .NET Core API'ları içerir.
* .NET standart + Platform uzantıları: WCF ve ASP.NET Core, FSharp ve Azure gibi diğer .NET ekosistemi yanı sıra .NET standart API'lerini içerir.

## <a name="how-to-use-portability-analyzer"></a>Taşınabilirlik Çözümleyicisi'ni kullanma

.NET taşınabilirlik Analyzer'ı kullanmaya başlamak için önce uzantısını yükleyip gerek [Visual Studio Market'te](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Visual Studio 2015 ve Visual Studio 2017 üzerinde çalışır. Visual Studio yapılandırma **Çözümle** > **taşınabilirlik Çözümleyicisi ayarları** ve hedef platformları seçin.

![Taşınabilirlik ekran görüntüsü](./media/portability-analyzer/portability-screenshot.png)

Tüm projenizi analiz etmek için projenize sağ tıklayın **Çözüm Gezgini** seçip **analiz derleme taşınabilirlik**. Aksi takdirde, Git **Çözümle** menü ve Seç **analiz derleme taşınabilirlik**. Buradan, projenizin çalıştırılabilir veya DLL seçin.

![Taşınabilirlik Çözüm Gezgini](./media/portability-analyzer/portability-solution-explorer.png)

Analiz çalıştırdıktan sonra .NET taşınabilirlik raporunuzu görürsünüz. Yalnızca hedef platformu tarafından desteklenmeyen türlerini listede görünür ve önerileri gözden geçirebilirsiniz **iletileri** sekmesinde **hata listesi**. Sorunlu alanları doğrudan da atlayabilirsiniz **iletileri** sekmesi.

![Taşınabilirlik raporu](./media/portability-analyzer/portability-report.png)

Visual Studio kullanmak istemiyor musunuz? Komut isteminden taşınabilirlik Çözümleyicisi'ni de kullanabilirsiniz. Yalnızca karşıdan [API taşınabilirlik Çözümleyicisi](http://www.microsoft.com/download/details.aspx?id=42678).

*   Geçerli dizin çözümlemek için aşağıdaki komutu yazın: `\...\ApiPort.exe analyze -f .`
*   Belirli bir .dll dosyaları listesini çözümlemek için aşağıdaki komutu yazın: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`

.NET taşınabilirlik raporunuzu bir Excel dosyası olarak kaydedilir (*.xlsx*) geçerli dizininizde. **Ayrıntıları** Excel çalışma kitabı sekmesi daha fazla bilgi içerir.

.NET taşınabilirlik Çözümleyicisi hakkında daha fazla bilgi için ziyaret [GitHub belgelerine](https://github.com/Microsoft/dotnet-apiport#documentation) ve [A kısa bakabilir .NET taşınabilirlik Çözümleyicisi](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Channel 9 video.
