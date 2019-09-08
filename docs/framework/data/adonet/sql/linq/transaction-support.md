---
title: Suporte a transações
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: 9c7128ef432fa609b8d628bc74caebe790058ede
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792279"
---
# <a name="transaction-support"></a>Suporte a transações
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]dá suporte a três modelos de transação distintos. Veja a seguir esses modelos na ordem das verificações executadas.  
  
## <a name="explicit-local-transaction"></a>Transação local explícita  
 Quando o método <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é chamado, se a propriedade <xref:System.Data.Linq.DataContext.Transaction%2A> estiver definida como uma transação (`IDbTransaction`), a chamada <xref:System.Data.Linq.DataContext.SubmitChanges%2A> será executada no contexto da mesma transação.  
  
 Cabe a você confirmar ou reverter a transação após sua execução bem-sucedida. A conexão que corresponde à transação deve corresponder à conexão usada para construir a classe <xref:System.Data.Linq.DataContext>. Uma exceção será gerada se outra conexão for usada.  
  
## <a name="explicit-distributable-transaction"></a>Transação distribuível explícita  
 Você pode chamar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (incluindo, mas não se <xref:System.Data.Linq.DataContext.SubmitChanges%2A>limitando a) no escopo de <xref:System.Transactions.Transaction>um ativo. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]detecta que a chamada está no escopo de uma transação e não cria uma nova transação. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]também evita que você feche a conexão nesse caso. Você pode fazer a consulta e executar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no contexto de uma transação.  
  
## <a name="implicit-transaction"></a>Transação implícita  
 Quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o verifica se a chamada está no escopo de um <xref:System.Transactions.Transaction> ou se a `Transaction` Propriedade (`IDbTransaction`) está definida como uma transação local iniciada pelo usuário. Se ele não encontrar nenhuma transação [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , iniciará uma transação`IDbTransaction`local () e a usará para executar os comandos SQL gerados. Quando todos os comandos SQL tiverem sido concluídos com [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] êxito, o confirmará a transação local e retornará.  
  
## <a name="see-also"></a>Consulte também

- [Informações gerais](background-information.md)
- [Como: Envios de dados de colchetes usando transações](how-to-bracket-data-submissions-by-using-transactions.md)
