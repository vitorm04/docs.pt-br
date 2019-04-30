---
title: Transporte do MSMQ
ms.date: 03/30/2017
ms.assetid: 3f29a2fe-24df-4614-b64c-b0c084fb7003
ms.openlocfilehash: a2e5384808b82f48bd1d4856bf893130da8c5f1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959413"
---
# <a name="msmq-transport"></a>Transporte do MSMQ
Este tópico lista todas as exceções geradas pelo transporte MSMQ.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|MsmqActiveDirectoryRequiresNativeTransfer|A validação de associação para a mensagem de falha. O cliente não pode enviar mensagens. Um conflito nas propriedades de associação causado essa falha. UseActiveDirectory está definida como true e QueueTransferProtocol está definida para nativo. Para resolver o conflito, corrija uma das propriedades.|  
|MsmqAuthNoneRequiresProtectionNone|A validação de associação para o serviço falhou. O ponto de extremidade de serviço ou o cliente não pode ser iniciado. Um conflito nas propriedades de associação causado essa falha. MsmqAuthenticationMode está definida como None e MsmqProtectionLevel não está definida como None. Para resolver o conflito, corrija uma das propriedades.|  
|MsmqCustomRequiresPerAddDLQ|A validação de associação para a mensagem de falha. O cliente não é possível enviar a mensagem. A propriedade DeadLetterQueue estiver definida como personalizado, mas a propriedade CustomDeadLetterQueue não for especificada. Especifique o URI da fila de mensagens mortas de cada aplicativo na propriedade CustomDeadLetterQueue.|  
|MsmqDeserializationError|Erro encontrado ao desserializar a mensagem XML. A mensagem não pode ser recebida e é descartada.|  
|MsmqDLQNotWriteable|A validação de associação para o cliente falhou. O cliente não pode enviar uma mensagem. A fila de inatividade especificada não existe ou não pode ser gravada. Verifique se que a fila existe com a autorização adequada para gravar nele.|  
|MsmqGetPrivateComputerInformationError|A verificação de versão falhou com o erro especificado. A versão do MSMQ não pode ser detectada por todas as operações que estão no canal em fila falharão. Certifique-se de que o MSMQ está instalado e está disponível.|  
|MsmqNoAssurancesForVolatile|A validação de associação para o serviço falhou. O ponto de extremidade de serviço ou o cliente não pode ser iniciado. A propriedade é definida como true e a propriedade Durable de ExactlyOnce é definida como false. Isso não é suportado. Para resolver o conflito, corrija uma dessas propriedades.|  
|MsmqNonTransactionalQueueNeeded|Foi detectada uma incompatibilidade entre a ligação e a configuração de fila do MSMQ. O ponto de extremidade de serviço não pode ser iniciado. A propriedade ExactlyOnce é definida como false e para ler mensagens de fila é uma fila transacional. Corrija o erro, definindo a propriedade ExactlyOnce como verdadeira ou criar uma associação não-transacional.|  
|MsmqOpenError|Ocorreu um erro ao abrir a fila especificada. A mensagem não pode ser enviada ou recebida da fila. Certifique-se de que o MSMQ está instalado e em execução. Certifique-se também de que a fila está disponível para ser aberto com o modo de acesso necessário e a autorização.|  
|MsmqPathLookupError|Ocorreu um erro ao converter o nome do caminho de fila especificada para o nome do formato. Falharam em todas as operações no canal em fila. Certifique-se de que o endereço da fila é válido. MSMQ deve ser instalado com a integração do Active Directory habilitada e o acesso a ele está disponível.|  
|MsmqPerAppDLQRequiresCustom|Falha na validação de associação no cliente. O cliente não pode enviar mensagens. A propriedade CustomDeadLetterQueue está definida, mas a propriedade DeadLetterQueue não está definida como personalizado. Defina a propriedade DeadLetterQueue personalizada.|  
|MsmqPerAppDLQRequiresExactlyOnce|A validação de associação para o cliente falhou. O cliente não pode enviar mensagens. Um conflito nas propriedades de associação está causando a falha. Para usar a fila de inatividade personalizada, ExactlyOnce deve ser definido como true para resolver o conflito.|  
|MsmqPerAppDLQRequiresMsmq4|Foi detectada uma incompatibilidade entre a ligação e a configuração do MSMQ. O cliente não pode enviar mensagens. Para usar a fila de inatividade personalizada, você deve ter o MSMQ versão 4.0 ou superior. Se você não tiver o MSMQ versão 4.0 ou superior, defina a propriedade DeadLetterQueue como System ou None.|  
|MsmqReceiveError|Ocorreu um erro ao receber uma mensagem da fila. Certifique-se de que o MSMQ está instalado e em execução. Verifique se que a fila está disponível para receber do.|  
|MsmqSameTransactionExpected|Ocorreu um erro de transação para esta sessão. O canal de sessão está com defeito. Mensagens da sessão não podem ser enviadas ou recebidas. Uma sessão na fila não pode ser associada a mais de uma transação. Certifique-se de que todas as mensagens na sessão são enviadas ou recebidos usando uma única transação.|  
|MsmqSendError|Ocorreu um erro durante o envio para a fila especificada. Certifique-se de que o MSMQ está instalado e em execução. Se você estiver enviando a uma fila local, verifique se que a fila existe com o modo de acesso necessário e a autorização.|  
|MsmqTimeSpanTooLarge|A mensagem a vida útil é muito grande. A mensagem não pode ser enviada. A mensagem de tempo de vida (TTL) não pode exceder o valor máximo de Int32.|  
|MsmqTokenProviderNeededForCertificates|Não foi encontrado um X509SecurityTokenProvider. A mensagem não pode ser enviada. O modo de autenticação de certificado requer um provedor de token X.509. Certifique-se de que um provedor de token de segurança está disponível para o certificado instalado.|  
|MsmqTransactedDLQExpected|Ocorreu uma incompatibilidade entre a ligação e a configuração do MSMQ. Não não possível enviar mensagens. A fila de inatividade personalizada especificada na associação deve ser uma fila de transações. Certifique-se de que o endereço da fila de mensagens mortas personalizada está correto e se a fila é uma fila transacional.|  
|MsmqTransactionalQueueNeeded|Ocorreu uma incompatibilidade entre a ligação e a configuração de fila do MSMQ. O ponto de extremidade de serviço não pode ser iniciado. A propriedade ExactlyOnce está definida como true e a fila para ler mensagens de não é uma fila transacional. Para corrigir o erro, defina a propriedade ExactlyOnce como falso ou criar uma fila transacional para essa associação.|  
|MsmqTransactionCurrentRequired|Nenhuma transação está disponível para enviar mensagens da sessão. Para enviar uma mensagem em uma sessão em fila requer uma transação. Certifique-se de que um escopo de transação é especificado para enviar a mensagem na sessão.|  
|MsmqTransactionRequired|Uma transação é necessária, mas não está disponível. As mensagens não podem ser enviadas ou recebidas. Certifique-se de que o escopo da transação é especificado para enviar ou receber mensagens.|  
|MsmqUnsupportedSerializationFormat|Ocorreu um erro de desserialização. A mensagem não pode ser recebida e é descartada. Não há suporte para o formato de serialização especificado.|  
|MsmqWrongPrivateQueueSyntax|A URL é inválida. A URL para a fila não pode conter o caractere '$'. Use a sintaxe MSMQ://machine/private/queueName para identificar uma fila particular.|
