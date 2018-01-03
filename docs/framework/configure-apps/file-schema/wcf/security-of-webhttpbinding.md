---
title: "&lt;segurança&gt; de &lt;webHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3afd67e7f2d42cec458db7919529e09e4607f1ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a>&lt;segurança&gt; de &lt;webHttpBinding&gt;
Especifica os requisitos de segurança para um ponto de extremidade configurado com um [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 \<sistema. ServiceModel >  
\<associações >  
\<webHttpBinding >  
\<associação >  
\<segurança >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.ServiceModel>  
    <bindings>  
        <webHttpBinding>  
            <binding name = "string">  
              <security mode="None/Transport/TransportCredentialOnly">  
                                    <transport clientCredentialType =   
                                     "Basic/Certificate/Digest/None/Ntlm/Windows"  
                                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                                     realm="string" />  
              </security>  
        </webHttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|modo|Especifica se a segurança em nível de transporte ou nenhuma segurança é usada por um ponto de extremidade. O padrão é `None`. Esse atributo é do tipo <xref:System.ServiceModel.WebHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>Atributo mode  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|A segurança é desabilitada.|  
|Transporte|A proteção é fornecida usando HTTPS. O serviço precisa ser configurado com certificados SSL. A mensagem é totalmente protegida usando HTTPS e o serviço é autenticado pelo cliente usando o certificado SSL do serviço. A autenticação do cliente é controlada por meio de `ClientCredentialType` atributo do [ \<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).|  
|TransportCredentialOnly|Esse modo não fornece confidencialidade e integridade de mensagens. Ele fornece autenticação de cliente com base em HTTP. Esse modo deve ser usado com cuidado. Ele deve ser usado em ambientes onde a segurança de transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pelo [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infraestrutura.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|Define as configurações de segurança de transporte. Esse elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Um elemento de associação que é usado para configurar pontos de extremidade para [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] que responda a solicitações HTTP em vez de mensagens SOAP de serviços da Web.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Selecionando um tipo de credencial](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)  
 [Modelo de programação HTTP Web do WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
