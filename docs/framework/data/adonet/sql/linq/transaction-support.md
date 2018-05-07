---
title: Suporte a transações
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: ff4d65c37e2d7f76c8c9f0de1de9717c8dca7b27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-support"></a>Suporte a transações
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dá suporte a três modelos de transação distinta. Veja a seguir esses modelos na ordem das verificações executadas.  
  
## <a name="explicit-local-transaction"></a>Transação local explícita  
 Quando o método <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é chamado, se a propriedade <xref:System.Data.Linq.DataContext.Transaction%2A> estiver definida como uma transação (`IDbTransaction`), a chamada <xref:System.Data.Linq.DataContext.SubmitChanges%2A> será executada no contexto da mesma transação.  
  
 Cabe a você confirmar ou reverter a transação após sua execução bem-sucedida. A conexão que corresponde à transação deve corresponder à conexão usada para construir a classe <xref:System.Data.Linq.DataContext>. Uma exceção será gerada se outra conexão for usada.  
  
## <a name="explicit-distributable-transaction"></a>Transação distribuível explícita  
 Você pode chamar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (incluindo, mas não limitado a <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) no escopo de um ativo <xref:System.Transactions.Transaction>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] detecta que a chamada está no escopo de uma transação e não cria uma nova transação. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] evita também fechando a conexão nesse caso. Você pode fazer a consulta e executar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no contexto de uma transação.  
  
## <a name="implicit-transaction"></a>Transação implícita  
 Quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] verifica se a chamada está no escopo de um <xref:System.Transactions.Transaction> ou se o `Transaction` propriedade (`IDbTransaction`) é definido como uma transação local iniciado pelo usuário. Se ele encontrar nenhuma transação [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] inicia uma transação local (`IDbTransaction`) e o utiliza para executar os comandos SQL gerados. Quando todos os comandos SQL foi concluídos com êxito, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] confirma a transação local e retorna.  
  
## <a name="see-also"></a>Consulte também  
 [Informações gerais](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Como delimitar submissões de dados entre colchetes usando transações](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
