---
title: O que você pode fazer com LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: 719c2e5c97d3f8c64de53831ac50b2e7156a38fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="what-you-can-do-with-linq-to-sql"></a>O que você pode fazer com LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oferece suporte a todos os recursos de chave esperado como um desenvolvedor SQL. Você pode consultar informações, e inserir, atualizar e excluir informações de tabelas.  
  
## <a name="selecting"></a>Selecionando  
 Selecionar (*projeção*) é obtida simplesmente gravando um [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] consultar em sua linguagem de programação e, em seguida, executar a consulta para recuperar os resultados. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se converte todas as operações necessárias para as operações necessárias do SQL que você está familiarizado com. Para obter mais informações, consulte [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 No exemplo a seguir, os nomes de empresas de clientes de Londres são recuperados e exibidos na janela do console.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Inserindo  
 Para executar um `Insert` do SQL, basta adicionar objetos ao modelo de objetos que você criou e chamar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> em <xref:System.Data.Linq.DataContext>.  
  
 No exemplo a seguir, um novo cliente e informações sobre o cliente são adicionados à tabela `Customers` usando <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Atualizando  
 Para `Update` uma entrada de banco de dados, primeiro recupere o item e edite-o diretamente no modelo de objeto. Depois que você modificou o objeto, chame <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no <xref:System.Data.Linq.DataContext> para atualizar o banco de dados.  
  
 No exemplo a seguir, todos os clientes que são de Londres são recuperados. O nome da cidade é alterado de “Londres” para “Londres - metro”. Finalmente, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é chamado para enviar as alterações para o banco de dados.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Excluindo  
 Para `Delete` um item, remova-o da coleção à qual ele pertence e, em seguida, chame <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no <xref:System.Data.Linq.DataContext> para confirmar a alteração.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não reconhece as operações de exclusão em cascata. Se você quiser excluir uma linha em uma tabela que tem restrições em relação a ela, consulte [como: excluir linhas do banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 No exemplo a seguir, o cliente que tem `CustomerID` de `98128` é recuperado do banco de dados. Em seguida, após ter confirmado que a linha do cliente foi recuperada, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> é chamado para remover esse objeto da coleção. Finalmente, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é chamado para encaminhar a exclusão para o banco de dados.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [O modelo de objeto LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Introdução](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
