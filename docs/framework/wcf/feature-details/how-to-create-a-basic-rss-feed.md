---
title: 'Nasıl Yapılır: Temel Bir RSS Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
ms.openlocfilehash: d5b62d968c38401a19fc9009954450bef210e5a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-basic-rss-feed"></a>Nasıl Yapılır: Temel Bir RSS Akışı Oluşturma
Windows Communication Foundation (WCF), akışı bir dağıtım kullanıma sunan bir hizmet oluşturmanıza olanak sağlar. Bu konu, akışı bir RSS dağıtım gösteren bir dağıtım hizmetin nasıl oluşturulacağını açıklar.  
  
### <a name="to-create-a-basic-syndication-service"></a>Bir temel dağıtım hizmet oluşturmak için  
  
1.  İle işaretlenen arabirimini kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği. Bir dağıtım akışı döndürmelidir olarak sunulan her işlem bir <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> nesnesi.  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Geçerli tüm hizmet işlemleri <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği, HTTP GET isteklerine eşlendi. İşlemi farklı bir HTTP yöntem eşleyin <xref:System.ServiceModel.Web.WebInvokeAttribute> yerine. Daha fazla bilgi için bkz: [nasıl yapılır: temel bir WCF Web HTTP hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).  
  
2.  Hizmet sözleşmesini uygulama.  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3.  Oluşturma bir <xref:System.ServiceModel.Syndication.SyndicationFeed> nesne ve yazar, kategori ve açıklama ekleyin.  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4.  Birkaç oluşturmak <xref:System.ServiceModel.Syndication.SyndicationItem> nesneleri.  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5.  Ekleme <xref:System.ServiceModel.Syndication.SyndicationItem> akışa.  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6.  Akış döndür.  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a>Bir hizmet barındırmak için  
  
1.  Oluşturma bir <xref:System.ServiceModel.Web.WebServiceHost> nesnesi.  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2.  Hizmet ana bilgisayarı'nı açın ve kullanıcı ENTER tuşuna bastığında kadar bekleyin.  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Bir HTTP GET ile GetBlog() çağırmak için  
  
1.  Internet Explorer'ı açın, aşağıdaki URL'yi yazın ve ENTER tuşuna basın: http://localhost:8000/BlogService/GetBlog. Hizmetin taban adresi URL içerir (http://localhost:8000/BlogService), göreli adresi uç nokta ve hizmet işlemini çağırın.  
  
### <a name="to-call-getblog-from-code"></a>Koddan GetBlog() çağırmak için  
  
1.  Oluşturma bir <xref:System.Xml.XmlReader> taban adresini ve çağırdığınız yöntemi.  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2.  Statik çağrısı <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> tümleştirilmesidir yöntemi <xref:System.Xml.XmlReader> , yeni oluşturduğunuz.  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     Bu hizmet işlemini çağırır ve yeni bir doldurur <xref:System.ServiceModel.Syndication.SyndicationFeed> hizmet işleminden döndürülen biçimlendirici ile.  
  
3.  Erişim akış nesnesi.  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Örnek  
 Bu örnek için listeleme tam kod aşağıda verilmiştir.  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki kod derlerken System.ServiceModel.dll ve System.ServiceModel.Web.dll başvuru.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
