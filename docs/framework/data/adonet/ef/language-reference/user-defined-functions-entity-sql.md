---
title: Funções definidas pelo usuário (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 9e5ad1f6edb0e719733edd2518c5d62a7fc6bdf7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180966"
---
# <a name="user-defined-functions-entity-sql"></a><span data-ttu-id="ce00a-102">Funções definidas pelo usuário (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ce00a-102">User-Defined Functions (Entity SQL)</span></span>

<span data-ttu-id="ce00a-103">Suporte de Entity SQL que chamam funções definidas pelo usuário em uma consulta.</span><span class="sxs-lookup"><span data-stu-id="ce00a-103">Entity SQL supports calling user-defined functions in a query.</span></span> <span data-ttu-id="ce00a-104">Você pode definir essas funções embutidas com a consulta (consulte [como: chamar uma função definida pelo usuário](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) ou como parte do modelo conceitual (consulte [como: definir funções personalizadas no modelo conceitual](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="ce00a-104">You can define these functions inline with the query (see [How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) or as part of the conceptual model (see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))).</span></span> <span data-ttu-id="ce00a-105">As funções de modelo conceitual são definidas como um comando Entity SQL no elemento de [definição](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) de um elemento [Function](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="ce00a-105">Conceptual model functions are defined as an Entity SQL command in the [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) element of a [Function](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) element in the conceptual model.</span></span>  
  
 <span data-ttu-id="ce00a-106">Entity SQL permite que você defina funções no comando de consulta próprias.</span><span class="sxs-lookup"><span data-stu-id="ce00a-106">Entity SQL enables you to define functions in the query command itself.</span></span> <span data-ttu-id="ce00a-107">O operador [Function](function-entity-sql.md) define funções embutidas.</span><span class="sxs-lookup"><span data-stu-id="ce00a-107">The [FUNCTION](function-entity-sql.md) operator defines inline functions.</span></span> <span data-ttu-id="ce00a-108">Você pode definir várias funções em um único comando, e essas funções podem ter o mesmo nome de função, como as assinaturas de função são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="ce00a-108">You can define multiple functions in a single command, and these functions can have the same function name, as long as the function signatures are unique.</span></span> <span data-ttu-id="ce00a-109">Para obter mais informações, consulte [resolução de sobrecarga de função](function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ce00a-109">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce00a-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="ce00a-110">See also</span></span>

- [<span data-ttu-id="ce00a-111">Funções</span><span class="sxs-lookup"><span data-stu-id="ce00a-111">Functions</span></span>](functions-entity-sql.md)
