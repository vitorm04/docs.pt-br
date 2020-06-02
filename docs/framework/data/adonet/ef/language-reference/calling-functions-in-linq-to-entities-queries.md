---
title: Chamando funções em consultas no LINQ to Entities
description: Use estes artigos para ver como as classes EntityFunctions e SqlFunctions fornecem acesso às funções canônicas e de banco de dados como parte do Entity Framework.
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: faa6406713592f10e5e7371cd73f29bec4b03b7b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286851"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="93bbb-103">Chamando funções em consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="93bbb-103">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="93bbb-104">Os tópicos nesta seção descrevem como chamar funções em consultas LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="93bbb-104">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="93bbb-105">As classes <xref:System.Data.Objects.EntityFunctions> e <xref:System.Data.Objects.SqlClient.SqlFunctions> fornecem acesso às funções canônicas e de banco de dados como parte do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="93bbb-105">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="93bbb-106">Para obter mais informações, consulte [como: chamar funções canônicas](how-to-call-canonical-functions.md) e [como chamar funções de banco de dados](how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="93bbb-106">For more information, see [How to: Call Canonical Functions](how-to-call-canonical-functions.md) and [How to: Call Database Functions](how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="93bbb-107">O processo para chamar uma função personalizada exige três etapas básicas:</span><span class="sxs-lookup"><span data-stu-id="93bbb-107">The process for calling a custom function requires three basic steps:</span></span>  
  
1. <span data-ttu-id="93bbb-108">Defina uma função no modelo conceitual ou declare uma função no modelo de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="93bbb-108">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2. <span data-ttu-id="93bbb-109">Adicione um método ao seu aplicativo e mapeie-o para a função no modelo com um <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="93bbb-109">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3. <span data-ttu-id="93bbb-110">Chame a função em uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="93bbb-110">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="93bbb-111">Para obter mais informações, consulte os tópicos nesta seção.</span><span class="sxs-lookup"><span data-stu-id="93bbb-111">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="93bbb-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="93bbb-112">In This Section</span></span>  
 [<span data-ttu-id="93bbb-113">Como: Funções canônicas de chamada</span><span class="sxs-lookup"><span data-stu-id="93bbb-113">How to: Call Canonical Functions</span></span>](how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="93bbb-114">Como: Funções de base de dados de chamada</span><span class="sxs-lookup"><span data-stu-id="93bbb-114">How to: Call Database Functions</span></span>](how-to-call-database-functions.md)  
  
 [<span data-ttu-id="93bbb-115">Como: Funções de base de dados personalizados de chamada</span><span class="sxs-lookup"><span data-stu-id="93bbb-115">How to: Call Custom Database Functions</span></span>](how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="93bbb-116">Como: o chamar funções definidas em consultas</span><span class="sxs-lookup"><span data-stu-id="93bbb-116">How to: Call Model-Defined Functions in Queries</span></span>](how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="93bbb-117">Como: o chamar funções definidas como métodos de objeto</span><span class="sxs-lookup"><span data-stu-id="93bbb-117">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="93bbb-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="93bbb-118">See also</span></span>

- [<span data-ttu-id="93bbb-119">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="93bbb-119">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="93bbb-120">Funções canônicas</span><span class="sxs-lookup"><span data-stu-id="93bbb-120">Canonical Functions</span></span>](canonical-functions.md)
- <span data-ttu-id="93bbb-121">[Visão geral do arquivo. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="93bbb-121">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="93bbb-122">[Como definir funções personalizadas no modelo conceitual](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="93bbb-122">[How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
