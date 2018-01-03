---
title: '&lt;transporte&gt; de &lt;netPeerTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed3e933e1c3468a09b1d6b089b4abf52dad85017
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a>&lt;transporte&gt; de &lt;netPeerTcpBinding&gt;
Especifica as configurações de segurança em nível de transporte ao usar o [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).  
  
 \<sistema. ServiceModel >  
\<associações >  
\<netPeerTcpBinding >  
\<associação >  
\<segurança >  
\<transporte >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|credentialType|Opcional. Especifica o tipo de credenciais usado para verificar as mensagens enviadas com o transporte de par. Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.|  
  
## <a name="credentialtype-attribute"></a>credentialType atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|certificado|Requer a autenticação do transporte de canal par X509 certificado.|  
|Senha|A autenticação do transporte de canal par requer uma senha correta.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|Define as configurações de segurança para o [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
