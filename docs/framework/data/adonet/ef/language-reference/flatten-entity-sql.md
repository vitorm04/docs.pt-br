---
title: ACHATAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 84b846e3db86c664bc42363f3d983a1001f5c318
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833814"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="f0a0f-102">ACHATAR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f0a0f-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="f0a0f-103">Converte uma coleção de coleções em uma coleção combinada.</span><span class="sxs-lookup"><span data-stu-id="f0a0f-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="f0a0f-104">A nova coleção contém todos os mesmos elementos que a coleção antiga, mas sem uma estrutura aninhada.</span><span class="sxs-lookup"><span data-stu-id="f0a0f-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0a0f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0a0f-105">Syntax</span></span>  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="f0a0f-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="f0a0f-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="f0a0f-107">Qualquer expressão válida que retorna uma coleção de coleções valor de ajuste em uma única coleção.</span><span class="sxs-lookup"><span data-stu-id="f0a0f-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0a0f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f0a0f-108">Remarks</span></span>  
 <span data-ttu-id="f0a0f-109">`FLATTEN` é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f0a0f-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="f0a0f-110">Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="f0a0f-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="f0a0f-111">Consulte [exceto](except-entity-sql.md) para obter informações de precedência para os operadores de conjunto [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0a0f-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0a0f-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f0a0f-112">Example</span></span>  
 <span data-ttu-id="f0a0f-113">A seguinte consulta SQL Entity usa o operador de `FLATTEN` para converter uma coleção das coleções em uma coleção aplainada.</span><span class="sxs-lookup"><span data-stu-id="f0a0f-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="f0a0f-114">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="f0a0f-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f0a0f-115">Siga o procedimento em [How para: Executa uma consulta que retorna os resultados de Estruturaistype @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="f0a0f-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f0a0f-116">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="f0a0f-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="f0a0f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0a0f-117">See also</span></span>

- [<span data-ttu-id="f0a0f-118">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f0a0f-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
