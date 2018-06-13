---
title: 'Comunicações principais: estrutura de conexão'
ms.date: 03/30/2017
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
ms.openlocfilehash: a3f52ac82c2bf09ded504e412d7f216dd0b39959
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471970"
---
# <a name="core-communications-connection-framework"></a>Comunicações principais: estrutura de conexão
Este tópico lista todas as exceções geradas pela estrutura de Conexão do Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|CloseTimedOut|O método Close atingiu o tempo limite após o período especificado. Aumente o valor de tempo limite que é passado para a chamada para fechar ou aumente o valor de CloseTimeout na associação. O tempo determinado para essa operação pode ter sido uma parte de um tempo limite maior.|  
|ContentTypeMismatch|O tipo de conteúdo especificado foi enviado a um serviço que estava esperando especificado. As associações de cliente e serviço talvez não sejam compatíveis.|  
|DuplexChannelAbortedDuringOpen|O canal duplex para especificado foi finalizado durante o processo de abertura.|  
|FramingValueNotAvailable|O valor não pode ser acessado porque ele não é totalmente decodificado.|  
|OperationAbortedDuringConnectionEstablishment|A operação foi encerrada ao estabelecer uma conexão especificado.|  
|ReceiveTimedOut2|A operação de recebimento expirou após o período especificado. O tempo determinado para essa operação pode ter sido uma parte de um tempo limite maior.|  
|SendCannotBeCalledAfterCloseOutputSession|Você não pode enviar mensagens em um canal após CloseOutputSession ter sido chamado.|
