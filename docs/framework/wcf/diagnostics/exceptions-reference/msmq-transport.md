---
title: Transporte do MSMQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f29a2fe-24df-4614-b64c-b0c084fb7003
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c8f1283a27488c56a866973270409c22efc1fb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="msmq-transport"></a>Transporte do MSMQ
Este tópico lista todas as exceções geradas pelo transporte MSMQ.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|MsmqActiveDirectoryRequiresNativeTransfer|A validação de associação para a mensagem de falha. O cliente não pode enviar mensagens. Um conflito nas propriedades da associação causou essa falha. A propriedade UseActiveDirectory está definida como true e QueueTransferProtocol está definida como Native. Para resolver o conflito, corrija uma das propriedades.|  
|MsmqAuthNoneRequiresProtectionNone|A validação de associação para o serviço falhou. O ponto de extremidade de serviço ou o cliente não pode ser iniciado. Um conflito nas propriedades da associação causou essa falha. MsmqAuthenticationMode está definida como None e MsmqProtectionLevel não está definida como None. Para resolver o conflito, corrija uma das propriedades.|  
|MsmqCustomRequiresPerAddDLQ|A validação de associação para a mensagem de falha. O cliente não é possível enviar a mensagem. A propriedade DeadLetterQueue está definida como Custom, mas a propriedade CustomDeadLetterQueue não está especificada. Especifique o URI da fila de mensagens mortas para cada aplicativo na propriedade CustomDeadLetterQueue.|  
|MsmqDeserializationError|Ocorreu um erro ao desserializar a mensagem XML. A mensagem não pode ser recebida e é descartada.|  
|MsmqDLQNotWriteable|Falha na validação de associação para o cliente. O cliente não pode enviar uma mensagem. A fila de mensagens mortas especificada não existe ou não pode ser gravada. Certifique-se de que a fila existe com a autorização adequada para gravar nele.|  
|MsmqGetPrivateComputerInformationError|A verificação de versão falhou com o erro especificado. A versão do MSMQ não pode ser detectada por todas as operações que estão no canal em fila falharão. Verifique se o MSMQ está instalado e está disponível.|  
|MsmqNoAssurancesForVolatile|A validação de associação para o serviço falhou. O ponto de extremidade de serviço ou o cliente não pode ser iniciado. A propriedade ExactlyOnce está definida como true e a propriedade Durable é definido como false. Não há suporte para isso. Para resolver o conflito, corrija uma dessas propriedades.|  
|MsmqNonTransactionalQueueNeeded|Foi detectada uma incompatibilidade entre a ligação e a configuração de fila do MSMQ. O ponto de extremidade de serviço não pode ser iniciado. A propriedade ExactlyOnce está definida como false e ler mensagens de fila é transacional. Corrija o erro definindo a propriedade ExactlyOnce como true ou crie uma associação não transacional.|  
|MsmqOpenError|Ocorreu um erro ao abrir a fila especificada. A mensagem não pode ser enviada ou recebida da fila. Certifique-se de que o MSMQ está instalado e em execução. Certifique-se também de que a fila está disponível para ser aberto com o modo de acesso necessários e a autorização.|  
|MsmqPathLookupError|Ocorreu um erro ao converter o nome de caminho de fila especificado para o nome de formato. Falharam de todas as operações no canal em fila. Certifique-se de que o endereço da fila é válido. MSMQ deve ser instalado com a integração do Active Directory habilitada e o acesso a ele está disponível.|  
|MsmqPerAppDLQRequiresCustom|Falha na validação de associação no cliente. O cliente não pode enviar mensagens. A propriedade CustomDeadLetterQueue está definida, mas a propriedade DeadLetterQueue não está definida como personalizado. Defina a propriedade DeadLetterQueue como Custom.|  
|MsmqPerAppDLQRequiresExactlyOnce|Falha na validação de associação para o cliente. O cliente não pode enviar mensagens. Um conflito nas propriedades da associação está causando a falha. Para usar a fila de mensagens mortas personalizada, ExactlyOnce deve ser definido como verdadeiro para resolver o conflito.|  
|MsmqPerAppDLQRequiresMsmq4|Foi detectada uma incompatibilidade entre a ligação e a configuração do MSMQ. O cliente não pode enviar mensagens. Para usar a fila de mensagens mortas personalizada, você deve ter o MSMQ versão 4.0 ou superior. Se você não tiver o MSMQ versão 4.0 ou superior, defina a propriedade DeadLetterQueue como System ou None.|  
|MsmqReceiveError|Ocorreu um erro ao receber uma mensagem da fila. Certifique-se de que o MSMQ está instalado e em execução. Verifique se que a fila está disponível para recebimento.|  
|MsmqSameTransactionExpected|Ocorreu um erro de transação para esta sessão. O canal da sessão está com defeito. Mensagens na sessão não podem ser enviadas ou recebidas. Uma sessão em fila não pode ser associada a mais de uma transação. Certifique-se de que todas as mensagens na sessão são enviadas ou recebidos por meio de uma única transação.|  
|MsmqSendError|Ocorreu um erro ao enviar para a fila especificada. Certifique-se de que o MSMQ está instalado e em execução. Se você estiver enviando a uma fila local, certifique-se de que a fila existe com a autorização e o modo de acesso necessário.|  
|MsmqTimeSpanTooLarge|O tempo de vida da mensagem é muito grande. Não é possível enviar a mensagem. A tempo de vida (TTL) da mensagem não pode exceder o valor máximo de Int32.|  
|MsmqTokenProviderNeededForCertificates|Não é possível encontrar um X509SecurityTokenProvider. Não é possível enviar a mensagem. O modo de autenticação de certificado requer um provedor de token x. 509. Certifique-se de que um provedor de token de segurança está disponível para o certificado instalado.|  
|MsmqTransactedDLQExpected|Ocorreu uma incompatibilidade entre a ligação e a configuração do MSMQ. Não não possível enviar mensagens. A fila de mensagens mortas personalizada especificada na associação deve ser uma fila de transações. Certifique-se de que o endereço da fila de mensagens mortas personalizada está correto e se a fila é transacional.|  
|MsmqTransactionalQueueNeeded|Ocorreu uma incompatibilidade entre a ligação e a configuração de fila do MSMQ. O ponto de extremidade de serviço não pode ser iniciado. A propriedade ExactlyOnce está definida como true e a fila para ler mensagens de não é uma fila transacional. Para corrigir o erro, defina a propriedade ExactlyOnce como false ou criar uma fila transacional para essa associação.|  
|MsmqTransactionCurrentRequired|Nenhuma transação está disponível para enviar mensagens na sessão. Para enviar uma mensagem em uma sessão em fila requer uma transação. Certifique-se de que um escopo de transação está especificado para enviar a mensagem na sessão.|  
|MsmqTransactionRequired|Uma transação é necessária, mas não está disponível. As mensagens não podem ser enviadas ou recebidas. Certifique-se de que o escopo de transação é especificado para enviar ou receber mensagens.|  
|MsmqUnsupportedSerializationFormat|Ocorreu um erro de desserialização. A mensagem não pode ser recebida e é descartada. Não há suporte para o formato de serialização especificada.|  
|MsmqWrongPrivateQueueSyntax|A URL é inválida. A URL para a fila não pode conter o caractere '$'. Use a sintaxe no MSMQ: //machine/private/queueName para endereçar uma fila particular.|
