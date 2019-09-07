---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 20c0057c80b668df97379d0168bb7c005d9927ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400382"
---
# <a name="enablewebscript"></a>\<enableWebScript>
Esse elemento habilita o comportamento do ponto de extremidade que torna possível consumir o serviço de páginas da Web do ASP.NET AJAX.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> enableWebScript**  
  
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
|[\<> de comportamento](behavior-of-endpointbehaviors.md)|Especifica o conjunto de comportamentos de ponto de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 Esse comportamento só deve ser usado em conjunto com a associação de [ \<WebHttpBinding >](webhttpbinding.md) padrão ou com o elemento de associação de [ \<> webMessageEncoding](webmessageencoding.md) .  Para obter mais informações sobre esse comportamento, <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>consulte.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [Integração AJAX e suporte para JSON](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
