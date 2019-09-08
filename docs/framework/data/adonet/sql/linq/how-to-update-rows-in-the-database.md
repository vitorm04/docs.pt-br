---
title: 'Como: atualizar linhas no banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: c2055e1dd988352b50a439531ab5533f34a4965e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793125"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="8a9e1-102">Como: atualizar linhas no banco de dados</span><span class="sxs-lookup"><span data-stu-id="8a9e1-102">How to: Update Rows in the Database</span></span>

<span data-ttu-id="8a9e1-103">Você pode atualizar linhas em um banco de dados modificando valores de membro dos objetos associados [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> à coleção e, em seguida, enviando as alterações para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="8a9e1-103">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8a9e1-104">traduz as alterações nos comandos SQL `UPDATE` apropriados.</span><span class="sxs-lookup"><span data-stu-id="8a9e1-104">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="8a9e1-105">Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`.</span><span class="sxs-lookup"><span data-stu-id="8a9e1-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="8a9e1-106">Para obter mais informações, consulte [Personalizando as operações de inserção, atualização e exclusão](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8a9e1-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="8a9e1-107">Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para desenvolver procedimentos armazenados para a mesma finalidade.</span><span class="sxs-lookup"><span data-stu-id="8a9e1-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="8a9e1-108">As etapas a seguir presumem que um <xref:System.Data.Linq.DataContext> válido conecta você ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="8a9e1-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="8a9e1-109">Para obter mais informações, confira [Como: Conecte-se a](how-to-connect-to-a-database.md)um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="8a9e1-109">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="8a9e1-110">Para atualizar uma linha no banco de dados</span><span class="sxs-lookup"><span data-stu-id="8a9e1-110">To update a row in the database</span></span>

1. <span data-ttu-id="8a9e1-111">Consulte a linha ser atualizada no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="8a9e1-111">Query the database for the row to be updated.</span></span>

2. <span data-ttu-id="8a9e1-112">Faça as alterações desejadas nos valores dos membros no objeto [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] resultante.</span><span class="sxs-lookup"><span data-stu-id="8a9e1-112">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>

3. <span data-ttu-id="8a9e1-113">Envie as alterações ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="8a9e1-113">Submit the changes to the database.</span></span>

## <a name="example"></a><span data-ttu-id="8a9e1-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8a9e1-114">Example</span></span>

<span data-ttu-id="8a9e1-115">O exemplo a seguir consulta a ordem #11000 no banco de dados e modifica os valores de `ShipName` e de `ShipVia` no objeto `Order` resultante.</span><span class="sxs-lookup"><span data-stu-id="8a9e1-115">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="8a9e1-116">Finalmente, as alterações nesses valores membro são enviadas ao banco de dados como alterações nas colunas `ShipName` e `ShipVia`.</span><span class="sxs-lookup"><span data-stu-id="8a9e1-116">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="8a9e1-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a9e1-117">See also</span></span>

- [<span data-ttu-id="8a9e1-118">Como: Gerenciar conflitos de alterações</span><span class="sxs-lookup"><span data-stu-id="8a9e1-118">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="8a9e1-119">Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="8a9e1-119">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="8a9e1-120">Realizando e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="8a9e1-120">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
