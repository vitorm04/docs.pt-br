---
title: Como atualizar linhas no banco de dados
description: Saiba como atualizar linhas em um banco de dados modificando LINQ to SQL objetos em uma coleção relacionada à tabela. LINQ to SQL traduz as adições aos comandos SQL UPDATE.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: f25efb91fb5a83fb1c7c109bd018c8210edaec8b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286333"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="4316d-104">Como atualizar linhas no banco de dados</span><span class="sxs-lookup"><span data-stu-id="4316d-104">How to: Update Rows in the Database</span></span>

<span data-ttu-id="4316d-105">Você pode atualizar linhas em um banco de dados modificando valores de membro dos objetos associados à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> coleção e, em seguida, enviando as alterações para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="4316d-105">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="4316d-106">traduz as alterações nos comandos SQL apropriados `UPDATE` .</span><span class="sxs-lookup"><span data-stu-id="4316d-106">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="4316d-107">Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`.</span><span class="sxs-lookup"><span data-stu-id="4316d-107">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="4316d-108">Para obter mais informações, consulte [Personalizando as operações de inserção, atualização e exclusão](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="4316d-108">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="4316d-109">Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para desenvolver procedimentos armazenados para a mesma finalidade.</span><span class="sxs-lookup"><span data-stu-id="4316d-109">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="4316d-110">As etapas a seguir presumem que um <xref:System.Data.Linq.DataContext> válido conecta você ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="4316d-110">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="4316d-111">Para obter mais informações, consulte [como conectar-se a um banco de dados](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="4316d-111">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="4316d-112">Para atualizar uma linha no banco de dados</span><span class="sxs-lookup"><span data-stu-id="4316d-112">To update a row in the database</span></span>

1. <span data-ttu-id="4316d-113">Consulte a linha ser atualizada no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="4316d-113">Query the database for the row to be updated.</span></span>

2. <span data-ttu-id="4316d-114">Faça as alterações desejadas nos valores dos membros no objeto [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] resultante.</span><span class="sxs-lookup"><span data-stu-id="4316d-114">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>

3. <span data-ttu-id="4316d-115">Envie as alterações ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="4316d-115">Submit the changes to the database.</span></span>

## <a name="example"></a><span data-ttu-id="4316d-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4316d-116">Example</span></span>

<span data-ttu-id="4316d-117">O exemplo a seguir consulta a ordem #11000 no banco de dados e modifica os valores de `ShipName` e de `ShipVia` no objeto `Order` resultante.</span><span class="sxs-lookup"><span data-stu-id="4316d-117">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="4316d-118">Finalmente, as alterações nesses valores membro são enviadas ao banco de dados como alterações nas colunas `ShipName` e `ShipVia`.</span><span class="sxs-lookup"><span data-stu-id="4316d-118">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="4316d-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="4316d-119">See also</span></span>

- [<span data-ttu-id="4316d-120">Como gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="4316d-120">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="4316d-121">Como atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="4316d-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="4316d-122">Fazendo e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="4316d-122">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
