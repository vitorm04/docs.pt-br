---
title: Operações de consulta básica
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
ms.openlocfilehash: efae72c65ad67b4a1b157b67dcc4d4d65f31f77b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266372"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="a9f3b-102">Operações de consulta básica (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9f3b-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="a9f3b-103">Este tópico fornece uma breve introdução às expressões LINQ (Language-Integrated Query) no Visual Basic e a alguns dos tipos típicos de operações que você executa em uma consulta.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-103">This topic provides a brief introduction to Language-Integrated Query (LINQ) expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="a9f3b-104">Para obter mais informações, consulte estes tópicos:</span><span class="sxs-lookup"><span data-stu-id="a9f3b-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="a9f3b-105">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a9f3b-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="a9f3b-106">Consultas</span><span class="sxs-lookup"><span data-stu-id="a9f3b-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="a9f3b-107">Instruções passo a passo: escrevendo consultas em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a9f3b-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="a9f3b-108">Especificando a Fonte de Dados (De)</span><span class="sxs-lookup"><span data-stu-id="a9f3b-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="a9f3b-109">Em uma consulta LINQ, o primeiro passo é especificar a fonte de dados que você deseja consultar.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-109">In a LINQ query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="a9f3b-110">Portanto, a `From` cláusula em uma consulta sempre vem em primeiro lugar.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="a9f3b-111">Os operadores de consulta selecionam e moldam o resultado com base no tipo da fonte.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="a9f3b-112">A `From` cláusula especifica a `customers`fonte de dados `cust`e uma variável *de intervalo.*</span><span class="sxs-lookup"><span data-stu-id="a9f3b-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="a9f3b-113">A variável de intervalo é como uma variável de iteração de loop, exceto que em uma expressão de consulta, não ocorre nenhuma iteração real.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="a9f3b-114">Quando a consulta é executada, muitas `For Each` vezes usando um loop, a variável `customers`de intervalo serve como referência a cada elemento sucessivo em .</span><span class="sxs-lookup"><span data-stu-id="a9f3b-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="a9f3b-115">Uma vez que o compilador pode inferir o tipo de `cust`, você não precisa especificá-lo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="a9f3b-116">Para exemplos de consultas escritas com e sem digitação explícita, consulte [Relações de tipo em Operações de Consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a9f3b-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="a9f3b-117">Para obter mais informações `From` sobre como usar a cláusula no Visual Basic, consulte [A partir da cláusula](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a9f3b-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="a9f3b-118">Filtrando Dados (Onde)</span><span class="sxs-lookup"><span data-stu-id="a9f3b-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="a9f3b-119">Provavelmente a operação de consulta mais comum é a aplicação de um filtro na forma de uma expressão booleana.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="a9f3b-120">A consulta então retorna apenas os elementos para os quais a expressão é verdadeira.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="a9f3b-121">Uma `Where` cláusula é usada para realizar a filtragem.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="a9f3b-122">O filtro especifica quais elementos na fonte de dados serão ressonados na seqüência resultante.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="a9f3b-123">No exemplo a seguir, apenas os clientes que têm um endereço em Londres estão incluídos.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="a9f3b-124">Você pode usar operadores `And` `Or` lógicos como e `Where` combinar expressões de filtro em uma cláusula.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="a9f3b-125">Por exemplo, para retornar apenas os clientes que são de Londres e cujo nome é Devon, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="a9f3b-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 <span data-ttu-id="a9f3b-126">Para devolver clientes de Londres ou Paris, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="a9f3b-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 <span data-ttu-id="a9f3b-127">Para obter mais informações `Where` sobre como usar a cláusula no Visual Basic, consulte [Onde cláusula](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a9f3b-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="a9f3b-128">Ordenando Dados (Ordenar Por)</span><span class="sxs-lookup"><span data-stu-id="a9f3b-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="a9f3b-129">Muitas vezes é conveniente classificar os dados devolvidos em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="a9f3b-130">A `Order By` cláusula fará com que os elementos da seqüência retornada sejam classificados em um campo ou campos especificados.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="a9f3b-131">Por exemplo, a consulta a seguir `Name` classifica os resultados com base na propriedade.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="a9f3b-132">Por `Name` ser uma seqüência, os dados retornados serão classificados alfabeticamente, de A a Z.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="a9f3b-133">Para ordenar os resultados na ordem inversa, de Z para a, use a cláusula `Order By...Descending`.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="a9f3b-134">O padrão `Ascending` é `Ascending` `Descending` quando nem nem é especificado.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="a9f3b-135">Para obter mais informações `Order By` sobre como usar a cláusula no Visual Basic, consulte [Ordem por Cláusula](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a9f3b-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="a9f3b-136">Selecionando Dados (Selecionar)</span><span class="sxs-lookup"><span data-stu-id="a9f3b-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="a9f3b-137">A `Select` cláusula especifica o formulário e o conteúdo dos elementos retornados.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="a9f3b-138">Por exemplo, você pode especificar se `Customer` seus resultados `Customer` consistirão em objetos completos, apenas uma propriedade, um subconjunto de propriedades, uma combinação de propriedades de várias fontes de dados ou algum novo tipo de resultado com base em um cálculo.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="a9f3b-139">Quando a cláusula `Select` produz algo diferente de uma cópia do elemento de origem, a operação é chamada de *projeção*.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="a9f3b-140">Para recuperar uma coleção que `Customer` consiste em objetos completos, selecione a variável de intervalo em si:</span><span class="sxs-lookup"><span data-stu-id="a9f3b-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="a9f3b-141">Se `Customer` uma instância for um objeto grande que tem muitos campos, e tudo `cust.Name`o que você deseja recuperar é o nome, você pode selecionar, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="a9f3b-142">A inferência do tipo local reconhece que isso `Customer` altera o tipo de resultado de uma coleção de objetos para uma coleção de strings.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="a9f3b-143">Para selecionar vários campos na fonte de dados, você tem duas opções:</span><span class="sxs-lookup"><span data-stu-id="a9f3b-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="a9f3b-144">Na `Select` cláusula, especifique os campos que deseja incluir no resultado.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="a9f3b-145">O compilador definirá um tipo anônimo que tem esses campos como suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="a9f3b-146">Para obter mais informações, consulte [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="a9f3b-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="a9f3b-147">Como os elementos retornados no exemplo a seguir são instâncias de um tipo anônimo, você não pode se referir ao tipo por nome em outro lugar em seu código.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="a9f3b-148">O nome designado pelo compilador para o tipo contém caracteres que não são válidos no código Visual Basic normal.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="a9f3b-149">No exemplo a seguir, os elementos da coleção que `londonCusts4` são devolvidos pela consulta em são instâncias de um tipo anônimo</span><span class="sxs-lookup"><span data-stu-id="a9f3b-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="a9f3b-150">-ou-</span><span class="sxs-lookup"><span data-stu-id="a9f3b-150">-or-</span></span>  
  
- <span data-ttu-id="a9f3b-151">Defina um tipo nomeado que contenha os campos específicos que você deseja incluir no `Select` resultado e crie e inicialize instâncias do tipo na cláusula.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="a9f3b-152">Use esta opção somente se você tiver que usar resultados individuais fora da coleção em que eles são devolvidos, ou se você tiver que passá-los como parâmetros em chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="a9f3b-153">O tipo `londonCusts5` de no exemplo a seguir é IEnumerable (Of NamePhone).</span><span class="sxs-lookup"><span data-stu-id="a9f3b-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="a9f3b-154">Para obter mais informações `Select` sobre como usar a cláusula no Visual Basic, consulte [Selecionar Cláusula](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a9f3b-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="a9f3b-155">Ingressando Dados (Ingressar e Agrupar Junções)</span><span class="sxs-lookup"><span data-stu-id="a9f3b-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="a9f3b-156">Você pode combinar mais de `From` uma fonte de dados na cláusula de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="a9f3b-157">Por exemplo, o código a seguir usa duas fontes de dados e combina implicitamente propriedades de ambas no resultado.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="a9f3b-158">A consulta seleciona alunos cujos sobrenomes começam com uma vogal.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="a9f3b-159">Você pode executar este código com a lista de alunos criados em [Como: Criar uma Lista de Itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="a9f3b-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="a9f3b-160">A `Join` palavra-chave é `INNER JOIN` equivalente a um em SQL.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="a9f3b-161">Combina duas coleções com base na correspondência de valores-chave entre os elementos das duas coleções.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="a9f3b-162">A consulta retorna todos ou parte dos elementos de coleção que têm valores-chave correspondentes.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="a9f3b-163">Por exemplo, o código a seguir duplica a ação da adesão implícita anterior.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="a9f3b-164">`Group Join`combina coleções em uma única coleção hierárquica, assim como uma `LEFT JOIN` em SQL.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="a9f3b-165">Para obter mais informações, consulte [Aderse a Cláusula](../../../../visual-basic/language-reference/queries/join-clause.md) e [Cláusula de Adesão ao Grupo](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a9f3b-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="a9f3b-166">Agrupando Dados (Agrupar Por)</span><span class="sxs-lookup"><span data-stu-id="a9f3b-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="a9f3b-167">Você pode `Group By` adicionar uma cláusula para agrupar os elementos em um resultado de consulta de acordo com um ou mais campos dos elementos.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="a9f3b-168">Por exemplo, os seguintes grupos de código são estudantes por ano de aula.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="a9f3b-169">Se você executar este código usando a lista de alunos criados em [Como: Criar uma Lista de Itens,](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)a saída da `For Each` declaração é:</span><span class="sxs-lookup"><span data-stu-id="a9f3b-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="a9f3b-170">Ano: Júnior</span><span class="sxs-lookup"><span data-stu-id="a9f3b-170">Year: Junior</span></span>  
  
 <span data-ttu-id="a9f3b-171">Tucker</span><span class="sxs-lookup"><span data-stu-id="a9f3b-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="a9f3b-172">Garcia</span><span class="sxs-lookup"><span data-stu-id="a9f3b-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="a9f3b-173">Garcia</span><span class="sxs-lookup"><span data-stu-id="a9f3b-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="a9f3b-174">Tucker</span><span class="sxs-lookup"><span data-stu-id="a9f3b-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="a9f3b-175">Ano: Sênior</span><span class="sxs-lookup"><span data-stu-id="a9f3b-175">Year: Senior</span></span>  
  
 <span data-ttu-id="a9f3b-176">Omelchenko</span><span class="sxs-lookup"><span data-stu-id="a9f3b-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="a9f3b-177">Osada</span><span class="sxs-lookup"><span data-stu-id="a9f3b-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="a9f3b-178">Fakhouri</span><span class="sxs-lookup"><span data-stu-id="a9f3b-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="a9f3b-179">Feng</span><span class="sxs-lookup"><span data-stu-id="a9f3b-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="a9f3b-180">Adams</span><span class="sxs-lookup"><span data-stu-id="a9f3b-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="a9f3b-181">Ano: Calouro</span><span class="sxs-lookup"><span data-stu-id="a9f3b-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="a9f3b-182">Mortensen</span><span class="sxs-lookup"><span data-stu-id="a9f3b-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="a9f3b-183">Garcia</span><span class="sxs-lookup"><span data-stu-id="a9f3b-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="a9f3b-184">A variação mostrada no código a seguir ordena os anos de aula e, em seguida, ordena os alunos dentro de cada ano pelo sobrenome.</span><span class="sxs-lookup"><span data-stu-id="a9f3b-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="a9f3b-185">Para obter `Group By`mais informações sobre , consulte [Grupo por Cláusula](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a9f3b-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f3b-186">Confira também</span><span class="sxs-lookup"><span data-stu-id="a9f3b-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="a9f3b-187">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a9f3b-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="a9f3b-188">Consultas</span><span class="sxs-lookup"><span data-stu-id="a9f3b-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="a9f3b-189">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9f3b-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="a9f3b-190">Linq</span><span class="sxs-lookup"><span data-stu-id="a9f3b-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
