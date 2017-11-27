---
title: "Suporte a transações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c1d438a83f090795a158ade1dfdbb7d2b2df863
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="transaction-support"></a>Suporte a transações
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]dá suporte a três modelos de transação distinta. Veja a seguir esses modelos na ordem das verificações executadas.  
  
## <a name="explicit-local-transaction"></a>Transação local explícita  
 Quando o método <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é chamado, se a propriedade <xref:System.Data.Linq.DataContext.Transaction%2A> estiver definida como uma transação (`IDbTransaction`), a chamada <xref:System.Data.Linq.DataContext.SubmitChanges%2A> será executada no contexto da mesma transação.  
  
 Cabe a você confirmar ou reverter a transação após sua execução bem-sucedida. A conexão que corresponde à transação deve corresponder à conexão usada para construir a classe <xref:System.Data.Linq.DataContext>. Uma exceção será gerada se outra conexão for usada.  
  
## <a name="explicit-distributable-transaction"></a>Transação distribuível explícita  
 Você pode chamar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (incluindo, mas não limitado a <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) no escopo de um ativo <xref:System.Transactions.Transaction>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]detecta que a chamada está no escopo de uma transação e não cria uma nova transação. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]evita também fechando a conexão nesse caso. Você pode fazer a consulta e executar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no contexto de uma transação.  
  
## <a name="implicit-transaction"></a>Transação implícita  
 Quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] verifica se a chamada está no escopo de um <xref:System.Transactions.Transaction> ou se o `Transaction` propriedade (`IDbTransaction`) é definido como uma transação local iniciado pelo usuário. Se ele encontrar nenhuma transação [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] inicia uma transação local (`IDbTransaction`) e o utiliza para executar os comandos SQL gerados. Quando todos os comandos SQL foi concluídos com êxito, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] confirma a transação local e retorna.  
  
## <a name="see-also"></a>Consulte também  
 [Informações de plano de fundo](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Como: submissões de dados colchete usando transações](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
