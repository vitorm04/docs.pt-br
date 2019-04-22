---
title: Agrupando dados (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: c658ac5c46baec1bfa976074b78ac86d791b6515
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842043"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="1374a-102">Agrupando dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1374a-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="1374a-103">O agrupamento refere-se à operação de colocação de dados em grupos, de modo que os elementos em cada grupo compartilhem um atributo comum.</span><span class="sxs-lookup"><span data-stu-id="1374a-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="1374a-104">A ilustração a seguir mostra os resultados do agrupamento de uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1374a-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="1374a-105">A chave para cada grupo é o caractere.</span><span class="sxs-lookup"><span data-stu-id="1374a-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="1374a-106">![Operações de agrupamento LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="1374a-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="1374a-107">Os métodos do operador de consulta padrão que agrupam elementos de dados estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="1374a-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1374a-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="1374a-108">Methods</span></span>  
  
|<span data-ttu-id="1374a-109">Nome do método</span><span class="sxs-lookup"><span data-stu-id="1374a-109">Method Name</span></span>|<span data-ttu-id="1374a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="1374a-110">Description</span></span>|<span data-ttu-id="1374a-111">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1374a-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="1374a-112">Mais informações</span><span class="sxs-lookup"><span data-stu-id="1374a-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="1374a-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="1374a-113">GroupBy</span></span>|<span data-ttu-id="1374a-114">Agrupa elementos que compartilham um atributo comum.</span><span class="sxs-lookup"><span data-stu-id="1374a-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="1374a-115">Cada grupo é representado por um objeto <xref:System.Linq.IGrouping%602>.</span><span class="sxs-lookup"><span data-stu-id="1374a-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1374a-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="1374a-116">ToLookup</span></span>|<span data-ttu-id="1374a-117">Insere os elementos em um <xref:System.Linq.Lookup%602> (um dicionário one-to-many) com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="1374a-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="1374a-118">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="1374a-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="1374a-119">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="1374a-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="1374a-120">O seguinte exemplo de código usa a cláusula `Group By` para agrupar inteiros em uma lista de acordo com se eles são pares ou ímpares.</span><span class="sxs-lookup"><span data-stu-id="1374a-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers   
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a><span data-ttu-id="1374a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1374a-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="1374a-122">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1374a-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="1374a-123">Cláusula Group By</span><span class="sxs-lookup"><span data-stu-id="1374a-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="1374a-124">Como: Agrupar arquivos por extensão (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1374a-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="1374a-125">Como: Dividir um arquivo em vários arquivos usando grupos (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1374a-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
