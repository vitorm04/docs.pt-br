---
title: Chamando funções em consultas no LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 267bb393d9e75c66eb18139e8897da34bd86e159
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251258"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="0088c-102">Chamando funções em consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0088c-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="0088c-103">Os tópicos nesta seção descrevem como chamar funções em consultas LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="0088c-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="0088c-104">As classes <xref:System.Data.Objects.EntityFunctions> e <xref:System.Data.Objects.SqlClient.SqlFunctions> fornecem acesso às funções canônicas e de banco de dados como parte do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="0088c-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="0088c-105">Para obter mais informações, confira [Como: Chame funções](how-to-call-canonical-functions.md) canônicas [e como: Chamar funções](how-to-call-database-functions.md)de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0088c-105">For more information, see [How to: Call Canonical Functions](how-to-call-canonical-functions.md) and [How to: Call Database Functions](how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="0088c-106">O processo para chamar uma função personalizada exige três etapas básicas:</span><span class="sxs-lookup"><span data-stu-id="0088c-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1. <span data-ttu-id="0088c-107">Defina uma função no modelo conceitual ou declare uma função no modelo de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="0088c-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2. <span data-ttu-id="0088c-108">Adicione um método ao seu aplicativo e mapeie-o para a função no modelo com um <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0088c-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3. <span data-ttu-id="0088c-109">Chame a função em uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="0088c-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="0088c-110">Para obter mais informações, consulte os tópicos nesta seção.</span><span class="sxs-lookup"><span data-stu-id="0088c-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0088c-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0088c-111">In This Section</span></span>  
 [<span data-ttu-id="0088c-112">Como: Chamar funções canônicas</span><span class="sxs-lookup"><span data-stu-id="0088c-112">How to: Call Canonical Functions</span></span>](how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="0088c-113">Como: Chamar funções de banco de dados</span><span class="sxs-lookup"><span data-stu-id="0088c-113">How to: Call Database Functions</span></span>](how-to-call-database-functions.md)  
  
 [<span data-ttu-id="0088c-114">Como: Chamar funções de banco de dados personalizadas</span><span class="sxs-lookup"><span data-stu-id="0088c-114">How to: Call Custom Database Functions</span></span>](how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="0088c-115">Como: Chamar funções definidas pelo modelo em consultas</span><span class="sxs-lookup"><span data-stu-id="0088c-115">How to: Call Model-Defined Functions in Queries</span></span>](how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="0088c-116">Como: Chamar funções definidas pelo modelo como métodos de objeto</span><span class="sxs-lookup"><span data-stu-id="0088c-116">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="0088c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0088c-117">See also</span></span>

- [<span data-ttu-id="0088c-118">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0088c-118">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- <span data-ttu-id="0088c-119">[Canonical Functions](canonical-functions.md) (Funções canônicas)</span><span class="sxs-lookup"><span data-stu-id="0088c-119">[Canonical Functions](canonical-functions.md)</span></span>
- <span data-ttu-id="0088c-120">[Visão geral do arquivo. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0088c-120">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="0088c-121">[Como: Definir funções personalizadas no modelo conceitual](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0088c-121">[How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
