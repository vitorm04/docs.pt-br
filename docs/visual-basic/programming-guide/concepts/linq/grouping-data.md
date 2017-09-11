---
title: Agrupando dados (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
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
ms.openlocfilehash: ce4e8f924f91eed451d3b1a02cd0bcff75589537
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="07d06-102">Agrupando dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07d06-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="07d06-103">Agrupamento refere-se a operação de colocar dados em grupos para que os elementos em cada grupo compartilham um atributo comum.</span><span class="sxs-lookup"><span data-stu-id="07d06-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="07d06-104">A ilustração a seguir mostra os resultados de uma sequência de caracteres de agrupamento.</span><span class="sxs-lookup"><span data-stu-id="07d06-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="07d06-105">A chave para cada grupo é o caractere.</span><span class="sxs-lookup"><span data-stu-id="07d06-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="07d06-106">![Operações de agrupamento LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="07d06-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="07d06-107">Os métodos de operador de consulta padrão que agrupam os elementos de dados são listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="07d06-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="07d06-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="07d06-108">Methods</span></span>  
  
|<span data-ttu-id="07d06-109">Nome do método</span><span class="sxs-lookup"><span data-stu-id="07d06-109">Method Name</span></span>|<span data-ttu-id="07d06-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="07d06-110">Description</span></span>|<span data-ttu-id="07d06-111">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07d06-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="07d06-112">Mais informações</span><span class="sxs-lookup"><span data-stu-id="07d06-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="07d06-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="07d06-113">GroupBy</span></span>|<span data-ttu-id="07d06-114">Agrupa elementos que compartilham um atributo comum.</span><span class="sxs-lookup"><span data-stu-id="07d06-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="07d06-115">Cada grupo é representado por um <xref:System.Linq.IGrouping%602>objeto.</xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="07d06-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<span data-ttu-id="07d06-116"><xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="07d06-116"><xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="07d06-117"><xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="07d06-117"><xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="07d06-118">ToLookup</span><span class="sxs-lookup"><span data-stu-id="07d06-118">ToLookup</span></span>|<span data-ttu-id="07d06-119">Insere elementos em um <xref:System.Linq.Lookup%602>(um dicionário de um-para-muitos) com base em uma função de seletor de chave.</xref:System.Linq.Lookup%602></span><span class="sxs-lookup"><span data-stu-id="07d06-119">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="07d06-120">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="07d06-120">Not applicable.</span></span>|<span data-ttu-id="07d06-121"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="07d06-121"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="07d06-122">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="07d06-122">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="07d06-123">O seguinte exemplo de código usa o `Group By` cláusula para inteiros de grupo em uma lista se elas estiverem par ou ímpar.</span><span class="sxs-lookup"><span data-stu-id="07d06-123">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07d06-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07d06-124">See Also</span></span>  
 <span data-ttu-id="07d06-125"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="07d06-125"><xref:System.Linq></span></span>   
<span data-ttu-id="07d06-126"> [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="07d06-126"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="07d06-127"> [Cláusula Group By](../../../../visual-basic/language-reference/queries/group-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="07d06-127"> [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md) </span></span>  
<span data-ttu-id="07d06-128"> [Como: agrupar arquivos por extensão (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span><span class="sxs-lookup"><span data-stu-id="07d06-128"> [How to: Group Files by Extension (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span></span>  
<span data-ttu-id="07d06-129"> [Como: dividir um arquivo em vários arquivos usando grupos (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span><span class="sxs-lookup"><span data-stu-id="07d06-129"> [How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span></span>
