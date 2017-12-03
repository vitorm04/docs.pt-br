---
title: "Conceitos básicos de transação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 353f4ee2-e6bf-4b1c-b1c8-385fc8a486c0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f33e6ada38e3e1cb5b7b564f75ca43aa07ee1882
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-fundamentals"></a>Conceitos básicos de transação
Transações associar várias tarefas. Por exemplo, imagine que um aplicativo executa duas tarefas. Primeiro, ele cria uma nova tabela em um banco de dados. Em seguida, ele chama um objeto especializado para coletar, formatar e inserir dados na nova tabela. Essas duas tarefas estão relacionadas e até mesmo interdependentes, que você deseja evitar a criação de uma nova tabela, a menos que você pode preenchê-lo com dados. Ambas as tarefas dentro do escopo de uma única transação em execução impõe a conexão entre elas. Se a segunda tarefa falhar, a primeira tarefa será revertida para um ponto antes que a nova tabela foi criada.  
  
 Para garantir um comportamento previsível, todas as transações devem ter as propriedades básicas de ACID (atômicas, consistentes, isoladas e duráveis). Essas propriedades reforçam a função de transações de missão crítica como propostas de tudo ou nada. Para obter mais informações sobre ACID, consulte [propriedades ACID](http://go.microsoft.com/fwlink/?LinkId=98791). Em resumo, ACID garante que um conjunto de relacionadas tarefas ter êxito ou falharem como uma unidade. Na transação terminologia, a transação seja confirmada ou anulada. Para uma transação de confirmação, todos os participantes devem garantir que qualquer alteração nos dados será permanente. As alterações devem persistir mesmo que haja falhas do sistema ou outros eventos imprevisíveis. Se até mesmo um único participante não fizer essa garantia, a transação inteira falhará. Todas as alterações de dados dentro do escopo da transação serão revertidas para um ponto específico do conjunto.  
  
 Uma transação pode ser restrito a um recurso de dados simples, como uma fila de banco de dados ou mensagem. Nesse cenário, a transação local é gerenciada pelo Gerenciador de transações fornecida pelo <xref:System.Transactions> , que gera o ganho de desempenho. Controlado pelo recurso de dados, essas transações são eficientes e fáceis de gerenciar.  
  
 As transações também podem abranger vários recursos de dados. Transações distribuídas lhe oferece a capacidade de incorporar várias operações distintas que ocorrem em diferentes sistemas em uma única passagem ou falha da ação. Nesse cenário, as transações são coordenadas pelo Microsoft Distributed transação coordenador (MSDTC) que reside em cada sistema.  
  
 Quando você desenvolve um aplicativo transacional usando as classes fornecidas pela <xref:System.Transactions>, você não precisa se preocupar sobre que tipo de transações que você precisa, ou o Gerenciador de transações envolvidos. O <xref:System.Transactions> infra-estrutura gerencia automaticamente para você.  
  
 Quando você cria uma transação, você pode especificar o nível de isolamento que se aplica à transação. O nível de isolamento definido pelo <xref:System.Transactions.IsolationLevel> da classe, determina o nível de acesso que outras transações deve ter os dados afetado pela sua transação.  
  
 Você pode criar transações usando o ADO.NET, <xref:System.EnterpriseServices>, ou o modelo de programação transacional fornecido pelo <xref:System.Transactions> namespace. O [recursos fornecidos pelo System. Transactions](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md) tópico aborda os recursos que você pode usar para escrever um aplicativo transacional usando o <xref:System.Transactions> namespace.  
  
## <a name="see-also"></a>Consulte também  
 [Features Provided by System.Transactions](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md) (Recursos fornecidos por System.Transactions)
