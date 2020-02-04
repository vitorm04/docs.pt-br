---
title: O ADO.NET e LINQ to SQL
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 4d2376a2e32ff099497a5dbcd6cb68d8ed526884
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979996"
---
# <a name="adonet-and-linq-to-sql"></a>O ADO.NET e LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is part of the ADO.NET family of technologies. It is based on services provided by the ADO.NET provider model. You can therefore mix [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] code with existing ADO.NET applications and migrate current ADO.NET solutions to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. A ilustração a seguir fornece uma exibição de alto nível de relacionamento.  
  
 ![LINQ to SQL and ADO.NET](./media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Conexões  
 You can supply an existing ADO.NET connection when you create a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>. All operations against the <xref:System.Data.Linq.DataContext> (including queries) use this provided connection. If the connection is already open, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] leaves it as is when you are finished with it.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Você sempre pode acessar a conexão e fechá-lo você mesmo usando a propriedade de <xref:System.Data.Linq.DataContext.Connection%2A> , como no código a seguir:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>Transações  
 Você pode fornecer seu <xref:System.Data.Linq.DataContext> com sua própria transação de base de dados quando seu aplicativo é iniciado na transação e você deseja que o <xref:System.Data.Linq.DataContext> a ser empacotado.  
  
 The preferred method of doing transactions with the .NET Framework is to use the <xref:System.Transactions.TransactionScope> object. Usando essa abordagem, você pode fazer as transações distribuídas que funcionam através de bases de dados e outros gerentes de recurso de memória residente. Transaction scopes require few resources to start. They promote themselves to distributed transactions only when there are multiple connections within the scope of the transaction.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Você não pode usar essa abordagem para todos os bases de dados. For example, the SqlClient connection cannot promote system transactions when it works against a SQL Server 2000 server. Em vez disso, inscreve-se automaticamente para uma transação completa, distribuído consulta sempre que um escopo de transação que está sendo usado.  
  
## <a name="direct-sql-commands"></a>Comandos SQL diretos  
 Às vezes você pode encontrar situações onde a capacidade de <xref:System.Data.Linq.DataContext> de consulte ou enviar alterações insuficientes para a tarefa específica que você deseja executar. Nesteas circunstâncias você pode usar o método de <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> para emitir comandos SQL a base de dados e para converter os resultados da consulta a objetos.  
  
 Por exemplo, suponha que os dados para a classe de `Customer` são espalhado sobre duas tabelas (customer1 e customer2). A seguinte consulta retorna uma sequência de objetos `Customer` :  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.  
  
### <a name="parameters"></a>Parâmetros  
 O método de <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> aceita parâmetros. O código a seguir executa uma consulta parametrizada:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> Os parâmetros são expressos no texto da consulta usando a mesma notação encaracolado usada por `Console.WriteLine()` e por `String.Format()`. `String.Format()` leva a cadeia de caracteres de consulta que você fornece e substitui os parâmetros encaracolado- apoiados com nomes de parâmetro gerados como `@p0`, `@p1` …, `@p(n)`.  
  
## <a name="see-also"></a>Veja também

- [Informações gerais](background-information.md)
- [Como reutilizar uma conexão entre um comando ADO.NET e um DataContext](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
