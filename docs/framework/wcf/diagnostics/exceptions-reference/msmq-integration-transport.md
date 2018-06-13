---
title: Transporte de integração do MSMQ
ms.date: 03/30/2017
ms.assetid: 2bf9893a-fbd1-41fc-b6de-a41a44279936
ms.openlocfilehash: 52fd98354ded57bd7d7c075d4f08ca543760e598
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473367"
---
# <a name="msmq-integration-transport"></a>Transporte de integração do MSMQ
Este tópico lista todas as exceções geradas pelo transporte de integração do MSMQ.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|MessageSizeMustBeInIntegerRange|Esta fábrica armazena mensagens no buffer, portanto, os tamanhos das mensagens devem estar no intervalo de um valor inteiro.|  
|MsmqByteArrayBodyExpected|Ocorreu uma incompatibilidade entre o formato de serialização especificada e o corpo da mensagem do MSMQ. A mensagem não pode ser enviada ou recebida. O formato de serialização ByteArray requer que o corpo da mensagem do MSMQ seja do tipo byte [].|  
|MsmqCannotDeserializeActiveXMessage|Ocorreu um erro de serialização ActiveX. A mensagem não pode ser enviada ou recebida. O tipo de variante especificado para o corpo não coincide com o corpo da mensagem MSMQ real.|  
|MsmqCannotUseBodyTypeWithActiveXSerialization|As propriedades da mensagem são incompatíveis. A mensagem não pode ser enviada ou recebida. A propriedade de mensagem BodyType não pode ser especificado se o formato de serialização ActiveX será usado.|  
|MsmqInvalidServiceOperationForMsmqIntegrationBinding|Falha na validação de MsmqIntegrationBinding. O ponto de extremidade de serviço não pode ser iniciado. A associação especificada não dá suporte a assinatura do método para a operação de serviço especificado no contrato especificado. Corrija a operação de serviço para usar MsmqIntegrationBinding.|  
|MsmqInvalidTypeDeserialization|Falha na serialização ActiveX porque não é possível reconhecer o formato de serialização. A mensagem não pode ser enviada ou recebida.|  
|MsmqInvalidTypeSerialization|O tipo de variante não é reconhecido. Falha na serialização ActiveX. A mensagem não pode ser enviada ou recebida. Não há suporte para o tipo de variante especificado.|  
|MsmqStreamBodyExpected|Incompatibilidade entre o formato de serialização e o corpo de conteúdo. Mensagem não pode ser enviada ou recebida. Somente um corpo de fluxo de tipo pode ser enviado ou recebidas usando o modo de serialização de fluxo.|
