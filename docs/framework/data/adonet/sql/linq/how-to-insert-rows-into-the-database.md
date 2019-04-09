---
title: 'Como: inserir linhas no banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: cc9f276cc278d4a9c376d72f1ab38d89ea6dd5b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169592"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="f4cf1-102">Como: inserir linhas no banco de dados</span><span class="sxs-lookup"><span data-stu-id="f4cf1-102">How to: Insert Rows Into the Database</span></span>
<span data-ttu-id="f4cf1-103">Inserir linhas em um banco de dados adicionando objetos associados [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> coleção e, em seguida, enviar as alterações no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f4cf1-103">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f4cf1-104">converte suas alterações em apropriados do SQL `INSERT` comandos.</span><span class="sxs-lookup"><span data-stu-id="f4cf1-104">translates your changes into the appropriate SQL `INSERT` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4cf1-105">Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`.</span><span class="sxs-lookup"><span data-stu-id="f4cf1-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="f4cf1-106">Para obter mais informações, consulte [personalizando inserir, atualizar e excluir operações](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="f4cf1-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="f4cf1-107">Os desenvolvedores usando o Visual Studio podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para desenvolver procedimentos armazenados para a mesma finalidade.</span><span class="sxs-lookup"><span data-stu-id="f4cf1-107">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="f4cf1-108">As etapas a seguir presumem que um <xref:System.Data.Linq.DataContext> válido conecta você ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="f4cf1-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="f4cf1-109">Para obter mais informações, confira [Como: Conectar-se ao banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="f4cf1-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="f4cf1-110">Para inserir uma linha no banco de dados</span><span class="sxs-lookup"><span data-stu-id="f4cf1-110">To insert a row into the database</span></span>  
  
1.  <span data-ttu-id="f4cf1-111">Crie um novo objeto que inclui os dados da coluna a serem enviados.</span><span class="sxs-lookup"><span data-stu-id="f4cf1-111">Create a new object that includes the column data to be submitted.</span></span>  
  
2.  <span data-ttu-id="f4cf1-112">Adicionar o novo objeto para o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` coleção associada à tabela de destino no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f4cf1-112">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>  
  
3.  <span data-ttu-id="f4cf1-113">Envie a alteração para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f4cf1-113">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4cf1-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4cf1-114">Example</span></span>  
 <span data-ttu-id="f4cf1-115">O exemplo de código a seguir cria um novo objeto do tipo `Order` e preenche-o com valores apropriados.</span><span class="sxs-lookup"><span data-stu-id="f4cf1-115">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="f4cf1-116">Ele em seguida adiciona o novo objeto à coleção `Order`.</span><span class="sxs-lookup"><span data-stu-id="f4cf1-116">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="f4cf1-117">Finalmente, ele envia a alteração para o banco de dados como uma nova linha na tabela `Orders`.</span><span class="sxs-lookup"><span data-stu-id="f4cf1-117">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f4cf1-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4cf1-118">See also</span></span>

- [<span data-ttu-id="f4cf1-119">Como: gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="f4cf1-119">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="f4cf1-120">Métodos de DataContext (Designer de Objeto Relacional)</span><span class="sxs-lookup"><span data-stu-id="f4cf1-120">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="f4cf1-121">Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="f4cf1-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="f4cf1-122">Fazendo e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="f4cf1-122">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
