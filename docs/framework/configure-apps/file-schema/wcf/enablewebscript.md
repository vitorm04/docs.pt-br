---
title: '&lt;enableWebScript&gt;'
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 1115b598776ca7d28698815974e06f3de57be598
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600096"
---
# <a name="ltenablewebscriptgt"></a>&lt;enableWebScript&gt;
Esse elemento permite que o comportamento de ponto de extremidade que torna possível consumir o serviço de páginas da web de ASP.NET AJAX.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<behavior>  
\<enableWebScript>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica o conjunto de comportamentos de ponto de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 Esse comportamento só deve ser usado em conjunto com qualquer um de [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação padrão, ou o [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) elemento de associação.  Para obter mais informações sobre esse comportamento, consulte <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [Integração AJAX e suporte para JSON](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
