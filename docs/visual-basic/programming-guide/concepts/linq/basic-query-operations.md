---
title: Operações de consulta básica (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: ed5ed56366911c3676c4413711207ac0a8f85765
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826191"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="18806-102">Operações de consulta básica (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18806-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="18806-103">Este tópico fornece uma breve introdução ao [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressões no Visual Basic e para alguns dos tipos típicos de operações que podem ser executadas em uma consulta.</span><span class="sxs-lookup"><span data-stu-id="18806-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="18806-104">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="18806-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="18806-105">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18806-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="18806-106">Consultas</span><span class="sxs-lookup"><span data-stu-id="18806-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="18806-107">Passo a passo: Escrevendo consultas em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18806-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="18806-108">Especificando a Fonte de Dados (De)</span><span class="sxs-lookup"><span data-stu-id="18806-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="18806-109">Em um [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consulta, a primeira etapa é especificar a fonte de dados que você deseja consultar.</span><span class="sxs-lookup"><span data-stu-id="18806-109">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="18806-110">Portanto, o `From` cláusula em uma consulta sempre vem em primeiro lugar.</span><span class="sxs-lookup"><span data-stu-id="18806-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="18806-111">Operadores de consulta selecionam e formatar o resultado com base no tipo da fonte.</span><span class="sxs-lookup"><span data-stu-id="18806-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="18806-112">O `From` cláusula Especifica a fonte de dados `customers`e um *variável de intervalo*, `cust`.</span><span class="sxs-lookup"><span data-stu-id="18806-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="18806-113">A variável de intervalo é como uma variável de iteração do loop, exceto que em uma expressão de consulta, nenhuma iteração real ocorre.</span><span class="sxs-lookup"><span data-stu-id="18806-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="18806-114">Quando a consulta é executada, geralmente usando um `For Each` loop, a variável de intervalo serve como uma referência para cada elemento sucessivo em `customers`.</span><span class="sxs-lookup"><span data-stu-id="18806-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="18806-115">Uma vez que o compilador pode inferir o tipo de `cust`, você não precisa especificá-lo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="18806-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="18806-116">Para obter exemplos de consultas escritas com e sem tipagem explícita, consulte [relacionamentos de tipo em operações de consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="18806-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="18806-117">Para obter mais informações sobre como usar o `From` cláusula no Visual Basic, consulte [cláusula From](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="18806-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="18806-118">Filtrando Dados (Onde)</span><span class="sxs-lookup"><span data-stu-id="18806-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="18806-119">Provavelmente, a operação de consulta mais comuns é aplicar um filtro na forma de uma expressão booliana.</span><span class="sxs-lookup"><span data-stu-id="18806-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="18806-120">A consulta, em seguida, retorna apenas os elementos para o qual a expressão for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="18806-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="18806-121">Um `Where` cláusula é usada para executar a filtragem.</span><span class="sxs-lookup"><span data-stu-id="18806-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="18806-122">O filtro especifica quais elementos na fonte de dados para incluir na sequência resultante.</span><span class="sxs-lookup"><span data-stu-id="18806-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="18806-123">No exemplo a seguir, são incluídos somente aqueles clientes que têm um endereço em Londres.</span><span class="sxs-lookup"><span data-stu-id="18806-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="18806-124">Você pode usar operadores lógicos, como `And` e `Or` combinar expressões de filtro em um `Where` cláusula.</span><span class="sxs-lookup"><span data-stu-id="18806-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="18806-125">Por exemplo, para retornar somente os clientes que são de Londres e cujo nome é Devon, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="18806-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="18806-126">Para retornar os clientes de Londres ou Paris, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="18806-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="18806-127">Para obter mais informações sobre como usar o `Where` cláusula no Visual Basic, consulte [cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="18806-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="18806-128">Ordenando Dados (Ordenar Por)</span><span class="sxs-lookup"><span data-stu-id="18806-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="18806-129">Muitas vezes é conveniente classificar dados retornados em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="18806-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="18806-130">O `Order By` cláusula fará com que os elementos na sequência retornada deve ser classificada em um campo ou campos especificados.</span><span class="sxs-lookup"><span data-stu-id="18806-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="18806-131">Por exemplo, a consulta a seguir classifica os resultados com base no `Name` propriedade.</span><span class="sxs-lookup"><span data-stu-id="18806-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="18806-132">Porque `Name` é uma cadeia de caracteres, os dados retornados serão classificados em ordem alfabética, de À Z.</span><span class="sxs-lookup"><span data-stu-id="18806-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="18806-133">Para ordenar os resultados na ordem inversa, de Z para a, use a cláusula `Order By...Descending`.</span><span class="sxs-lookup"><span data-stu-id="18806-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="18806-134">O padrão é `Ascending` quando nenhuma `Ascending` nem `Descending` for especificado.</span><span class="sxs-lookup"><span data-stu-id="18806-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="18806-135">Para obter mais informações sobre como usar o `Order By` cláusula no Visual Basic, consulte [cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="18806-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="18806-136">Selecionando Dados (Selecionar)</span><span class="sxs-lookup"><span data-stu-id="18806-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="18806-137">O `Select` cláusula Especifica o formato e o conteúdo de elementos retornados.</span><span class="sxs-lookup"><span data-stu-id="18806-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="18806-138">Por exemplo, você pode especificar se os resultados consistirão de concluída `Customer` objetos, apenas um `Customer` propriedade, um subconjunto de propriedades, uma combinação de propriedades de várias fontes de dados ou algum novo tipo de resultado com base em um cálculo.</span><span class="sxs-lookup"><span data-stu-id="18806-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="18806-139">Quando a cláusula `Select` produz algo diferente de uma cópia do elemento de origem, a operação é chamada de *projeção*.</span><span class="sxs-lookup"><span data-stu-id="18806-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="18806-140">Para recuperar uma coleção que consiste em completa `Customer` objetos, selecione a variável de intervalo:</span><span class="sxs-lookup"><span data-stu-id="18806-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="18806-141">Se um `Customer` instância é um objeto grande com muitos campos, e tudo o que você deseja recuperar é o nome, você pode selecionar `cust.Name`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="18806-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="18806-142">Inferência de tipo local reconhece que isso altera o tipo de resultado de uma coleção de `Customer` objetos a uma coleção de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="18806-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="18806-143">Para selecionar vários campos da fonte de dados, você tem duas opções:</span><span class="sxs-lookup"><span data-stu-id="18806-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
-   <span data-ttu-id="18806-144">No `Select` cláusula, especifique os campos que você deseja incluir no resultado.</span><span class="sxs-lookup"><span data-stu-id="18806-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="18806-145">O compilador definirá um tipo anônimo que tem esses campos como suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="18806-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="18806-146">Para obter mais informações, consulte [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="18806-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="18806-147">Como os elementos retornados no exemplo a seguir são instâncias de um tipo anônimo, você não pode se referir ao tipo por nome em outro lugar no seu código.</span><span class="sxs-lookup"><span data-stu-id="18806-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="18806-148">O nome para o tipo designado pelo compilador contém caracteres que não são válidos no código normal do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="18806-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="18806-149">No exemplo a seguir, os elementos da coleção que é retornado pela consulta em `londonCusts4` são instâncias de um tipo anônimo</span><span class="sxs-lookup"><span data-stu-id="18806-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="18806-150">- ou -</span><span class="sxs-lookup"><span data-stu-id="18806-150">-or-</span></span>  
  
-   <span data-ttu-id="18806-151">Definir um tipo nomeado que contém os campos específicos que você deseja incluir no resultado, criar e inicializar instâncias do tipo no `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="18806-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="18806-152">Use essa opção somente se você precisa usar os resultados individuais fora da coleção na qual eles são retornados, ou se você tiver passá-los como parâmetros nas chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="18806-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="18806-153">O tipo de `londonCusts5` no exemplo a seguir é IEnumerable (Of NamePhone).</span><span class="sxs-lookup"><span data-stu-id="18806-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="18806-154">Para obter mais informações sobre como usar o `Select` cláusula no Visual Basic, consulte [cláusula Select](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="18806-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="18806-155">Ingressando Dados (Ingressar e Agrupar Junções)</span><span class="sxs-lookup"><span data-stu-id="18806-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="18806-156">Você pode combinar mais de uma fonte de dados no `From` cláusula de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="18806-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="18806-157">Por exemplo, o código a seguir usa duas fontes de dados e implicitamente combina as propriedades de ambos no resultado.</span><span class="sxs-lookup"><span data-stu-id="18806-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="18806-158">A consulta seleciona os alunos cujos sobrenomes começam com uma vogal.</span><span class="sxs-lookup"><span data-stu-id="18806-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
>  <span data-ttu-id="18806-159">Você pode executar esse código com a lista de alunos criado no [como: Criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="18806-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="18806-160">O `Join` palavra-chave é equivalente a um `INNER JOIN` no SQL.</span><span class="sxs-lookup"><span data-stu-id="18806-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="18806-161">Ele combina duas coleções com base nos valores de chave de correspondência entre os elementos em duas coleções.</span><span class="sxs-lookup"><span data-stu-id="18806-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="18806-162">A consulta retorna todo ou parte dos elementos da coleção que têm valores de chave de correspondência.</span><span class="sxs-lookup"><span data-stu-id="18806-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="18806-163">Por exemplo, o código a seguir duplica a ação da junção implícita anterior.</span><span class="sxs-lookup"><span data-stu-id="18806-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="18806-164">`Group Join` combina coleções em uma única coleção hierárquica, assim como um `LEFT JOIN` no SQL.</span><span class="sxs-lookup"><span data-stu-id="18806-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="18806-165">Para obter mais informações, consulte [cláusula Join](../../../../visual-basic/language-reference/queries/join-clause.md) e [cláusula de junção de grupo](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="18806-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="18806-166">Agrupando Dados (Agrupar Por)</span><span class="sxs-lookup"><span data-stu-id="18806-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="18806-167">Você pode adicionar um `Group By` cláusula para agrupar os elementos em um resultado de consulta acordo com um ou mais campos dos elementos.</span><span class="sxs-lookup"><span data-stu-id="18806-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="18806-168">Por exemplo, o código a seguir agrupa os alunos por ano de classe.</span><span class="sxs-lookup"><span data-stu-id="18806-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="18806-169">Se você executar esse código usando a lista de alunos criado no [como: Criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), a saída do `For Each` instrução é:</span><span class="sxs-lookup"><span data-stu-id="18806-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="18806-170">Ano: Júnior</span><span class="sxs-lookup"><span data-stu-id="18806-170">Year: Junior</span></span>  
  
 <span data-ttu-id="18806-171">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="18806-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="18806-172">Garcia, Hugo</span><span class="sxs-lookup"><span data-stu-id="18806-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="18806-173">Garcia, Debra</span><span class="sxs-lookup"><span data-stu-id="18806-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="18806-174">Tucker, Lance</span><span class="sxs-lookup"><span data-stu-id="18806-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="18806-175">Ano: Sênior</span><span class="sxs-lookup"><span data-stu-id="18806-175">Year: Senior</span></span>  
  
 <span data-ttu-id="18806-176">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="18806-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="18806-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="18806-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="18806-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="18806-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="18806-179">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="18806-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="18806-180">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="18806-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="18806-181">Ano: Freshman</span><span class="sxs-lookup"><span data-stu-id="18806-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="18806-182">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="18806-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="18806-183">Garcia, Cesar</span><span class="sxs-lookup"><span data-stu-id="18806-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="18806-184">A variação mostrada no código a seguir ordena os anos de classe e, em seguida, ordena os alunos em cada ano por sobrenome.</span><span class="sxs-lookup"><span data-stu-id="18806-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="18806-185">Para obter mais informações sobre `Group By`, consulte [por cláusula Group](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="18806-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18806-186">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18806-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="18806-187">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18806-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="18806-188">Consultas</span><span class="sxs-lookup"><span data-stu-id="18806-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="18806-189">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18806-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="18806-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="18806-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
