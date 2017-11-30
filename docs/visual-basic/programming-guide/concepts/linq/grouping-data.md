---
title: Agrupando dados (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5f2e5c4c4713f1056f1eb2243f27e5acf0494542
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="47a00-102">Agrupando dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47a00-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="47a00-103">O agrupamento refere-se à operação de colocação de dados em grupos, de modo que os elementos em cada grupo compartilhem um atributo comum.</span><span class="sxs-lookup"><span data-stu-id="47a00-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="47a00-104">A ilustração a seguir mostra os resultados do agrupamento de uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="47a00-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="47a00-105">A chave para cada grupo é o caractere.</span><span class="sxs-lookup"><span data-stu-id="47a00-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="47a00-106">![Operações de agrupamento LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="47a00-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="47a00-107">Os métodos do operador de consulta padrão que agrupam elementos de dados estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="47a00-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="47a00-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="47a00-108">Methods</span></span>  
  
|<span data-ttu-id="47a00-109">Nome do método</span><span class="sxs-lookup"><span data-stu-id="47a00-109">Method Name</span></span>|<span data-ttu-id="47a00-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="47a00-110">Description</span></span>|<span data-ttu-id="47a00-111">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47a00-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="47a00-112">Mais informações</span><span class="sxs-lookup"><span data-stu-id="47a00-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="47a00-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="47a00-113">GroupBy</span></span>|<span data-ttu-id="47a00-114">Agrupa elementos que compartilham um atributo comum.</span><span class="sxs-lookup"><span data-stu-id="47a00-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="47a00-115">Cada grupo é representado por um objeto <xref:System.Linq.IGrouping%602>.</span><span class="sxs-lookup"><span data-stu-id="47a00-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="47a00-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="47a00-116">ToLookup</span></span>|<span data-ttu-id="47a00-117">Insere os elementos em um <xref:System.Linq.Lookup%602> (um dicionário one-to-many) com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="47a00-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="47a00-118">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="47a00-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="47a00-119">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="47a00-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="47a00-120">O seguinte exemplo de código usa a cláusula `Group By` para agrupar inteiros em uma lista de acordo com se eles são pares ou ímpares.</span><span class="sxs-lookup"><span data-stu-id="47a00-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="47a00-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47a00-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="47a00-122">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47a00-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="47a00-123">Cláusula Group By</span><span class="sxs-lookup"><span data-stu-id="47a00-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)  
 [<span data-ttu-id="47a00-124">Como: agrupar arquivos por extensão (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47a00-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 [<span data-ttu-id="47a00-125">Como: dividir um arquivo em vários arquivos usando grupos (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47a00-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
