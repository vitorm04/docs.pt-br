---
title: Escrever um aplicativo transacional
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 048df434ff0ada2ab5f8c7473913f6c34c05d1a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793485"
---
# <a name="writing-a-transactional-application"></a>Escrever um aplicativo transacional
Como um programador de aplicativo transacional, você pode tirar proveito dos dois modelos de programação fornecidas pelo <xref:System.Transactions> namespace para criar uma transação. Você pode utilizar o modelo de programação explícito usando o <xref:System.Transactions.Transaction> classe ou o modelo de programação implícito na qual as transações são automaticamente gerenciadas pela infra-estrutura, usando o <xref:System.Transactions.TransactionScope> classe. É recomendável que você use o modelo de transação implícita para o desenvolvimento. Você pode encontrar mais informações sobre como usar um escopo de transação na [implementando uma transação implícita, usando o escopo da transação](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) tópico.  
  
 Ambos os modelos dão suporte a confirmar uma transação quando o programa atingir um estado consistente. Se a confirmação for bem-sucedida, a transação é permanentemente confirmada. Se a confirmação falhar, a transação é anulada. Se o programa de aplicativo não puder concluir com êxito a transação, ele tenta cancelar e desfazer os efeitos da transação.  
  
## <a name="in-this-section"></a>Nesta seção  
  
### <a name="creating-a-transaction"></a>Criando uma transação  
 O <xref:System.Transactions> namespace fornece dois modelos para a criação de uma transação. Esses modelos são abordados nos tópicos a seguir.  
  
 [Implementando uma transação implícita, usando o escopo da transação](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Descreve como o <xref:System.Transactions> namespace oferece suporte à criação de transações implícitas usando o <xref:System.Transactions.TransactionScope> classe.  
  
 [Implementando uma transação explícita usando CommittableTransaction](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Descreve como o <xref:System.Transactions> namespace oferece suporte à criação de transações explícitas usando o <xref:System.Transactions.CommittableTransaction> classe.  
  
### <a name="escalating-transaction-management"></a>Cada vez maiores de gerenciamento de transações  
 Quando uma transação que precisa acessar um recurso em outro domínio de aplicativo, ou se você deseja inscrever-se em outro gerenciador de recursos duráveis, a transação será escalonada automaticamente para ser gerenciado pelo MSDTC. Escalonamento de bloqueios de transação é abordado a [escalonamento de gerenciamento de transações](../../../../docs/framework/data/transactions/transaction-management-escalation.md) tópico.  
  
### <a name="concurrency"></a>Concorrência  
 O tópico [Gerenciando a simultaneidade com DependentTransaction](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) demonstra como a simultaneidade pode ser obtida entre tarefas assíncronas usando o <xref:System.Transactions.DependentTransaction> classe.  
  
### <a name="com-interop"></a>Interoperabilidade do COM+  
 O tópico [interoperabilidade com serviços da empresa e transações COM+](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md) ilustra como você pode fazer com que suas transações distribuídas interagem com transações COM+.  
  
### <a name="diagnostics"></a>Diagnóstico  
 [Rastreamentos de diagnóstico](../../../../docs/framework/data/transactions/diagnostic-traces.md) descreve como você pode usar os códigos de rastreamento gerados pelo <xref:System.Transactions> infra-estrutura para solucionar problemas de erros em seus aplicativos.  
  
### <a name="working-within-aspnet"></a>Trabalhando no ASP.NET  
 O [usando o System. Transactions no ASP.NET](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) tópico descreve como você pode usar com êxito <xref:System.Transactions> dentro de um aplicativo ASP.NET.
