---
title: '&lt;soapProcessing&gt;'
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: cc720c9e3a8ab934ffa8d3cb0c6eceb47a708fb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359543"
---
# <a name="ltsoapprocessinggt"></a>&lt;soapProcessing&gt;

Define o comportamento de ponto de extremidade de cliente usado para realizar marshaling de mensagens entre diferentes tipos de associação e versões de mensagem.

**\<sistema. ServiceModel >**   
&nbsp;&nbsp;**\<comportamentos >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comportamento >**   
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
| `processMessages` | Um valor booleano que especifica se as mensagens devem ser empacotadas entre versões de mensagem SOAP. |

### <a name="child-elements"></a>Elementos filho

Nenhum

### <a name="parent-elements"></a>Elementos pai

|     | Descrição |
| --- | ----------- |
| [**\<comportamento >**](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | Especifica um comportamento de ponto de extremidade. |

## <a name="remarks"></a>Comentários

Processamento de SOAP é o processo em que as mensagens são convertidas entre as versões de mensagem.

O serviço de roteamento do Windows Communication Foundation (WCF) pode converter mensagens de um protocolo para outro. Se as versões de mensagem de entrada e saída são diferentes, é criada uma nova mensagem da versão correta. Processamento de mensagens de um <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion` para outro é feito criando uma nova mensagem WCF que contém a parte do corpo e os cabeçalhos relevantes da mensagem recebida do WCF. Cabeçalhos específicos de endereçamento, ou que são entendidas no nível do roteador, não são usados durante a construção da nova mensagem WCF porque esses cabeçalhos são de uma versão diferente (no caso de cabeçalhos de endereçamento) ou tem sido processados como parte da comunicação entre o cliente e o roteador.

Se um cabeçalho é colocado na mensagem de saída é determinado pelo ou não foi marcado como compreender quando transmitidas por meio da camada de canal de entrada. Cabeçalhos que não são compreendidos (como cabeçalhos personalizados) não são removidos e passam para o serviço de roteamento por que está sendo copiado para a mensagem de saída. O corpo da mensagem é copiado para a mensagem de saída. A mensagem é enviada, em seguida, o canal de saída, no momento em que todos os cabeçalhos e outros dados de envelope específicos para essa comunicação/transporte de protocolo será criado e adicionado.

Essas etapas de processamento ocorrem quando o comportamento de processamento de SOAP é especificado. Isso [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) comportamento é um comportamento de ponto de extremidade que é aplicado a todos os pontos de extremidade do cliente (saída) quando o serviço de roteamento é iniciado. padrão, o [ \<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) comportamento cria e anexa um novo [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) comportamento com `processMessages` definida como `true` para cada ponto de extremidade do cliente. Se você tiver um protocolo que o serviço de roteamento não entender ou deseja substituir o comportamento padrão de processamento, você pode desativar o processamento para todo o serviço de roteamento ou apenas para pontos de extremidade específicos de SOAP.  Para desativar o processamento para todo o serviço de roteamento em todos os pontos de extremidade SOAP, defina o `soapProcessing` atributo do [ \<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) comportamento `false`. Para desativar o processamento de um determinado ponto de extremidade SOAP, use esse comportamento e defina seu `processMessages` atributo `false`, em seguida, anexar esse comportamento para o ponto de extremidade que você não quiser que o padrão de processamento de código para ser executado em.  Quando o [ \<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) comportamento configura o serviço de roteamento, ele ignorará reaplicar o comportamento de ponto de extremidade, pois já existe um.
