---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 7336c9f7d8a117f9a9bfd338e47941eeb648fa51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925852"
---
# <a name="dispatchersynchronization"></a>\<> dispatcherSynchronization
  
Especifica um comportamento de ponto de extremidade que permite que um serviço envie respostas de forma assíncrona.  
  
\<system.serviceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<> de comportamento  
  
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
| `maxPendingReceives`    | Um inteiro que especifica o número de recebimentos simultâneos que podem ser emitidos no canal.<br /><br /> Esse valor deve ser configurado somente depois que você tiver configurado corretamente o comportamento de limitação de serviço. |

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |  
| ------- | ----------- |  
| [\<> de comportamento](behavior-of-endpointbehaviors.md)|Especifica um comportamento de ponto de extremidade. |

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
