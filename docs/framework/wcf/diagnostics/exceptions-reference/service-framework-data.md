---
title: Dados de estrutura de serviço
ms.date: 03/30/2017
ms.assetid: 2a2c8ddc-4e82-4e7f-a79f-97085c469517
ms.openlocfilehash: 5c65e9d473b5fe3f2b1c29824dcc1151abb0c3f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780797"
---
# <a name="service-framework-data"></a>Dados de estrutura de serviço
Este tópico lista todas as exceções geradas pelo serviço de estrutura de dados.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|AddressingExtensionInBadNS|O elemento especificado no namespace especificado não é válido. Isso significa que o elemento especificado é um elemento duplicado ou que não é uma extensão válida porque os elementos de extensão não podem ser no namespace de endereçamento.|  
|BinaryEncoderSessionInvalid|A sessão do codificador binário não é válida porque ocorreu um erro ao decodificar uma mensagem anterior.|  
|CannotDetectAddressingVersion|Não é possível detectar a versão do WS-Addressing. EndpointAddress não começa com um elemento.|  
|CouldNotFindNamespaceForPrefix|O prefixo especificado não tenha nenhuma associação de namespace no escopo.|  
|EncoderBadContentType|Não é possível processar a contentType.|  
|EncoderEnvelopeVersionMismatch|A versão de envelope da mensagem de entrada especificada não coincide com o codificador especificado. Verifique se que a associação está configurada com a mesma versão das mensagens esperadas.|  
|EncoderMessageVersionMismatch|A versão de mensagem da mensagem de saída especificada não coincide com o codificador especificado. Verifique se que a associação está configurada com a mesma versão que a mensagem.|  
|ExtraContentIsPresentInFaultDetail|Conteúdo adicional de Extensible Markup Language está presente no elemento de detalhe de falha. É permitido somente um elemento.|  
|FilterBadTableType|A interface IMessageFilterTable criada para um filtro não pode ser MessageFilterTable ou derivado MessageFilterTable.|  
|FilterTableInvalidForLookup|O estado de MessageFilterTable está corrompido. A pesquisa solicitada não pode ser executada.|  
|MandatoryHeaderNotUnderstood|Um ou mais necessária em blocos de cabeçalho de protocolo de acesso de objeto simples não foram compreendidos.|  
|MessageBodyIsStream|O corpo da mensagem é um fluxo.|  
|MessageBodyIsUnknown|O formato do corpo da mensagem é desconhecido.|  
|MessageBodyReaderInvalidReadState|O ReadState especificado do leitor de corpo de mensagem não pode ser consumido.|  
|MessageTextEncodingNotSupported|Não há suporte para a codificação de texto especificado que é usado no formato de mensagem de texto.|  
|MissingMessageID|Solicitação de que mensagem não tem um cabeçalho MessageID. Um cabeçalho MessageID é necessário para correlacionar uma resposta.|  
|MultipleMessageHeaders|Foram encontrados mais de um cabeçalho com o nome e namespace especificados.|  
|MultipleMessageHeadersWithActor|Mais de um cabeçalho com o nome especificado, o namespace e a função foi encontrada.|  
|MultipleRelatesToHeaders|Foram encontrados mais de um cabeçalho RelatesTo com a relação especificada. Somente um é permitido para cada relação.|  
|QueryFunctionTypeNotSupported|Não há suporte para o IXsltContextFunction tipo de retorno especificado.|  
|QueryIteratorOutOfScope|XPathNodeIterator foi invalidado. XPathNodeIterators que são passados como argumentos para IXsltContextFunctions só são válidos dentro da função. Não pode ser armazenado em cache para uso posterior ou retornados pela função.|  
|QueryVariableNull|Métodos de IXsltContextVariable não podem retornar nulos.|  
|QueryVariableTypeNotSupported|O IXsltContextVariable especificado, não há suporte para o tipo derivado.|  
|ReceiveShutdownReturnedMessage|O canal recebeu uma mensagem de entrada inesperada com ação especificada durante o fechamento. Feche o canal quando não estiver esperando mais mensagens de entrada.|  
|XmlBufferInInvalidState|Ocorreu um erro interno. A operação não pode ser executada devido ao estado do buffer de XML.|  
|XmlBufferQuotaExceeded|O tamanho necessário para armazenar em buffer o conteúdo XML excedeu a cota de buffer.|
