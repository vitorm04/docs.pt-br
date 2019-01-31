---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: ca6d401109d14ce11dcd40c393cd079170e4d20d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259859"
---
# <a name="webhttp"></a>\<webHttp>
Esse elemento Especifica o <xref:System.ServiceModel.Description.WebHttpBehavior> em um ponto de extremidade por meio da configuração. Esse comportamento, quando usado em conjunto com o [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) habilita a associação padrão, o modelo de programação da Web para um serviço do Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<behavior>  
\<webHttp>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Quando essa propriedade é definida como `true`, a infraestrutura WCF determina o melhor formato para usar. Seleção automática de formato com versões anteriores é desabilitada por padrão para compatibilidade. Seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração.|  
|defaultBodyStyle|Especifica o estilo de corpo padrão das mensagens retornadas. Para obter mais informações, consulte <xref:System.ServiceModel.Web.WebMessageBodyStyle> e [formatação do WCF Web HTTP](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|Especifica o formato de resposta da saída padrão para mensagens. Para obter mais informações, consulte [formatação do WCF Web HTTP](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|faultExceptionEnabled|Obtém ou define o sinalizador que especifica se uma FaultException é gerada quando ocorre um erro de servidor interno (código de status HTTP: 500).|  
|helpEnabled|Obtém ou define um valor que determina se a página de Ajuda está habilitada.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica o conjunto de comportamentos de ponto de extremidade.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Integração AJAX e suporte para JSON](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
