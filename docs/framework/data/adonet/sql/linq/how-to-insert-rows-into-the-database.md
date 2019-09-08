---
title: 'Como: inserir linhas no banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 8186b90a666a7b75ce626cccb7cc28af38de7c5b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781869"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="9d454-102">Como: inserir linhas no banco de dados</span><span class="sxs-lookup"><span data-stu-id="9d454-102">How to: Insert Rows Into the Database</span></span>

<span data-ttu-id="9d454-103">Você insere linhas em um banco de dados adicionando objetos à coleção [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] associada <xref:System.Data.Linq.Table%601> e, em seguida, enviando as alterações ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9d454-103">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9d454-104">traduz as alterações nos comandos SQL `INSERT` apropriados.</span><span class="sxs-lookup"><span data-stu-id="9d454-104">translates your changes into the appropriate SQL `INSERT` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="9d454-105">Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`.</span><span class="sxs-lookup"><span data-stu-id="9d454-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="9d454-106">Para obter mais informações, consulte [Personalizando as operações de inserção, atualização e exclusão](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9d454-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="9d454-107">Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para desenvolver procedimentos armazenados para a mesma finalidade.</span><span class="sxs-lookup"><span data-stu-id="9d454-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="9d454-108">As etapas a seguir presumem que um <xref:System.Data.Linq.DataContext> válido conecta você ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="9d454-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="9d454-109">Para obter mais informações, confira [Como: Conecte-se a](how-to-connect-to-a-database.md)um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9d454-109">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="9d454-110">Para inserir uma linha no banco de dados</span><span class="sxs-lookup"><span data-stu-id="9d454-110">To insert a row into the database</span></span>

1. <span data-ttu-id="9d454-111">Crie um novo objeto que inclui os dados da coluna a serem enviados.</span><span class="sxs-lookup"><span data-stu-id="9d454-111">Create a new object that includes the column data to be submitted.</span></span>

2. <span data-ttu-id="9d454-112">Adicione o novo objeto à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` coleção associada à tabela de destino no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9d454-112">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>

3. <span data-ttu-id="9d454-113">Envie a alteração para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9d454-113">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="9d454-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d454-114">Example</span></span>

<span data-ttu-id="9d454-115">O exemplo de código a seguir cria um novo objeto do tipo `Order` e preenche-o com valores apropriados.</span><span class="sxs-lookup"><span data-stu-id="9d454-115">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="9d454-116">Ele em seguida adiciona o novo objeto à coleção `Order`.</span><span class="sxs-lookup"><span data-stu-id="9d454-116">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="9d454-117">Finalmente, ele envia a alteração para o banco de dados como uma nova linha na tabela `Orders`.</span><span class="sxs-lookup"><span data-stu-id="9d454-117">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="9d454-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d454-118">See also</span></span>

- [<span data-ttu-id="9d454-119">Como: Gerenciar conflitos de alterações</span><span class="sxs-lookup"><span data-stu-id="9d454-119">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="9d454-120">Métodos DataContext (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="9d454-120">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="9d454-121">Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="9d454-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="9d454-122">Realizando e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="9d454-122">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
