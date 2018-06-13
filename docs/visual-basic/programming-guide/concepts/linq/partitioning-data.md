---
title: Particionamento de dados (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 17e929d3c95e079a0a73b8e8cadf51d3ece6f5f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645906"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="fcf19-102">Particionamento de dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcf19-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="fcf19-103">Particionamento em LINQ refere-se à operação de dividir uma sequência de entrada em duas seções sem reorganizar os elementos e, depois, retornar uma das seções.</span><span class="sxs-lookup"><span data-stu-id="fcf19-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="fcf19-104">A ilustração a seguir mostra os resultados de três operações de particionamento diferentes em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fcf19-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="fcf19-105">A primeira operação retorna os três primeiros elementos na sequência.</span><span class="sxs-lookup"><span data-stu-id="fcf19-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="fcf19-106">A segunda operação ignora os três primeiros elementos e retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="fcf19-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="fcf19-107">A terceira operação ignora os dois primeiros elementos na sequência e retorna os três elementos seguintes.</span><span class="sxs-lookup"><span data-stu-id="fcf19-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="fcf19-108">![Operações de particionamento de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="fcf19-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="fcf19-109">Os métodos de operador de consulta padrão que particionam sequências estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="fcf19-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="fcf19-110">Operadores</span><span class="sxs-lookup"><span data-stu-id="fcf19-110">Operators</span></span>  
  
|<span data-ttu-id="fcf19-111">Nome do operador</span><span class="sxs-lookup"><span data-stu-id="fcf19-111">Operator Name</span></span>|<span data-ttu-id="fcf19-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="fcf19-112">Description</span></span>|<span data-ttu-id="fcf19-113">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fcf19-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="fcf19-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="fcf19-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="fcf19-115">Skip</span><span class="sxs-lookup"><span data-stu-id="fcf19-115">Skip</span></span>|<span data-ttu-id="fcf19-116">Ignora elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="fcf19-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fcf19-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="fcf19-117">SkipWhile</span></span>|<span data-ttu-id="fcf19-118">Ignora elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="fcf19-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fcf19-119">Take</span><span class="sxs-lookup"><span data-stu-id="fcf19-119">Take</span></span>|<span data-ttu-id="fcf19-120">Aceita elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="fcf19-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fcf19-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="fcf19-121">TakeWhile</span></span>|<span data-ttu-id="fcf19-122">Aceita elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="fcf19-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="fcf19-123">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="fcf19-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="fcf19-124">Skip</span><span class="sxs-lookup"><span data-stu-id="fcf19-124">Skip</span></span>  
 <span data-ttu-id="fcf19-125">O seguinte exemplo de código usa o `Skip` cláusula no Visual Basic para ignorar as primeiras quatro cadeias de caracteres em uma matriz de cadeias de caracteres antes de retornar o restante das cadeias de caracteres na matriz.</span><span class="sxs-lookup"><span data-stu-id="fcf19-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a><span data-ttu-id="fcf19-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="fcf19-126">SkipWhile</span></span>  
 <span data-ttu-id="fcf19-127">O seguinte exemplo de código usa o `Skip While` cláusula no Visual Basic para ignorar as cadeias de caracteres em uma matriz durante a primeira letra da cadeia de caracteres "a".</span><span class="sxs-lookup"><span data-stu-id="fcf19-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="fcf19-128">As cadeias de caracteres restantes na matriz são retornadas.</span><span class="sxs-lookup"><span data-stu-id="fcf19-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a><span data-ttu-id="fcf19-129">Take</span><span class="sxs-lookup"><span data-stu-id="fcf19-129">Take</span></span>  
 <span data-ttu-id="fcf19-130">O seguinte exemplo de código usa o `Take` cláusula no Visual Basic para retornar as primeiras duas cadeias de caracteres em uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fcf19-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a><span data-ttu-id="fcf19-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="fcf19-131">TakeWhile</span></span>  
 <span data-ttu-id="fcf19-132">O seguinte exemplo de código usa o `Take While` cláusula no Visual Basic para retornar cadeias de caracteres de uma matriz, enquanto o comprimento da cadeia de caracteres for cinco ou menos.</span><span class="sxs-lookup"><span data-stu-id="fcf19-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fcf19-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcf19-133">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="fcf19-134">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcf19-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="fcf19-135">Cláusula Skip</span><span class="sxs-lookup"><span data-stu-id="fcf19-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="fcf19-136">Cláusula Skip While</span><span class="sxs-lookup"><span data-stu-id="fcf19-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="fcf19-137">Cláusula Take</span><span class="sxs-lookup"><span data-stu-id="fcf19-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="fcf19-138">Cláusula Take While</span><span class="sxs-lookup"><span data-stu-id="fcf19-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)
