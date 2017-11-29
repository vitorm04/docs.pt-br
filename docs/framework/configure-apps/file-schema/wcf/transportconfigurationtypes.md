---
title: '&lt;transportConfigurationTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b048b160f337897765fa4fcff73a4906534ab08b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportconfigurationtypesgt"></a>&lt;transportConfigurationTypes&gt;
Representa uma coleção de elementos de configuração que identificam o tipo de um transporte particular. Isso pode ser usado para adicionar protocolos personalizados do WAS.  
  
 \<sistema. ServiceModel >  
\<ServiceHostingEnvironment >  
\<transportConfigurationTypes >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|O nome do transporte|  
|transportConfigurationType|O tipo que implementa o transporte|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|Adiciona um elemento de configuração que identifica o tipo de um transporte particular.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Define o tipo que o ambiente de hospedagem de serviço instancia para um transporte particular.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [Hospedagem](../../../../../docs/framework/wcf/feature-details/hosting.md)
