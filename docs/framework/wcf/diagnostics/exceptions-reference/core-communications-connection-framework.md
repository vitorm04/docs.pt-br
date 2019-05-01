---
title: 'Comunicações principais: Estrutura de conexão'
ms.date: 03/30/2017
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
ms.openlocfilehash: a3f52ac82c2bf09ded504e412d7f216dd0b39959
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998680"
---
# <a name="core-communications-connection-framework"></a>Comunicações principais: Estrutura de conexão
Este tópico lista todas as exceções geradas pelo Framework de Conexão do Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|CloseTimedOut|O método Close atingiu o tempo limite após o tempo especificado. Aumente o valor de tempo limite que é passado para a chamada para fechar ou aumente o valor de CloseTimeout na associação. O tempo determinado para essa operação pode ter sido uma parte de um tempo limite maior.|  
|ContentTypeMismatch|O tipo de conteúdo especificado foi enviado a um serviço que estava esperando especificado. As associações de cliente e serviço talvez não sejam compatíveis.|  
|DuplexChannelAbortedDuringOpen|O canal duplex especificado encerrado durante o processo de abertura.|  
|FramingValueNotAvailable|O valor não pode ser acessado porque ele não é totalmente decodificado.|  
|OperationAbortedDuringConnectionEstablishment|A operação foi encerrada ao estabelecer uma conexão especificada.|  
|ReceiveTimedOut2|A operação de recebimento expirou após o tempo especificado. O tempo determinado para essa operação pode ter sido uma parte de um tempo limite maior.|  
|SendCannotBeCalledAfterCloseOutputSession|Você não pode enviar mensagens em um canal após CloseOutputSession ter sido chamado.|
