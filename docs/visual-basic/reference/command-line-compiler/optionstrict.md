---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: da1bd6d3b6746561655a82cd49aa0014563a1d40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-optionstrict"></a>-optionstrict
Örtük tür dönüşümleri kısıtlamak için kesin türü anlamları zorlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. `-optionstrict+` Seçeneği örtük tür dönüştürmesi kısıtlar. Bu seçenek için varsayılan değer `-optionstrict-`. `-optionstrict+` Seçenektir aynı `-optionstrict`. Her iki izin türü anlamları için kullanabilirsiniz.  
  
 `custom`  
 Gerekli. Kesin dil semantiği değil dikkate olduğunda uyar.  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman `-optionstrict+` , yalnızca genişletme tür dönüştürmeleri örtük olarak sunulabilir etkindir. Örtük daraltma türü dönüşümleri, atama gibi bir `Decimal` türü tamsayı türü nesnesini, hata olarak bildirilir.  
  
 Örtük daraltma tür dönüştürmeleri için uyarıları oluşturmak için kullanmak `-optionstrict:custom`. Kullanım `-nowarn:numberlist` belirli uyarılarını gözardı etme ve `-warnaserror:numberlist` belirli uyarıları hata olarak değerlendirmek için.  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Visual Studio IDE'de - optionstrict ayarlamak için  
  
1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri.**   
  
2.  Tıklatın **derleme** sekmesi.  
  
3.  Değer değiştirme **Option Strict** kutusu.  
  
### <a name="to-set--optionstrict-programmatically"></a>-Optionstrict programlı olarak ayarlamak için  
  
-   Bkz: [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `Test.vb` kullanarak strict türü anlamları.  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [-warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
