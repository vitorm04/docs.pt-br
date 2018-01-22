---
title: "Chamando funções em consultas no LINQ to Entities"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d7199c41f8bcf81340956b17f616bec76e534dcc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="37179-102">Chamando funções em consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="37179-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="37179-103">Os tópicos nesta seção descrevem como chamar funções em consultas LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="37179-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="37179-104">As classes <xref:System.Data.Objects.EntityFunctions> e <xref:System.Data.Objects.SqlClient.SqlFunctions> fornecem acesso às funções canônicas e de banco de dados como parte do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="37179-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="37179-105">Para obter mais informações, consulte [como: chamar funções canônicas](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) e [como: chamar funções de banco de dados](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="37179-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="37179-106">O processo para chamar uma função personalizada exige três etapas básicas:</span><span class="sxs-lookup"><span data-stu-id="37179-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1.  <span data-ttu-id="37179-107">Defina uma função no modelo conceitual ou declare uma função no modelo de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="37179-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2.  <span data-ttu-id="37179-108">Adicione um método ao seu aplicativo e mapeie-o para a função no modelo com um <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="37179-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3.  <span data-ttu-id="37179-109">Chame a função em uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="37179-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="37179-110">Para obter mais informações, consulte os tópicos nesta seção.</span><span class="sxs-lookup"><span data-stu-id="37179-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37179-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="37179-111">In This Section</span></span>  
 [<span data-ttu-id="37179-112">Como chamar funções canônicas</span><span class="sxs-lookup"><span data-stu-id="37179-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="37179-113">Como chamar funções de banco de dados</span><span class="sxs-lookup"><span data-stu-id="37179-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="37179-114">Como chamar funções de banco de dados personalizado</span><span class="sxs-lookup"><span data-stu-id="37179-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="37179-115">Como chamar funções definidas em consultas</span><span class="sxs-lookup"><span data-stu-id="37179-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="37179-116">Como chamar funções definidas por modelo como métodos de objeto</span><span class="sxs-lookup"><span data-stu-id="37179-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="37179-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37179-117">See Also</span></span>  
 [<span data-ttu-id="37179-118">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="37179-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 <span data-ttu-id="37179-119">[Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) (Funções canônicas)</span><span class="sxs-lookup"><span data-stu-id="37179-119">[Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)</span></span>  
 [<span data-ttu-id="37179-120">Visão geral do arquivo. edmx</span><span class="sxs-lookup"><span data-stu-id="37179-120">.edmx File Overview</span></span>](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="37179-121">Como: definir funções personalizadas no modelo conceitual</span><span class="sxs-lookup"><span data-stu-id="37179-121">How to: Define Custom Functions in the Conceptual Model</span></span>](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)
