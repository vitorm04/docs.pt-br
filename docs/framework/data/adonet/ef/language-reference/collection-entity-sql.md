---
title: COLEÇÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: c960ee69f8188f6dd3184b6fb31f3432f8d58fee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197944"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="2e0dd-102">COLEÇÃO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2e0dd-102">COLLECTION (Entity SQL)</span></span>

<span data-ttu-id="2e0dd-103">A palavra-chave de COLEÇÃO é usado somente na definição de uma função in-line.</span><span class="sxs-lookup"><span data-stu-id="2e0dd-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="2e0dd-104">Funções de coleção são as funções que operam em um conjunto de valores e gerenciar uma saída escalares.</span><span class="sxs-lookup"><span data-stu-id="2e0dd-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e0dd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e0dd-105">Syntax</span></span>  
  
```csharp  
COLLECTION(type_definition)
```  
  
## <a name="arguments"></a><span data-ttu-id="2e0dd-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="2e0dd-106">Arguments</span></span>  

 `type_definition`  
 <span data-ttu-id="2e0dd-107">Uma expressão que retorna uma coleção de tipos suportados, de linhas, ou de referências.</span><span class="sxs-lookup"><span data-stu-id="2e0dd-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e0dd-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e0dd-108">Remarks</span></span>  

 <span data-ttu-id="2e0dd-109">Para obter mais informações sobre a palavra-chave COLLECTION, consulte [definições de tipo](type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2e0dd-109">For more information about the COLLECTION keyword, see [Type Definitions](type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e0dd-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e0dd-110">Example</span></span>  

 <span data-ttu-id="2e0dd-111">O exemplo a seguir mostra como usar a palavra-chave de COLEÇÃO para declarar uma coleção de decimais como um argumento para uma função in-line de consulta.</span><span class="sxs-lookup"><span data-stu-id="2e0dd-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="2e0dd-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="2e0dd-112">See also</span></span>

- [<span data-ttu-id="2e0dd-113">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2e0dd-113">Entity SQL Reference</span></span>](entity-sql-reference.md)
