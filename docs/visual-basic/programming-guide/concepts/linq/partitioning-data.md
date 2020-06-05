---
title: Particionar dados
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 34749f9d7b137bade66b6103650871246c3cc532
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406840"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="0c957-102">Dados de particionamento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c957-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="0c957-103">Particionamento em LINQ refere-se à operação de dividir uma sequência de entrada em duas seções sem reorganizar os elementos e, depois, retornar uma das seções.</span><span class="sxs-lookup"><span data-stu-id="0c957-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="0c957-104">A ilustração a seguir mostra os resultados de três operações de particionamento diferentes em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0c957-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="0c957-105">A primeira operação retorna os três primeiros elementos na sequência.</span><span class="sxs-lookup"><span data-stu-id="0c957-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="0c957-106">A segunda operação ignora os três primeiros elementos e retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="0c957-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="0c957-107">A terceira operação ignora os dois primeiros elementos na sequência e retorna os três elementos seguintes.</span><span class="sxs-lookup"><span data-stu-id="0c957-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Ilustração que mostra as três operações de particionamento do LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="0c957-109">Os métodos de operador de consulta padrão que particionam sequências estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="0c957-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="0c957-110">Operadores</span><span class="sxs-lookup"><span data-stu-id="0c957-110">Operators</span></span>  
  
|<span data-ttu-id="0c957-111">Nome do operador</span><span class="sxs-lookup"><span data-stu-id="0c957-111">Operator Name</span></span>|<span data-ttu-id="0c957-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c957-112">Description</span></span>|<span data-ttu-id="0c957-113">Visual Basic sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="0c957-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="0c957-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="0c957-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="0c957-115">Ignorar</span><span class="sxs-lookup"><span data-stu-id="0c957-115">Skip</span></span>|<span data-ttu-id="0c957-116">Ignora elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="0c957-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0c957-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="0c957-117">SkipWhile</span></span>|<span data-ttu-id="0c957-118">Ignora elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="0c957-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0c957-119">Take</span><span class="sxs-lookup"><span data-stu-id="0c957-119">Take</span></span>|<span data-ttu-id="0c957-120">Aceita elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="0c957-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0c957-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="0c957-121">TakeWhile</span></span>|<span data-ttu-id="0c957-122">Aceita elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="0c957-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="0c957-123">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="0c957-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="0c957-124">Ignorar</span><span class="sxs-lookup"><span data-stu-id="0c957-124">Skip</span></span>  
 <span data-ttu-id="0c957-125">O exemplo de código a seguir usa a `Skip` cláusula em Visual Basic para ignorar as primeiras quatro cadeias de caracteres em uma matriz de cadeias de caracteres antes de retornar as cadeias de caracteres restantes na matriz.</span><span class="sxs-lookup"><span data-stu-id="0c957-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="0c957-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="0c957-126">SkipWhile</span></span>  
 <span data-ttu-id="0c957-127">O exemplo de código a seguir usa a `Skip While` cláusula em Visual Basic para ignorar as cadeias de caracteres em uma matriz, enquanto a primeira letra da cadeia é "a".</span><span class="sxs-lookup"><span data-stu-id="0c957-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="0c957-128">As cadeias de caracteres restantes na matriz são retornadas.</span><span class="sxs-lookup"><span data-stu-id="0c957-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="0c957-129">Take</span><span class="sxs-lookup"><span data-stu-id="0c957-129">Take</span></span>  
 <span data-ttu-id="0c957-130">O exemplo de código a seguir usa a `Take` cláusula em Visual Basic para retornar as duas primeiras cadeias de caracteres em uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0c957-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="0c957-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="0c957-131">TakeWhile</span></span>  
 <span data-ttu-id="0c957-132">O exemplo de código a seguir usa a `Take While` cláusula em Visual Basic para retornar cadeias de caracteres de uma matriz, enquanto o comprimento da cadeia de caracteres é de cinco ou menos.</span><span class="sxs-lookup"><span data-stu-id="0c957-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="0c957-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="0c957-133">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="0c957-134">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c957-134">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="0c957-135">Cláusula Skip</span><span class="sxs-lookup"><span data-stu-id="0c957-135">Skip Clause</span></span>](../../../language-reference/queries/skip-clause.md)
- [<span data-ttu-id="0c957-136">Cláusula Skip While</span><span class="sxs-lookup"><span data-stu-id="0c957-136">Skip While Clause</span></span>](../../../language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="0c957-137">Cláusula Take</span><span class="sxs-lookup"><span data-stu-id="0c957-137">Take Clause</span></span>](../../../language-reference/queries/take-clause.md)
- [<span data-ttu-id="0c957-138">Cláusula Take While</span><span class="sxs-lookup"><span data-stu-id="0c957-138">Take While Clause</span></span>](../../../language-reference/queries/take-while-clause.md)
