---
title: Filtragem de dados (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fa2d3b6c5b81f137ab3a81f9b18707bb2da91f6e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="39e29-102">Filtragem de dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39e29-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="39e29-103">Filtragem refere-se a operação de restringir o conjunto de resultados para conter apenas os elementos que satisfazem uma condição especificada.</span><span class="sxs-lookup"><span data-stu-id="39e29-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="39e29-104">Ele também é conhecido como seleção.</span><span class="sxs-lookup"><span data-stu-id="39e29-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="39e29-105">A ilustração a seguir mostra os resultados de uma sequência de caracteres de filtragem.</span><span class="sxs-lookup"><span data-stu-id="39e29-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="39e29-106">O predicado para a operação de filtragem Especifica que o caractere deve ser 'A'.</span><span class="sxs-lookup"><span data-stu-id="39e29-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="39e29-107">![Operação de filtragem de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="39e29-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="39e29-108">Os métodos de operador de consulta padrão que executam a seleção são listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="39e29-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39e29-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="39e29-109">Methods</span></span>  
  
|<span data-ttu-id="39e29-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="39e29-110">Method Name</span></span>|<span data-ttu-id="39e29-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="39e29-111">Description</span></span>|<span data-ttu-id="39e29-112">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39e29-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="39e29-113">Mais informações</span><span class="sxs-lookup"><span data-stu-id="39e29-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="39e29-114">OfType</span><span class="sxs-lookup"><span data-stu-id="39e29-114">OfType</span></span>|<span data-ttu-id="39e29-115">Seleciona valores, dependendo de sua capacidade de ser convertido em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="39e29-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="39e29-116">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="39e29-116">Not applicable.</span></span>|<span data-ttu-id="39e29-117"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="39e29-117"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="39e29-118"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="39e29-118"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="39e29-119">Where</span><span class="sxs-lookup"><span data-stu-id="39e29-119">Where</span></span>|<span data-ttu-id="39e29-120">Seleciona valores com base em uma função de predicado.</span><span class="sxs-lookup"><span data-stu-id="39e29-120">Selects values that are based on a predicate function.</span></span>|`Where`|<span data-ttu-id="39e29-121"><xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="39e29-121"><xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="39e29-122"><xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="39e29-122"><xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="39e29-123">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="39e29-123">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="39e29-124">O exemplo a seguir usa o `Where` para filtrar em uma matriz essas cadeias de caracteres com um comprimento específico.</span><span class="sxs-lookup"><span data-stu-id="39e29-124">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
```vb  
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim query = From word In words   
            Where word.Length = 3   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
```  
  
## <a name="see-also"></a><span data-ttu-id="39e29-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39e29-125">See Also</span></span>  
 <span data-ttu-id="39e29-126"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="39e29-126"><xref:System.Linq></span></span>   
<span data-ttu-id="39e29-127"> [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="39e29-127"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="39e29-128"> [Onde cláusula](../../../../visual-basic/language-reference/queries/where-clause.md) </span><span class="sxs-lookup"><span data-stu-id="39e29-128"> [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md) </span></span>  
<span data-ttu-id="39e29-129"> [Como: Filtrar resultados de consulta](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md) </span><span class="sxs-lookup"><span data-stu-id="39e29-129"> [How to: Filter Query Results](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md) </span></span>  
<span data-ttu-id="39e29-130"> [Como: consultar metadados de um Assembly com reflexão (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span><span class="sxs-lookup"><span data-stu-id="39e29-130"> [How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span></span>  
<span data-ttu-id="39e29-131"> [Como: consultar arquivos com um atributo especificado ou o nome (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span><span class="sxs-lookup"><span data-stu-id="39e29-131"> [How to: Query for Files with a Specified Attribute or Name (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span></span>  
<span data-ttu-id="39e29-132"> [Como: classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span><span class="sxs-lookup"><span data-stu-id="39e29-132"> [How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span></span>
