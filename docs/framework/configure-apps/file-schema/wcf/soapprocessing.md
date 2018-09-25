---
title: '&lt;soapProcessing&gt;'
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 296993f1a91a6da93f01610357f35dac4cfab9e6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083894"
---
# <a name="ltsoapprocessinggt"></a>&lt;soapProcessing&gt;

Define o comportamento de ponto de extremidade de cliente usado para realizar marshaling de mensagens entre diferentes tipos de associação e versões de mensagem.

**\<sistema. ServiceModel >**   
&nbsp;&nbsp;**\<comportamentos >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comportamento de >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing >**

## <a name="syntax"></a>Sintaxe

```xml
<soapProcessing processMessages="true|false" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|                   | Descrição |
| ----------------- | ----------- |
| `processMessages` | Um valor booliano que especifica se as mensagens devem passar por marshaling entre versões de mensagem SOAP. |

### <a name="child-elements"></a>Elementos filho

Nenhum

### <a name="parent-elements"></a>Elementos pai

|     | Descrição |
| --- | ----------- |
| [**\<comportamento de >**](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | Especifica um comportamento de ponto de extremidade. |

## <a name="remarks"></a>Comentários

Processamento de SOAP é o processo em que as mensagens são convertidas entre versões de mensagem.

O serviço de roteamento do Windows Communication Foundation (WCF) pode converter as mensagens de um protocolo para outro. Se as versões de mensagem de entrada e saída são diferentes, uma nova mensagem da versão correta é criada. Processamento de mensagens de um <xref:System.ServiceModel.Channels.MessageVersion> para outro é feito construindo uma nova mensagem do WCF que contém a parte do corpo e cabeçalhos relevantes da mensagem de entrada de WCF. Cabeçalhos que são específicos para endereçamento, ou que são entendidas no nível do roteador, não são usados durante a construção da nova mensagem do WCF, porque esses cabeçalhos são de uma versão diferente (no caso de cabeçalhos de endereçamento) ou tem sido processados como parte das comunicação entre o cliente e o roteador.

Se um cabeçalho é colocado na mensagem de saída é determinado pelo ou não foi marcado como entendidas à medida que ele passado por meio da camada de canal de entrada. Cabeçalhos que não são compreendidos (como cabeçalhos personalizados) não são removidos e então passam pelo serviço de roteamento, que está sendo copiado para a mensagem de saída. O corpo da mensagem é copiado para a mensagem de saída. A mensagem é enviada, em seguida, limite o canal de saída, no momento em que todos os cabeçalhos e outros dados de envelope específicos para que a comunicação/transporte de protocolo será criado e adicionado.

Essas etapas de processamento ocorrem quando o comportamento de processamento SOAP é especificado. Isso [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) comportamento é um comportamento de ponto de extremidade que é aplicado a todos os pontos de extremidade do cliente (saída) quando o serviço de roteamento é iniciado. padrão, o [ \<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) comportamento cria e anexa um novo [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) comportamento com `processMessages` definida como `true` para cada ponto de extremidade do cliente. Se você tiver um protocolo que o serviço de roteamento não compreender ou deseja substituir o comportamento padrão de processamento, você pode desabilitar para todo o serviço de roteamento ou apenas para pontos de extremidade específicos de processamento SOAP.  Para desabilitar o processamento para todo o serviço de roteamento em todos os pontos de extremidade SOAP, defina a `soapProcessing` atributo o [ \<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) comportamento para `false`. Para desativar o processamento para um determinado ponto de extremidade SOAP, use esse comportamento e defina sua `processMessages` de atributo para `false`, em seguida, anexar esse comportamento ao ponto de extremidade que você não quiser que o processamento de código seja executado por padrão.  Quando o [ \<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) comportamento configura o serviço de roteamento, ele ignorará reaplicando o comportamento de ponto de extremidade, pois já existe um.
