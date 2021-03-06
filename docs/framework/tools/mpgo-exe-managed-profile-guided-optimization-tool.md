---
title: Mpgo.exe (Yönetilen Profil Temelli İyileştirme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Mpgo.exe
- training scenarios, generating profiles with
- Managed Profile Guided Optimization Tool
- Ngen.exe
- Ngen.exe, profilers and native images
ms.assetid: f6976502-a000-4fbe-aaf5-a7aab9ce4ec2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42e1fb080ac0af34c621cef3a991cad7bcf603ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (Yönetilen Profil Temelli İyileştirme Aracı)
Yönetilen profil temelli iyileştirme Aracı (Mpgo.exe) tarafından oluşturulan yerel görüntü derlemeleri en iyi duruma getirmek için son kullanıcı senaryoları kullanan bir komut satırı aracıdır [yerel Görüntü Oluşturucu (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). Bu araç, profil verilerini oluşturan eğitim senaryolarını çalıştırmanızı sağlar. [Yerel Görüntü Oluşturucu (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) kendi oluşturulan yerel görüntü uygulama derlemeleri iyileştirmek için bu verileri kullanır. Eğitim senaryosu, uygulamanızın beklenen bir kullanımına ilişkin denemedir. Mpgo.exe, Visual Studio Ultimate 2012 ve sonraki sürümlerinde kullanılabilir. İle başlayarak [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], ayrıca Mpgo.exe en iyi duruma getirmek için kullanabileceğiniz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.  
  
 Profil destekli en iyi duruma getirme süreci, eğitim senaryolarından veri toplayıp yerel görüntülerin düzenini en iyi duruma getirmek üzere onları kullanarak verimi, bellek kullanımını (çalışma kümesi boyutu) ve uygulama başlatma süresini iyileştirir.  
  
 Ara Dil (IL) derlemeleri için başlatma süresi ve çalışma kümesi boyutuyla ilgili performansı sorunlarıyla karşılaştığınızda, just-in-time (JIT) (tam zamanında) derleme maliyetlerini ortadan kaldırmak ve kod paylaşımını kolaylaştırmak için ilk Ngen.exe'yi kullanmanızı öneririz. Ek geliştirmeler gerekiyorsa, uygulamanızı daha ileri düzeyde iyi hale getirmek etmek için Mpgo.exe kullanabilirsiniz. Performans artışlarını değerlendirmek için temel olarak, en iyi duruma getirilmemiş yerel görüntü derlemelerindeki performans verilerini kullanabilirsiniz. Mpgo.exe kullanıldığında soğuk başlangıç sürelerinde kısalma ve çalışma kümesi boyutunda azalma görülebilir. Mpgo.exe, en iyi duruma getirilmiş yerel görüntü derlemeleri oluşturmak için Ngen.exe'yi kullanan IL derlemelerine bilgi ekler. Daha fazla bilgi için bkz: Giriş [Masaüstü uygulamalarınızın Başlat performans geliştirme](http://go.microsoft.com/fwlink/p/?LinkId=248943) .NET Web günlüğündeki.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, yönetici kimlik bilgileriyle Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın ve komut istemine aşağıdaki komutu yazın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Masaüstü uygulamaları için:  
  
```  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
 İçin [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
#### <a name="parameters"></a>Parametreler  
 Mpgo.exe için tüm bağımsız değişkenler büyük/küçük harfe duyarsızdır. Komutlara önek olarak bir tire işareti eklenir.  
  
> [!NOTE]
>  Kullanabilirsiniz `–Scenario` veya `–Import` gerekli komutu, ancak ikisini olarak. Belirtirseniz gerekli parametrelerin hiçbiri kullanılan `–Reset` seçeneği.  
  
|Gerekli parametre|Açıklama|  
|------------------------|-----------------|  
|`-Scenario` \<*komutu*><br /><br /> —veya—<br /><br /> `-Scenario` \<*packageName*><br /><br /> -veya-<br /><br /> `-Import` \<*Dizin*>|Masaüstü uygulamaları için kullanmak `–Scenario` istediğiniz iyileştirmek herhangi bir komut satırı bağımsız değişkeni de dahil olmak üzere uygulamayı çalıştırmak için komutu belirtmek için. Üç adet çift tırnak işaretleri kullanın *komutu* boşluklar; içeren bir yolunu belirtir, örneğin: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. Çift tırnak işaretleri kullanmayın; Bunlar düzgün çalışmaz *komutu* alanları içerir.<br /><br /> -veya-<br /><br /> İçin [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları, `–Scenario` için profil bilgilerini oluşturmak istediğiniz paketi belirtin. Tam paket adı yerine, paketin görünen adını veya paket aile adını belirtirseniz ve yalnızca tek bir eşleşme varsa Mpgo.exe sağladığınız adla eşleşen paketi seçer. Belirtilen adla eşleşen birden çok paket varsa, Mpgo.exe sizden bir paket seçmenizi ister.<br /><br /> —veya—<br /><br /> Kullanım `-Import` bu en iyi duruma getirme belirtmek için daha önce en iyi duruma getirilmiş derlemelerden veri derlemelerde en iyi duruma getirmek için kullanılması gereken `-AssemblyList`. *Dizin* önceden iyileştirilmiş dosyaları içeren dizini belirtir. Belirtilen derlemelere `–AssemblyList` veya `–AssemblyListFile` verileri içeri aktarılan dosyalarını kullanarak en iyi duruma getirilmesi derlemeleri yeni sürümleri. Derlemelerin eski sürümlerine ait en iyi duruma getirme verilerini kullanmak, senaryoyu yeniden çalıştırmadan derlemelerin yeni sürümlerini en iyi duruma getirmenizi sağlar.  Ancak, içe aktarılan ve hedef derlemeler önemli ölçüde farklı kodlar içeriyorsa, en iyi duruma getirme verileri etkisiz olur. Belirtilen derleme adları `–AssemblyList` veya `–AssemblyListFile` tarafından belirtilen dizininde mevcut olmalıdır `–Import` *directory*. Üç adet çift tırnak işaretleri kullanın *directory* alanları içeren bir yolu belirtir.<br /><br /> Ya da belirtmeniz gerekir `–Scenario` veya `–Import`, ancak parametrelerinin her ikisini de değil.|  
|`-OutDir` \<*Dizin*>|En iyi duruma getirilmiş derlemelerin yerleştirileceği dizin. Çıktı dizini klasöründe bir derleme zaten varsa, yeni bir kopya oluşturulur ve adının sonuna bir dizin numarası; Örneğin: *assemblyname*-1.exe. Çift tırnak işaretleri içine alın *directory* alanları içeren bir yolu belirtir.|  
|`-AssemblyList` \<*assembly1 assembly2...*><br /><br /> —veya—<br /><br /> `-AssemblyListFile` \<*Dosya*>|Hakkında profil bilgileri toplamak istediğiniz derlemeleri (.exe ve .dll dosyaları gibi) boşluklarla ayrılmış olarak içeren bir liste. Belirleyebileceğiniz `C:\Dir\*.dll` veya `*.dll` atanmış veya geçerli çalışma dizininde tüm derlemelerin seçmek için. Daha fazla bilgi için Açıklamalar bölümüne bakın.<br /><br /> —veya—<br /><br /> Her satırda bir derleme olacak şekilde, hakkında profil bilgileri toplamak istediğiniz derlemelerin listesini içeren bir metin dosyası. Bir derleme adı tire işareti (-) ile başlıyorsa, bir derleme dosyası listesi kullanın veya derlemeyi yeniden adlandırın.|  
|`-AppID` \<*AppID*>|Belirtilen paketteki uygulamanın kimliği. Joker karakter kullanıyorsanız (\*), Mpgo.exe uygulama paketinde listeleme dener ve geri döner \< *package_family_name*>! Arıza durumunda uygulama. Başında önek olarak ünlem işareti (!) konmuş bir dize belirtirseniz, Mpgo.exe paket aile adını sağlanan bağımsız değişkenle birleştirir.|  
|`-Timeout` \<*Saniye*>|İzin vermek için süre miktarını [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] önce uygulama çıkar çalıştırmak için uygulamayı.|  
  
|İsteğe bağlı parametre|Açıklama|  
|------------------------|-----------------|  
|`-64bit`|64-bit sistemler için derlemeleri kullanır.  Derlemeniz kendisini 64-bit olarak bildiriyor olsa da 64-bit derlemeler için bu parametreyi belirtmelisiniz.|  
|`-ExeConfig` \<*Dosya adı*>|Senaryonuzun sürüm ve yükleyici bilgilerini sağlamak üzere kullandığı yapılandırma dosyasını belirtir.|  
|`-f`|İmzalanmış olsa da, ikili bir derlemeye profil verilerinin eklenmesini sağlar.  Derleme imzalanmışsa, yeniden imzalanması gerekir; aksi takdirde derleme yüklenemez ve çalıştırılamaz.|  
|`-Reset`|İptal edilen bir profil oluşturma oturumunun derlemelerinizi etkilemediğinden emin olmak için ortamı sıfırlar ve ardından çıkış yapar. Ortam varsayılan olarak bir profil oluşturma oturumundan önce ve sonra sıfırlanır.|  
|`-Timeout` \<*saniye cinsinden süre*>|Profil oluşturma süresini saniye cinsinden belirtir. GUI uygulamaları için, gözlemlenen başlangıç zamanlarınızdan biraz daha büyük bir değer kullanın. Uygulama çalışmaya devam etse de, zaman aşımı süresinin sonunda profil verileri kaydedilir. Bu seçeneği ayarlamazsanız, profil oluşturma işlemi uygulamayı kapanana kadar devam eder, ardından veriler kaydedilir.|  
|`-LeaveNativeImages`|Kullanılan yerel görüntülerin senaryo çalıştırıldıktan sonra kaldırılmayacağını belirtir. Bu seçenek öncelikle senaryo için belirttiğiniz uygulamayı çalıştırırken kullanılır. Mpgo.exe'nin sonraki çalışmaları için yerel görüntülerin yeniden oluşturulmasını önler. Bu seçeneği belirtirseniz, uygulamanızı çalıştırmayı tamamladığınızda, önbellekte üst öğesi olmayan yerel görüntüler olabilir. Bu durumda, aynı senaryo ve derleme listesiyle Mpgo.exe çalıştırın ve kullanın `–RemoveNativeImages` bu yerel görüntüler kaldırmak için parametre.|  
|`-RemoveNativeImages`|Bir çalıştırma temizler nerede `–LeaveNativeImages` belirtildi. Belirtirseniz `-RemoveNativeImages`, Mpgo.exe yoksayar dışında herhangi bir bağımsız değişken `-64bit` ve `–AssemblyList`ve tüm Araçlı yerel görüntüler kaldırdıktan sonra çıkar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her ikisi de kullanabilirsiniz `–AssemblyList` ve `- AssemblyListFile` birden çok kez komut satırında.  
  
 Derlemeleri belirtirken tam yol adları belirtmezseniz, Mpgo.exe geçerli dizinde arar. Yanlış bir yol belirtirseniz, Mpgo.exe bir hata iletisi görüntüler, ancak diğer derlemeler için veri oluşturmaya devam eder. Eğitim senaryosu sırasında yüklenmemiş bir derleme belirtirseniz, o derleme için eğitim verisi oluşturulmaz.  
  
 Listedeki bir derleme genel derleme önbelleğinde ise, profil bilgilerini içerecek şekilde güncelleştirilmez.  Profil bilgilerini toplamak için onu genel derleme önbelleğinden kaldırın.  
  
 Ngen.exe ve Mpgo.exe'nin kullanılması yalnızca yönetilen büyük uygulamalar için önerilir, çünkü önceden derlenmiş yerel görüntülerin yararı genellikle yalnızca çalışma zamanında önemli ölçüde JIT derlemesini kaldırdığında görülür. Mpgo.exe çalışma kümesi yoğun olmayan "Hello World" stili uygulamalar üzerinde çalışan tüm avantajları sağlamaz ve Mpgo.exe bile profil verilerini toplamak başarısız olabilir.  
  
> [!NOTE]
>  Ngen.exe ve Mpgo.exe, ASP.NET uygulamaları ve Windows Communication Foundation (WCF) hizmetleri için önerilmez.  
  
## <a name="to-use-mpgoexe"></a>Mpgo.exe'yi kullanmak için  
  
1.  Visual Studio Ultimate 2012 ve uygulamanızın yüklü olduğu bir bilgisayar kullanın.  
  
2.  Mpgo.exe'yi bir yönetici olarak gerekli parametrelerle çalıştırın.  Örnek komutlar için sonraki bölüme bakın.  
  
     En iyi duruma getirilmiş Ara dile (IL) derlemeleri tarafından belirtilen klasörde oluşturulan `–OutDir` parametre (Bu örneklerde olduğu `C:\Optimized` klasörü).  
  
3.  Belirtilen dizinden profil bilgilerini içeren yeni IL derlemeler ile Ngen.exe için kullandığınız IL derlemeleri Değiştir `–OutDir`.  
  
4.  Mpgo.exe tarafından sağlanan görüntüleri kullanan uygulama kurulumu en iyi duruma getirilmiş yerel görüntüleri yükler.  
  
## <a name="suggested-workflow"></a>Önerilen İş Akışı  
  
1.  Mpgo.exe ile kullanarak en iyi duruma getirilmiş IL derlemeler kümesini oluşturma `–Scenario` parametresi.  
  
2.  En iyi duruma getirilmiş IL derlemelerini kaynak denetime girin.  
  
3.  Yapı işleminde Mpgo.exe ile çağrı `–Import` parametre oluşturmak için oluşturma sonrası bir adım olarak en iyi duruma getirilmiş Ngen.exe için geçirilecek IL görüntüler.  
  
 Bu işlem tüm derlemelerin en iyi duruma getirilmiş verilere sahip olmasını sağlar. Güncelleştirilmiş en iyi duruma getirilmiş derlemeleri daha sık iade ederseniz (1. ve 2. adım), tüm üretim geliştirme sürecinde performans numaraları daha tutarlı olur.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Visual Studio'dan Mpgo.exe'yi kullanma  
 Visual Studio'dan Mpgo.exe çalıştırabilirsiniz (makalesine bakın [nasıl yapılır: derleme olayları belirtme (C#)](http://msdn.microsoft.com/library/b4ce1ad9-5215-4b6f-b6a2-798b249aa335)) aşağıdaki kısıtlamalarla:  
  
-   Visual Studio makroları aynı zamanda varsayılan olarak sonlarında eğik çizgiler içerdiğinden, sonda eğik çizgileri olan tırnak işaretli yollar kullanamazsınız. (Örneğin, `–OutDir "C:\Output Folder\"` geçersiz.) Bu kısıtlamayı çözmek için sondaki eğik çizgilerden kaçınabilirsiniz. (Örneğin, `-OutDir "$(OutDir)\"` yerine.)  
  
-   Varsayılan olarak, Mpgo.exe Visual Studio yapı yolu üzerinde değildir. Yolu Visual Studio'ya eklemeli ya da Mpgo komut satırında tam yolu belirtmelisiniz. Kullanabilirsiniz `–Scenario` veya `–Import` Visual Studio'da oluşturma sonrası olay parametresi. Ancak, tipik bir işlem kullanmaktır `–Scenario` birinde bir kez bir Visual Studio Geliştirici komut istemine ve ardından `–Import` her yapıdan sonra; en iyi duruma getirilmiş derlemeleri güncelleştirmek için örneğin: `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.  
  
<a name="samples"></a>   
## <a name="examples"></a>Örnekler  
 Visual Studio geliştirici komut isteminden çalıştırılan aşağıdaki Mpgo.exe komutu bir vergi uygulamasını en iyi duruma getirir:  
  
```  
mpgo –scenario "C:\MyApp\MyTax.exe /params par" –AssemblyList Mytax.dll MyTaxUtil2011.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Aşağıdaki Mpgo.exe komut bir ses uygulamasını en iyi duruma getirir:  
  
```  
mpgo –scenario "C:\MyApp\wav2wma.exe –input song1.wav –output song1.wma" –AssemblyList transcode.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Aşağıdaki Mpgo.exe komutu yeni sürümleri en iyi duruma getirmek için daha önce en iyi duruma getirilmiş derlemelere ait verileri kullanır:  
  
```  
mpgo.exe -import "C:\Optimized" -assemblylist "C:\MyApp\MyTax.dll" "C:\MyApp\MyTaxUtil2011.dll" -outdir C:\ReOptimized  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ngen.exe (Yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)  
 [Masaüstü uygulamalarınızın başlatma performansı iyileştirme](http://go.microsoft.com/fwlink/p/?LinkId=248943)  
 [.NET 4.5, performans iyileştirmeleri genel bakış](http://go.microsoft.com/fwlink/p/?LinkId=249131)
