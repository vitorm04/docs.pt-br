---
title: + (Adicionar)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: abd5921653e65c69da99a1aff60506aafd814278
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="-add"></a><span data-ttu-id="a66a2-102">+ (Adicionar)</span><span class="sxs-lookup"><span data-stu-id="a66a2-102">+ (Add)</span></span>
<span data-ttu-id="a66a2-103">Adiciona dois números.</span><span class="sxs-lookup"><span data-stu-id="a66a2-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a66a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a66a2-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a66a2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a66a2-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a66a2-106">Qualquer expressão válida de qualquer dos tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="a66a2-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a66a2-107">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="a66a2-107">Result Types</span></span>  
 <span data-ttu-id="a66a2-108">O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="a66a2-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="a66a2-109">Para obter mais informações sobre a promoção de tipo implícito, consulte [sistema de tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a66a2-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a66a2-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a66a2-110">Remarks</span></span>  
 <span data-ttu-id="a66a2-111">Para tipos de EDM.String, a adição é concatenação.</span><span class="sxs-lookup"><span data-stu-id="a66a2-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a66a2-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a66a2-112">Example</span></span>  
 <span data-ttu-id="a66a2-113">A seguinte consulta SQL Entity usa operador + aritmético para adicionar dois números.</span><span class="sxs-lookup"><span data-stu-id="a66a2-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="a66a2-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a66a2-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a66a2-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="a66a2-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a66a2-116">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a66a2-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="a66a2-117">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="a66a2-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="a66a2-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a66a2-118">See Also</span></span>  
 [<span data-ttu-id="a66a2-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a66a2-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="a66a2-120">Tipos de modelo conceitual (CSDL)</span><span class="sxs-lookup"><span data-stu-id="a66a2-120">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4)
