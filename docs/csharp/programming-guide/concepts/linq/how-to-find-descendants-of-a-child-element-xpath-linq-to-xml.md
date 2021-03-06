---
title: 'Nasıl yapılır: Bul (XPath-LINQ-XML) alt öğenin alt öğeleri (C#)'
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: 548ec3f76a17ef8575e7e5e90ef4cbf8d2666a64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a>Nasıl yapılır: Bul (XPath-LINQ-XML) alt öğenin alt öğeleri (C#)
Bu konuda, belirli bir ada sahip bir alt öğenin alt öğelerini alma gösterilmektedir.  
  
 XPath ifadesi şöyledir:  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a>Örnek  
 Bu örnek bir sözcük işleme belgesini XML gösteriminden metin ayıklama sorunları benzetimini yapar. Bu ilk tüm seçer `Paragraph` öğeleri ve ardından seçer tüm `Text` her alt öğeleri `Paragraph` öğesi. Bu alt öğesi seçin değil `Text` öğeleri `Comment` öğesi.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root>  
  <Paragraph>  
    <Text>This is the start of</Text>  
  </Paragraph>  
  <Comment>  
    <Text>This comment is not part of the paragraph text.</Text>  
  </Comment>  
  <Paragraph>  
    <Annotation Emphasis='true'>  
      <Text> a sentence.</Text>  
    </Annotation>  
  </Paragraph>  
  <Paragraph>  
    <Text>  This is a second sentence.</Text>  
  </Paragraph>  
</Root>");  
  
// LINQ to XML query  
string str1 =  
    root  
    .Elements("Paragraph")  
    .Descendants("Text")  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
// XPath expression  
string str2 =  
    ((IEnumerable)root.XPathEvaluate("./Paragraph//Text/text()"))  
    .Cast<XText>()  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
if (str1 == str2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(str2);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML XPath kullanıcıların (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
