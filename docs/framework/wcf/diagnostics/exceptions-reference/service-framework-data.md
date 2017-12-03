---
title: "Dados de estrutura de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a2c8ddc-4e82-4e7f-a79f-97085c469517
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7c20da9f4eafa615ff23bad4d78e669a8417464
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="service-framework-data"></a>Dados de estrutura de serviço
Este tópico lista todas as exceções geradas pelo serviço de estrutura de dados.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|AddressingExtensionInBadNS|O elemento especificado no namespace especificado não é válido. Isso significa que o elemento especificado é um elemento duplicado ou que não é uma extensão legal porque os elementos de extensão não podem estar em namespaces de endereçamento.|  
|BinaryEncoderSessionInvalid|A sessão de codificador binário não é válida porque houve um erro ao decodificar uma mensagem anterior.|  
|CannotDetectAddressingVersion|Não é possível detectar a versão do WS-Addressing. EndpointAddress não começar com um elemento.|  
|CouldNotFindNamespaceForPrefix|O prefixo especificado não tem nenhuma associação de namespace no escopo.|  
|EncoderBadContentType|Não é possível processar contentType.|  
|EncoderEnvelopeVersionMismatch|A versão de envelope da mensagem de entrada especificada não coincide com o codificador especificado. Verifique se que a associação está configurada com a mesma versão das mensagens esperadas.|  
|EncoderMessageVersionMismatch|A versão de mensagem da mensagem de saída especificada não coincide com o codificador especificado. Verifique se que a associação está configurada com a mesma versão da mensagem.|  
|ExtraContentIsPresentInFaultDetail|Conteúdo XML adicional está presente no elemento de detalhes da falha. É permitido somente um elemento.|  
|FilterBadTableType|A interface IMessageFilterTable criada para um filtro não pode ser MessageFilterTable ou derivado de MessageFilterTable.|  
|FilterTableInvalidForLookup|O estado de MessageFilterTable está corrompido. A pesquisa solicitada não pode ser executada.|  
|MandatoryHeaderNotUnderstood|Um ou mais necessários não foram entendidos blocos de cabeçalho de protocolo de acesso de objeto simples.|  
|MessageBodyIsStream|O corpo da mensagem é um fluxo.|  
|MessageBodyIsUnknown|O formato do corpo da mensagem é desconhecido.|  
|MessageBodyReaderInvalidReadState|O ReadState especificado do leitor de corpo de mensagem não pode ser consumido.|  
|MessageTextEncodingNotSupported|Não há suporte para a codificação do texto especificado que é usado no formato de mensagem de texto.|  
|MissingMessageID|Solicitação de que mensagem está faltando um cabeçalho MessageID. Um cabeçalho MessageID é necessário para correlacionar uma resposta.|  
|MultipleMessageHeaders|Mais de um cabeçalho com o nome especificado e o namespace foi encontrado.|  
|MultipleMessageHeadersWithActor|Foi encontrado mais de um cabeçalho com o nome especificado, o namespace e a função.|  
|MultipleRelatesToHeaders|Foi encontrado mais de um cabeçalho RelatesTo com a relação especificada. Somente um é permitido para cada relação.|  
|QueryFunctionTypeNotSupported|Não há suporte para o IXsltContextFunction tipo de retorno especificado.|  
|QueryIteratorOutOfScope|XPathNodeIterator foi invalidado. XPathNodeIterators transmitidos como argumentos a IXsltContextFunctions apenas são válidos na função. Não pode ser armazenado em cache para uso posterior ou retornados pela função.|  
|QueryVariableNull|Métodos de IXsltContextVariable não podem retornar nulos.|  
|QueryVariableTypeNotSupported|O IXsltContextVariable especificado, não há suporte para tipo derivado.|  
|ReceiveShutdownReturnedMessage|O canal recebeu uma mensagem de entrada inesperada com ação especificada durante o fechamento. Feche o canal quando não estiver esperando mais mensagens de entrada.|  
|XmlBufferInInvalidState|Ocorreu um erro interno. A operação não pode ser executada devido ao estado do buffer de XML.|  
|XmlBufferQuotaExceeded|O tamanho necessário para armazenar em buffer o conteúdo XML ultrapassou a cota de buffer.|
