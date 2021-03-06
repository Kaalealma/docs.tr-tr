---
title: Şema İçeri ve Dışarı Aktarma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
ms.openlocfilehash: c9bb0d6df362380a37ae3079694ab91e9577741d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="schema-import-and-export"></a>Şema İçeri ve Dışarı Aktarma
Windows Communication Foundation (WCF) içeren yeni bir seri hale getirme motoru <xref:System.Runtime.Serialization.DataContractSerializer>. `DataContractSerializer` Arasında çevirir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nesneleri ve XML (her iki yönde). Serileştirici kendisini yanı sıra, ilişkili şema alma ve şema verme mekanizmaları WCF içerir. *Şema* seri hale getirici üreten veya seri durumdan çıkarıcının erişebileceği XML şeklini resmi, kesin ve makine tarafından okunabilir açıklamasıdır. WCF World Wide Web Konsorsiyumu (W3C) XML Şeması Tanım Dili (XSD) çok sayıda üçüncü taraf platformlarıyla yaygın olarak çalışabilir, şema gösterimi olarak kullanır.  
  
 Şema alma bileşen <xref:System.Runtime.Serialization.XsdDataContractImporter>, bir XSD şema belgesi alır ve oluşturur [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sağlayacak şekilde serileştirilmiş forms verilen şemaya karşılık gelen sınıfları (normalde veri sözleşmesi sınıflar).  
  
 Örneğin, aşağıdaki şema parça:  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 (biraz daha fazla okunabilirlik için Basitleştirilmiş) aşağıdaki türü oluşturur.  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 Oluşturulan tür birkaç veri sözleşmesi en iyi uygulama izlediğini unutmayın (bulunan [en iyi uygulamalar: veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)):  
  
-   Tür uygular <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi. Daha fazla bilgi için bkz: [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
-   Veri üyeleri özel alanlar sarmalamak ortak özellikleri olarak uygulanır.  
  
-   Bir parçalı sınıf sınıftır ve oluşturulan kodunu değiştirmeden eklemeleri yapılabilir.  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter> Ters yapmanıza olanak tanır — ile seri hale getirilebilir türler ele `DataContractSerializer` ve bir XSD şema belgesi oluşturabilirsiniz.  
  
## <a name="fidelity-is-not-guaranteed"></a>Doğruluğu garanti edilmez  
 Şema veya türleri toplam doğruluk ile gidiş dönüş olun garanti edilmez. (A *gidiş dönüş* sınıfları kümesi oluşturmak ve bir şema yeniden oluşturmak için sonucu vermek için bir şema içeri aktarmak anlamına gelir.) Aynı şemaya döndürülemez. İşlemi ters da uygunluğunu korumak için kesin değildir. (Şemasına oluşturmak için bir tür dışarı aktarın ve sonra türü geri alın. Bu aynı türde döndürülen düşüktür.)  
  
## <a name="supported-types"></a>Desteklenen türler  
 Veri sözleşmesi modeli yalnızca sınırlı bir alt kümesini WC3 şema destekler. Bu alt uymuyor herhangi bir şema, içeri aktarma işlemi sırasında bir özel durum neden olur. Örneğin, bir XML özniteliği olarak veri üyesi bir veri sözleşmesi seri hale olduğunu belirtmek için yolu yoktur. Bu nedenle, XML öznitelikleri kullanılmasını şemaları desteklenmez ve bir veri sözleşmesine doğru XML projeksiyon oluşturmak mümkün olduğu için özel durumlar içeri aktarma sırasında neden olur.  
  
 Örneğin, aşağıdaki şema parça varsayılan içeri aktarma ayarları kullanarak içeri aktarılamıyor.  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 Daha fazla bilgi için bkz: [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Bir şema veri sözleşmesi kurallarına uymuyor farklı serileştirme motoruna kullanın. Örneğin, <xref:System.Xml.Serialization.XmlSerializer> kendi ayrı şema alma mekanizması kullanır. Ayrıca, desteklenen şema aralığını genişletilmiş olarak özel alma modu yoktur. Bölüm oluşturma hakkında daha fazla bilgi için bkz <xref:System.Xml.Serialization.IXmlSerializable> türlerini [oluşturmak sınıfları içeri aktarma şemaya](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 `XsdDataContractExporter` Destekler [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ile seri hale getirilebilir türler `DataContractSerializer`. Daha fazla bilgi için bkz: [veri sözleşmesi seri hale getirici tarafından desteklenen türleri](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Bu şema kullanılarak oluşturulan Not `XsdDataContractExporter` normalde geçerli veriler, `XsdDataContractImporter` kullanabilirsiniz (sürece <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> şema özelleştirmek için kullanılan).  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.Runtime.Serialization.XsdDataContractImporter>, bkz: [oluşturmak sınıfları içeri aktarma şemaya](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.Runtime.Serialization.XsdDataContractExporter>, bkz: [sınıflardan Şemaları dışarı aktarma](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 [Sınıf Oluşturmak için Şemayı İçeri Aktarma](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)  
 [Sınıflardan Şemaları Dışarı Aktarma](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
