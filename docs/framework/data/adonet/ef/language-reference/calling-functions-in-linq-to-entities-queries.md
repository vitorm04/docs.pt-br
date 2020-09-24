---
title: Chamando funções em consultas no LINQ to Entities
description: Use estes artigos para ver como as classes EntityFunctions e SqlFunctions fornecem acesso às funções canônicas e de banco de dados como parte do Entity Framework.
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 8c771c93e0c3ed82f3ad550613dd855fd06b6f48
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177482"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="ef42d-103">Chamando funções em consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ef42d-103">Calling Functions in LINQ to Entities Queries</span></span>

<span data-ttu-id="ef42d-104">Os tópicos nesta seção descrevem como chamar funções em consultas LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="ef42d-104">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="ef42d-105">As classes <xref:System.Data.Objects.EntityFunctions> e <xref:System.Data.Objects.SqlClient.SqlFunctions> fornecem acesso às funções canônicas e de banco de dados como parte do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ef42d-105">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="ef42d-106">Para obter mais informações, consulte [como: chamar funções canônicas](how-to-call-canonical-functions.md) e [como chamar funções de banco de dados](how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="ef42d-106">For more information, see [How to: Call Canonical Functions](how-to-call-canonical-functions.md) and [How to: Call Database Functions](how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="ef42d-107">O processo para chamar uma função personalizada exige três etapas básicas:</span><span class="sxs-lookup"><span data-stu-id="ef42d-107">The process for calling a custom function requires three basic steps:</span></span>  
  
1. <span data-ttu-id="ef42d-108">Defina uma função no modelo conceitual ou declare uma função no modelo de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="ef42d-108">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2. <span data-ttu-id="ef42d-109">Adicione um método ao seu aplicativo e mapeie-o para a função no modelo com um <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ef42d-109">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3. <span data-ttu-id="ef42d-110">Chame a função em uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="ef42d-110">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="ef42d-111">Para obter mais informações, consulte os tópicos nesta seção.</span><span class="sxs-lookup"><span data-stu-id="ef42d-111">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef42d-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ef42d-112">In This Section</span></span>  

 [<span data-ttu-id="ef42d-113">Como: Funções canônicas de chamada</span><span class="sxs-lookup"><span data-stu-id="ef42d-113">How to: Call Canonical Functions</span></span>](how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="ef42d-114">Como: Funções de base de dados de chamada</span><span class="sxs-lookup"><span data-stu-id="ef42d-114">How to: Call Database Functions</span></span>](how-to-call-database-functions.md)  
  
 [<span data-ttu-id="ef42d-115">Como: Funções de base de dados personalizados de chamada</span><span class="sxs-lookup"><span data-stu-id="ef42d-115">How to: Call Custom Database Functions</span></span>](how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="ef42d-116">Como: o chamar funções definidas em consultas</span><span class="sxs-lookup"><span data-stu-id="ef42d-116">How to: Call Model-Defined Functions in Queries</span></span>](how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="ef42d-117">Como: o chamar funções definidas como métodos de objeto</span><span class="sxs-lookup"><span data-stu-id="ef42d-117">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="ef42d-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="ef42d-118">See also</span></span>

- [<span data-ttu-id="ef42d-119">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ef42d-119">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="ef42d-120">Funções canônicas</span><span class="sxs-lookup"><span data-stu-id="ef42d-120">Canonical Functions</span></span>](canonical-functions.md)
- <span data-ttu-id="ef42d-121">[Visão geral do arquivo. edmx](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ef42d-121">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="ef42d-122">[Como definir funções personalizadas no modelo conceitual](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ef42d-122">[How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
