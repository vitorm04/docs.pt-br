---
title: Transporte de integração do MSMQ
ms.date: 03/30/2017
ms.assetid: 2bf9893a-fbd1-41fc-b6de-a41a44279936
ms.openlocfilehash: 52fd98354ded57bd7d7c075d4f08ca543760e598
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777358"
---
# <a name="msmq-integration-transport"></a>Transporte de integração do MSMQ
Este tópico lista todas as exceções geradas pelo transporte de integração de MSMQ.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|MessageSizeMustBeInIntegerRange|Esta fábrica armazena mensagens no buffer, portanto, os tamanhos das mensagens devem estar no intervalo de um valor inteiro.|  
|MsmqByteArrayBodyExpected|Ocorreu uma incompatibilidade entre o formato de serialização especificado e o corpo da mensagem do MSMQ. A mensagem não pode ser enviada ou recebida. O formato de serialização ByteArray requer que o corpo da mensagem do MSMQ seja do tipo byte [].|  
|MsmqCannotDeserializeActiveXMessage|Ocorreu um erro de serialização do ActiveX. A mensagem não pode ser enviada ou recebida. O tipo de variante especificado para o corpo não coincide com o corpo da mensagem MSMQ real.|  
|MsmqCannotUseBodyTypeWithActiveXSerialization|As propriedades da mensagem são incompatíveis. A mensagem não pode ser enviada ou recebida. A propriedade de mensagem BodyType não pode ser especificado se o formato de serialização do ActiveX será usado.|  
|MsmqInvalidServiceOperationForMsmqIntegrationBinding|Falha na validação MsmqIntegrationBinding. O ponto de extremidade de serviço não pode ser iniciado. A associação especificada não dá suporte a assinatura do método para a operação de serviço especificado no contrato especificado. Corrija a operação de serviço para usar o MsmqIntegrationBinding.|  
|MsmqInvalidTypeDeserialization|A serialização do ActiveX falhou porque o formato de serialização não pode ser reconhecido. A mensagem não pode ser enviada ou recebida.|  
|MsmqInvalidTypeSerialization|O tipo de variante não é reconhecido. Falha na serialização ActiveX. A mensagem não pode ser enviada ou recebida. Não há suporte para o tipo de variante especificado.|  
|MsmqStreamBodyExpected|Incompatibilidade entre o formato de serialização e o conteúdo do corpo. Mensagem não pode ser enviada ou recebida. Somente um corpo de fluxo de tipo pode ser enviado ou recebidos usando o modo de fluxo de serialização.|
