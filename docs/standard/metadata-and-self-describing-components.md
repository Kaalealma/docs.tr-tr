---
title: Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- runtime, metadata
- languages, interoperability
- portable executable files, metadata
- self-describing files
- metadata, about metadata
- common language runtime, metadata
- PE files, metadata
- components [.NET Framework], metadata
ms.assetid: 3dd13c5d-a508-455b-8dce-0a852882a5a7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bc603d90ae4636ac50ab9cbabf7d176309498b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="metadata-and-self-describing-components"></a>Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler
Geçmişte, tek bir dilde yazılmış bir yazılım bileşeni (.exe veya .dll) başka bir dilde yazılmış bir yazılım bileşeni kolayca kullanılamadı. COM bu sorunun çözümüne yönelik bir adım sağlanır. .NET Framework bileşenini birlikte çalışabilirlik bile ek bildirim temelli bilgi tüm modülleri ve derlemeleri Yayma derleyicileri vererek kolaylaştırır. Meta veri olarak adlandırılan bu bilgi, sorunsuz bir şekilde etkileşim kurmak için bileşenleri yardımcı olur.  
  
 Meta veriler, bir ortak dil çalışma zamanı taşınabilir yürütülebilir (PE) dosyasında veya bellekte depolanır programınızı açıklayan ikili bilgilerdir. PE dosyasına kodunuzu derlerken meta veri dosyasının bir bölümünü eklenir ve kodunuzu Microsoft Ara dili (MSIL) dönüştürülür ve dosyanın başka bir bölümünü eklenir. Her tür ve tanımlanmış ve bir modül veya derleme başvurulan üye meta veri içinde açıklanmıştır. Kod yürütüldüğünde, çalışma zamanı meta veri belleğe yükler ve kodunuzu 's sınıflar, üyeler, devralma ve benzeri hakkında bilgi bulmak için başvurur.  
  
 Meta veriler, her tür ve üye bir dilden şekilde kodunuzda tanımlanan açıklar. Meta veriler aşağıdaki bilgileri depolar:  
  
-   Derleme açıklaması.  
  
    -   Kimliği (ad, sürüm, kültür, ortak anahtar).  
  
    -   Verilen türleri.  
  
    -   Bu derlemeye bağımlı diğer derlemeler.  
  
    -   Çalıştırmak için gereken güvenlik izinleri.  
  
-   Türleri açıklaması.  
  
    -   Adı, görünürlük, temel sınıf ve arabirimler uygulanmadı.  
  
    -   Üyeler (yöntemler, alanları, özellikleri, olaylar, iç içe geçmiş türler).  
  
-   Öznitelikler.  
  
    -   Türleri ve üyeleri değiştirmek ek açıklayıcı öğeler.  
  
## <a name="benefits-of-metadata"></a>Meta veri yararları  
 Meta veri basit bir programlama modeline anahtarıdır ve arabirim tanım dili (IDL) dosyaları, üst bilgi dosyaları veya herhangi bir dış yöntemini bileşen başvuru gereksinimini ortadan kaldırır. Meta veri Geliştirici ve kullanıcı tarafından görünmeyen bir dilden şekilde kendilerini otomatik olarak tanımlamak .NET Framework dilleri etkinleştirir. Ayrıca, meta veri kullanımı ile öznitelikleri genişletilebilir. Meta veriler aşağıdaki yararları sağlar:  
  
-   Kendiliğinden açıklayıcı dosyalar.  
  
     Ortak dil çalışma zamanı modülleri ve derlemeler kendiliğinden açıklayıcı. Bir modülün meta verileri başka bir modül ile etkileşim kurmak için gereken her şeyi içerir. Tanım ve uygulama için bir dosya kullanabilmeniz için meta verileri otomatik olarak COM, IDL işlevselliğini sağlar. Çalışma zamanı modülleri ve derlemeler bile işletim sistemiyle kayıt gerektirmez. Sonuç olarak, her zaman çalışma zamanı tarafından kullanılan açıklamaları gerçek bir kod uygulamalarının güvenilirliğini artırır, derlenmiş dosyanızdaki yansıtır.  
  
-   Diller arası birlikte çalışabilirlik ve daha kolay bileşen tabanlı tasarım.  
  
     Meta veriler, farklı bir dilde PE dosyasından bir sınıf devralmak derlenmiş kod hakkında gerekli tüm bilgileri sağlar. Tüm yönetilen (ortak dil çalışma zamanı hedefleyen herhangi bir dil) açık sıralama veya özel birlikte çalışabilirlik kodu kullanma hakkında endişelenmeden dilde sınıfının bir örneğini oluşturabilirsiniz.  
  
-   Öznitelikler.  
  
     .NET Framework meta verileri derlenmiş dosyanızda öznitelikler, denen, belirli türde bildirme olanak sağlar. Öznitelikler .NET Framework bulunabilir ve daha ayrıntılı olarak programınızın çalışma zamanında biçimini denetlemek için kullanılır. Ayrıca, kullanıcı tanımlı özel öznitelikler aracılığıyla .NET Framework dosyalarına kendi özel meta verileri yayma. Daha fazla bilgi için bkz: [öznitelikleri](../../docs/standard/attributes/index.md).  
  
## <a name="metadata-and-the-pe-file-structure"></a>Meta Veri ve PE Dosya Yapısı  
 Metaveriler .NET Framework taşınabilir yürütülebilir (PE) dosyasının bir bölümünde saklanırken, Microsoft ara dili (MSIL) PE dosyasının başka bir bölümünde saklanır. Dosyanın metaveri bölümü bir dizi tablo ve yığın veri yapısı içerir. MSIL bölümü, MSIL kodu ve PE dosyasının metaveri bölümüne atıfta bulunan metaveri belirteçleri içerir. Araçları gibi kullandığınızda, meta veri simgesi karşılaşabileceğiniz [MSIL ayrıştırıcı (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) kodunuzu görüntülemek için kullanıcının MSIL, örneğin.  
  
### <a name="metadata-tables-and-heaps"></a>Metaveri Tabloları ve Yığınlar  
 Her metaveri tablosu, programınızın öğeleri hakkında bilgi içerir. Örneğin, bir metaveri tablosu kodunuzdaki sınıfları, başka bir tablo alanları, vb. açıklar. Eğer kodunuzda on sınıf varsa, sınıf tablosu her sınıf için bir tane olmak üzere on satır içerir. Metaveri tabloları diğer tablolara ve yığınlara atıfta bulunur. Örneğin, sınıfların metaveri tablosu, metotların tablosuna atıfta bulunur.  
  
 Metaveri, ayrıca, dört yığın yapısında bilgi tutar: Dize, blob, kullanıcı dizesi ve GUID. Türleri ve üyeleri adlandırmak için kullanılan tüm dizeler dize yığınında tutulur. Örneğin, bir yöntem tablosu belirli bir yöntemin adını doğrudan saklamaz; bunun yerine, dize yığınındaki yöntem adına işaret eder.  
  
### <a name="metadata-tokens"></a>Meta Veri Belirteçleri  
 Her metaveri tablosunun her satırı, PE dosyasının MSIL bölümünde bir metaveri belirteci tarafından benzersiz olarak tanımlanır. Metaveri belirteçleri, kavramsal olarak MSIL'de kalıcı olarak bulunan ve belirli bir metaveri tablosuna atıfta bulunan işaretçilere benzer.  
  
 Metaveri belirteci, dört baytlık bir sayıdır. Üstteki bayt, belirtecin atıfta bulunduğu belirli bir metaveri tablosunu (yöntem, tür vb.) belirtir. Diğer üç bayt, metaveri tablosunda açıklanan programlama öğesine karşılık gelen satırı belirtir. Eğer C# dilinde bir yöntem tanımlayıp bunu bir PE dosyası olarak derlerseniz, PE dosyasının MSIL bölümünde aşağıdaki metaveri belirteci bulunabilir:  
  
```  
0x06000004  
```  
  
 Üst bayt (`0x06`) bu olduğunu belirten bir **MethodDef** belirteci. Alt üç bayt (`000004`) Dördüncü satırında aramak için ortak dil çalışma zamanı söyler **MethodDef** tablosu için bu yöntem tanımını açıklayan bilgiler.  
  
### <a name="metadata-within-a-pe-file"></a>Bir PE Dosyasının İçindeki Metaveriler  
 Bir program ortak dil çalışma zamanı için derlendiğinde, üç bölümden oluşan bir PE dosyasına dönüştürülür. Aşağıdaki tabloda her bölümün içeriği açıklanmaktadır.  
  
|PE bölümü|PE bölümünün içerikleri|  
|----------------|----------------------------|  
|PE üst bilgisi|PE dosyasının ana bölümlerinin ve giriş noktası adresinin dizini.<br /><br /> Çalışma zamanı, bu bilgileri, dosyayı bir PE dosyası olarak tanımlamak ve programı belleğe yüklerken yürütmenin nereden başlayacağını belirlemek için kullanır.|  
|MSIL yönergeleri|Kodunuzu oluşturan Microsoft ara dili (MSIL) yönergeleri. Birçok MSIL yönergesi metaveri belirteçleri ile birlikte bulunur.|  
|Meta Veriler|Metaveri tabloları ve yığınlar Çalışma zamanı, bu bölümü, kodunuzdaki tüm türler ve üyeler hakkında bilgi kaydetmek için kullanır. Bu bölüm ayrıca özel öznitelikler ve güvenlik bilgileri de içerir.|  
  
## <a name="run-time-use-of-metadata"></a>Meta Verilerin Çalışma Zamanında Kullanımı  
 Meta verileri ve ortak dil çalışma zamanında rolü daha iyi anlamak için basit bir program oluşturmak ve meta veri çalışma zamanı ömrü nasıl etkilediğini göstermek faydalı olabilir. Aşağıdaki kod örneğinde adlı bir sınıf içinde iki yöntem gösterilmektedir `MyApp`. `Main` Yöntemdir program giriş noktası sırada `Add` yöntemi yalnızca iki tamsayı bağımsız toplamını döndürür.  
  
```vb  
Public Class MyApp  
   Public Shared Sub Main()  
      Dim ValueOne As Integer = 10  
      Dim ValueTwo As Integer = 20  
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo))  
   End Sub  
  
   Public Shared Function Add(One As Integer, Two As Integer) As Integer  
      Return (One + Two)  
   End Function  
End Class  
```  
  
```csharp  
using System;    
public class MyApp  
{  
   public static int Main()  
   {  
      int ValueOne = 10;  
      int ValueTwo = 20;           
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo));  
      return 0;  
   }  
   public static int Add(int One, int Two)  
   {  
      return (One + Two);  
   }  
}  
```  
  
 Kod çalıştığında, çalışma zamanı modülü belleğe yükler ve bu sınıf için meta veriler başvurur. Yüklenen sonra çalışma zamanı hızlı yerel makine yönergelerine dönüştürmek için yöntemin Microsoft Ara dili (MSIL) akışın kapsamlı çözümlemesi gerçekleştirir. Çalışma zamanı tam zamanında (JIT) derleyici MSIL yönergeleri gerektiği gibi aynı anda yerel makine kod bir yönteme dönüştürmek için kullanır.  
  
 Aşağıdaki örnek, önceki koddan 's üretilen MSIL parçası gösterir `Main` işlevi. MSIL ve tüm .NET Framework kullanarak uygulama meta verileri görüntüleyebilirsiniz [MSIL ayrıştırıcı (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md).  
  
```  
.entrypoint  
.maxstack  3  
.locals ([0] int32 ValueOne,  
         [1] int32 ValueTwo,  
         [2] int32 V_2,  
         [3] int32 V_3)  
IL_0000:  ldc.i4.s   10  
IL_0002:  stloc.0  
IL_0003:  ldc.i4.s   20  
IL_0005:  stloc.1  
IL_0006:  ldstr      "The Value is: {0}"  
IL_000b:  ldloc.0  
IL_000c:  ldloc.1  
IL_000d:  call int32 ConsoleApplication.MyApp::Add(int32,int32) /* 06000003 */  
```  
  
 JIT Derleyici MSIL tüm yöntemi için kapsamlı olarak analiz eder ve verimli yerel yönergeler yöntemi için oluşturur okur. Konumundaki `IL_000d`, meta veri simgesi için `Add` yöntemi (`/*` `06000003 */`) ile karşılaşıldı ve çalışma zamanı üçüncü satır incelediğinizden belirteci kullanır **MethodDef** tablo.  
  
 Aşağıdaki tabloda parçası gösterilmektedir **MethodDef** açıklayan meta veri simgesi tarafından başvurulan tablo `Add` yöntemi. Diğer meta veri tablolarına bu derlemede var ve kendi benzersiz değerlere sahip olsa da, yalnızca bu tablo ele alınmıştır.  
  
|Satır|Göreli sanal adres (RAV)|ImplFlags|Bayraklar|Ad<br /><br /> (String yığın noktalarına.)|İmza (yığın BLOB noktaları.)|  
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|  
|1.|0x00002050|IL<br /><br /> Yönetilen|Ortak<br /><br /> ReuseSlot<br /><br /> SpecialName<br /><br /> RTSpecialName<br /><br /> .ctor|.ctor (oluşturucu)||  
|2|0x00002058|IL<br /><br /> Yönetilen|Ortak<br /><br /> Statik<br /><br /> ReuseSlot|Ana|Dize|  
|3|0x0000208c|IL<br /><br /> Yönetilen|Ortak<br /><br /> Statik<br /><br /> ReuseSlot|Ekle|int, int, int|  
  
 Tablonun her sütunu kodunuzu hakkında önemli bilgiler içerir. **RVA** sütun bu yöntem tanımlar MSIL başlangıç bellek adresini hesaplamak çalışma zamanı sağlar. **ImplFlags** ve **bayrakları** sütunlar (örneğin, yöntemi genel veya özel olup) yöntemi açıklayan bir bit maskesi içerir. **Adı** sütun dizinleri dizesi yığın yönteminden adı. **İmza** sütun dizinleri yöntemin imzası blob yığınındaki tanımı.  
  
 Çalışma zamanı istenen uzaklık adresinden hesaplar **RVA** üçüncü satır sütununda ve bu adresi yeni adresine devam eder JIT Derleyici döndürür. JIT derleme başka bir meta veri simgesi bulduğu ve işlem yinelenir kadar yeni adresinde MSIL işlemeye devam eder.  
  
 Meta verileri kullanarak, çalışma zamanı kodunuzu yükle ve yerel makine talimatları işlemek gerekli tüm bilgilere erişebilir. Bu şekilde, kendiliğinden açıklayıcı dosyalar meta veri sağlar ve ortak tür sistemi diller arası devralma ile birlikte.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Öznitelikler](../../docs/standard/attributes/index.md)|Öznitelikleri uygulama, özel öznitelikler yazma ve özniteliklerde depolanan bilgileri almak açıklar.|
