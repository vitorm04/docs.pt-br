---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 86660620113b162a9a5260b7026a64455284d184
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151456"
---
# <a name="ltdispatchersynchronizationgt"></a>&lt;dispatcherSynchronization&gt;
  
Especifica um comportamento de ponto de extremidade que habilita um serviço enviar respostas de forma assíncrona.  
  
\<system.serviceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<comportamento de >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a>Tipo  
  
`Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
  
As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos

| Atributo               | Descrição       |
| ----------------------- | ----------------- |
| asynchronousSendEnabled | Um booliano que especifica se o comportamento de envio assíncrono está habilitado. |
| `maxPendingReceives`    | Um inteiro que especifica que o número de recebimentos concorrentes que pode ser emitido no canal.<br /><br /> Esse valor deve ser configurado somente depois que você configurou corretamente o comportamento de limitação do serviço. |

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |  
| ------- | ----------- |  
| [\<comportamento de >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um comportamento de ponto de extremidade. |

## <a name="see-also"></a>Consulte também

 <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
