---
title: 'Como: excluir linhas do banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: a53a30d1da7dbc7e279a416db5709a256ee9272e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648703"
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="9e374-102">Como: excluir linhas do banco de dados</span><span class="sxs-lookup"><span data-stu-id="9e374-102">How to: Delete Rows From the Database</span></span>
<span data-ttu-id="9e374-103">Você pode excluir linhas em um banco de dados, removendo correspondente [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objetos de sua coleção de tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="9e374-103">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="9e374-104">converte suas alterações para o SQL apropriado `DELETE` comandos.</span><span class="sxs-lookup"><span data-stu-id="9e374-104">translates your changes to the appropriate SQL `DELETE` commands.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="9e374-105">não oferece suporte ou reconhece operações cascade-delete.</span><span class="sxs-lookup"><span data-stu-id="9e374-105">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="9e374-106">Se você deseja excluir uma linha em uma tabela com restrições, deverá concluir uma das seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="9e374-106">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>  
  
- <span data-ttu-id="9e374-107">Defina a regra `ON DELETE CASCADE` na restrição de chave estrangeira no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9e374-107">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>  
  
- <span data-ttu-id="9e374-108">Use seu próprio código para excluir primeiro os objetos filho que impedem que o objeto pai seja excluído.</span><span class="sxs-lookup"><span data-stu-id="9e374-108">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>  
  
 <span data-ttu-id="9e374-109">Caso contrário, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="9e374-109">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="9e374-110">Consulte o segundo exemplo de código posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="9e374-110">See the second code example later in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e374-111">Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`.</span><span class="sxs-lookup"><span data-stu-id="9e374-111">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="9e374-112">Para obter mais informações, consulte [personalizando inserir, atualizar e excluir operações](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9e374-112">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="9e374-113">Os desenvolvedores usando o Visual Studio podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para desenvolver procedimentos armazenados para a mesma finalidade.</span><span class="sxs-lookup"><span data-stu-id="9e374-113">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="9e374-114">As etapas a seguir presumem que um <xref:System.Data.Linq.DataContext> válido conecta você ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="9e374-114">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="9e374-115">Para obter mais informações, confira [Como: Conectar-se ao banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="9e374-115">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="9e374-116">Para excluir uma linha no banco de dados</span><span class="sxs-lookup"><span data-stu-id="9e374-116">To delete a row in the database</span></span>  
  
1. <span data-ttu-id="9e374-117">Consulte o banco de dados para a linha ser excluída.</span><span class="sxs-lookup"><span data-stu-id="9e374-117">Query the database for the row to be deleted.</span></span>  
  
2. <span data-ttu-id="9e374-118">Chame o método <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>.</span><span class="sxs-lookup"><span data-stu-id="9e374-118">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>  
  
3. <span data-ttu-id="9e374-119">Envie a alteração para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9e374-119">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e374-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e374-120">Example</span></span>  
 <span data-ttu-id="9e374-121">O primeiro exemplo de código consulta o banco de dados para obter os detalhes do pedido que pertencem ao Pedido #11000, marca esses detalhes do pedido para exclusão e envia estas alterações para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9e374-121">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="9e374-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e374-122">Example</span></span>  
 <span data-ttu-id="9e374-123">No segundo exemplo, o objetivo é remover uma pedido (#10250).</span><span class="sxs-lookup"><span data-stu-id="9e374-123">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="9e374-124">O código primeiro examina a tabela `OrderDetails` para ver se o pedido a ser removido tem filhos nela.</span><span class="sxs-lookup"><span data-stu-id="9e374-124">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="9e374-125">Se o pedido tiver filhos, primeiro os filhos e, em seguida, o pedido serão marcados para remoção.</span><span class="sxs-lookup"><span data-stu-id="9e374-125">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="9e374-126">O <xref:System.Data.Linq.DataContext> coloca as exclusões reais na ordem correta de modo que os comandos de exclusão enviados para o banco de dados aceitem as restrições do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9e374-126">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9e374-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e374-127">See also</span></span>

- [<span data-ttu-id="9e374-128">Como: Gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="9e374-128">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="9e374-129">Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="9e374-129">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="9e374-130">Realizando e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="9e374-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
