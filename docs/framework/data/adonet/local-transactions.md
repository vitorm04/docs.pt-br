---
title: Transações locais
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
ms.openlocfilehash: 979d51a97245bc9616349679ec8cf05cae8c595a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783710"
---
# <a name="local-transactions"></a>Transações locais
As transações em ADO.NET são usadas quando você deseja associar várias tarefas para que elas sejam executadas como uma única unidade de trabalho. Por exemplo, imagine que um aplicativo executa duas tarefas. Primeiro, ele atualiza uma tabela com informações sobre pedidos. Em seguida, ele atualiza uma tabela que contém informações de inventário, debitando os itens pedidos. Se uma das tarefas falhar, as duas atualizações serão revertidas.  
  
## <a name="determining-the-transaction-type"></a>Determinando o tipo de transação  
 Uma transação é considerada uma transação local quando é uma transação de fase única e é manipulada diretamente pelo banco de dados. Uma transação é considerada como uma transação distribuída quando é coordenada por um monitor de transação e usa mecanismos à prova de falhas (como confirmação em duas fases) para a resolução da transação.  
  
 Cada um dos provedores de dados de .NET Framework tem `Transaction` seu próprio objeto para executar transações locais. Se você precisar executar uma transação em um banco de dados do SQL Server, selecione uma transação <xref:System.Data.SqlClient>. Para uma transação Oracle, use o provedor <xref:System.Data.OracleClient>. Além disso, há uma <xref:System.Data.Common.DbTransaction> classe que está disponível para escrever código independente de provedor que requer transações.  
  
> [!NOTE]
> As transações são mais eficientes quando são executadas no servidor. Se você estiver trabalhando com um banco de dados do SQL Server que faz uso extensivo de transações explícitas, considere criá-las como procedimentos armazenados usando a instrução Transact-SQL BEGIN TRANSACTION.
  
## <a name="performing-a-transaction-using-a-single-connection"></a>Executando uma transação com uma única conexão  
 No ADO.net, você controla as transações com `Connection` o objeto. É possível iniciar uma transação local com o método `BeginTransaction`. Depois de iniciar uma transação, você pode inscrever um comando nessa transação com a propriedade `Transaction` de um objeto `Command`. Em seguida, você poderá confirmar ou reverter todas as modificações feitas na fonte de dados com base no êxito ou na falha dos componentes de transação.  
  
> [!NOTE]
> O método `EnlistDistributedTransaction` não deve ser usado para uma transação local.  
  
 O escopo da transação é limitado à conexão. O exemplo a seguir executa uma transação explícita que consiste em dois comandos separados no bloco `try`. Os comandos executam instruções INSERT na tabela Production. ScrapReason da AdventureWorks SQL Server banco de dados de exemplo, que são confirmadas se nenhuma exceção for gerada. O código no bloco `catch` reverte a transação se uma exceção é gerada. Se a transação for anulada ou a conexão for fechada antes de a transação ser concluída, a transação será automaticamente revertida.  
  
## <a name="example"></a>Exemplo  
 Siga estas etapas para executar uma transação.  
  
1. Chame o método <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> do objeto <xref:System.Data.SqlClient.SqlConnection> para marcar o início da transação. O método <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> retorna uma referência à transação. Essa referência é atribuída aos objetos <xref:System.Data.SqlClient.SqlCommand> inscritos na transação.  
  
2. Atribua o objeto `Transaction` à propriedade <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> de <xref:System.Data.SqlClient.SqlCommand> a ser executado. Se um comando for executado em uma conexão com uma transação ativa, e o objeto `Transaction` não tiver sido atribuído à propriedade `Transaction` do objeto `Command`, uma exceção será gerada.  
  
3. Execute os comandos necessários.  
  
4. Chame o método <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> do objeto <xref:System.Data.SqlClient.SqlTransaction> para concluir a transação, ou chame o método <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> para finalizar a transação. Se a conexão for fechada ou descartada antes do método <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> ou <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> ser executado, a transação será revertida.  
  
 O exemplo de código a seguir demonstra a lógica transacional usando ADO.NET com Microsoft SQL Server.  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Transações e simultaneidade](transactions-and-concurrency.md)
- [Transações distribuídas](distributed-transactions.md)
- [Integração de System.Transactions com o SQL Server](system-transactions-integration-with-sql-server.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
