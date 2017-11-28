---
title: '&lt;webHttp&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c51c8ac43549994752999db08dbb92d43bc7a86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebhttpgt"></a>&lt;webHttp&gt;
Este elemento Especifica o <xref:System.ServiceModel.Description.WebHttpBehavior> em um ponto de extremidade por meio da configuração. Esse comportamento, quando usado em conjunto com o [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação padrão, permite que o modelo de programação da Web para um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviço.  
  
 \<sistema. ServiceModel >  
\<comportamentos >  
\<endpointBehaviors >  
\<comportamento >  
\<webHttp >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<webHttp />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Quando essa propriedade é definida como `true`, a infraestrutura WCF determina o melhor formato a ser usado. Seleção automática de formato com versões anteriores é desabilitada por padrão para compatibilidade. Seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração.|  
|defaultBodyStyle|Especifica o estilo de corpo padrão das mensagens retornadas. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.Web.WebMessageBodyStyle> e [formatação HTTP Web do WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|Especifica o formato de resposta de saída do padrão de mensagens. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Formatação HTTP Web do WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|faultExceptionEnabled|Obtém ou define o sinalizador que especifica se uma FaultException é gerada quando um erro de servidor interno (código de status HTTP: 500) ocorre.|  
|helpEnabled|Obtém ou define um valor que determina se a página de Ajuda está habilitada.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica o conjunto de comportamentos de ponto de extremidade.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.WebHttpElement>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [Integração de AJAX e suporte a JSON](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [\<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
