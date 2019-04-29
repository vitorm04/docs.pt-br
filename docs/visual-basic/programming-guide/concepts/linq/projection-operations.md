---
title: Operações de projeção (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: e2af45f9cbbed9eb88095a30e2b77a7730740898
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766671"
---
# <a name="projection-operations-visual-basic"></a><span data-ttu-id="a2e04-102">Operações de projeção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2e04-102">Projection Operations (Visual Basic)</span></span>
<span data-ttu-id="a2e04-103">Projeção refere-se à operação de transformar um objeto em um novo formulário que geralmente consiste apenas nas propriedades que serão usadas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="a2e04-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="a2e04-104">Usando a projeção, você pode construir um novo tipo que é criado de cada objeto.</span><span class="sxs-lookup"><span data-stu-id="a2e04-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="a2e04-105">É possível projetar uma propriedade e executar uma função matemática nela.</span><span class="sxs-lookup"><span data-stu-id="a2e04-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="a2e04-106">Também é possível projetar o objeto original sem alterá-lo.</span><span class="sxs-lookup"><span data-stu-id="a2e04-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="a2e04-107">Os métodos de operador de consulta padrão que realizam a projeção estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="a2e04-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a2e04-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="a2e04-108">Methods</span></span>  
  
|<span data-ttu-id="a2e04-109">Nome do método</span><span class="sxs-lookup"><span data-stu-id="a2e04-109">Method Name</span></span>|<span data-ttu-id="a2e04-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2e04-110">Description</span></span>|<span data-ttu-id="a2e04-111">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2e04-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="a2e04-112">Mais informações</span><span class="sxs-lookup"><span data-stu-id="a2e04-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="a2e04-113">Selecionar</span><span class="sxs-lookup"><span data-stu-id="a2e04-113">Select</span></span>|<span data-ttu-id="a2e04-114">Projeta valores com base em uma função de transformação.</span><span class="sxs-lookup"><span data-stu-id="a2e04-114">Projects values that are based on a transform function.</span></span>|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a2e04-115">SelectMany</span><span class="sxs-lookup"><span data-stu-id="a2e04-115">SelectMany</span></span>|<span data-ttu-id="a2e04-116">Projeta sequências de valores baseados em uma função de transformação e os mescla em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="a2e04-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="a2e04-117">Use várias cláusulas `From`</span><span class="sxs-lookup"><span data-stu-id="a2e04-117">Use multiple `From` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="a2e04-118">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="a2e04-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="a2e04-119">Selecionar</span><span class="sxs-lookup"><span data-stu-id="a2e04-119">Select</span></span>  
 <span data-ttu-id="a2e04-120">O exemplo a seguir usa a cláusula `Select` para projetar a primeira letra de cada cadeia de caracteres em uma lista de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a2e04-120">The following example uses the `Select` clause to project the first letter from each string in a list of strings.</span></span>  
  
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
  
### <a name="selectmany"></a><span data-ttu-id="a2e04-121">SelectMany</span><span class="sxs-lookup"><span data-stu-id="a2e04-121">SelectMany</span></span>  
 <span data-ttu-id="a2e04-122">O exemplo a seguir usa vários `From` cláusulas para projetar cada palavra de cada cadeia de caracteres em uma lista de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a2e04-122">The following example uses multiple `From` clauses to project each word from each string in a list of strings.</span></span>  
  
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
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="a2e04-123">Select versus SelectMany</span><span class="sxs-lookup"><span data-stu-id="a2e04-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="a2e04-124">O trabalho de `Select()` e `SelectMany()` é produzir um valor (ou valores) de resultado dos valores de origem.</span><span class="sxs-lookup"><span data-stu-id="a2e04-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="a2e04-125">`Select()` produz um valor de resultado para cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="a2e04-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="a2e04-126">O resultado geral, portanto, é uma coleção que tem o mesmo número de elementos que a coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="a2e04-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="a2e04-127">Por outro lado, `SelectMany()` produz um único resultado geral que contém subcoleções concatenadas de cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="a2e04-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="a2e04-128">A função de transformação passada como um argumento para `SelectMany()` deve retornar uma sequência enumerável de valores para cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="a2e04-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="a2e04-129">Essas sequências enumeráveis, então, são concatenadas por `SelectMany()` para criar uma sequência grande.</span><span class="sxs-lookup"><span data-stu-id="a2e04-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="a2e04-130">As duas ilustrações a seguir mostram a diferença conceitual entre as ações desses dois métodos.</span><span class="sxs-lookup"><span data-stu-id="a2e04-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="a2e04-131">Em cada caso, presuma que a função de seletor (transformação) seleciona a matriz de flores de cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="a2e04-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="a2e04-132">A ilustração mostra como `Select()` retorna uma coleção que tem o mesmo número de elementos que a coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="a2e04-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 ![Gráfico que mostra a ação de Select&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 <span data-ttu-id="a2e04-134">Esta ilustração mostra como `SelectMany()` concatena a sequência intermediária de matrizes em um valor de resultado final que contém cada valor de cada matriz intermediária.</span><span class="sxs-lookup"><span data-stu-id="a2e04-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 ![Gráfico mostrando a ação de SelectMany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a><span data-ttu-id="a2e04-136">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="a2e04-136">Code Example</span></span>  
 <span data-ttu-id="a2e04-137">O exemplo a seguir compara o comportamento de `Select()` e de `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="a2e04-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="a2e04-138">O código cria um "buquê" de flores usando os dois primeiros itens de cada lista de nomes de flor na coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="a2e04-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="a2e04-139">Neste exemplo, o "valor único" que a função de transformação <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> usa é uma coleção de valores.</span><span class="sxs-lookup"><span data-stu-id="a2e04-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="a2e04-140">Isso requer o loop `For Each` extra para enumerar cada cadeia de caracteres em cada subsequência.</span><span class="sxs-lookup"><span data-stu-id="a2e04-140">This requires the extra `For Each` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2e04-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2e04-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="a2e04-142">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2e04-142">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="a2e04-143">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="a2e04-143">Select Clause</span></span>](../../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="a2e04-144">Como: Combinar dados com junções</span><span class="sxs-lookup"><span data-stu-id="a2e04-144">How to: Combine Data with Joins</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
- [<span data-ttu-id="a2e04-145">Como: Preencher coleções de objetos de várias fontes (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2e04-145">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="a2e04-146">Como: Retornar um resultado de consulta LINQ como um tipo específico</span><span class="sxs-lookup"><span data-stu-id="a2e04-146">How to: Return a LINQ Query Result as a Specific Type</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [<span data-ttu-id="a2e04-147">Como: Dividir um arquivo em vários arquivos usando grupos (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2e04-147">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
