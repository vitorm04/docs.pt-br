---
title: '&lt;comportamento&gt; de &lt;serviceBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 9cb5676897255d11b502080f4f7f3fb897027917
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt"></a>&lt;comportamento&gt; de &lt;serviceBehaviors&gt;
O `behavior` elemento contém uma coleção de configurações para o comportamento de um serviço. Cada comportamento é indexado pela sua `name`. Serviços podem vincular a cada comportamento por esse nome usando o `behaviorConfiguration` atributo do [ \<ponto de extremidade >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elemento. Isso permite que os pontos de extremidade compartilhem configurações comuns de comportamento sem redefinir as configurações. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!NOTE]
>  Elementos de comportamento específicos para atividades de fluxo de trabalho do Windows, como o [ \<sendMessageChannelCache >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md) elemento, estão documentados a [ \<comportamento > de \< serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) página.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
       <behavior name="String" />  
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Uma cadeia de caracteres exclusiva que contém o nome da configuração do comportamento. Esse valor é uma cadeia de caracteres definida pelo usuário que deve ser exclusiva, pois ele atua como a cadeia de caracteres de identificação para o elemento. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)|Contém dados de configuração do DataContractSerializer.|  
|[\<persistenceProvider >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistenceprovider.md)|Especifica o tipo de implementação do provedor de persistência a ser usado, bem como o tempo limite a ser usado para operações de persistência.|  
|[\<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|Fornece acesso de tempo de execução ao serviço de roteamento para permitir a modificação dinâmica da configuração de roteamento.|  
|[\<serviceAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthenticationmanager.md)|Fornece um elemento de configuração de fluxo de trabalho que estabelece o nível de serviço a validade de uma transmissão, a mensagem ou o originador.|  
|[\<serviceAuthorization >](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)|Especifica configurações que autorizam o acesso a operações de serviço.|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.|  
|[\<serviceDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)|Especifica os recursos de informações de depuração e ajuda para um serviço do Windows Communication Foundation (WCF).|  
|[\<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)|Especifica a descoberta de pontos de extremidade de serviço.|  
|[\<serviceMetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)|Especifica a publicação de metadados de serviço e as informações associadas.|  
|[\<serviceSecurityAudit >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)|Especifica configurações que habilitem a auditoria de eventos de segurança durante operações de serviço.|  
|[\<serviceThrottling >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)|Especifica o mecanismo de limitação de um serviço WCF.|  
|[\<serviceTimeouts >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicetimeouts.md)|Especifica o tempo limite para um serviço.|  
|[\<workflowRuntime>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|Especifica configurações para uma instância de WorkflowRuntime para hospedagem de serviços do WCF com base em fluxo de trabalho.|  
|[\<useRequestHeadersForMetadataAddress >](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|Permite a recuperação de informações de endereço de metadados de cabeçalhos de mensagem de solicitação.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|Uma coleção de elementos de comportamento de serviço.|
