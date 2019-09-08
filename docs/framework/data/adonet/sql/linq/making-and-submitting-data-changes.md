---
title: Fazendo e enviando alterações de dados
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 18468c9a2018a28e85d87155d98b0853854013fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792969"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="83e66-102">Fazendo e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="83e66-102">Making and Submitting Data Changes</span></span>

<span data-ttu-id="83e66-103">Os tópicos desta seção descrevem como fazer e transmitir alterações para o banco de dados e como tratar conflitos de simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="83e66-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>

> [!NOTE]
> <span data-ttu-id="83e66-104">Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`.</span><span class="sxs-lookup"><span data-stu-id="83e66-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="83e66-105">Para obter mais informações, consulte [Personalizando as operações de inserção, atualização e exclusão](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="83e66-105">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="83e66-106">Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para desenvolver procedimentos armazenados para a mesma finalidade.</span><span class="sxs-lookup"><span data-stu-id="83e66-106">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="83e66-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="83e66-107">In This Section</span></span>

<span data-ttu-id="83e66-108">[Como: Inserir linhas no banco de dados](how-to-insert-rows-into-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="83e66-108">[How to: Insert Rows Into the Database](how-to-insert-rows-into-the-database.md) </span></span>\
<span data-ttu-id="83e66-109">Descreve como inserir linhas no banco de dados adicionando objetos ao modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="83e66-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>

<span data-ttu-id="83e66-110">[Como: Atualizar linhas no banco de dados](how-to-update-rows-in-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="83e66-110">[How to: Update Rows in the Database](how-to-update-rows-in-the-database.md) </span></span>\
<span data-ttu-id="83e66-111">Descreve como atualizar linhas no banco de dados atualizando objetos no modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="83e66-111">Describes how to update rows in the database by updating objects in the object model.</span></span>

<span data-ttu-id="83e66-112">[Como: Excluir linhas do banco de dados](how-to-delete-rows-from-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="83e66-112">[How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md) </span></span>\
<span data-ttu-id="83e66-113">Descreve como excluir linhas no banco de dados excluindo objetos no modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="83e66-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>

<span data-ttu-id="83e66-114">[Como: Enviar alterações para o banco de dados](how-to-submit-changes-to-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="83e66-114">[How to: Submit Changes to the Database](how-to-submit-changes-to-the-database.md) </span></span>\
<span data-ttu-id="83e66-115">Descreve como enviar alterações no modelo de objeto ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="83e66-115">Describes how to send object-model changes to the database.</span></span>

<span data-ttu-id="83e66-116">[Como: Envios de dados de colchetes usando transações](how-to-bracket-data-submissions-by-using-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="83e66-116">[How to: Bracket Data Submissions by Using Transactions](how-to-bracket-data-submissions-by-using-transactions.md) </span></span>\
<span data-ttu-id="83e66-117">Descreve como incluir operações em uma transação.</span><span class="sxs-lookup"><span data-stu-id="83e66-117">Describes how to include operations in a transaction.</span></span>

<span data-ttu-id="83e66-118">[Como: Criar dinamicamente um banco de dados](how-to-dynamically-create-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="83e66-118">[How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md) </span></span>\
<span data-ttu-id="83e66-119">Descreve como gerar bancos de dados dinamicamente e cenários típicos para essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="83e66-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>

<span data-ttu-id="83e66-120">[Como: Gerenciar conflitos de alterações](how-to-manage-change-conflicts.md) </span><span class="sxs-lookup"><span data-stu-id="83e66-120">[How to: Manage Change Conflicts](how-to-manage-change-conflicts.md) </span></span>\
<span data-ttu-id="83e66-121">Descreve técnicas de como resolver problemas de simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="83e66-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
