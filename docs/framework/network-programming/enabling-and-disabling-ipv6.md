---
title: Habilitando e desabilitando o IPv6
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9edb87cf1ee35ac6848a478552cf8d0732177a81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-and-disabling-ipv6"></a>Habilitando e desabilitando o IPv6
Para usar o protocolo IPv6, verifique se você está executando uma versão do sistema operacional que dá suporte ao IPv6 e se o sistema operacional e as classes de rede estão configuradas corretamente.  
  
## <a name="configuration-steps"></a>Etapas de configuração  
 A tabela a seguir lista várias configurações  
  
|Sistema operacional habilitado para IPv6?|Classes de rede habilitadas para IPv6?|Descrição|  
|-------------------------------------|---------------------------------------|-----------------|  
|Não|Não|Pode analisar endereços IPv6.|  
|Não|Sim|Pode analisar endereços IPv6.|  
|Sim|Não|Pode analisar endereços IPv6 e resolver endereços IPv6 usando métodos de resolução de nomes não marcados como obsoletos.|  
|Sim|Sim|Pode analisar e resolver endereços IPv6 usando todos os métodos, incluindo aqueles marcados como obsoletos.|  
  
 Lembre-se de que, para habilitar o suporte ao IPv6 em todas as classes no namespace System.Net, é necessário modificar o arquivo de configuração do computador ou o arquivo de configuração do aplicativo. O arquivo de configuração de um aplicativo tem precedência sobre o arquivo de configuração do computador.  
  
 Para obter um exemplo de como modificar o arquivo de configuração do computador, *machine.config*, para habilitar o suporte ao IPv6, consulte [Como modificar o arquivo de configuração do computador para habilitar o suporte ao IPv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md). Além disso, verifique se o suporte ao IPv6 está habilitado no sistema operacional.  
  
 O .NET Framework tem uma opção de configuração definida em um arquivo de configuração da seguinte maneira  
  
```xml  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 Para o .NET Framework versão 1.1 e anterior, o valor da opção de configuração **ipv6 enabled** especifica se os membros da classe <xref:System.Net.Dns?displayProperty=nameWithType> retornam endereços IPv6.  
  
 Para o .NET Framework versão 2.0 e posterior, se o Windows der suporte ao IPv6, os membros da classe <xref:System.Net.Dns?displayProperty=nameWithType>, (por exemplo, o método <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType>), retornarão endereços IPv6 com uma limitação. Os membros obsoletos do DNS <xref:System.Net.Dns?displayProperty=nameWithType> (por exemplo, o método <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType>) lerão e reconhecerão o valor no arquivo de configuração para a configuração ipv6 enabled.  
  
## <a name="see-also"></a>Consulte também  
 [Protocolo IP versão 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Soquetes](../../../docs/framework/network-programming/sockets.md)  
 [Esquema de configurações de rede](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<Elemento ipv6> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
