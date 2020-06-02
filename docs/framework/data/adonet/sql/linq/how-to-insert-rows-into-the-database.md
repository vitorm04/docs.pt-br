---
title: Como inserir linhas no banco de dados
description: Aprenda a inserir linhas em um banco de dados adicionando LINQ to SQL objetos a uma coleção relacionada à tabela. LINQ to SQL traduz as adições aos comandos SQL INSERT.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 39eee6edf59d2adb7de41efd88899050fbe69fd8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286346"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="aad8c-104">Como inserir linhas no banco de dados</span><span class="sxs-lookup"><span data-stu-id="aad8c-104">How to: Insert Rows Into the Database</span></span>

<span data-ttu-id="aad8c-105">Você insere linhas em um banco de dados adicionando objetos à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> coleção associada e, em seguida, enviando as alterações ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="aad8c-105">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="aad8c-106">traduz as alterações nos comandos SQL apropriados `INSERT` .</span><span class="sxs-lookup"><span data-stu-id="aad8c-106">translates your changes into the appropriate SQL `INSERT` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="aad8c-107">Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`.</span><span class="sxs-lookup"><span data-stu-id="aad8c-107">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="aad8c-108">Para obter mais informações, consulte [Personalizando as operações de inserção, atualização e exclusão](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="aad8c-108">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="aad8c-109">Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para desenvolver procedimentos armazenados para a mesma finalidade.</span><span class="sxs-lookup"><span data-stu-id="aad8c-109">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="aad8c-110">As etapas a seguir presumem que um <xref:System.Data.Linq.DataContext> válido conecta você ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="aad8c-110">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="aad8c-111">Para obter mais informações, consulte [como conectar-se a um banco de dados](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="aad8c-111">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="aad8c-112">Para inserir uma linha no banco de dados</span><span class="sxs-lookup"><span data-stu-id="aad8c-112">To insert a row into the database</span></span>

1. <span data-ttu-id="aad8c-113">Crie um novo objeto que inclui os dados da coluna a serem enviados.</span><span class="sxs-lookup"><span data-stu-id="aad8c-113">Create a new object that includes the column data to be submitted.</span></span>

2. <span data-ttu-id="aad8c-114">Adicione o novo objeto à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` coleção associada à tabela de destino no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="aad8c-114">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>

3. <span data-ttu-id="aad8c-115">Envie a alteração para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="aad8c-115">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="aad8c-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aad8c-116">Example</span></span>

<span data-ttu-id="aad8c-117">O exemplo de código a seguir cria um novo objeto do tipo `Order` e preenche-o com valores apropriados.</span><span class="sxs-lookup"><span data-stu-id="aad8c-117">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="aad8c-118">Ele em seguida adiciona o novo objeto à coleção `Order`.</span><span class="sxs-lookup"><span data-stu-id="aad8c-118">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="aad8c-119">Finalmente, ele envia a alteração para o banco de dados como uma nova linha na tabela `Orders`.</span><span class="sxs-lookup"><span data-stu-id="aad8c-119">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="aad8c-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="aad8c-120">See also</span></span>

- [<span data-ttu-id="aad8c-121">Como gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="aad8c-121">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="aad8c-122">Métodos DataContext (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="aad8c-122">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="aad8c-123">Como atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="aad8c-123">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="aad8c-124">Fazendo e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="aad8c-124">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
