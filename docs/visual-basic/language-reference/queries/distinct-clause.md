---
title: "Cláusula DISTINCT (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryDistinct
dev_langs:
- VB
helpviewer_keywords:
- Distinct clause
- Distinct statement
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0f4c3da7fdf9e6839c6d1241a322ec7763ffecb7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="cb87e-102">Cláusula Distinct (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb87e-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="cb87e-103">Restringe os valores da variável range atual para eliminar valores duplicados nas cláusulas de consulta subsequentes.</span><span class="sxs-lookup"><span data-stu-id="cb87e-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb87e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb87e-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="cb87e-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb87e-105">Remarks</span></span>  
 <span data-ttu-id="cb87e-106">Você pode usar o `Distinct` cláusula para retornar uma lista de itens exclusivos.</span><span class="sxs-lookup"><span data-stu-id="cb87e-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="cb87e-107">O `Distinct` cláusula faz a consulta ignorar resultados de consulta duplicados.</span><span class="sxs-lookup"><span data-stu-id="cb87e-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="cb87e-108">O `Distinct` cláusula aplica-se a valores duplicados para todos os campos de retorno especificados pelo `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="cb87e-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="cb87e-109">Se nenhum `Select` cláusula for especificada, o `Distinct` cláusula é aplicada à variável de intervalo para a consulta identificada no `From` cláusula.</span><span class="sxs-lookup"><span data-stu-id="cb87e-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="cb87e-110">Se a variável de intervalo não é um tipo imutável, a consulta irá apenas ignorar um resultado de consulta se todos os membros do tipo correspondem a um resultado de consulta existente.</span><span class="sxs-lookup"><span data-stu-id="cb87e-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb87e-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb87e-111">Example</span></span>  
 <span data-ttu-id="cb87e-112">A expressão de consulta a seguir associa uma lista de clientes e uma lista de pedidos de clientes.</span><span class="sxs-lookup"><span data-stu-id="cb87e-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="cb87e-113">O `Distinct` cláusula é incluída para retornar uma lista de nomes exclusivos de clientes e datas de pedido.</span><span class="sxs-lookup"><span data-stu-id="cb87e-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 <span data-ttu-id="cb87e-114">[!code-vb[20 VbSimpleQuerySamples](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cb87e-114">[!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb87e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb87e-115">See Also</span></span>  
 <span data-ttu-id="cb87e-116">[Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="cb87e-116">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="cb87e-117"> [Consultas](../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="cb87e-117"> [Queries](../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="cb87e-118"> [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="cb87e-118"> [From Clause](../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="cb87e-119"> [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="cb87e-119"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="cb87e-120"> [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)</span><span class="sxs-lookup"><span data-stu-id="cb87e-120"> [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)</span></span>
