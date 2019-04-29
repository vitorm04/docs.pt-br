---
title: Metadados de estrutura de serviço
ms.date: 03/30/2017
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
ms.openlocfilehash: f65f53ff99202275876fb6e3c431bc49ae2bd38b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780790"
---
# <a name="service-framework-metadata"></a>Metadados de estrutura de serviço
Este tópico lista todas as exceções geradas pelo serviço de estrutura de metadados.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|Um final assíncrono foi chamado em canal incorreto.|  
|AsyncEndCalledWithAnIAsyncResult|Um final assíncrono foi chamado com IAsyncResult de um método Begin diferente.|  
|AttemptedToGetContractTypeForButThatTypeIs1|Tentativa de obter o tipo de contrato especificado. O tipo não é um ServiceContract e não herda um ServiceContract.|  
|CannotHaveTwoOperationsWithTheSameName3|Não é possível ter duas operações no mesmo contrato com o mesmo nome. Os métodos especificados no tipo especificado violam essa regra. Altere o nome de uma das operações alterando o nome do método ou usando a propriedade Name de OperationContractAttribute.|  
|CannotInheritTwoOperationsWithTheSameName3|Não é possível herdar duas operações diferentes com o mesmo nome. A operação especificada dos contratos especificados violam essa regra. Altere o nome de uma das operações alterando o nome do método ou usando a propriedade Name de OperationContractAttribute.|  
|CantCreateChannelWithManualAddressing|Não é possível criar um canal para um contrato que requer uma solicitação/resposta e uma associação que requer endereçamento manual, mas só dá suporte à comunicação duplex.|  
|DuplicateBehavior1|O valor não pode ser adicionado à coleção. A coleção já contém um item do mesmo tipo especificado. Essa coleção só oferece suporte a uma instância de cada tipo.|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|Como o contrato de serviço base especificado tem um contrato de retorno de chamada especificada, o contrato de serviço derivado especificado também deve especificar o tipo especificado ou um tipo derivado como seu contrato de retorno de chamada.|  
|InvalidAsyncBeginMethodSignatureForMethod2|Assíncrona Begin método assinatura inválida para o método especificado no tipo especificado de ServiceContract. Seu começar método deve usar AsyncCallback e um objeto como os dois últimos argumentos e retornar IAsyncResult.|  
|InvalidAsyncEndMethodSignatureForMethod2|Assíncrona final método assinatura inválida para o método especificado no tipo especificado de ServiceContract. Seu método end deve usar IAsyncResult como último argumento.|  
|MessagePropertiesArraySize0|A matriz passada não tem espaço suficiente para conter todas as propriedades incluídas na coleção.|  
|OneWayAndFaultsIncompatible2|O método especificado no tipo especificado está marcado como IsOneWay = true e declara um ou mais FaultContractAttributes. Métodos unidirecionais não podem declarar FaultContractAttributes. Altere IsOneWay para false ou remova FaultContractAttributes.|  
|UnsupportedWSDLOnlyOneMessage|Não há suporte para Web Services Description Language. Apenas uma parte da mensagem tem suporte para mensagens de falha. Essa mensagem de falha se refere a mais de uma parte da mensagem. Se você tiver acesso de edição para o arquivo de Web Services Description Language, você pode corrigir o problema removendo as partes extras de mensagem tal que apenas uma parte de referências de mensagem de falha.|  
|UnsupportedWSDLTheFault|Não há suporte para Web Services Description Language. A parte da mensagem de falha deve fazer referência a um elemento. Essa mensagem de falha não faz referência a um elemento. Se você tiver acesso de edição para o documento de linguagem de definição de serviços da Web, você pode corrigir o problema fazendo referência a um elemento de esquema usando o atributo 'element'.|  
|WsdlImportErrorDependencyDetail|Ocorreu um erro ao importar especificado que o outro valor especificado é dependente. O Xpath também é especificado.|  
|XsdMissingRequiredAttribute1|Atributo ausente especificado foi necessário.|
