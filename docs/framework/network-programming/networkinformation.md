---
title: NetworkInformation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
caps.latest.revision: 5
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3a72eb23c7ad053d6f0fe505668cd037e65d582b
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="networkinformation"></a><span data-ttu-id="64c19-102">NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="64c19-102">NetworkInformation</span></span>
<span data-ttu-id="64c19-103">O namespace <xref:System.Net.NetworkInformation> permite que você colete informações sobre eventos, alterações, estatísticas e propriedades de rede.</span><span class="sxs-lookup"><span data-stu-id="64c19-103">The <xref:System.Net.NetworkInformation> namespace enables you to gather information about network events, changes, statistics, and properties.</span></span> <span data-ttu-id="64c19-104">Você também pode determinar se um host remoto está acessível usando a classe <xref:System.Net.NetworkInformation.Ping?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="64c19-104">You can also determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=fullName> class.</span></span>  
  
## <a name="network-availability-and-events"></a><span data-ttu-id="64c19-105">Disponibilidade de rede e eventos</span><span class="sxs-lookup"><span data-stu-id="64c19-105">Network Availability and Events</span></span>  
 <span data-ttu-id="64c19-106">A classe <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=fullName> permite que você determine se o endereço de rede ou a disponibilidade foi alterada.</span><span class="sxs-lookup"><span data-stu-id="64c19-106">The <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=fullName> class enables you to determine whether the network address or availability has changed.</span></span> <span data-ttu-id="64c19-107">Para usar essa classe, crie um manipulador de eventos para processar a alteração e associe-o a um <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> ou <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="64c19-107">To use this class, create an event handler to process the change, and associate it with a <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> or a <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span></span> <span data-ttu-id="64c19-108">Para obter mais informações, consulte [Como detectar a disponibilidade de rede e alterações de endereço](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).</span><span class="sxs-lookup"><span data-stu-id="64c19-108">For more information, see [How to: Detect Network Availability and Address Changes](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).</span></span>  
  
## <a name="network-statistics-and-properties"></a><span data-ttu-id="64c19-109">Propriedades e estatísticas de rede</span><span class="sxs-lookup"><span data-stu-id="64c19-109">Network Statistics and Properties</span></span>  
 <span data-ttu-id="64c19-110">Você pode coletar estatísticas de rede e propriedades por protocolo ou por interface.</span><span class="sxs-lookup"><span data-stu-id="64c19-110">You can gather network statistics and properties on an interface or protocol basis.</span></span> <span data-ttu-id="64c19-111">As classes <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType> e <xref:System.Net.NetworkInformation.PhysicalAddress> fornecem informações sobre um adaptador de rede específico, enquanto as classes <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics> e <xref:System.Net.NetworkInformation.UdpStatistics> fornecem informações sobre os pacotes de camada 3 e de camada 4.</span><span class="sxs-lookup"><span data-stu-id="64c19-111">The <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, and <xref:System.Net.NetworkInformation.PhysicalAddress> classes give information about a particular network interface, while the <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, and <xref:System.Net.NetworkInformation.UdpStatistics> classes give information about layer 3 and layer 4 packets.</span></span> <span data-ttu-id="64c19-112">Para obter mais informações, consulte [Como obter informações de interface e de protocolo](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).</span><span class="sxs-lookup"><span data-stu-id="64c19-112">For more information, see [How to: Get Interface and Protocol Information](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).</span></span>  
  
## <a name="determine-if-a-remote-host-is-reachable"></a><span data-ttu-id="64c19-113">Determinar se um Host remoto é alcançável</span><span class="sxs-lookup"><span data-stu-id="64c19-113">Determine if a Remote Host is Reachable</span></span>  
 <span data-ttu-id="64c19-114">Você pode usar a classe <xref:System.Net.NetworkInformation.Ping> para determinar se um Host remoto está funcionando, se está na rede e se pode ser acessado.</span><span class="sxs-lookup"><span data-stu-id="64c19-114">You can use the <xref:System.Net.NetworkInformation.Ping> class to determine whether a Remote Host is up, on the network, and reachable.</span></span> <span data-ttu-id="64c19-115">Para obter mais informações, consulte [Como executar ping em um host](../../../docs/framework/network-programming/how-to-ping-a-host.md).</span><span class="sxs-lookup"><span data-stu-id="64c19-115">For more information, see [How to: Ping a Host](../../../docs/framework/network-programming/how-to-ping-a-host.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64c19-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64c19-116">See Also</span></span>  
 <span data-ttu-id="64c19-117">[Amostras de programação de rede](../../../docs/framework/network-programming/network-programming-samples.md) </span><span class="sxs-lookup"><span data-stu-id="64c19-117">[Network Programming Samples](../../../docs/framework/network-programming/network-programming-samples.md) </span></span>  
 <span data-ttu-id="64c19-118">[Amostra de tecnologia da informação de rede](http://go.microsoft.com/fwlink/?LinkID=179564) </span><span class="sxs-lookup"><span data-stu-id="64c19-118">[Network Information Technology Sample](http://go.microsoft.com/fwlink/?LinkID=179564) </span></span>  
 <span data-ttu-id="64c19-119">[Amostra de tecnologia de ferramenta NetStat](http://go.microsoft.com/fwlink/?LinkID=179562) </span><span class="sxs-lookup"><span data-stu-id="64c19-119">[NetStat Tool Technology Sample](http://go.microsoft.com/fwlink/?LinkID=179562) </span></span>  
 [<span data-ttu-id="64c19-120">Amostra de tecnologia de cliente de ping</span><span class="sxs-lookup"><span data-stu-id="64c19-120">Ping Client Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179565)

