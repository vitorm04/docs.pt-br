---
title: "Operações de projeção (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
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
ms.openlocfilehash: aac5cf69e6c3f4041a4302e8d606ca8dfddbc8a2
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="projection-operations-visual-basic"></a><span data-ttu-id="263e0-102">Operações de projeção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="263e0-102">Projection Operations (Visual Basic)</span></span>
<span data-ttu-id="263e0-103">Projeção refere-se a operação de transformar um objeto em um novo formulário que geralmente consiste apenas as propriedades que serão usadas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="263e0-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="263e0-104">Usando a projeção, você pode criar um novo tipo que é criado a partir de cada objeto.</span><span class="sxs-lookup"><span data-stu-id="263e0-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="263e0-105">Você pode projetar uma propriedade e executar uma função matemática nele.</span><span class="sxs-lookup"><span data-stu-id="263e0-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="263e0-106">Você também pode projetar o objeto original sem alterá-lo.</span><span class="sxs-lookup"><span data-stu-id="263e0-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="263e0-107">Os métodos de operador de consulta padrão que executam projeção são listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="263e0-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="263e0-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="263e0-108">Methods</span></span>  
  
|<span data-ttu-id="263e0-109">Nome do método</span><span class="sxs-lookup"><span data-stu-id="263e0-109">Method Name</span></span>|<span data-ttu-id="263e0-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="263e0-110">Description</span></span>|<span data-ttu-id="263e0-111">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="263e0-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="263e0-112">Mais informações</span><span class="sxs-lookup"><span data-stu-id="263e0-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="263e0-113">Selecionar</span><span class="sxs-lookup"><span data-stu-id="263e0-113">Select</span></span>|<span data-ttu-id="263e0-114">Valores de projetos com base em uma função de transformação.</span><span class="sxs-lookup"><span data-stu-id="263e0-114">Projects values that are based on a transform function.</span></span>|`Select`|<span data-ttu-id="263e0-115"><xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="263e0-115"><xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="263e0-116"><xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="263e0-116"><xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="263e0-117">SelectMany</span><span class="sxs-lookup"><span data-stu-id="263e0-117">SelectMany</span></span>|<span data-ttu-id="263e0-118">Sequências de projetos de valores que se baseiam em uma função de transformação e, em seguida, nivela-los em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="263e0-118">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="263e0-119">Usar várias `From` cláusulas</span><span class="sxs-lookup"><span data-stu-id="263e0-119">Use multiple `From` clauses</span></span>|<span data-ttu-id="263e0-120"><xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="263e0-120"><xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="263e0-121"><xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="263e0-121"><xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="263e0-122">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="263e0-122">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="263e0-123">Selecionar</span><span class="sxs-lookup"><span data-stu-id="263e0-123">Select</span></span>  
 <span data-ttu-id="263e0-124">O exemplo a seguir usa o `Select` cláusula para projetar a primeira letra de cada cadeia de caracteres em uma lista de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="263e0-124">The following example uses the `Select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```vb  
Dim words = New List(Of String) From {"an", "apple", "a", "day"}  
  
Dim query = From word In words   
            Select word.Substring(0, 1)  
  
Dim sb As New System.Text.StringBuilder()  
For Each letter As String In query  
    sb.AppendLine(letter)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' a  
' a  
' a  
' d  
```  
  
### <a name="selectmany"></a><span data-ttu-id="263e0-125">SelectMany</span><span class="sxs-lookup"><span data-stu-id="263e0-125">SelectMany</span></span>  
 <span data-ttu-id="263e0-126">O exemplo a seguir usa vários `From` cláusulas para cada palavra de cada cadeia de caracteres em uma lista de cadeias de caracteres de projeto.</span><span class="sxs-lookup"><span data-stu-id="263e0-126">The following example uses multiple `From` clauses to project each word from each string in a list of strings.</span></span>  
  
```vb  
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}  
  
Dim query = From phrase In phrases   
            From word In phrase.Split(" "c)   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' an  
' apple  
' a  
' day  
' the  
' quick  
' brown  
' fox  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="263e0-127">Selecione versus SelectMany</span><span class="sxs-lookup"><span data-stu-id="263e0-127">Select versus SelectMany</span></span>  
 <span data-ttu-id="263e0-128">O trabalho de ambos `Select()` e `SelectMany()` é produzir um resultado (ou valores) de valores de origem.</span><span class="sxs-lookup"><span data-stu-id="263e0-128">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="263e0-129">`Select()`produz um valor de resultado para cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="263e0-129">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="263e0-130">O resultado geral, portanto, é uma coleção que tem o mesmo número de elementos que a coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="263e0-130">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="263e0-131">Por outro lado, `SelectMany()` produz um único resultado geral que contém subcoleções concatenadas de cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="263e0-131">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="263e0-132">A função de transformação que é passada como um argumento para `SelectMany()` deve retornar uma sequência enumerável de valores para cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="263e0-132">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="263e0-133">Essas sequências enumeráveis depois são concatenadas por `SelectMany()` para criar uma sequência grande.</span><span class="sxs-lookup"><span data-stu-id="263e0-133">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="263e0-134">As ilustrações a seguir mostram a diferença conceitual entre as ações desses dois métodos.</span><span class="sxs-lookup"><span data-stu-id="263e0-134">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="263e0-135">Em cada caso, suponha que a função de seletor (transformação) seleciona a matriz de flores de cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="263e0-135">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="263e0-136">Esta ilustração mostra como `Select()` retorna uma coleção que tem o mesmo número de elementos como a coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="263e0-136">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 <span data-ttu-id="263e0-137">![Ilustração conceitual da ação de Select ()](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span><span class="sxs-lookup"><span data-stu-id="263e0-137">![Conceptual illustration of the action of Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span></span>  
  
 <span data-ttu-id="263e0-138">Esta ilustração mostra como `SelectMany()` concatena a sequência intermediária de matrizes em um valor de resultado final que contém cada valor de cada matriz intermediário.</span><span class="sxs-lookup"><span data-stu-id="263e0-138">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 <span data-ttu-id="263e0-139">![Gráfico mostrando a ação de SelectMany (). ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span><span class="sxs-lookup"><span data-stu-id="263e0-139">![Graphic showing the action of SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span></span>  
  
### <a name="code-example"></a><span data-ttu-id="263e0-140">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="263e0-140">Code Example</span></span>  
 <span data-ttu-id="263e0-141">O exemplo a seguir compara o comportamento de `Select()` e `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="263e0-141">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="263e0-142">O código cria um "Buquê" de flores executando os primeiros dois itens de cada lista de nomes da flor na coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="263e0-142">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="263e0-143">Neste exemplo, o "valor único" que a função de transformação <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>usa é uma coleção de valores.</xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29></span><span class="sxs-lookup"><span data-stu-id="263e0-143">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="263e0-144">Isso requer o extra `For Each` loop para enumerar cada cadeia de caracteres em cada sequência subpropriedades.</span><span class="sxs-lookup"><span data-stu-id="263e0-144">This requires the extra `For Each` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```vb  
Class Bouquet  
    Public Flowers As List(Of String)  
End Class  
  
Sub SelectVsSelectMany()  
    Dim bouquets = New List(Of Bouquet) From {   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}  
  
    Dim output As New System.Text.StringBuilder  
  
    ' Select()  
    Dim query1 = bouquets.Select(Function(b) b.Flowers)  
  
    output.AppendLine("Using Select():")  
    For Each flowerList In query1  
        For Each str As String In flowerList  
            output.AppendLine(str)  
        Next  
    Next  
  
    ' SelectMany()  
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)  
  
    output.AppendLine(vbCrLf & "Using SelectMany():")  
    For Each str As String In query2  
        output.AppendLine(str)  
    Next  
  
    ' Display the output  
    MsgBox(output.ToString())  
  
    ' This code produces the following output:  
    '  
    ' Using Select():  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
    ' Using SelectMany()  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="263e0-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="263e0-145">See Also</span></span>  
 <span data-ttu-id="263e0-146"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="263e0-146"><xref:System.Linq></span></span>   
<span data-ttu-id="263e0-147"> [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="263e0-147"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="263e0-148"> [Cláusula Select](../../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="263e0-148"> [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="263e0-149"> [Como: combinar dados com junções](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md) </span><span class="sxs-lookup"><span data-stu-id="263e0-149"> [How to: Combine Data with Joins](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md) </span></span>  
<span data-ttu-id="263e0-150"> [Como: preencher coleções de objetos de várias fontes (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md) </span><span class="sxs-lookup"><span data-stu-id="263e0-150"> [How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md) </span></span>  
<span data-ttu-id="263e0-151"> [Como: retornar um resultado de consulta LINQ como um tipo específico](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md) </span><span class="sxs-lookup"><span data-stu-id="263e0-151"> [How to: Return a LINQ Query Result as a Specific Type](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md) </span></span>  
<span data-ttu-id="263e0-152"> [Como: dividir um arquivo em vários arquivos usando grupos (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span><span class="sxs-lookup"><span data-stu-id="263e0-152"> [How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span></span>
