---
title: Escrever um aplicativo transacional
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 318771c83a5b7ebc0f3fb2bb8c59240269a2dea9
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205815"
---
# <a name="writing-a-transactional-application"></a>Escrever um aplicativo transacional
Como um programador de aplicativo transacional, você pode tirar proveito dos dois modelos de programação fornecidas pelo <xref:System.Transactions> namespace para criar uma transação. Você pode utilizar o modelo de programação explícito usando a <xref:System.Transactions.Transaction> classe ou o modelo de programação implícito no qual as transações são gerenciadas automaticamente pela infraestrutura, usando a <xref:System.Transactions.TransactionScope> classe. Recomendamos que você use o modelo de transação implícita para desenvolvimento. Você pode encontrar mais informações sobre como usar um escopo de transação no tópico [implementando uma transação implícita usando escopo de transação](implementing-an-implicit-transaction-using-transaction-scope.md) .  
  
 Ambos os modelos dão suporte a confirmar uma transação quando o programa atingir um estado consistente. Se a confirmação for bem-sucedida, a transação é permanentemente confirmada. Se a confirmação falhar, a transação é anulada. Se o programa de aplicativo não puder concluir com êxito a transação, ele tenta cancelar e desfazer os efeitos da transação.  
  
## <a name="in-this-section"></a>Nesta seção  
  
### <a name="creating-a-transaction"></a>Criando uma transação  
 O <xref:System.Transactions> namespace fornece dois modelos para a criação de uma transação. Esses modelos são abordados nos tópicos a seguir.  
  
 [Implementando uma transação implícita, usando o escopo da transação](implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Descreve como o <xref:System.Transactions> namespace oferece suporte à criação de transações implícitas usando o <xref:System.Transactions.TransactionScope> classe.  
  
 [Implementando uma transação explícita usando CommittableTransaction](implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Descreve como o <xref:System.Transactions> namespace oferece suporte à criação de transações explícitas usando o <xref:System.Transactions.CommittableTransaction> classe.  
  
### <a name="escalating-transaction-management"></a>Cada vez maiores de gerenciamento de transações  
 Quando uma transação que precisa acessar um recurso em outro domínio de aplicativo, ou se você deseja inscrever-se em outro gerenciador de recursos duráveis, a transação será escalonada automaticamente para ser gerenciado pelo MSDTC. O escalonamento de transações é abordado no tópico [escalonamento de gerenciamento de transações](transaction-management-escalation.md) .  
  
### <a name="concurrency"></a>Concorrência  
 O tópico [Gerenciando a simultaneidade com o DependentTransaction](managing-concurrency-with-dependenttransaction.md) demonstra como a simultaneidade pode ser obtida <xref:System.Transactions.DependentTransaction> entre tarefas assíncronas usando a classe.  
  
### <a name="com-interop"></a>Interoperabilidade do COM+  
 O tópico [interoperabilidade com os serviços corporativos e as transações com+](interoperability-with-enterprise-services-and-com-transactions.md) ilustra como você pode fazer com que suas transações distribuídas interajam com transações com+.  
  
### <a name="diagnostics"></a>Diagnóstico  
 [Rastreamentos de diagnóstico](diagnostic-traces.md) descreve como você pode usar os códigos de rastreamento gerados pela <xref:System.Transactions> infraestrutura para solucionar erros em seus aplicativos.  
  
### <a name="working-within-aspnet"></a>Trabalhando no ASP.NET  
 O tópico [usando System. Transactions no ASP.net](using-system-transactions-in-aspnet.md) descreve como você pode usar <xref:System.Transactions> com êxito dentro de um aplicativo ASP.net.
