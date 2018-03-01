---
title: "Atributos de transação de ServiceModel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [WCF], ServiceModel attributes
ms.assetid: 1e0d2436-6ae5-439b-9765-a448d6f60000
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aac52f3c542f88adbca40c6cbbdddc734e12903b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="servicemodel-transaction-attributes"></a>Atributos de transação de ServiceModel
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Fornece as propriedades padrão de três <xref:System.ServiceModel> atributos que permitem que você configure o comportamento das transações para um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço:  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute>  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute>  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute>  
  
## <a name="transactionflowattribute"></a>TransactionFlowAttribute  
 O <xref:System.ServiceModel.TransactionFlowAttribute> atributo especifica a disposição de uma operação em um contrato de serviço para aceitar as transações de entrada de um cliente. O atributo fornece esse controle com a seguinte propriedade: as transações que usam o <xref:System.ServiceModel.TransactionFlowOption> enumeração para especificar se uma transação de entrada é <xref:System.ServiceModel.TransactionFlowOption.Mandatory>, <xref:System.ServiceModel.TransactionFlowOption.Allowed>, ou <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.  
  
 Este é o único atributo que relaciona as operações de serviço para interações externas com um cliente. Os atributos descritos nas seções a seguir se relacionam com o uso de transações da execução da operação.  
  
## <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute  
 O <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo especifica o comportamento de execução interna de uma implementação do contrato de serviço. Propriedades de transação específica desse atributo incluem:  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A>Especifica se a concluir uma transação incompleta quando a sessão for fechada. O valor padrão dessa propriedade é `false`. Se essa propriedade for `true`e a sessão de entrada foi fechada normalmente em vez de fechar devido à rede ou cliente de falhas, qualquer transação incompleta for concluída com êxito. Caso contrário, se essa propriedade for `false` ou se a sessão não foi fechada normalmente, qualquer transação incompleta é revertida quando a sessão for fechada. Se essa propriedade for `true`, o canal de entrada deve ser baseada em sessão.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A>Especifica se a instância de serviço subjacente é lançada quando uma transação é concluída. O valor padrão dessa propriedade é `true`. A próxima mensagem de entrada faz com que uma nova instância subjacente deve ser criada, descartando qualquer estado por transação que a instância anterior pode ter mantidos. Liberar uma instância de serviço é uma ação interna, o serviço usa e não tem nenhum impacto em qualquer conexões existentes ou sessões que os clientes podem estabelecer. Essa funcionalidade é equivalente ao recurso de ativação just-in-time QUE COM+ fornece. Se a propriedade for `true`, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> deve ser igual a <xref:System.ServiceModel.ConcurrencyMode.Single>. Caso contrário, o serviço gera uma exceção de validação de configuração inválido durante a inicialização.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>Especifica o nível de isolamento a ser usado para transações dentro do serviço; Essa propriedade tem um do <xref:System.Transactions.IsolationLevel> valores. Se a propriedade de nível de isolamento local for algo diferente de <xref:System.Transactions.IsolationLevel.Unspecified>, o nível de isolamento de uma transação de entrada deve corresponder à configuração da propriedade local. Caso contrário, a transação de entrada é rejeitada e uma falha é enviada de volta ao cliente. Se <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> é `true`, e nenhuma transação flui, essa propriedade determina o <xref:System.Transactions.IsolationLevel> valor a ser usado para a transação localmente criada. Se <xref:System.Transactions.IsolationLevel> é definido como <xref:System.Transactions.IsolationLevel.Unspecified>, <xref:System.Transactions.IsolationLevel> <xref:System.Transactions.IsolationLevel.Serializable> é usado.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>Especifica o período de tempo dentro do qual deve concluir uma nova transação criada no serviço. Se esse tempo for alcançado e a transação não foi concluída, será anulada. O <xref:System.TimeSpan> é usado como o <xref:System.Transactions.TransactionScope> tempo limite para todas as operações que têm <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> definido como `true` e para o qual foi criada uma nova transação. O tempo limite é a duração máxima permitida da criação da transação para a conclusão da fase 1 no protocolo de confirmação de duas fases. O valor de tempo limite usado sempre é o menor valor entre o <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> propriedade e o `transactionTimeout` de configuração.  
  
## <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute  
 O <xref:System.ServiceModel.OperationBehaviorAttribute> atributo especifica os comportamentos dos métodos na implementação do serviço. Você pode usar isso para indicar o comportamento de execução específica da operação. Propriedades desse atributo não afetam a descrição de serviço descrição linguagem WSDL (Web) do contrato de serviço e são apenas os elementos do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação que permitem que os desenvolvedores precisam implementar os recursos comuns si mesmos.  
  
 Este atributo tem as seguintes propriedades de transação específica:  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>Especifica se um método deve ser executada em um escopo de transação ativa. O padrão é `false`. Se o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo não está definido para um método, isso também significa que o método não será executado em uma transação. Se um escopo de transação não é necessário para uma operação, qualquer transação que está presente no cabeçalho da mensagem não está ativada e permanece como um elemento de <xref:System.ServiceModel.OperationContext.IncomingMessageProperties%2A> do <xref:System.ServiceModel.OperationContext>. Se um escopo de transação é necessário para uma operação, a origem da transação é derivada de uma das seguintes opções:  
  
    -   Se uma transação flui do cliente, o método é executado em um escopo de transação criado usando a transação distribuída.  
  
    -   Com um transporte em fila, a transação usada para a mensagem de remoção da fila é usada. Observe que a transação usada não é uma transação que fluiu, em que ele não foi fornecido pelo remetente da mensagem original.  
  
    -   Um transporte personalizado pode fornecer uma transação com o uso do `TransportTransactionProperty`.  
  
    -   Se nenhum deles fornece uma fonte externa para uma transação, um novo <xref:System.Transactions.Transaction> instância for criada imediatamente antes de chamar o método.  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>Especifica se a transação na qual o método é executado é preenchida automaticamente se nenhuma exceção sem tratamento é geradas. Se essa propriedade for `true`, a infraestrutura de chamada marca automaticamente a transação como "concluído", se o método de usuário retornar sem gerar uma exceção. Se essa propriedade for `false`, a transação está associada à instância e só é marcada como "concluído" se o cliente chama um método subsequente que está marcado com essa propriedade igual a `true`, ou se um explicitamente as chamadas método subsequentes <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A>. Falha ao executar qualquer um deles resulta na transação nunca sendo "concluída" e o trabalho independente não é confirmado, a menos que o <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> está definida como `true`. Se essa propriedade é definida como `true`, você deve usar um canal com uma sessão e o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> deve ser definido como <xref:System.ServiceModel.InstanceContextMode.PerSession>.
