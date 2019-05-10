---
title: Recursos fornecidos por System.Transactions
ms.date: 03/30/2017
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
ms.openlocfilehash: 75277090652cd439d3466a307790f4b918ddb090
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645710"
---
# <a name="features-provided-by-systemtransactions"></a>Recursos fornecidos por System.Transactions
Esta seção descreve como você pode usar os recursos fornecidos pelo <xref:System.Transactions> namespace para escrever seu próprio Gerenciador de recursos e dos aplicativos transacional. Especificamente, esta seção aborda como criar e participar de uma transação (local ou distribuída) com um ou vários participantes.  
  
## <a name="overview-of-systemtransactions"></a>Visão geral do System. Transactions  
 A infra-estrutura fornecida pelas classes de <xref:System.Transactions> namespace torna transacional de programação simples e eficiente, oferecendo suporte a transações iniciadas no SQL Server, ADO.NET, enfileiramento de mensagens (MSMQ) e Microsoft Distributed Transaction coordenador (MSDTC). O <xref:System.Transactions> namespace fornece dois um modelo de programação explícito com base no <xref:System.Transactions.Transaction> classe, bem como um modelo de programação implícito usando a <xref:System.Transactions.TransactionScope> classe, em que as transações são automaticamente gerenciadas pela infra-estrutura. Para obter mais informações sobre como criar um aplicativo transacional usando esses dois modelos, consulte [escrevendo um aplicativo transacional](../../../../docs/framework/data/transactions/writing-a-transactional-application.md).  
  
 O <xref:System.Transactions> namespace também fornece tipos para implementar um Gerenciador de recursos. Um Gerenciador de recursos gerencia dados duráveis ou voláteis usados em uma transação e trabalhar em cooperação com o Gerenciador de transações para fornecer o aplicativo com uma garantia de atomicidade e isolamento. O Gerenciador de transações fornecida pelo <xref:System.Transactions> infra-estrutura oferece suporte a transações que envolvem vários recursos voláteis ou um único recurso durável. Para obter mais informações sobre como implementar um Gerenciador de recursos, consulte [implementar um Gerenciador de recursos](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md).  
  
 O Gerenciador de transações também transparentemente escala transações locais para transações distribuídas através da coordenação com um Gerenciador de transações baseadas em disco como o DTC, quando um Gerenciador de recursos adicionais de durável inscreve-se com uma transação. Há duas maneiras principais que o <xref:System.Transactions> infra-estrutura proporciona um desempenho aprimorado.  
  
- Escalonamento dinâmico, o que garante que o <xref:System.Transactions> infra-estrutura apenas emprega o MSDTC quando uma transação engloba vários recursos distribuídos. Para obter mais informações sobre o escalonamento dinâmico. ver [escalonamento de gerenciamento de transações](../../../../docs/framework/data/transactions/transaction-management-escalation.md) tópico.  
  
- Podem ser promovidas inscrições, que permite que um recurso, como um banco de dados, apropriar-se da transação se for a única entidade participa da transação. Posteriormente, se necessário, o <xref:System.Transactions> infra-estrutura ainda pode escalonar o gerenciamento da transação para o MSDTC. Isso reduz ainda mais a possibilidade de usar o MSDTC. Podem ser promovidas são abordadas em detalhes no tópico[otimização usando confirmação de fase única e notificação de fase única passível de promoção](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
 O <xref:System.Transactions> namespace define três níveis de confiança - AllowPartiallyTrustedCallers (APTCA), DistributedTransactionPermission(DTP) e confiança total - que restringem o acesso aos tipos de recursos ele expõe. Para obter mais informações sobre os vários níveis de confiança, consulte [níveis de confiança de segurança no acessando recursos](../../../../docs/framework/data/transactions/security-trust-levels-in-accessing-resources.md).  
  
## <a name="in-this-section"></a>Nesta seção  
  
### <a name="writing-a-transactional-application"></a>Escrevendo um aplicativo transacional  
 O <xref:System.Transactions> namespace fornece dois modelos para criar aplicativos transacionais. [Implementando uma transação implícita, usando o escopo da transação](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) descreve como o <xref:System.Transactions> namespace oferece suporte à criação de transações implícitas usando o <xref:System.Transactions.TransactionScope> classe.  
  
 [Implementando uma transação explícita usando CommittableTransaction](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md) descreve como o <xref:System.Transactions> namespace oferece suporte à criação de transações explícitas usando o <xref:System.Transactions.CommittableTransaction> classe.  
  
 Para tópicos adicionais que abrangem escrevendo um aplicativo transacional, consulte [escrevendo um aplicativo transacional](../../../../docs/framework/data/transactions/writing-a-transactional-application.md).  
  
### <a name="implementing-a-resource-manager"></a>Implementar um Gerenciador de recursos  
 Para implementar um Gerenciador de recursos que pode participar em uma transação, consulte [implementar um Gerenciador de recursos](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md). Esta seção aborda a inscrição de um recurso, confirmar uma transação, a recuperação após falha e práticas recomendadas de otimização.
