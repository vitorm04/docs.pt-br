---
title: Particionamento de dados (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9d0df2bc473f48fba4bbb094317166407f7c7ec2
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="cb828-102">Particionamento de dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb828-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="cb828-103">Particionamento em LINQ refere-se a operação de dividir uma sequência de entrada em duas seções, sem reorganizar os elementos e, em seguida, retornando uma das seções.</span><span class="sxs-lookup"><span data-stu-id="cb828-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="cb828-104">A ilustração a seguir mostra os resultados de três particionamentos operações diferentes em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="cb828-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="cb828-105">A primeira operação retorna os três primeiros elementos na sequência.</span><span class="sxs-lookup"><span data-stu-id="cb828-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="cb828-106">A segunda operação ignora os três primeiros elementos e retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="cb828-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="cb828-107">A terceira operação ignora os primeiros dois elementos na sequência e retorna os três elementos.</span><span class="sxs-lookup"><span data-stu-id="cb828-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="cb828-108">![Operações de particionamento de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="cb828-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="cb828-109">Os métodos de operador de consulta padrão que sequências de partição são listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="cb828-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="cb828-110">Operadores</span><span class="sxs-lookup"><span data-stu-id="cb828-110">Operators</span></span>  
  
|<span data-ttu-id="cb828-111">Nome do operador</span><span class="sxs-lookup"><span data-stu-id="cb828-111">Operator Name</span></span>|<span data-ttu-id="cb828-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb828-112">Description</span></span>|<span data-ttu-id="cb828-113">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cb828-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="cb828-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="cb828-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="cb828-115">Skip</span><span class="sxs-lookup"><span data-stu-id="cb828-115">Skip</span></span>|<span data-ttu-id="cb828-116">Ignora elementos até uma posição especificada em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="cb828-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<span data-ttu-id="cb828-117"><xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cb828-117"><xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="cb828-118"><xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cb828-118"><xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="cb828-119">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="cb828-119">SkipWhile</span></span>|<span data-ttu-id="cb828-120">Ignora elementos com base em uma função de predicado até que um elemento não atendem à condição.</span><span class="sxs-lookup"><span data-stu-id="cb828-120">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<span data-ttu-id="cb828-121"><xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cb828-121"><xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="cb828-122"><xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cb828-122"><xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="cb828-123">Take</span><span class="sxs-lookup"><span data-stu-id="cb828-123">Take</span></span>|<span data-ttu-id="cb828-124">Usa elementos até uma posição especificada em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="cb828-124">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<span data-ttu-id="cb828-125"><xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cb828-125"><xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="cb828-126"><xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cb828-126"><xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="cb828-127">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="cb828-127">TakeWhile</span></span>|<span data-ttu-id="cb828-128">Usa elementos com base em uma função de predicado até que um elemento não atendem à condição.</span><span class="sxs-lookup"><span data-stu-id="cb828-128">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<span data-ttu-id="cb828-129"><xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cb828-129"><xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="cb828-130"><xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cb828-130"><xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="cb828-131">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="cb828-131">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="cb828-132">Skip</span><span class="sxs-lookup"><span data-stu-id="cb828-132">Skip</span></span>  
 <span data-ttu-id="cb828-133">O seguinte exemplo de código usa o `Skip` cláusula [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para ignorar as primeiras quatro cadeias de caracteres em uma matriz de cadeias de caracteres antes de retornar as cadeias de caracteres restantes na matriz.</span><span class="sxs-lookup"><span data-stu-id="cb828-133">The following code example uses the `Skip` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 <span data-ttu-id="cb828-134">[!code-vb[CsLINQPartitioning n º&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cb828-134">[!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]</span></span>  
  
### <a name="skipwhile"></a><span data-ttu-id="cb828-135">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="cb828-135">SkipWhile</span></span>  
 <span data-ttu-id="cb828-136">O seguinte exemplo de código usa o `Skip While` cláusula [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ignorar as cadeias de caracteres em uma matriz durante a primeira letra da cadeia de caracteres é "a".</span><span class="sxs-lookup"><span data-stu-id="cb828-136">The following code example uses the `Skip While` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="cb828-137">As cadeias de caracteres restantes na matriz são retornadas.</span><span class="sxs-lookup"><span data-stu-id="cb828-137">The remaining strings in the array are returned.</span></span>  
  
 <span data-ttu-id="cb828-138">[!code-vb[CsLINQPartitioning n º&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="cb828-138">[!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]</span></span>  
  
### <a name="take"></a><span data-ttu-id="cb828-139">Take</span><span class="sxs-lookup"><span data-stu-id="cb828-139">Take</span></span>  
 <span data-ttu-id="cb828-140">O seguinte exemplo de código usa o `Take` cláusula [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para retornar as primeiras duas cadeias de caracteres em uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="cb828-140">The following code example uses the `Take` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to return the first two strings in an array of strings.</span></span>  
  
 <span data-ttu-id="cb828-141">[!code-vb[CsLINQPartitioning n º&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="cb828-141">[!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]</span></span>  
  
### <a name="takewhile"></a><span data-ttu-id="cb828-142">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="cb828-142">TakeWhile</span></span>  
 <span data-ttu-id="cb828-143">O seguinte exemplo de código usa o `Take While` cláusula [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para retornar cadeias de caracteres de uma matriz, enquanto o comprimento da cadeia de caracteres é de cinco ou menos.</span><span class="sxs-lookup"><span data-stu-id="cb828-143">The following code example uses the `Take While` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to return strings from an array while the length of the string is five or less.</span></span>  
  
 <span data-ttu-id="cb828-144">[!code-vb[CsLINQPartitioning n º&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="cb828-144">[!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb828-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb828-145">See Also</span></span>  
 <span data-ttu-id="cb828-146"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="cb828-146"><xref:System.Linq></span></span>   
<span data-ttu-id="cb828-147"> [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="cb828-147"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="cb828-148"> [Cláusula Skip](../../../../visual-basic/language-reference/queries/skip-clause.md) </span><span class="sxs-lookup"><span data-stu-id="cb828-148"> [Skip Clause](../../../../visual-basic/language-reference/queries/skip-clause.md) </span></span>  
<span data-ttu-id="cb828-149"> [Cláusula Skip While](../../../../visual-basic/language-reference/queries/skip-while-clause.md) </span><span class="sxs-lookup"><span data-stu-id="cb828-149"> [Skip While Clause](../../../../visual-basic/language-reference/queries/skip-while-clause.md) </span></span>  
<span data-ttu-id="cb828-150"> [Cláusula Take](../../../../visual-basic/language-reference/queries/take-clause.md) </span><span class="sxs-lookup"><span data-stu-id="cb828-150"> [Take Clause](../../../../visual-basic/language-reference/queries/take-clause.md) </span></span>  
<span data-ttu-id="cb828-151"> [Cláusula Take While](../../../../visual-basic/language-reference/queries/take-while-clause.md)</span><span class="sxs-lookup"><span data-stu-id="cb828-151"> [Take While Clause](../../../../visual-basic/language-reference/queries/take-while-clause.md)</span></span>
