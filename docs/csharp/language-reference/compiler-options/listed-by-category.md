---
title: Kategorilere Göre Listelenen C# Derleyici Seçenekleri
ms.date: 05/15/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: 88ae18b11a48fd8b9610032e913c97d4c15d1c21
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
---
# <a name="c-compiler-options-listed-by-category"></a>Kategorilere Göre Listelenen C# Derleyici Seçenekleri

Aşağıdaki derleyici seçenekleri kategoriye göre sıralanır. Alfabetik bir listesi için bkz: [C# derleyici seçenekleri listelenen alfabetik olarak](listed-alphabetically.md).

## <a name="optimization"></a>En iyi duruma getirme

|Seçenek|Amaç|
|------------|-------------|
|[-filealign](filealign-compiler-option.md)|Çıktı dosyasında bölümlerin boyutunu belirtir.|
|[-optimize](optimize-compiler-option.md)|En iyi duruma getirme etkinleştirir/devre dışı bırakır.|

## <a name="output-files"></a>Çıkış dosyaları

|Seçenek|Amaç|
|------------|-------------|
|[-deterministic](deterministic-compiler-option.md)|Derleyicinin girişleri özdeş ise ikili içerikleri derlemeleri arasında aynı olan bir derleme çıktı neden olur.|
|[-doc](doc-compiler-option.md)|İşlenen belge açıklamaları yazılacak olduğu bir XML dosyası belirtir.|
|[-out](out-compiler-option.md)|Çıkış dosyasını belirtir.|
|[-pathmap](pathmap-compiler-option.md)|Kaynak yolu adları çıktısı için bir eşleme derleyici tarafından belirtin|
|[-pdb](pdb-compiler-option.md)|.Pdb dosyasının konumu ve dosya adını belirtir.|
|[-platform](platform-compiler-option.md)|Çıktı platformunu belirtin.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Derleyici çıktısı için bir dil belirtin.|
|[-refout](refout-compiler-option.md)|Bir referans derlemesini birincil derlemesinin yanı sıra oluşturur.|
|[-refonly](refonly-compiler-option.md)|Bir referans derlemesini birincil derlemesi yerine oluşturur.|
|[-target](target-compiler-option.md)|Beş seçenekten birini kullanarak çıktı dosyasının biçimini belirtir: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: library](target-library-compiler-option.md), [-target: module ](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md), veya [-target: winmdobj](target-winmdobj-compiler-option.md).|
|-modulename:\<dize >|Kaynak modülünün adını belirtin|

## <a name="net-framework-assemblies"></a>.NET framework derlemeleri

|Seçenek|Amaç|
|------------|-------------|
|[-addmodule](addmodule-compiler-option.md)|Bu derleme parçası olarak bir veya daha fazla modül belirtir.|
|[-delaysign](delaysign-compiler-option.md)|Ortak anahtar eklemek için ancak derlemeyi imzasız bırakmayı derleyiciye.|
|[-keycontainer](keycontainer-compiler-option.md)|Şifreleme anahtarı kapsayıcısının adını belirtir.|
|[-keyfile](keyfile-compiler-option.md)|Şifreleme anahtarını içeren dosya adını belirtir.|
|[-lib](lib-compiler-option.md)|Tarafından başvurulan derlemelerin konumunu belirtir [-başvuru](reference-compiler-option.md).|
|[-nostdlib](nostdlib-compiler-option.md)|Standart Kitaplığı (mscorlib.dll) almamanız için derleyicisi bildirir.|
|[-publicsign](publicsign-compiler-option.md)|Derleme imzalama olmadan bir ortak anahtar geçerli, ancak derleme imzalanmamış belirten derlemede bit ayarlayın.|
|[-reference](reference-compiler-option.md)|Meta veriler içeren bir derleme bir dosyadan içeri aktarır.|
|-Çözümleyicisi|Bu derlemedeki çözümleyiciler çalıştırın (kısa form: / a)|
|-additionalfile|Kod oluşturma doğrudan etkilemez ancak çözümleyicileri tarafından hatalar veya uyarılar üretmek için kullanılabilir başka dosya adları.|

## <a name="debuggingerror-checking"></a>Hata ayıklama hata denetimi

|Seçenek|Amaç|
|------------|-------------|
|[-bugreport](bugreport-compiler-option.md)|Bir hata raporu kolaylaştırır bilgilerini içeren bir dosya oluşturur.|
|[-checked](checked-compiler-option.md)|Tamsayı veri türü sınırlarına taşar aritmetik çalışma zamanında bir özel durum neden olup olmayacağını belirtir.|
|[-debug](debug-compiler-option.md)|Hata ayıklama bilgisi yayması için görevlendirin.|
|[-errorreport](errorreport-compiler-option.md)|Hata Raporlama davranışını ayarlar.|
|[-fullpaths](fullpaths-compiler-option.md)|Derleyici çıktısında mutlak dosya yolunu belirtir.|
|[-nowarn](nowarn-compiler-option.md)|Derleyicinin belirtilen uyarılarının oluşturulmasını önler.|
|[-warn](warn-compiler-option.md)|Uyarı düzeyi ayarlar.|
|[-warnaserror](warnaserror-compiler-option.md)|Hatalar için uyarıları yükseltir.|
|-ruleset:\<dosyası >|Belirli Tanılama'yı devre dışı bırakan bir ruleset belirtin.|

## <a name="preprocessor"></a>Ön işlemci

|Seçenek|Amaç|
|------------|-------------|
|[-define](define-compiler-option.md)|Önişlemci simgelerini tanımlar.|

## <a name="resources"></a>Kaynaklar

|Seçenek|Amaç|
|------------|-------------|
|[-link](link-compiler-option.md)|COM türü bilgileri, belirtilen derlemelerde proje kullanılabilmesini sağlar.|
|[-linkresource](linkresource-compiler-option.md)|Yönetilen kaynak bağlantısını oluşturur.|
|[-resource](resource-compiler-option.md)|.NET Framework kaynağı çıkış dosyası içine katıştırır.|
|[-win32icon](win32icon-compiler-option.md)|Çıktı dosyasına eklemek için bir .ico dosyasını belirtir.|
|[-win32res](win32res-compiler-option.md)|Çıktı dosyasına eklemek için bir Win32 kaynağı belirtir.|

## <a name="miscellaneous"></a>Çeşitli

|Seçenek|Amaç|
|------------|-------------|
|[@](response-file-compiler-option.md)|Bir yanıt dosyası belirtir.|
|[-?](help-compiler-option.md)|Stdout derleyici seçenekleri listeler.|
|[-baseaddress](baseaddress-compiler-option.md)|Tercih edilen temel adrese DLL yükleneceği belirtir.|
|[-codepage](codepage-compiler-option.md)|Derlemedeki tüm kaynak kodu dosyaları için kullanmak üzere kod sayfasını belirtir.|
|[-Yardım](help-compiler-option.md)|Stdout derleyici seçenekleri listeler.|
|[-highentropyva](highentropyva-compiler-option.md)|Yürütülebilir dosya adres boşluğu düzeni rastgele seçimini (ASLR) desteklediğini belirtir.|
|[-langversion](langversion-compiler-option.md)|Dil sürümünü belirtin: varsayılan, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 ya da son |
|[-main](main-compiler-option.md)|Konumunu belirten **ana** yöntemi.|
|[-noconfig](noconfig-compiler-option.md)|Csc.rsp ile derleme değil derleyiciye.|
|[-nologo](nologo-compiler-option.md)|Derleyici başlık bilgilerini gizler.|
|[-recurse](recurse-compiler-option.md)|Alt dizinleri derlemek kaynak dosyaları için arar.|
|[-subsystemversion](subsystemversion-compiler-option.md)|En düşük sürüm yürütülebilir dosyasını kullanabilirsiniz alt sisteminin belirtir.|
|[-unsafe](unsafe-compiler-option.md)|Kullanan kodu derlemesini etkinleştirir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) anahtar sözcüğü.|
|[-utf8output](utf8output-compiler-option.md)|UTF-8 kodlaması kullanarak derleyici çıkışı görüntülenir.|
|-Paralel [+&#124;-]|Eş zamanlı yapı (+) kullanılıp kullanılmayacağını belirtir.|
|-checksumalgorithm:\<algoritma >|PDB içinde depolanan kaynak dosya sağlama toplamı hesaplama algoritması belirtin.  Desteklenen değerler: SHA1 (varsayılan) veya SHA256.|

## <a name="obsolete-options"></a>Artık kullanılmayan seçenekleri

|Seçenek|Amaç|
|---|---|
|-artan|Artımlı derleme sağlar.|

## <a name="see-also"></a>Ayrıca Bkz.

 [C# Derleyici Seçenekleri](index.md)  
 [Alfabetik Listelenmiş C# Derleyici Seçenekleri](listed-alphabetically.md)  
 [Nasıl yapılır: Visual Studio Komut Satırı için Ortam Değişkenlerini Ayarlama](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
