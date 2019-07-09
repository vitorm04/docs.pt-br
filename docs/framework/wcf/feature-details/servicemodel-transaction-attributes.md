---
title: Atributos de transação de ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel attributes
ms.assetid: 1e0d2436-6ae5-439b-9765-a448d6f60000
ms.openlocfilehash: d4b7482431404241577111d8dd3841319b65696e
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663691"
---
# <a name="servicemodel-transaction-attributes"></a>Atributos de transação de ServiceModel

Windows Communication Foundation (WCF) fornece as propriedades no padrão de três <xref:System.ServiceModel> atributos que permitem que você configure o comportamento de transações para um serviço WCF:

- <xref:System.ServiceModel.TransactionFlowAttribute>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>

- <xref:System.ServiceModel.OperationBehaviorAttribute>

## <a name="transactionflowattribute"></a>TransactionFlowAttribute

O <xref:System.ServiceModel.TransactionFlowAttribute> atributo especifica a disposição de uma operação em um contrato de serviço para aceitar as transações de entrada de um cliente. O atributo fornece esse controle com a seguinte propriedade: As transações que usam o <xref:System.ServiceModel.TransactionFlowOption> enumeração para especificar se uma transação de entrada <xref:System.ServiceModel.TransactionFlowOption.Mandatory>, <xref:System.ServiceModel.TransactionFlowOption.Allowed>, ou <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.

Isso é o único atributo que relaciona as operações de serviço para interações externas com um cliente. Os atributos descritos nas seções a seguir estão relacionadas ao uso de transações da execução da operação.

## <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute

O <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo especifica o comportamento de execução interna de uma implementação de contrato de serviço. Propriedades de transação específica desse atributo incluem:

- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> Especifica se deve concluir uma transação incompleta quando a sessão é fechada. O valor padrão desta propriedade é `false`. Se essa propriedade for `true`e a sessão de entrada foi desligar normalmente em vez de falhas de fechamento devido à rede ou cliente, qualquer transação incompleta é concluída com êxito. Caso contrário, se essa propriedade é `false` ou se a sessão não foi fechada normalmente, qualquer transação incompleta é revertida quando a sessão é fechada. Se essa propriedade for `true`, o canal de entrada deve ser baseada em sessão.

- <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> Especifica se a instância do serviço subjacente é liberada quando uma transação é concluída. O valor padrão desta propriedade é `true`. A próxima mensagem de entrada faz com que uma nova instância subjacente deve ser criada, descartando qualquer estado por transação que a instância anterior pode ter mantido. Liberação de uma instância de serviço é uma ação interna, o serviço usa e não tem impacto sobre quaisquer conexões existentes ou sessões que os clientes podem ter estabelecido. Essa funcionalidade é equivalente a COM+ fornece o recurso de ativação just-in-time. Se a propriedade estiver `true`, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> deve ser igual a <xref:System.ServiceModel.ConcurrencyMode.Single>. Caso contrário, o serviço gera uma exceção de validação de uma configuração inválida durante a inicialização.

- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> Especifica o nível de isolamento a ser usado para transações dentro do serviço; Esta propriedade usa um do <xref:System.Transactions.IsolationLevel> valores. Se a propriedade de nível de isolamento local for algo diferente de <xref:System.Transactions.IsolationLevel.Unspecified>, o nível de isolamento de uma transação de entrada deve corresponder à configuração dessa propriedade local. Caso contrário, a transação de entrada é rejeitada e uma falha é enviada de volta ao cliente. Se <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> está `true`, e nenhuma transação é colocada em fluxo, essa propriedade determina o <xref:System.Transactions.IsolationLevel> valor a ser usado para a transação criada localmente. Se <xref:System.Transactions.IsolationLevel> é definido como <xref:System.Transactions.IsolationLevel.Unspecified>, <xref:System.Transactions.IsolationLevel> <xref:System.Transactions.IsolationLevel.Serializable> é usado.

- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> Especifica o período de tempo dentro do qual uma nova transação criada no serviço deve ser concluída. Se esse tempo for atingido e a transação não foi concluída, ela será anulada. O <xref:System.TimeSpan> é usado como o <xref:System.Transactions.TransactionScope> tempo limite para todas as operações que têm <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> definido como `true` e para o qual foi criada uma nova transação. O tempo limite é a duração máxima permitida da criação da transação para a conclusão da fase 1 no protocolo 2PC. O valor de tempo limite usado é sempre o menor valor entre o <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> propriedade e o `transactionTimeout` definição de configuração.

## <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute

O <xref:System.ServiceModel.OperationBehaviorAttribute> atributo especifica os comportamentos dos métodos na implementação do serviço. Você pode usá-lo para indicar o comportamento de execução específica da operação. As propriedades desse atributo não afetam a descrição de descrição linguagem WSDL (Web Service) do contrato de serviço e são puramente os elementos do modelo de programação WCF que habilitam recursos comuns que os desenvolvedores caso contrário, precisam implementar em si.

Este atributo tem as seguintes propriedades de transação específica:

- <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Especifica se um método deve ser executado dentro de um escopo de transação ativa. O padrão é `false`. Se o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo não for definido para um método, ele também implica que o método não será executado em uma transação. Se um escopo de transação não é necessário para uma operação, qualquer transação que está presente no cabeçalho da mensagem não está ativada e permanece como um elemento do <xref:System.ServiceModel.OperationContext.IncomingMessageProperties%2A> do <xref:System.ServiceModel.OperationContext>. Se um escopo de transação é necessário para uma operação, o código-fonte para a transação é derivado de um dos seguintes:

  - Se uma transação flui do cliente, o método é executado em um escopo de transação criado usando essa transação distribuída.

  - Com um transporte em fila, a transação usada para remover a mensagem da fila é usada. Observe que a transação usada não é uma transação fluída, em que ele não foi fornecido pelo remetente da mensagem original.

  - Um transporte personalizado pode fornecer uma transação com o uso da `TransportTransactionProperty`.

  - Se nenhum deles fornece uma fonte externa para uma transação, um novo <xref:System.Transactions.Transaction> instância é criada imediatamente antes de chamar o método.

- <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Especifica se a transação na qual o método é executado é preenchida automaticamente se nenhuma exceção sem tratamento é geradas. Se essa propriedade for `true`, a infraestrutura de chamada marca automaticamente a transação como "concluído", se o método de usuário retornar sem gerar uma exceção. Se essa propriedade estiver `false`, a transação é anexada à instância e só é marcada como "concluído" se o cliente chama um método subsequente que é marcado com essa propriedade igual a `true`, ou se um explicitamente as chamadas método subsequentes <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A>. Falha ao executar qualquer uma delas resulta na transação nunca sendo "concluída", e o trabalho independente não for confirmado, a menos que o <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> estiver definida como `true`. Se essa propriedade é definida como `true`, você deve usar um canal com uma sessão e o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> deve ser definida como <xref:System.ServiceModel.InstanceContextMode.PerSession>.
