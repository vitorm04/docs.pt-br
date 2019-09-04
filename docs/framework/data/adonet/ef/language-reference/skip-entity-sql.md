---
title: IGNORAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 19d3001fb8f226b02f16167dfb51ce1caa80ba3b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249227"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="93a46-102">IGNORAR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="93a46-102">SKIP (Entity SQL)</span></span>

<span data-ttu-id="93a46-103">Você pode executar a físico paginação usando a cláusula subpropriedades de SKIP na cláusula GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="93a46-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="93a46-104">A SKIP não pode ser usada separada de cláusula GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="93a46-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>

## <a name="syntax"></a><span data-ttu-id="93a46-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93a46-105">Syntax</span></span>

```
[ SKIP n ]
```

## <a name="arguments"></a><span data-ttu-id="93a46-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="93a46-106">Arguments</span></span>

`n` \
<span data-ttu-id="93a46-107">O número de itens para ignorar.</span><span class="sxs-lookup"><span data-stu-id="93a46-107">The number of items to skip.</span></span>

## <a name="remarks"></a><span data-ttu-id="93a46-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="93a46-108">Remarks</span></span>

<span data-ttu-id="93a46-109">Se uma subpropriedades cláusula de expressão de SKIP está presente em uma cláusula GROUP BY, os resultados que serão classificados concordam a especificação do tipo e o conjunto de resultados incluirá as linhas a partir da linha seguinte logo após a expressão de SKIP.</span><span class="sxs-lookup"><span data-stu-id="93a46-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="93a46-110">Por exemplo, a SKIP 5 ignorará as primeiras cinco linhas e retornará a sexta linha avançar.</span><span class="sxs-lookup"><span data-stu-id="93a46-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>

> [!NOTE]
> <span data-ttu-id="93a46-111">Uma consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não é válido se o modificador TOP e a subpropriedades cláusula de SKIP estiverem presentes na mesma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="93a46-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="93a46-112">A consulta deve ser reescrita alterando a expressão TOP para a expressão de LIMIT.</span><span class="sxs-lookup"><span data-stu-id="93a46-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>

> [!NOTE]
> <span data-ttu-id="93a46-113">No SQL Server 2000, usar SKIP com ORDER BY em colunas não chave pode retornar resultados incorretos.</span><span class="sxs-lookup"><span data-stu-id="93a46-113">In SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="93a46-114">Mais do que o número de linhas especificado podem ser ignoradas se a coluna de chave não tem dados duplicados nele.</span><span class="sxs-lookup"><span data-stu-id="93a46-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="93a46-115">Isso ocorre devido a como o SKIP é convertido para SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="93a46-115">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="93a46-116">Por exemplo, o seguinte código mais de cinco linhas podem ser ignoradas se `E.NonKeyColumn` tem valores duplicados:</span><span class="sxs-lookup"><span data-stu-id="93a46-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>
>
> `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`

<span data-ttu-id="93a46-117">A [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consulta em [como: A página através dos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) resultados da consulta usa o operador order by com Skip para especificar a ordem de classificação usada nos objetos retornados em uma instrução SELECT.</span><span class="sxs-lookup"><span data-stu-id="93a46-117">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="93a46-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93a46-118">See also</span></span>

- [<span data-ttu-id="93a46-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="93a46-119">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="93a46-120">[Como: Página por meio de resultados da consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="93a46-120">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="93a46-121">Paginação</span><span class="sxs-lookup"><span data-stu-id="93a46-121">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="93a46-122">TOP</span><span class="sxs-lookup"><span data-stu-id="93a46-122">TOP</span></span>](top-entity-sql.md)
