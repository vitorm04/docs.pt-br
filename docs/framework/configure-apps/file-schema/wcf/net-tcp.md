---
title: '&lt;NET. TCP&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a3d22b6feef80dbff8c7f20b130ce2b0f9702c9e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnettcpgt"></a>&lt;NET. TCP&gt;
Especifica as definições de configuração de rede. TCP porta de serviço de compartilhamento, que permite que vários processos compartilhem a mesma porta TCP.  
  
 \<system.serviceModel.activation >  
\<NET. TCP >  
  
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
|`listenBacklog`|Um inteiro que especifica o máximo de conexões pendente que é aceitas da conexão compartilhada, mas ainda não foram expedido para [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviços. O padrão é 10.|  
|`maxPendingAccepts`|Um inteiro que especifica o máximo threads de aceitação simultâneas pendentes no ponto de extremidade escutando para o serviço de compartilhamento. O padrão é 2.|  
|`MaxPendingConnections`|O número máximo de conexões que o ouvinte pode ter aguardando para serem aceitas pelo aplicativo. Quando esse valor de cota for ultrapassada, novas conexões de entrada são descartadas em vez de esperar ser aceito. Recursos de Conexão, como segurança de mensagem podem causar um cliente abrir mais de uma conexão. Os administradores de serviço devem levar em consideração para essas conexões adicionais ao definir esse valor de cota. O padrão é 10.|  
|`receiveTimeout`|Um `TimeSpan` que especifica o tempo limite para ler os dados de enquadramento e executar a expedição de conexão das conexões sublinhado. O padrão é "00: 00:10".|  
|`teredoEnabled`|Um valor booliano que indica se o serviço de compartilhamento de porta usa o serviço Teredo da Microsoft para escutar em TCP portas em nome de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviços. O padrão é `false`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<allowAccounts >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Uma coleção de elementos de configuração que contêm um `securityIdentifier` atributo para especificar contas de usuário para processos que hospedam [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviços e recebem acesso de conexão para o serviço de compartilhamento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Contém definições de configuração para o processo do ouvinte SMSvcHost.exe.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre o compartilhamento de porta, consulte [compartilhamento de porta NET. TCP](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded). Para entender como configurar a serviço de compartilhamento de porta, consulte [Configurando o serviço de compartilhamento de porta NET. TCP](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [Compartilhamento de porta do NET.TCP](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded)  
 [Configurando o serviço de compartilhamento de porta NET.TCP](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)
