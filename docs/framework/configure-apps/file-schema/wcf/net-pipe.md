---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: 90d081c1287362669286aaa1185ed3b0bbe09b07
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412104"
---
# <a name="netpipe"></a>\<net.pipe>
Especifica as definições de configuração para o serviço de ativação de Pipe nomeado, que gerencia o tempo de vida da conexão de pipe nomeado e manipula as solicitações de ativação que chegam através de pipes nomeados.  
  
 \<system.serviceModel.activation>  
\<net.pipe>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`maxPendingAccepts`|Um inteiro que especifica o máximo threads de aceitação simultâneo pendentes no ponto de extremidade escutando para o serviço de compartilhamento. O padrão é 2.|  
|`maxPendingConnections`|Um inteiro que especifica o número máximo de conexões que podem esperar por expedição. O padrão é 100.|  
|`receiveTimeout`|Um <xref:System.TimeSpan> que especifica o tempo limite para ler os dados de enquadramento e execução de expedição de conexão das conexões subjacentes. O padrão é "00: 00:10"|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<allowAccounts>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Uma coleção de elementos de configuração que contêm um `securityIdentifier` atributo para especificar contas de usuário para processos que hospedam serviços do WCF e recebem acesso de conexão para o serviço de compartilhamento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Contém definições de configuração para o processo de escuta SMSvcHost.exe.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
