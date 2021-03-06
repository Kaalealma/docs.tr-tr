---
title: Bir ikili ilk işlenen &#39;varsa&#39; ifadesi null olmalı veya bir başvuru türü
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 76078d315b2c32a2a29aa652a65b463622afec36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a>Bir ikili ilk işlenen &#39;varsa&#39; ifadesi null olmalı veya bir başvuru türü
Bir `If` ifadesi, iki veya üç bağımsız değişken alabilir. Yalnızca iki bağımsız değişken gönderdiğinizde, ilk bağımsız değişkeni bir başvuru türü veya boş değer atanabilir bir tür olmalıdır. İlk bağımsız değişkeni için herhangi bir şey dışında değerlendirilirse `Nothing`, bu değer döndürülür. İlk bağımsız değişken değerlendirilirse `Nothing`, ikinci bağımsız değişkeni değerlendirilir ve döndürdü.  
  
 Örneğin, aşağıdaki kod iki içeren `If` ifadeleri, üç bağımsız değişkenlerle diğeri iki bağımsız değişkenlere sahip. İfadeleri hesaplamak ve aynı değeri döndürür.  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 Aşağıdaki ifadeler bu hataya neden:  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **Hata Kimliği:** BC33107  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   İlk bağımsız değişkeni bir boş değer atanabilir veya reference türü böylece kodu değiştiremezsiniz, üç değişkenine dönüştürmeyi göz önüne `If` ifadesi veya bir `If...Then...Else` deyimi.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [If İşleci](../../../visual-basic/language-reference/operators/if-operator.md)  
 [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Boş Değer Atanabilen Değer Türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
