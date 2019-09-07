---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 92a8fa83b5cf5f429278ac8edc8439b627839aad
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400563"
---
# <a name="callbackdebug"></a>\<callbackDebug>
Especifica a depuração de serviço para um objeto de retorno de chamada Windows Communication Foundation (WCF).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> callbackDebug**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|Um valor que especifica se os objetos de retorno de chamada do cliente retornam informações de exceção gerenciada em falhas de SOAP de volta ao serviço.<br /><br /> Se você definir esse atributo como `true` programaticamente, poderá habilitar o fluxo de informações de exceção gerenciada em um objeto de retorno de chamada do cliente de volta para o serviço para fins de depuração. **Cuidado:**  Retornar informações de exceção gerenciada aos clientes pode ser um risco de segurança. Isso ocorre porque os detalhes da exceção expõem informações sobre a implementação do serviço interno que pode ser usada por clientes não autorizados.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<> de comportamento](behavior-of-endpointbehaviors.md)|Especifica um comportamento de ponto de extremidade.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
