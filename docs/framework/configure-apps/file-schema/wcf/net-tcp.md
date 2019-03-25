---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 692c4cf6688bfc2f9b99f065f4b16711f7f08063
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412039"
---
# <a name="nettcp"></a>\<net.tcp>
Especifica as definições de configuração para a rede. TCP porta de serviço de compartilhamento, que permite que vários processos compartilhem a mesma porta TCP.  
  
 \<system.serviceModel.activation>  
\<net.tcp>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="Integer"
             maxPendingAccepts="Integer"
             maxPendingConnections="Integer"
             receiveTimeout="TimeSpan"
             teredoEnabled="Boolean">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only)-->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
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
|`listenBacklog`|Um inteiro que especifica o máximo de conexões pendentes que serão aceitas da conexão compartilhada, mas ainda não foram expedido para serviços Windows Communication Foundation (WCF). O padrão é 10.|  
|`maxPendingAccepts`|Um inteiro que especifica o máximo threads de aceitação simultâneo pendentes no ponto de extremidade escutando para o serviço de compartilhamento. O padrão é 2.|  
|`MaxPendingConnections`|O número máximo de conexões que o ouvinte pode ter aguardando para serem aceitas pelo aplicativo. Quando esse valor de cota for excedida, novas conexões de entrada são descartadas em vez de esperar para ser aceito. Recursos de Conexão, como segurança de mensagem podem fazer com que um cliente abrir mais de uma conexão. Os administradores de serviço devem levar em consideração para essas conexões adicionais ao definir esse valor de cota. O padrão é 10.|  
|`receiveTimeout`|Um <xref:System.TimeSpan> que especifica o tempo limite para ler os dados de enquadramento e execução de expedição de conexão das conexões subjacentes. O padrão é "00: 00:10".|  
|`teredoEnabled`|Um valor booliano que indica se o serviço de compartilhamento de porta usa o serviço Teredo da Microsoft para escutar em portas TCP em nome dos serviços WCF. O padrão é `false`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<allowAccounts>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Uma coleção de elementos de configuração que contêm um `securityIdentifier` atributo para especificar contas de usuário para processos que hospedam serviços do WCF e recebem acesso de conexão para o serviço de compartilhamento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Contém definições de configuração para o processo de escuta SMSvcHost.exe.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre o compartilhamento de porta, consulte [compartilhamento de porta NET. TCP](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md). Para entender como configurar a serviço de compartilhamento de porta, consulte [Configurando o serviço de compartilhamento de porta NET. TCP](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [Compartilhamento de porta do NET.TCP](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Configurando o serviço de compartilhamento de porta NET.TCP](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
