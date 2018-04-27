---
title: Particionamento de dados (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 01e4e6d6db07a520b97911de5388b8e42b7e1acc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="3b296-102">Particionamento de dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b296-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="3b296-103">Particionamento em LINQ refere-se à operação de dividir uma sequência de entrada em duas seções sem reorganizar os elementos e, depois, retornar uma das seções.</span><span class="sxs-lookup"><span data-stu-id="3b296-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="3b296-104">A ilustração a seguir mostra os resultados de três operações de particionamento diferentes em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3b296-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="3b296-105">A primeira operação retorna os três primeiros elementos na sequência.</span><span class="sxs-lookup"><span data-stu-id="3b296-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="3b296-106">A segunda operação ignora os três primeiros elementos e retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="3b296-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="3b296-107">A terceira operação ignora os dois primeiros elementos na sequência e retorna os três elementos seguintes.</span><span class="sxs-lookup"><span data-stu-id="3b296-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="3b296-108">![Operações de particionamento de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="3b296-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="3b296-109">Os métodos de operador de consulta padrão que particionam sequências estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="3b296-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="3b296-110">Operadores</span><span class="sxs-lookup"><span data-stu-id="3b296-110">Operators</span></span>  
  
|<span data-ttu-id="3b296-111">Nome do operador</span><span class="sxs-lookup"><span data-stu-id="3b296-111">Operator Name</span></span>|<span data-ttu-id="3b296-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b296-112">Description</span></span>|<span data-ttu-id="3b296-113">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b296-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="3b296-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="3b296-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="3b296-115">Skip</span><span class="sxs-lookup"><span data-stu-id="3b296-115">Skip</span></span>|<span data-ttu-id="3b296-116">Ignora elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="3b296-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3b296-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="3b296-117">SkipWhile</span></span>|<span data-ttu-id="3b296-118">Ignora elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="3b296-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3b296-119">Take</span><span class="sxs-lookup"><span data-stu-id="3b296-119">Take</span></span>|<span data-ttu-id="3b296-120">Aceita elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="3b296-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3b296-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="3b296-121">TakeWhile</span></span>|<span data-ttu-id="3b296-122">Aceita elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="3b296-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="3b296-123">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="3b296-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="3b296-124">Skip</span><span class="sxs-lookup"><span data-stu-id="3b296-124">Skip</span></span>  
 <span data-ttu-id="3b296-125">O seguinte exemplo de código usa o `Skip` cláusula no Visual Basic para ignorar as primeiras quatro cadeias de caracteres em uma matriz de cadeias de caracteres antes de retornar o restante das cadeias de caracteres na matriz.</span><span class="sxs-lookup"><span data-stu-id="3b296-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a><span data-ttu-id="3b296-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="3b296-126">SkipWhile</span></span>  
 <span data-ttu-id="3b296-127">O seguinte exemplo de código usa o `Skip While` cláusula no Visual Basic para ignorar as cadeias de caracteres em uma matriz durante a primeira letra da cadeia de caracteres "a".</span><span class="sxs-lookup"><span data-stu-id="3b296-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="3b296-128">As cadeias de caracteres restantes na matriz são retornadas.</span><span class="sxs-lookup"><span data-stu-id="3b296-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a><span data-ttu-id="3b296-129">Take</span><span class="sxs-lookup"><span data-stu-id="3b296-129">Take</span></span>  
 <span data-ttu-id="3b296-130">O seguinte exemplo de código usa o `Take` cláusula no Visual Basic para retornar as primeiras duas cadeias de caracteres em uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3b296-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a><span data-ttu-id="3b296-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="3b296-131">TakeWhile</span></span>  
 <span data-ttu-id="3b296-132">O seguinte exemplo de código usa o `Take While` cláusula no Visual Basic para retornar cadeias de caracteres de uma matriz, enquanto o comprimento da cadeia de caracteres for cinco ou menos.</span><span class="sxs-lookup"><span data-stu-id="3b296-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3b296-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b296-133">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="3b296-134">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b296-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="3b296-135">Cláusula Skip</span><span class="sxs-lookup"><span data-stu-id="3b296-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="3b296-136">Cláusula Skip While</span><span class="sxs-lookup"><span data-stu-id="3b296-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="3b296-137">Cláusula Take</span><span class="sxs-lookup"><span data-stu-id="3b296-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="3b296-138">Cláusula Take While</span><span class="sxs-lookup"><span data-stu-id="3b296-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)
