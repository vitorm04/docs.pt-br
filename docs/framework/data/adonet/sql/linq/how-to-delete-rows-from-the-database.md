---
title: Como excluir linhas do banco de dados
description: Saiba como excluir linhas em um banco de dados removendo LINQ to SQL objetos de uma coleção relacionada à tabela. LINQ to SQL traduz as exclusões para comandos SQL DELETE.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: d08621e834961e1db9312cac36bd2e69133142b5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286385"
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="79a90-104">Como excluir linhas do banco de dados</span><span class="sxs-lookup"><span data-stu-id="79a90-104">How to: Delete Rows From the Database</span></span>

<span data-ttu-id="79a90-105">Você pode excluir linhas em um banco de dados removendo os [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objetos correspondentes de sua coleção relacionada à tabela.</span><span class="sxs-lookup"><span data-stu-id="79a90-105">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="79a90-106">traduz as alterações nos comandos SQL apropriados `DELETE` .</span><span class="sxs-lookup"><span data-stu-id="79a90-106">translates your changes to the appropriate SQL `DELETE` commands.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="79a90-107">Não dá suporte ou reconhece operações de exclusão em cascata.</span><span class="sxs-lookup"><span data-stu-id="79a90-107">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="79a90-108">Se você deseja excluir uma linha em uma tabela com restrições, deverá concluir uma das seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="79a90-108">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>

- <span data-ttu-id="79a90-109">Defina a regra `ON DELETE CASCADE` na restrição de chave estrangeira no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="79a90-109">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>

- <span data-ttu-id="79a90-110">Use seu próprio código para excluir primeiro os objetos filho que impedem que o objeto pai seja excluído.</span><span class="sxs-lookup"><span data-stu-id="79a90-110">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>

 <span data-ttu-id="79a90-111">Caso contrário, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="79a90-111">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="79a90-112">Consulte o segundo exemplo de código posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="79a90-112">See the second code example later in this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="79a90-113">Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`.</span><span class="sxs-lookup"><span data-stu-id="79a90-113">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="79a90-114">Para obter mais informações, consulte [Personalizando as operações de inserção, atualização e exclusão](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="79a90-114">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="79a90-115">Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para desenvolver procedimentos armazenados para a mesma finalidade.</span><span class="sxs-lookup"><span data-stu-id="79a90-115">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="79a90-116">As etapas a seguir presumem que um <xref:System.Data.Linq.DataContext> válido conecta você ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="79a90-116">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="79a90-117">Para obter mais informações, consulte [como conectar-se a um banco de dados](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="79a90-117">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="79a90-118">Para excluir uma linha no banco de dados</span><span class="sxs-lookup"><span data-stu-id="79a90-118">To delete a row in the database</span></span>

1. <span data-ttu-id="79a90-119">Consulte o banco de dados para a linha ser excluída.</span><span class="sxs-lookup"><span data-stu-id="79a90-119">Query the database for the row to be deleted.</span></span>

2. <span data-ttu-id="79a90-120">Chame o método <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> .</span><span class="sxs-lookup"><span data-stu-id="79a90-120">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>

3. <span data-ttu-id="79a90-121">Envie a alteração para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="79a90-121">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="79a90-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="79a90-122">Example</span></span>

<span data-ttu-id="79a90-123">O primeiro exemplo de código consulta o banco de dados para obter os detalhes do pedido que pertencem ao Pedido #11000, marca esses detalhes do pedido para exclusão e envia estas alterações para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="79a90-123">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>

[!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
[!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="79a90-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="79a90-124">Example</span></span>

<span data-ttu-id="79a90-125">No segundo exemplo, o objetivo é remover uma pedido (#10250).</span><span class="sxs-lookup"><span data-stu-id="79a90-125">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="79a90-126">O código primeiro examina a tabela `OrderDetails` para ver se o pedido a ser removido tem filhos nela.</span><span class="sxs-lookup"><span data-stu-id="79a90-126">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="79a90-127">Se o pedido tiver filhos, primeiro os filhos e, em seguida, o pedido serão marcados para remoção.</span><span class="sxs-lookup"><span data-stu-id="79a90-127">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="79a90-128">O <xref:System.Data.Linq.DataContext> coloca as exclusões reais na ordem correta de modo que os comandos de exclusão enviados para o banco de dados aceitem as restrições do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="79a90-128">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>

[!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
[!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="79a90-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="79a90-129">See also</span></span>

- [<span data-ttu-id="79a90-130">Como gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="79a90-130">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="79a90-131">Como atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="79a90-131">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="79a90-132">Fazendo e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="79a90-132">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
