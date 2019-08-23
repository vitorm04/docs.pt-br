---
title: O que você pode fazer com LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: 21ed620ab5b7a78fc4f396cc474e7c62b70f1ddd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946618"
---
# <a name="what-you-can-do-with-linq-to-sql"></a><span data-ttu-id="30715-102">O que você pode fazer com LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="30715-102">What You Can Do With LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="30715-103">o oferece suporte a todos os principais recursos que você espera como um desenvolvedor do SQL.</span><span class="sxs-lookup"><span data-stu-id="30715-103">supports all the key capabilities you would expect as a SQL developer.</span></span> <span data-ttu-id="30715-104">Você pode consultar informações, e inserir, atualizar e excluir informações de tabelas.</span><span class="sxs-lookup"><span data-stu-id="30715-104">You can query for information, and insert, update, and delete information from tables.</span></span>  
  
## <a name="selecting"></a><span data-ttu-id="30715-105">Selecionando</span><span class="sxs-lookup"><span data-stu-id="30715-105">Selecting</span></span>  
 <span data-ttu-id="30715-106">Selecionar (*projeção*) é obtido apenas escrevendo uma [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] consulta em sua própria linguagem de programação e, em seguida, executando essa consulta para recuperar os resultados.</span><span class="sxs-lookup"><span data-stu-id="30715-106">Selecting (*projection*) is achieved by just writing a [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] query in your own programming language, and then executing that query to retrieve the results.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="30715-107">Ele mesmo converte todas as operações necessárias nas operações de SQL necessárias com as quais você está familiarizado.</span><span class="sxs-lookup"><span data-stu-id="30715-107">itself translates all the necessary operations into the necessary SQL operations that you are familiar with.</span></span> <span data-ttu-id="30715-108">Para obter mais informações, consulte [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="30715-108">For more information, see [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="30715-109">No exemplo a seguir, os nomes de empresas de clientes de Londres são recuperados e exibidos na janela do console.</span><span class="sxs-lookup"><span data-stu-id="30715-109">In the following example, the company names of customers from London are retrieved and displayed in the console window.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a><span data-ttu-id="30715-110">Inserindo</span><span class="sxs-lookup"><span data-stu-id="30715-110">Inserting</span></span>  
 <span data-ttu-id="30715-111">Para executar um `Insert` do SQL, basta adicionar objetos ao modelo de objetos que você criou e chamar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> em <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="30715-111">To execute a SQL `Insert`, just add objects to the object model you have created, and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="30715-112">No exemplo a seguir, um novo cliente e informações sobre o cliente são adicionados à tabela `Customers` usando <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span><span class="sxs-lookup"><span data-stu-id="30715-112">In the following example, a new customer and information about the customer is added to the `Customers` table by using <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a><span data-ttu-id="30715-113">Atualizando</span><span class="sxs-lookup"><span data-stu-id="30715-113">Updating</span></span>  
 <span data-ttu-id="30715-114">Para `Update` uma entrada de banco de dados, primeiro recupere o item e edite-o diretamente no modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="30715-114">To `Update` a database entry, first retrieve the item and edit it directly in the object model.</span></span> <span data-ttu-id="30715-115">Depois que você modificou o objeto, chame <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no <xref:System.Data.Linq.DataContext> para atualizar o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="30715-115">After you have modified the object, call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to update the database.</span></span>  
  
 <span data-ttu-id="30715-116">No exemplo a seguir, todos os clientes que são de Londres são recuperados.</span><span class="sxs-lookup"><span data-stu-id="30715-116">In the following example, all customers who are from London are retrieved.</span></span> <span data-ttu-id="30715-117">O nome da cidade é alterado de “Londres” para “Londres - metro”.</span><span class="sxs-lookup"><span data-stu-id="30715-117">Then the name of the city is changed from "London" to "London - Metro".</span></span> <span data-ttu-id="30715-118">Finalmente, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é chamado para enviar as alterações para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="30715-118">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to send the changes to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a><span data-ttu-id="30715-119">Excluindo</span><span class="sxs-lookup"><span data-stu-id="30715-119">Deleting</span></span>  
 <span data-ttu-id="30715-120">Para `Delete` um item, remova-o da coleção à qual ele pertence e, em seguida, chame <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no <xref:System.Data.Linq.DataContext> para confirmar a alteração.</span><span class="sxs-lookup"><span data-stu-id="30715-120">To `Delete` an item, remove the item from the collection to which it belongs, and then call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to commit the change.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="30715-121">Não reconhece operações de exclusão em cascata.</span><span class="sxs-lookup"><span data-stu-id="30715-121">does not recognize cascade-delete operations.</span></span> <span data-ttu-id="30715-122">Se você quiser excluir uma linha em uma tabela com restrições, consulte [como: Excluir linhas do banco de](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)dados.</span><span class="sxs-lookup"><span data-stu-id="30715-122">If you want to delete a row in a table that has constraints against it, see [How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="30715-123">No exemplo a seguir, o cliente que tem `CustomerID` de `98128` é recuperado do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="30715-123">In the following example, the customer who has `CustomerID` of `98128` is retrieved from the database.</span></span> <span data-ttu-id="30715-124">Em seguida, após ter confirmado que a linha do cliente foi recuperada, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> é chamado para remover esse objeto da coleção.</span><span class="sxs-lookup"><span data-stu-id="30715-124">Then, after confirming that the customer row was retrieved, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> is called to remove that object from the collection.</span></span> <span data-ttu-id="30715-125">Finalmente, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é chamado para encaminhar a exclusão para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="30715-125">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to forward the deletion to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="30715-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30715-126">See also</span></span>

- [<span data-ttu-id="30715-127">Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="30715-127">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [<span data-ttu-id="30715-128">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="30715-128">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="30715-129">Introdução</span><span class="sxs-lookup"><span data-stu-id="30715-129">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
