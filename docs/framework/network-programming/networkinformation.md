---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 964e76a008e1c18fe9f609f1dd63bce565e95d44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="networkinformation"></a>NetworkInformation
<xref:System.Net.NetworkInformation> Ad alanı, ağ olayları, değişiklikleri, istatistikleri ve özellikler hakkında bilgi toplamak sağlar. Kullanarak uzak ana bilgisayar erişilebilir olup olmadığını belirleyebilirsiniz <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> sınıfı.  
  
## <a name="network-availability-and-events"></a>Ağ kullanılabilirliğini ve olaylar  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> Sınıfı, kullanılabilirlik ve ağ adresi değişip değişmediğini belirlemek sağlar. Bu sınıf kullanmak için değişiklik işlemek için bir olay işleyicisi oluşturun ve bu ilişkilendirmeyi bir <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> veya <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>. Daha fazla bilgi için bkz: [nasıl yapılır: Ağ kullanılabilirliğini algılamak ve adresi değişiklikleri](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).  
  
## <a name="network-statistics-and-properties"></a>Ağ istatistikleri ve özellikleri  
 Bir arabirim veya protokolü temelinde ağ istatistikleri ve özellikleri toplayabilirsiniz. <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, Ve <xref:System.Net.NetworkInformation.PhysicalAddress> sınıfları belirli bir ağ arabirimi hakkında bilgi vermek sırada <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, ve <xref:System.Net.NetworkInformation.UdpStatistics> sınıfları bilgi verin Katman 3 hakkında ve 4 paketleri katman. Daha fazla bilgi için bkz: [nasıl yapılır: arabirim almak ve protokol bilgileri](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Uzak bir ana bilgisayar erişilebilir olup olmadığını belirler  
 Kullanabileceğiniz <xref:System.Net.NetworkInformation.Ping> uzak bir ana bilgisayar ve yukarı, ağ üzerinde ve erişilebilir olup olmadığını belirlemek için sınıf. Daha fazla bilgi için bkz: [nasıl yapılır: bir ana bilgisayara Ping](../../../docs/framework/network-programming/how-to-ping-a-host.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ Programlama Örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Ağ bilgi teknolojisi örnek](http://go.microsoft.com/fwlink/?LinkID=179564)  
 [NetStat araç teknolojisi örneği](http://go.microsoft.com/fwlink/?LinkID=179562)  
 [Ping istemci teknolojisi örnek](http://go.microsoft.com/fwlink/?LinkID=179565)
