---
title: "Operações de inserção, atualização e exclusão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: bc279fa541ed14244ea093dcd3ea52c37a4698f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="insert-update-and-delete-operations"></a><span data-ttu-id="8d135-102">Operações de inserção, atualização e exclusão</span><span class="sxs-lookup"><span data-stu-id="8d135-102">Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="8d135-103">Você executa operações `Insert`, `Update` e `Delete` no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] adicionando, modificando e removendo objetos no seu modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="8d135-103">You perform `Insert`, `Update`, and `Delete` operations in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] by adding, changing, and removing objects in your object model.</span></span> <span data-ttu-id="8d135-104">Por padrão, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte suas ações para SQL e envia as alterações para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="8d135-104">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your actions to SQL and submits the changes to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8d135-105">oferece flexibilidade máxima ao manipular e persistência das alterações feitas aos objetos.</span><span class="sxs-lookup"><span data-stu-id="8d135-105"> offers maximum flexibility in manipulating and persisting changes that you made to your objects.</span></span> <span data-ttu-id="8d135-106">Assim que os objetos de entidade estão disponíveis (ou recuperando-os por meio de uma consulta ou com a construção de um novo), você pode alterá-los como típico de objetos em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8d135-106">As soon as entity objects are available (either by retrieving them through a query or by constructing them anew), you can change them as typical objects in your application.</span></span> <span data-ttu-id="8d135-107">Ou seja, você pode alterar seus valores, você pode adicioná-las às coleções e você poderá removê-los de suas coleções.</span><span class="sxs-lookup"><span data-stu-id="8d135-107">That is, you can change their values, you can add them to your collections, and you can remove them from your collections.</span></span> <span data-ttu-id="8d135-108">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] controla as alterações e está pronto para transmiti-las de volta para o banco de dados quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d135-108">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tracks your changes and is ready to transmit them back to the database when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8d135-109">não dá suporte ou reconhece as operações de exclusão em cascata.</span><span class="sxs-lookup"><span data-stu-id="8d135-109"> does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="8d135-110">Se você quiser excluir uma linha em uma tabela que tem restrições em relação a ela, você deve definir o `ON DELETE CASCADE` regra na restrição de chave estrangeira no banco de dados ou usar seu próprio código primeiro excluir os objetos filho que impedem que o objeto pai que está sendo excluído.</span><span class="sxs-lookup"><span data-stu-id="8d135-110">If you want to delete a row in a table that has constraints against it, you must either set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database, or use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span> <span data-ttu-id="8d135-111">Caso contrário, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="8d135-111">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="8d135-112">Para obter mais informações, consulte [como: excluir linhas do banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="8d135-112">For more information, see [How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="8d135-113">Os seguintes trechos usam as classes `Customer` e `Order` do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="8d135-113">The following excerpts use the `Customer` and `Order` classes from the Northwind sample database.</span></span> <span data-ttu-id="8d135-114">As definições de classe não são mostradas para abreviar.</span><span class="sxs-lookup"><span data-stu-id="8d135-114">Class definitions are not shown for brevity.</span></span>  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 <span data-ttu-id="8d135-115">Quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automaticamente gera e executa comandos SQL de que ele deve passar suas alterações de volta para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="8d135-115">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatically generates and executes the SQL commands that it must have to transmit your changes back to the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d135-116">Você pode substituir esse comportamento usando sua própria lógica personalizada, geralmente usando um procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="8d135-116">You can override this behavior by using your own custom logic, typically by way of a stored procedure.</span></span> <span data-ttu-id="8d135-117">Para obter mais informações, consulte [responsabilidades do desenvolvedor em Substituir padrão comportamento](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="8d135-117">For more information, see [Responsibilities of the Developer In Overriding Default Behavior](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).</span></span>  
>   
>  <span data-ttu-id="8d135-118">Os desenvolvedores que usam o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para desenvolver procedimentos armazenados para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="8d135-118">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for this purpose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d135-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d135-119">See Also</span></span>  
 <span data-ttu-id="8d135-120">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="8d135-120">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)</span></span>  
 [<span data-ttu-id="8d135-121">Personalizando as operações de inserção, atualização e exclusão</span><span class="sxs-lookup"><span data-stu-id="8d135-121">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
