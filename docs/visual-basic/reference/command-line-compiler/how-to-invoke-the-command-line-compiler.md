---
title: 'Nasıl yapılır: Komut Satırı Derleyicisini Çağırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 0b835bb5654574a5aa6f32eede1e942b11e7dcb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Nasıl yapılır: Komut Satırı Derleyicisini Çağırma (Visual Basic)
Komut satırına olarak da bilinen MS-DOS İstemi yürütülebilir dosyanın adını yazarak komut satırı derleyicisini çağırma. Varsayılan Windows komut istemi derleme yaparsanız, yürütülebilir dosyanın tam yolunu yazmanız gerekir. Bu varsayılan davranışı geçersiz kılmak için Visual Studio komut istemi kullanabilir veya PATH ortam değişkeni değiştirin. Her ikisi de, herhangi bir dizinden derleyici adını yazarak derlemek izin verir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a>Visual Studio komut istemi kullanarak derleyici çağırmak için  
  
1.  Microsoft Visual Studio program grubunu Visual Studio Araçları program klasördeki açın.  
  
2.  Visual Studio yüklüyse, derleyici, makinenizde herhangi bir dizinden erişmek için Visual Studio Komut İstemi'ni kullanabilirsiniz.  
  
3.  Visual Studio komut istemi çağırır.  
  
4.  Komut satırında `vbc.exe` *sourceFileName* yazıp ENTER tuşuna basın.  
  
     Örneğin, kaynak kodunuzu adlı bir dizinde depolanan `SourceFiles`, türü ve komut istemi açmak `cd SourceFiles` bu dizine gidin. Dizin adlı bir kaynak dosya içeriyorsa `Source.vb`, yazarak derleme `vbc.exe Source.vb`.  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Windows komut satırından derleyiciye PATH ortam değişkeni ayarlamak için  
  
1.  Yerel diskinize Vbc.exe bulmak için Windows Arama özelliğini kullanın.  
  
     Derleyici bulunduğu dizinin tam adı, Windows dizininin konumu ve sürümünü ".NET Framework'ün yüklü" bağlıdır. ".NET Framework'ün yüklü" birden çok sürüm varsa, hangi sürümün (genellikle en son sürüm) kullanılacağını belirlemeniz gerekir.  
  
2.  Öğesinden, **Başlat** menüsünde sağ **Bilgisayarım**ve ardından **özellikleri** kısayol menüsünden.  
  
3.  Tıklatın **Gelişmiş** sekmesini ve ardından **ortam değişkenleri**.  
  
4.  İçinde **sistem** değişkenleri bölmesinde, **yolu** tıklatın ve liste **Düzenle**.  
  
5.  İçinde **Düzenle sistem** değişken iletişim kutusunda, dizenin sonuna ekleme noktasını Taşı **değişken değeri** alan ve noktalı virgül (;) yazın adım 1'de bulunan tam dizin adı ve ardından.  
  
6.  Tıklatın **Tamam** yaptığınız düzenlemeleri onaylamak ve iletişim kutularını kapatın.  
  
     PATH ortam değişkeni değiştirdikten sonra Visual Basic derleyici Windows komut isteminde herhangi bir dizinden bilgisayarda çalıştırabilirsiniz.  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Windows komut istemi kullanarak derleyici çağırmak için  
  
1.  Gelen **Başlat** menüsünde tıklatın **Donatılar** klasörünü ve ardından açın **Windows Komut İstemi**.  
  
2.  Komut satırında `vbc.exe` *sourceFileName* yazıp ENTER tuşuna basın.  
  
     Örneğin, kaynak kodunuzu adlı bir dizinde depolanan `SourceFiles`, türü ve komut istemi açmak `cd SourceFiles` bu dizine gidin. Dizin adlı bir kaynak dosya içeriyorsa `Source.vb`, yazarak derleme `vbc.exe Source.vb`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
