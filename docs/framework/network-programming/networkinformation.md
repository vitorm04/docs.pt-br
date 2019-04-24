---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: 0820ad6a6d5000ef7ea575e856d883ba5325b1b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230974"
---
# <a name="networkinformation"></a>NetworkInformation
O namespace <xref:System.Net.NetworkInformation> permite que você colete informações sobre eventos, alterações, estatísticas e propriedades de rede. Você também pode determinar se um host remoto está acessível usando a classe <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType>.  
  
## <a name="network-availability-and-events"></a>Disponibilidade de rede e eventos  
 A classe <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> permite que você determine se o endereço de rede ou a disponibilidade foi alterada. Para usar essa classe, crie um manipulador de eventos para processar a alteração e associe-o a um <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> ou <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>. Para obter mais informações, confira [Como: Detectar a disponibilidade de rede e alterações de endereço](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).  
  
## <a name="network-statistics-and-properties"></a>Propriedades e estatísticas de rede  
 Você pode coletar estatísticas de rede e propriedades por protocolo ou por interface. As classes <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType> e <xref:System.Net.NetworkInformation.PhysicalAddress> fornecem informações sobre um adaptador de rede específico, enquanto as classes <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics> e <xref:System.Net.NetworkInformation.UdpStatistics> fornecem informações sobre os pacotes de camada 3 e de camada 4. Para obter mais informações, confira [Como: Obter informações de interface e de protocolo](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Determinar se um Host remoto é alcançável  
 Você pode usar a classe <xref:System.Net.NetworkInformation.Ping> para determinar se um Host remoto está funcionando, se está na rede e se pode ser acessado. Para obter mais informações, confira [Como: Executar ping em um host](../../../docs/framework/network-programming/how-to-ping-a-host.md).  
  
## <a name="see-also"></a>Consulte também

- [Amostras de programação de rede](../../../docs/framework/network-programming/network-programming-samples.md)
- [Amostra de tecnologia da informação de rede](https://go.microsoft.com/fwlink/?LinkID=179564)
- [Amostra de tecnologia de ferramenta NetStat](https://go.microsoft.com/fwlink/?LinkID=179562)
- [Amostra de tecnologia de cliente de ping](https://go.microsoft.com/fwlink/?LinkID=179565)
