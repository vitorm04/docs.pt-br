---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 678b1f71ac15d3ad30df28cec5abbe403fb08c95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937060"
---
# <a name="soapprocessing"></a>\<> soapProcessing

Define o comportamento de ponto de extremidade de cliente usado para realizar marshaling de mensagens entre diferentes tipos de associação e versões de mensagem.

**\<system.ServiceModel>**    
&nbsp;&nbsp; **\<comportamentos >**    
&nbsp;&nbsp;&nbsp;&nbsp; **\<endpointBehaviors>**    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de comportamento**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<soapProcessing>**
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
  
As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|                   | Descrição |
| ----------------- | ----------- |
| `processMessages` | Um valor booliano que especifica se as mensagens devem ser empacotadas entre as versões de mensagem SOAP. |

### <a name="child-elements"></a>Elementos filho

Nenhum

### <a name="parent-elements"></a>Elementos pai

|     | Descrição |
| --- | ----------- |
| [ **\<> de comportamento**](behavior-of-endpointbehaviors.md) | Especifica um comportamento de ponto de extremidade. |

## <a name="remarks"></a>Comentários

O processamento de SOAP é o processo em que as mensagens são convertidas entre as versões de mensagem.

O serviço de roteamento do Windows Communication Foundation (WCF) pode converter mensagens de um protocolo para outro. Se as versões de mensagens de entrada e saída forem diferentes, uma nova mensagem da versão correta será criada. O processamento de mensagens <xref:System.ServiceModel.Channels.MessageVersion> de um para outro é realizado pela construção de uma nova mensagem do WCF que contém a parte do corpo e os cabeçalhos relevantes da mensagem de entrada do WCF. Os cabeçalhos que são específicos para endereçamento, ou que são compreendidos no nível do roteador, não são usados durante a construção da nova mensagem do WCF, pois esses cabeçalhos são de uma versão diferente (no caso de cabeçalhos de endereçamento) ou foram processados como parte do comunicação entre o cliente e o roteador.

Se um cabeçalho é colocado na mensagem de saída é determinado por se ele foi marcado como compreendido ou não como sendo passado pela camada de canal de entrada. Os cabeçalhos que não são compreendidos (como cabeçalhos personalizados) não são removidos e, portanto, passam pelo serviço de roteamento ao serem copiados para a mensagem de saída. O corpo da mensagem é copiado para a mensagem de saída. Em seguida, a mensagem envia o canal de saída, ponto em que todos os cabeçalhos e outros dados de envelope específicos ao protocolo de comunicação/transporte serão criados e adicionados.

Essas etapas de processamento ocorrem quando o comportamento de processamento de SOAP é especificado. Esse comportamento de > de soapProcessingExtension é um comportamento de ponto de extremidade que é aplicado a todos os pontos de extremidades de cliente (enviados) quando o serviço de roteamento é iniciado. [ \<](soapprocessing.md) padrão, o comportamento de [ \<> de roteamento](routing-of-servicebehavior.md) cria e anexa um novo `processMessages` `true` [ \<comportamento de > soapProcessingExtension](soapprocessing.md) com definido como para cada ponto de extremidade do cliente. Se você tiver um protocolo que o serviço de roteamento não entende ou deseja substituir o comportamento de processamento padrão, você poderá desabilitar o processamento SOAP para o serviço de roteamento inteiro ou apenas para pontos de extremidade específicos.  Para desabilitar o processamento de SOAP para todo o serviço de roteamento em todos os pontos `soapProcessing` `false` [ \<](routing-of-servicebehavior.md) de extremidade, defina o atributo do comportamento de > de roteamento como. Para desativar o processamento de SOAP para um ponto de extremidade específico, use esse comportamento `processMessages` e defina `false`seu atributo como, em seguida, anexe esse comportamento ao ponto de extremidade no qual você não deseja que o código de processamento padrão seja executado.  Quando o comportamento de [ \<> de roteamento](routing-of-servicebehavior.md) configura o serviço de roteamento, ele ignorará a reaplicação do comportamento do ponto de extremidade desde que já exista um.
