---
title: ENTRE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 2c411fd7fcac9d98323d5fcfb1874f98bc664991
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225255"
---
# <a name="between-entity-sql"></a><span data-ttu-id="1e644-102">ENTRE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1e644-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="1e644-103">Determina se uma expressão resulta em um valor em um intervalo especificado.</span><span class="sxs-lookup"><span data-stu-id="1e644-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="1e644-104">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ENTER expressão tem a mesma funcionalidade que a expressão Transact-SQL entre.</span><span class="sxs-lookup"><span data-stu-id="1e644-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e644-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e644-105">Syntax</span></span>  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="1e644-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="1e644-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1e644-107">Qualquer expressão válida para testar no intervalo definido por `begin_expression` e por `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="1e644-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> `expression` <span data-ttu-id="1e644-108">deve ser o mesmo tipo que `begin_expression` e `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="1e644-108">must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="1e644-109">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="1e644-109">Any valid expression.</span></span> `begin_expression` <span data-ttu-id="1e644-110">deve ser o mesmo tipo que `expression` e `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="1e644-110">must be the same type as both `expression` and `end_expression`.</span></span> `begin_expression` <span data-ttu-id="1e644-111">deve ser menor que `end_expression`, caso contrário o valor retornado será negado.</span><span class="sxs-lookup"><span data-stu-id="1e644-111">should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="1e644-112">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="1e644-112">Any valid expression.</span></span> `end_expression` <span data-ttu-id="1e644-113">deve ser o mesmo tipo que `expression` e `begin_expression`.</span><span class="sxs-lookup"><span data-stu-id="1e644-113">must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="1e644-114">NOT</span><span class="sxs-lookup"><span data-stu-id="1e644-114">NOT</span></span>  
 <span data-ttu-id="1e644-115">Especifica que o resultado de ENTER é negado.</span><span class="sxs-lookup"><span data-stu-id="1e644-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="1e644-116">AND</span><span class="sxs-lookup"><span data-stu-id="1e644-116">AND</span></span>  
 <span data-ttu-id="1e644-117">Atua como um espaço reservado que indica que `expression` deve estar dentro do intervalo indicado por `begin_expression` e por `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="1e644-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e644-118">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1e644-118">Return Value</span></span>  
 `true` <span data-ttu-id="1e644-119">Se `expression` está entre o intervalo indicado por `begin_expression` e `end_expression`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="1e644-119">if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> `null` <span data-ttu-id="1e644-120">será retornado se `expression` está `null` ou se `begin_expression` ou `end_expression` é `null`.</span><span class="sxs-lookup"><span data-stu-id="1e644-120">will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e644-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="1e644-121">Remarks</span></span>  
 <span data-ttu-id="1e644-122">Para especificar um intervalo exclusivo, use o maior que (>) e menor que (<) operadores em vez de BETWEEN.</span><span class="sxs-lookup"><span data-stu-id="1e644-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e644-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1e644-123">Example</span></span>  
 <span data-ttu-id="1e644-124">Os seguintes usos da consulta SQL Entity ENTER o operador determinar se uma expressão resulta em um valor em um intervalo especificado.</span><span class="sxs-lookup"><span data-stu-id="1e644-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="1e644-125">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1e644-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1e644-126">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="1e644-126">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1e644-127">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1e644-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="1e644-128">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="1e644-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="1e644-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e644-129">See also</span></span>

- [<span data-ttu-id="1e644-130">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1e644-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
