---
title: "Cláusula Let (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryLet
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause
- Let statement
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: 16
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
ms.openlocfilehash: def3fe03791607811ffc6ed1fe19399ca71ebb07
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="9bd29-102">Cláusula Let (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bd29-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="9bd29-103">Calcula um valor e o atribui a uma nova variável dentro da consulta.</span><span class="sxs-lookup"><span data-stu-id="9bd29-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bd29-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bd29-104">Syntax</span></span>  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="9bd29-105">Partes</span><span class="sxs-lookup"><span data-stu-id="9bd29-105">Parts</span></span>  
  
|<span data-ttu-id="9bd29-106">Termo</span><span class="sxs-lookup"><span data-stu-id="9bd29-106">Term</span></span>|<span data-ttu-id="9bd29-107">Definição</span><span class="sxs-lookup"><span data-stu-id="9bd29-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="9bd29-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9bd29-108">Required.</span></span> <span data-ttu-id="9bd29-109">Um alias que pode ser usado para referenciar os resultados da expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="9bd29-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="9bd29-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9bd29-110">Required.</span></span> <span data-ttu-id="9bd29-111">Uma expressão que será avaliada e atribuída à variável especificada.</span><span class="sxs-lookup"><span data-stu-id="9bd29-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bd29-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bd29-112">Remarks</span></span>  
 <span data-ttu-id="9bd29-113">O `Let` cláusula permite que você calcule valores para cada resultado de consulta e referência-los usando um alias.</span><span class="sxs-lookup"><span data-stu-id="9bd29-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="9bd29-114">O alias pode ser usado em outras cláusulas, como o `Where` cláusula.</span><span class="sxs-lookup"><span data-stu-id="9bd29-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="9bd29-115">O `Let` cláusula permite que você crie uma instrução de consulta que é mais fácil de ler, pois você pode especificar um alias para uma cláusula de expressão incluída na consulta e substituir o alias cada vez que a cláusula de expressão for usada.</span><span class="sxs-lookup"><span data-stu-id="9bd29-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="9bd29-116">Você pode incluir qualquer número de `variable` e `expression` atribuições de `Let` cláusula.</span><span class="sxs-lookup"><span data-stu-id="9bd29-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="9bd29-117">Separe cada atribuição com uma vírgula (,).</span><span class="sxs-lookup"><span data-stu-id="9bd29-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bd29-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bd29-118">Example</span></span>  
 <span data-ttu-id="9bd29-119">O seguinte exemplo de código usa o `Let` cláusula para calcular 10% de desconto em produtos.</span><span class="sxs-lookup"><span data-stu-id="9bd29-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 <span data-ttu-id="9bd29-120">[!code-vb[VbSimpleQuerySamples n º&16;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9bd29-120">[!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd29-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bd29-121">See Also</span></span>  
 <span data-ttu-id="9bd29-122">[Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="9bd29-122">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="9bd29-123"> [Consultas](../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="9bd29-123"> [Queries](../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="9bd29-124"> [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="9bd29-124"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="9bd29-125"> [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="9bd29-125"> [From Clause](../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="9bd29-126"> [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)</span><span class="sxs-lookup"><span data-stu-id="9bd29-126"> [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)</span></span>
