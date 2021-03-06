---
title: Dönüşümleri XPathNodeIterator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d30760ef018c9b2d1264b323b57172417e4ef0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xpathnodeiterator-in-transformations"></a>Dönüşümleri XPathNodeIterator
<xref:System.Xml.XPath.XPathNodeIterator> Küme düğümlerinin bir XML Path dili (XPath) sorgusu veya bir düğüme dönüştürülen sonuç ağacı parçası sonucu olarak oluşturulan üzerinde yinelemek için yöntemler kümesi düğüm kümesi yöntemi kullanarak sağlar. <xref:System.Xml.XPath.XPathNodeIterator> Bu düğüm kümesi içindeki düğümler üzerinden yineleme olanak tanır. Bir düğüm kümesi alındıktan sonra <xref:System.Xml.XPath.XPathNodeIterator> sınıfı düğümleri seçilen kümesi için salt okunur, yalnızca ileri yönlü bir imleç sağlar. Bu yöntemin çağrılması belge sırayla bir sonraki düğüme taşınmasını düğüm kümesi belge sırayla oluşturulur. <xref:System.Xml.XPath.XPathNodeIterator> Kümedeki tüm düğümler düğüm ağacının oluşmuyor. Bunun yerine, ağacında hareket etme gibi işaret temel düğüm gösterme veri, bir tek düğümlü pencere sağlar. Kullanılabilir özellikler ve yöntemler <xref:System.Xml.XPath.XPathNodeIterator> sınıfı, geçerli düğümden bilgi almak etkinleştirin. Kullanılabilir yöntemleri ve özellikleri listesi için bkz: <xref:System.Windows.Forms.ToolBar>.  
  
 Bu yana bir <xref:System.Xml.XPath.XPathNodeIterator> taşır küme düğümleri üzerinde oluşturulan bir XPath sorgusu ve taşır iletmek yalnızca, taşıma kullanarak yoludur <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> yöntemi. Bu yöntemin dönüş türü `Boolean`, döndürme `true` sonraki Seçili düğüme geçerse ve `false` artık seçili düğümler varsa. Döndürürse `true`, aşağıdaki listede kullanılabilir özellikleri gösterir:  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 Bir düğümde zaman aradığınız ayarlamak ilk kez bir çağrı <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> konumlandırmak için yapılmalıdır <xref:System.Xml.XPath.XPathNodeIterator> seçili kümenin ilk düğümü üzerinde. Bu işlem biraz zaman verir döngü yazılacak.  
  
 Aşağıdaki kod örneğinde nasıl iletileceğini gösterir bir <xref:System.Xml.XPath.XPathNodeIterator> için bir <xref:System.Xml.Xsl.XslTransform> bir parametresi olarak <xref:System.Xml.Xsl.XsltArgumentList>. Giriş kodu **books.xml**, ve stil sayfası **text.xsl**. Dosya **test.xml** olan <xref:System.Xml.XPath.XPathDocument>.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
  
Public Class sample  
  
   Public Shared Sub Main()  
      Dim Doc As New XPathDocument("books.xml")  
      Dim nav As XPathNavigator = Doc.CreateNavigator()  
      Dim Iterator As XPathNodeIterator = nav.Select("/bookstore/book")  
  
      Dim arg As New XsltArgumentList()  
      arg.AddParam("param1", "", Iterator)  
  
      Dim xslt As New XslTransform()  
      xslt.Load("test.xsl")  
  
      Dim xd As New XPathDocument("test.xml")  
  
      Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
      xslt.Transform(xd, arg, strmTemp, Nothing)  
   End Sub 'Main  
End Class 'sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
using System.Xml.XPath;  
using System.Text;  
  
public class sample  
{  
    public static void Main()  
    {  
        XPathDocument Doc = new XPathDocument("books.xml");  
        XPathNavigator nav = Doc.CreateNavigator();  
        XPathNodeIterator Iterator = nav.Select("/bookstore/book");  
  
        XsltArgumentList arg = new XsltArgumentList();  
        arg.AddParam("param1", "", Iterator);  
  
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, arg, strmTemp, null);  
    }  
}  
```  
  
## <a name="booksxml"></a>Books.XML  
  
```xml  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database. -->  
<bookstore specialty="novel">  
    <book style="autobiography">  
    <title>Seven Years in Trenton</title>  
        <author>  
            <first-name>Jay</first-name>  
            <last-name>Adams</last-name>  
            <award>Trenton Literary Review Honorable Mention</award>  
            <country>USA</country>  
        </author>  
        <price>12</price>  
    </book>  
    <book style="textbook">  
        <title>History of Trenton</title>  
        <author>  
            <first-name>Kim</first-name>  
            <last-name>Akers</last-name>  
            <publication>  
                Selected Short Stories of  
                <first-name>Scott</first-name>  
                <last-name>Bishop</last-name>  
                <country>US</country>  
            </publication>  
        </author>  
        <price>55</price>  
    </book>  
</bookstore>  
```  
  
## <a name="testxsl"></a>Test.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
xmlns:msxsl="urn:schemas-microsoft-com:xslt" exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes"/>  
<xsl:param name="param1"/>  
  
<xsl:template match="/">  
    <out>  
        <xsl:for-each select="$param1/title">  
            <title><xsl:value-of select="."/></title>  
        </xsl:for-each>  
    </out>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a>Test.XML  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a>Çıktı (out.xml)  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
