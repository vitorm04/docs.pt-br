---
title: Filtragem de dados (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: d3f44d0b6478103a10fb731988aeebc005cde82e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="232eb-102">Filtragem de dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="232eb-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="232eb-103">A filtragem é a operação de restringir o conjunto de resultados de forma que ele contenha apenas os elementos correspondentes a uma condição especificada.</span><span class="sxs-lookup"><span data-stu-id="232eb-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="232eb-104">Ela também é conhecida como seleção.</span><span class="sxs-lookup"><span data-stu-id="232eb-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="232eb-105">A ilustração a seguir mostra os resultados da filtragem de uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="232eb-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="232eb-106">O predicado para a operação de filtragem especifica que o caractere deve ser "A".</span><span class="sxs-lookup"><span data-stu-id="232eb-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="232eb-107">![Operação de filtragem no LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="232eb-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="232eb-108">Os métodos de operador de consulta padrão que realizam a seleção estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="232eb-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="232eb-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="232eb-109">Methods</span></span>  
  
|<span data-ttu-id="232eb-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="232eb-110">Method Name</span></span>|<span data-ttu-id="232eb-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="232eb-111">Description</span></span>|<span data-ttu-id="232eb-112">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="232eb-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="232eb-113">Mais informações</span><span class="sxs-lookup"><span data-stu-id="232eb-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="232eb-114">OfType</span><span class="sxs-lookup"><span data-stu-id="232eb-114">OfType</span></span>|<span data-ttu-id="232eb-115">Seleciona valores, dependendo da capacidade de serem convertidos em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="232eb-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="232eb-116">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="232eb-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="232eb-117">Where</span><span class="sxs-lookup"><span data-stu-id="232eb-117">Where</span></span>|<span data-ttu-id="232eb-118">Seleciona valores com base em uma função de predicado.</span><span class="sxs-lookup"><span data-stu-id="232eb-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="232eb-119">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="232eb-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="232eb-120">O exemplo a seguir usa o `Where` para essas cadeias de caracteres que têm um período específico de filtro de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="232eb-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="232eb-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="232eb-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="232eb-122">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="232eb-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="232eb-123">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="232eb-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="232eb-124">Como filtrar resultados de consulta</span><span class="sxs-lookup"><span data-stu-id="232eb-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)  
 [<span data-ttu-id="232eb-125">Como: consultar metadados de um Assembly com reflexão (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="232eb-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 [<span data-ttu-id="232eb-126">Como: consultar arquivos com um atributo especificado ou o nome (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="232eb-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 [<span data-ttu-id="232eb-127">Como: classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="232eb-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
