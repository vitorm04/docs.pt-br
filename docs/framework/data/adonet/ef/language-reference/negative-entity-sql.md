---
title: '- Seriamente (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 71749dab073fade854c2a494841e3f6b408ebd1d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204405"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="4af13-102">- (Negativo) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4af13-102">- (Negative) (Entity SQL)</span></span>

<span data-ttu-id="4af13-103">Retorna o negativo o valor de uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="4af13-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af13-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4af13-104">Syntax</span></span>  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4af13-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="4af13-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="4af13-106">Qualquer expressão válida de qualquer dos tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="4af13-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4af13-107">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="4af13-107">Result Types</span></span>  

 <span data-ttu-id="4af13-108">O tipo de dados de `expression`.</span><span class="sxs-lookup"><span data-stu-id="4af13-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4af13-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4af13-109">Remarks</span></span>  

 <span data-ttu-id="4af13-110">Se `expression` é um tipo sem sinal, o tipo do resultado será o tipo com sinal que relaciona o melhor para o tipo de `expression`.</span><span class="sxs-lookup"><span data-stu-id="4af13-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="4af13-111">Por exemplo, se `expression` é de bytes de tipo, um valor do tipo Int16 será retornado.</span><span class="sxs-lookup"><span data-stu-id="4af13-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4af13-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4af13-112">Example</span></span>  

 <span data-ttu-id="4af13-113">A seguinte consulta SQL Entity usa o operador - aritmético para retornar o negativo o valor de uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="4af13-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="4af13-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4af13-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4af13-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="4af13-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4af13-116">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4af13-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="4af13-117">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="4af13-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="4af13-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="4af13-118">See also</span></span>

- [<span data-ttu-id="4af13-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4af13-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
