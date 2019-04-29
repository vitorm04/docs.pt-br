---
title: IGNORAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: e8ef529ea8d2be2ef8eb3a2eb606e7ca8bf13f0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797730"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="32c50-102">IGNORAR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="32c50-102">SKIP (Entity SQL)</span></span>
<span data-ttu-id="32c50-103">Você pode executar a físico paginação usando a cláusula subpropriedades de SKIP na cláusula GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="32c50-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="32c50-104">A SKIP não pode ser usada separada de cláusula GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="32c50-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32c50-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32c50-105">Syntax</span></span>  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="32c50-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="32c50-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="32c50-107">O número de itens para ignorar.</span><span class="sxs-lookup"><span data-stu-id="32c50-107">The number of items to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32c50-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="32c50-108">Remarks</span></span>  
 <span data-ttu-id="32c50-109">Se uma subpropriedades cláusula de expressão de SKIP está presente em uma cláusula GROUP BY, os resultados que serão classificados concordam a especificação do tipo e o conjunto de resultados incluirá as linhas a partir da linha seguinte logo após a expressão de SKIP.</span><span class="sxs-lookup"><span data-stu-id="32c50-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="32c50-110">Por exemplo, a SKIP 5 ignorará as primeiras cinco linhas e retornará a sexta linha avançar.</span><span class="sxs-lookup"><span data-stu-id="32c50-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32c50-111">Uma consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não é válido se o modificador TOP e a subpropriedades cláusula de SKIP estiverem presentes na mesma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="32c50-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="32c50-112">A consulta deve ser reescrita alterando a expressão TOP para a expressão de LIMIT.</span><span class="sxs-lookup"><span data-stu-id="32c50-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32c50-113">Em [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], usar a SKIP com cláusula ORDER BY em colunas não-chave pode retornar resultados incorretos.</span><span class="sxs-lookup"><span data-stu-id="32c50-113">In [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="32c50-114">Mais do que o número de linhas especificado podem ser ignoradas se a coluna de chave não tem dados duplicados nele.</span><span class="sxs-lookup"><span data-stu-id="32c50-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="32c50-115">Isso é devido a como SKIP é convertido para [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span><span class="sxs-lookup"><span data-stu-id="32c50-115">This is due to how SKIP is translated for [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="32c50-116">Por exemplo, o seguinte código mais de cinco linhas podem ser ignoradas se `E.NonKeyColumn` tem valores duplicados:</span><span class="sxs-lookup"><span data-stu-id="32c50-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 <span data-ttu-id="32c50-117">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consultar em [como: Página por meio de resultados da consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) usa o operador ORDER BY com SKIP especificar ordem de classificação usado em objetos retornados em uma instrução SELECT.</span><span class="sxs-lookup"><span data-stu-id="32c50-117">The  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c50-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32c50-118">See also</span></span>

- [<span data-ttu-id="32c50-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="32c50-119">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- <span data-ttu-id="32c50-120">[Como: Paginar os resultados da consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="32c50-120">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="32c50-121">Paginação</span><span class="sxs-lookup"><span data-stu-id="32c50-121">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [<span data-ttu-id="32c50-122">TOP</span><span class="sxs-lookup"><span data-stu-id="32c50-122">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
