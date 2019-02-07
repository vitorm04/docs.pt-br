---
title: Chamando funções em consultas no LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 8cb861c72f33a7dff3d6bef94719ae590a13706d
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828144"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="0e57c-102">Chamando funções em consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0e57c-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="0e57c-103">Os tópicos nesta seção descrevem como chamar funções em consultas LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="0e57c-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="0e57c-104">As classes <xref:System.Data.Objects.EntityFunctions> e <xref:System.Data.Objects.SqlClient.SqlFunctions> fornecem acesso às funções canônicas e de banco de dados como parte do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="0e57c-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="0e57c-105">Para obter mais informações, confira [Como: Chamar funções canônicas](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) e [como: Chamar funções de banco de dados](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0e57c-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="0e57c-106">O processo para chamar uma função personalizada exige três etapas básicas:</span><span class="sxs-lookup"><span data-stu-id="0e57c-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1.  <span data-ttu-id="0e57c-107">Defina uma função no modelo conceitual ou declare uma função no modelo de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="0e57c-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2.  <span data-ttu-id="0e57c-108">Adicione um método ao seu aplicativo e mapeie-o para a função no modelo com um <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0e57c-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3.  <span data-ttu-id="0e57c-109">Chame a função em uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="0e57c-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="0e57c-110">Para obter mais informações, consulte os tópicos nesta seção.</span><span class="sxs-lookup"><span data-stu-id="0e57c-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0e57c-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0e57c-111">In This Section</span></span>  
 [<span data-ttu-id="0e57c-112">Como: Chamar funções canônicas</span><span class="sxs-lookup"><span data-stu-id="0e57c-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="0e57c-113">Como: Chamar funções de banco de dados</span><span class="sxs-lookup"><span data-stu-id="0e57c-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="0e57c-114">Como: Chamar funções de banco de dados personalizado</span><span class="sxs-lookup"><span data-stu-id="0e57c-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="0e57c-115">Como: Chamar funções definidas em consultas</span><span class="sxs-lookup"><span data-stu-id="0e57c-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="0e57c-116">Como: Chamar funções definidas pelo modelo como métodos de objeto</span><span class="sxs-lookup"><span data-stu-id="0e57c-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="0e57c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e57c-117">See also</span></span>
- [<span data-ttu-id="0e57c-118">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0e57c-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- <span data-ttu-id="0e57c-119">[Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) (Funções canônicas)</span><span class="sxs-lookup"><span data-stu-id="0e57c-119">[Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)</span></span>
- <span data-ttu-id="0e57c-120">[Visão geral do arquivo. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0e57c-120">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="0e57c-121">[Como: Definir funções personalizadas no modelo conceitual](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0e57c-121">[How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
