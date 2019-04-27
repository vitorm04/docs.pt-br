---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 6be9752e8102a5d4db4fed31aae8ff6d56fdd24e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673401"
---
# <a name="dispatchersynchronization"></a>\<dispatcherSynchronization>
  
Especifica um comportamento de ponto de extremidade que habilita um serviço enviar respostas de forma assíncrona.  
  
\<system.serviceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<behavior>  
  
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
| [\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um comportamento de ponto de extremidade. |

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
