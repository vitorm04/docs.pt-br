---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397723"
---
# <a name="netpipe"></a>\<net.pipe>
Especifica as definições de configuração para o serviço de ativação de pipe nomeado, que gerencia o tempo de vida da conexão de pipe nomeado e lida com as solicitações de ativação que chegam em pipes nomeados.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<sistema. serviceModel. Activation >** ](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<> de net. pipe**  
  
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
|`maxPendingAccepts`|Um inteiro que especifica o máximo de threads de aceitação simultâneas pendentes no ponto de extremidade de escuta para o serviço de compartilhamento. O padrão é 2.|  
|`maxPendingConnections`|Um inteiro que especifica o número máximo de conexões que podem aguardar a expedição. O padrão é 100.|  
|`receiveTimeout`|Um <xref:System.TimeSpan> que especifica o tempo limite para ler os dados de enquadramento e executar a distribuição de conexão das conexões de sublinhado. O padrão é "00:00:10"|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|Uma coleção de elementos de configuração que contêm `securityIdentifier` um atributo para especificar contas de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|Contém definições de configuração para o processo de ouvinte SMSvcHost. exe.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
