---
title: Metadados de estrutura de serviço
ms.date: 03/30/2017
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
ms.openlocfilehash: f65f53ff99202275876fb6e3c431bc49ae2bd38b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474344"
---
# <a name="service-framework-metadata"></a>Metadados de estrutura de serviço
Este tópico lista todas as exceções geradas pelo serviço de estrutura de metadados.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|Um final assíncrono foi chamado em canal incorreto.|  
|AsyncEndCalledWithAnIAsyncResult|Um final assíncrono foi chamado com IAsyncResult um método diferente de início.|  
|AttemptedToGetContractTypeForButThatTypeIs1|Tentativa de obter o tipo de contrato especificado. O tipo não é um ServiceContract e herda um ServiceContract.|  
|CannotHaveTwoOperationsWithTheSameName3|Não é possível ter duas operações no mesmo contrato com o mesmo nome. Métodos especificados no tipo especificado violam essa regra. Altere o nome de uma das operações alterando o nome do método ou usando a propriedade Name de OperationContractAttribute.|  
|CannotInheritTwoOperationsWithTheSameName3|Não é possível herdar duas operações diferentes com o mesmo nome. A operação especificada de contratos especificados violam essa regra. Altere o nome de uma das operações alterando o nome do método ou usando a propriedade Name de OperationContractAttribute.|  
|CantCreateChannelWithManualAddressing|Não é possível criar um canal para um contrato que requer uma solicitação/resposta e uma associação que requer endereçamento manual, mas só oferece suporte à comunicação duplex.|  
|DuplicateBehavior1|O valor não pode ser adicionado à coleção. A coleção já contém um item do mesmo tipo especificado. Essa coleção apenas oferece suporte a uma instância de cada tipo.|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|Como o contrato de serviço base especificado tem um contrato de retorno de chamada especificada, o contrato de serviço derivada especificada também deve especificar o tipo especificado ou um tipo derivado como seu contrato de retorno de chamada.|  
|InvalidAsyncBeginMethodSignatureForMethod2|Assíncrona Begin método assinatura inválida para o método especificado no tipo de ServiceContract especificado. A começar método deve usar AsyncCallback e um objeto como os dois últimos argumentos e retornar um IAsyncResult.|  
|InvalidAsyncEndMethodSignatureForMethod2|Assíncrono final método assinatura inválida para o método especificado no tipo de ServiceContract especificado. Seu método end deve usar IAsyncResult como último argumento.|  
|MessagePropertiesArraySize0|A matriz que foi passada não tem espaço suficiente para conter todas as propriedades contidas por essa coleção.|  
|OneWayAndFaultsIncompatible2|O método especificado no tipo especificado está marcado como IsOneWay = true e declara um ou mais FaultContractAttributes. Métodos unidirecionais não podem declarar FaultContractAttributes. Altere IsOneWay para false ou remova FaultContractAttributes.|  
|UnsupportedWSDLOnlyOneMessage|Não há suporte para Web Services Description Language. Apenas uma parte da mensagem tem suporte para mensagens de falha. Essa mensagem de falha faz referência a mais de uma parte de mensagem. Se você tem acesso de edição para o arquivo do Web Services Description Language, você pode corrigir o problema removendo as partes extras de mensagem tal que apenas uma parte de referências de mensagem de falha.|  
|UnsupportedWSDLTheFault|Não há suporte para Web Services Description Language. A parte da mensagem de falha deve fazer referência a um elemento. Essa mensagem de falha não faz referência a um elemento. Se você tem acesso de edição ao documento de linguagem de definição de serviços Web, você pode corrigir o problema fazendo referência a um elemento de esquema usando o atributo 'elemento'.|  
|WsdlImportErrorDependencyDetail|Ocorreu um erro ao importar especificado que o outro valor especificado é dependente. O Xpath também é especificado.|  
|XsdMissingRequiredAttribute1|Atributo ausente especificado foi necessário.|
