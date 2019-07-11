---
title: Fazendo e enviando alterações de dados
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 23dc45c990763e69b41608f6c3ec15a8db17bf23
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743013"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="c9be1-102">Fazendo e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="c9be1-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="c9be1-103">Os tópicos desta seção descrevem como fazer e transmitir alterações para o banco de dados e como tratar conflitos de simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="c9be1-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9be1-104">Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`.</span><span class="sxs-lookup"><span data-stu-id="c9be1-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="c9be1-105">Para obter mais informações, consulte [personalizando inserir, atualizar e excluir operações](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="c9be1-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="c9be1-106">Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para desenvolver procedimentos armazenados para a mesma finalidade.</span><span class="sxs-lookup"><span data-stu-id="c9be1-106">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9be1-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c9be1-107">In This Section</span></span>  
 [<span data-ttu-id="c9be1-108">Como: Inserir linhas no banco de dados</span><span class="sxs-lookup"><span data-stu-id="c9be1-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="c9be1-109">Descreve como inserir linhas no banco de dados adicionando objetos ao modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="c9be1-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="c9be1-110">Como: Atualizar linhas no banco de dados</span><span class="sxs-lookup"><span data-stu-id="c9be1-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="c9be1-111">Descreve como atualizar linhas no banco de dados atualizando objetos no modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="c9be1-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="c9be1-112">Como: Excluir linhas do banco de dados</span><span class="sxs-lookup"><span data-stu-id="c9be1-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="c9be1-113">Descreve como excluir linhas no banco de dados excluindo objetos no modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="c9be1-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="c9be1-114">Como: Enviar alterações para o banco de dados</span><span class="sxs-lookup"><span data-stu-id="c9be1-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="c9be1-115">Descreve como enviar alterações no modelo de objeto ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c9be1-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="c9be1-116">Como: Envios de dados colchete usando transações</span><span class="sxs-lookup"><span data-stu-id="c9be1-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="c9be1-117">Descreve como incluir operações em uma transação.</span><span class="sxs-lookup"><span data-stu-id="c9be1-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="c9be1-118">Como: Criar um banco de dados de forma dinâmica</span><span class="sxs-lookup"><span data-stu-id="c9be1-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="c9be1-119">Descreve como gerar bancos de dados dinamicamente e cenários típicos para essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="c9be1-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="c9be1-120">Como: Gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="c9be1-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="c9be1-121">Descreve técnicas de como resolver problemas de simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="c9be1-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
