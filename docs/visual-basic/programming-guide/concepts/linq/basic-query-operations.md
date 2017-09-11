---
title: "Operações de consulta básica (Visual Basic) | Documentos do Microsoft"
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
caps.latest.revision: 37
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1ced446d6646bd26b9169f5894138e12a38efde7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="66463-102">Operações de consulta básica (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66463-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="66463-103">Este tópico fornece uma breve introdução a [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressões no Visual Basic e alguns dos tipos típicos de operações que podem ser executadas em uma consulta.</span><span class="sxs-lookup"><span data-stu-id="66463-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="66463-104">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="66463-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="66463-105">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66463-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="66463-106">Consultas</span><span class="sxs-lookup"><span data-stu-id="66463-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [<span data-ttu-id="66463-107">Passo a passo: Escrevendo consultas em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66463-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="66463-108">Especificando a Fonte de Dados (De)</span><span class="sxs-lookup"><span data-stu-id="66463-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="66463-109">Em um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta, a primeira etapa é especificar a fonte de dados que você deseja consultar.</span><span class="sxs-lookup"><span data-stu-id="66463-109">In a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="66463-110">Portanto, o `From` cláusula em uma consulta sempre vem em primeiro lugar.</span><span class="sxs-lookup"><span data-stu-id="66463-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="66463-111">Operadores de consulta selecionam e formatar o resultado com base no tipo de origem.</span><span class="sxs-lookup"><span data-stu-id="66463-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 <span data-ttu-id="66463-112">[!code-vb[VbLINQBasicOps n º&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="66463-112">[!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]</span></span>  
  
 <span data-ttu-id="66463-113">O `From` cláusula Especifica a fonte de dados, `customers`e um *variável de intervalo*, `cust`.</span><span class="sxs-lookup"><span data-stu-id="66463-113">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="66463-114">A variável de intervalo é como uma variável de iteração do loop, exceto que em uma expressão de consulta, nenhuma iteração real ocorre.</span><span class="sxs-lookup"><span data-stu-id="66463-114">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="66463-115">Quando a consulta é executada, geralmente usando um `For Each` loop, a variável de intervalo serve como uma referência para cada elemento sucessivo `customers`.</span><span class="sxs-lookup"><span data-stu-id="66463-115">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="66463-116">Porque o compilador pode inferir o tipo de `cust`, você não precisa especificá-lo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="66463-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="66463-117">Para obter exemplos de consultas escritas com e sem uma digitação explícita, consulte [relacionamentos de tipo em operações de consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="66463-117">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="66463-118">Para obter mais informações sobre como usar o `From` cláusula no Visual Basic, consulte [cláusula From](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="66463-118">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="66463-119">Filtrando Dados (Onde)</span><span class="sxs-lookup"><span data-stu-id="66463-119">Filtering Data (Where)</span></span>  
 <span data-ttu-id="66463-120">Provavelmente, a operação de consulta mais comuns é aplicar um filtro na forma de uma expressão booleana.</span><span class="sxs-lookup"><span data-stu-id="66463-120">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="66463-121">A consulta retorna apenas os elementos para o qual a expressão for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="66463-121">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="66463-122">Um `Where` cláusula é usada para executar a filtragem.</span><span class="sxs-lookup"><span data-stu-id="66463-122">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="66463-123">O filtro especifica quais elementos na fonte de dados para incluir na sequência resultante.</span><span class="sxs-lookup"><span data-stu-id="66463-123">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="66463-124">No exemplo a seguir, estão incluídos somente aqueles clientes que têm um endereço em Londres.</span><span class="sxs-lookup"><span data-stu-id="66463-124">In the following example, only those customers who have an address in London are included.</span></span>  
  
 <span data-ttu-id="66463-125">[!code-vb[VbLINQBasicOps n º&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="66463-125">[!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]</span></span>  
  
 <span data-ttu-id="66463-126">Você pode usar operadores lógicos como `And` e `Or` para combinar expressões de filtro em um `Where` cláusula.</span><span class="sxs-lookup"><span data-stu-id="66463-126">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="66463-127">Por exemplo, para retornar somente os clientes que são de Londres e cujo nome é Juliana PAEs, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="66463-127">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="66463-128">Para retornar os clientes de Londres ou Paris, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="66463-128">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="66463-129">Para obter mais informações sobre como usar o `Where` cláusula no Visual Basic, consulte [cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="66463-129">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="66463-130">Ordenando Dados (Ordenar Por)</span><span class="sxs-lookup"><span data-stu-id="66463-130">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="66463-131">Muitas vezes é conveniente classificar dados retornados em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="66463-131">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="66463-132">O `Order By` cláusula fará com que os elementos na sequência retornada seja classificada em um campo ou campos especificados.</span><span class="sxs-lookup"><span data-stu-id="66463-132">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="66463-133">Por exemplo, a consulta a seguir classifica os resultados com base no `Name` propriedade.</span><span class="sxs-lookup"><span data-stu-id="66463-133">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="66463-134">Porque `Name` é uma cadeia de caracteres, os dados retornados serão classificados em ordem alfabética, de À Z.</span><span class="sxs-lookup"><span data-stu-id="66463-134">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 <span data-ttu-id="66463-135">[!code-vb[VbLINQBasicOps n º&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="66463-135">[!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]</span></span>  
  
 <span data-ttu-id="66463-136">Para ordenar os resultados na ordem inversa, de Z a, use o `Order By...Descending` cláusula.</span><span class="sxs-lookup"><span data-stu-id="66463-136">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="66463-137">O padrão é `Ascending` quando nenhuma `Ascending` nem `Descending` for especificado.</span><span class="sxs-lookup"><span data-stu-id="66463-137">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="66463-138">Para obter mais informações sobre como usar o `Order By` cláusula no Visual Basic, consulte [cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="66463-138">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="66463-139">Selecionando Dados (Selecionar)</span><span class="sxs-lookup"><span data-stu-id="66463-139">Selecting Data (Select)</span></span>  
 <span data-ttu-id="66463-140">O `Select` cláusula Especifica o formato e conteúdo de elementos retornados.</span><span class="sxs-lookup"><span data-stu-id="66463-140">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="66463-141">Por exemplo, você pode especificar se os resultados consistirá em completa `Customer` objetos, apenas um `Customer` propriedade, um subconjunto de propriedades, uma combinação das propriedades de várias fontes de dados ou algum novo tipo de resultado com base em um cálculo.</span><span class="sxs-lookup"><span data-stu-id="66463-141">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="66463-142">Quando o `Select` cláusula produz algo diferente de uma cópia do elemento de origem, a operação é chamada uma *projeção*.</span><span class="sxs-lookup"><span data-stu-id="66463-142">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="66463-143">Para recuperar uma coleção que consiste em completa `Customer` objetos, selecione a variável de intervalo:</span><span class="sxs-lookup"><span data-stu-id="66463-143">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 <span data-ttu-id="66463-144">[!code-vb[VbLINQBasicOps n º&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="66463-144">[!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]</span></span>  
  
 <span data-ttu-id="66463-145">Se um `Customer` instância é um objeto grande com muitos campos, e tudo o que você deseja recuperar é o nome, você pode selecionar `cust.Name`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="66463-145">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="66463-146">Inferência de tipo local reconhece que isso altera o tipo de resultado de uma coleção de `Customer` objetos a uma coleção de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="66463-146">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 <span data-ttu-id="66463-147">[!code-vb[VbLINQBasicOps n º&5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="66463-147">[!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]</span></span>  
  
 <span data-ttu-id="66463-148">Para selecionar vários campos da fonte de dados, você tem duas opções:</span><span class="sxs-lookup"><span data-stu-id="66463-148">To select multiple fields from the data source, you have two choices:</span></span>  
  
-   <span data-ttu-id="66463-149">No `Select` cláusula, especifique os campos que deseja incluir no resultado.</span><span class="sxs-lookup"><span data-stu-id="66463-149">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="66463-150">O compilador definirá um tipo anônimo com esses campos como suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="66463-150">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="66463-151">Para obter mais informações, consulte [tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="66463-151">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="66463-152">Como os elementos retornados no exemplo a seguir são instâncias de um tipo anônimo, não faz referência a tipo por nome em outro lugar no seu código.</span><span class="sxs-lookup"><span data-stu-id="66463-152">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="66463-153">O nome do tipo designado pelo compilador contém caracteres que não são válidos no código do Visual Basic normal.</span><span class="sxs-lookup"><span data-stu-id="66463-153">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="66463-154">No exemplo a seguir, os elementos da coleção que é retornado pela consulta em `londonCusts4` são instâncias de um tipo anônimo</span><span class="sxs-lookup"><span data-stu-id="66463-154">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     <span data-ttu-id="66463-155">[!code-vb[VbLINQBasicOps n º&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="66463-155">[!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]</span></span>  
  
     <span data-ttu-id="66463-156">-ou-</span><span class="sxs-lookup"><span data-stu-id="66463-156">-or-</span></span>  
  
-   <span data-ttu-id="66463-157">Definir um tipo nomeado que contém os campos específicos que você deseja incluir no resultado e criar e inicializar instâncias do tipo de `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="66463-157">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="66463-158">Use esta opção somente se você precisa usar resultados individuais fora da coleção na qual eles são retornados ou se você tiver para passá-las como parâmetros em chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="66463-158">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="66463-159">O tipo de `londonCusts5` no exemplo a seguir é IEnumerable (Of NamePhone).</span><span class="sxs-lookup"><span data-stu-id="66463-159">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     <span data-ttu-id="66463-160">[!code-vb[VbLINQBasicOps&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="66463-160">[!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]</span></span>  
  
     <span data-ttu-id="66463-161">[!code-vb[VbLINQBasicOps n º&8;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="66463-161">[!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]</span></span>  
  
 <span data-ttu-id="66463-162">Para obter mais informações sobre como usar o `Select` cláusula no Visual Basic, consulte [cláusula Select](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="66463-162">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="66463-163">Ingressando Dados (Ingressar e Agrupar Junções)</span><span class="sxs-lookup"><span data-stu-id="66463-163">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="66463-164">Você pode combinar mais de uma fonte de dados de `From` cláusula de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="66463-164">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="66463-165">Por exemplo, o código a seguir usa duas fontes de dados e implicitamente combina propriedades de ambos no resultado.</span><span class="sxs-lookup"><span data-stu-id="66463-165">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="66463-166">A consulta seleciona os alunos cujos sobrenomes começam com um sinal de vogal.</span><span class="sxs-lookup"><span data-stu-id="66463-166">The query selects students whose last names start with a vowel.</span></span>  
  
 <span data-ttu-id="66463-167">[!code-vb[VbLINQBasicOps n º&9;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="66463-167">[!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66463-168">Você pode executar esse código com a lista de alunos criado em [como: criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="66463-168">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="66463-169">O `Join` palavra-chave é equivalente a um `INNER JOIN` no SQL.</span><span class="sxs-lookup"><span data-stu-id="66463-169">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="66463-170">Ele combina duas coleções baseadas nos valores de chave de correspondência entre os elementos em duas coleções.</span><span class="sxs-lookup"><span data-stu-id="66463-170">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="66463-171">A consulta retorna todo ou parte dos elementos da coleção que têm valores de chave correspondentes.</span><span class="sxs-lookup"><span data-stu-id="66463-171">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="66463-172">Por exemplo, o código a seguir duplica a ação da associação implícita anterior.</span><span class="sxs-lookup"><span data-stu-id="66463-172">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 <span data-ttu-id="66463-173">[!code-vb[VbLINQBasicOps n º&10;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="66463-173">[!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]</span></span>  
  
 <span data-ttu-id="66463-174">`Group Join`combina coleções em uma única coleção hierárquica, assim como um `LEFT JOIN` no SQL.</span><span class="sxs-lookup"><span data-stu-id="66463-174">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="66463-175">Para obter mais informações, consulte [cláusula Join](../../../../visual-basic/language-reference/queries/join-clause.md) e [cláusula Join do grupo](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="66463-175">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="66463-176">Agrupando Dados (Agrupar Por)</span><span class="sxs-lookup"><span data-stu-id="66463-176">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="66463-177">Você pode adicionar uma `Group By` cláusula para agrupar os elementos de acordo com um ou mais campos dos elementos de um resultado de consulta.</span><span class="sxs-lookup"><span data-stu-id="66463-177">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="66463-178">Por exemplo, o código a seguir agrupa os alunos por ano de classe.</span><span class="sxs-lookup"><span data-stu-id="66463-178">For example, the following code groups students by class year.</span></span>  
  
 <span data-ttu-id="66463-179">[!code-vb[VbLINQBasicOps n º&11;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="66463-179">[!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]</span></span>  
  
 <span data-ttu-id="66463-180">Se você executar esse código usando a lista de alunos criado em [como: criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), a saída do `For Each` instrução é:</span><span class="sxs-lookup"><span data-stu-id="66463-180">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="66463-181">Ano: júnior</span><span class="sxs-lookup"><span data-stu-id="66463-181">Year: Junior</span></span>  
  
 <span data-ttu-id="66463-182">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="66463-182">Tucker, Michael</span></span>  
  
 <span data-ttu-id="66463-183">Garcia, Hugo</span><span class="sxs-lookup"><span data-stu-id="66463-183">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="66463-184">Garcia, Debra</span><span class="sxs-lookup"><span data-stu-id="66463-184">Garcia, Debra</span></span>  
  
 <span data-ttu-id="66463-185">Tucker, Lance</span><span class="sxs-lookup"><span data-stu-id="66463-185">Tucker, Lance</span></span>  
  
 <span data-ttu-id="66463-186">Ano: sênior</span><span class="sxs-lookup"><span data-stu-id="66463-186">Year: Senior</span></span>  
  
 <span data-ttu-id="66463-187">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="66463-187">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="66463-188">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="66463-188">Osada, Michiko</span></span>  
  
 <span data-ttu-id="66463-189">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="66463-189">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="66463-190">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="66463-190">Feng, Hanying</span></span>  
  
 <span data-ttu-id="66463-191">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="66463-191">Adams, Terry</span></span>  
  
 <span data-ttu-id="66463-192">Ano: primeiro ano</span><span class="sxs-lookup"><span data-stu-id="66463-192">Year: Freshman</span></span>  
  
 <span data-ttu-id="66463-193">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="66463-193">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="66463-194">Garcia, Cesar</span><span class="sxs-lookup"><span data-stu-id="66463-194">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="66463-195">A variação mostrada no código a seguir ordena os anos de classe e, em seguida, os alunos os pedidos em cada ano por sobrenome.</span><span class="sxs-lookup"><span data-stu-id="66463-195">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 <span data-ttu-id="66463-196">[!code-vb[VbLINQBasicOps&#12;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="66463-196">[!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]</span></span>  
  
 <span data-ttu-id="66463-197">Para obter mais informações sobre `Group By`, consulte [grupo pela cláusula](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="66463-197">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66463-198">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66463-198">See Also</span></span>  
 <span data-ttu-id="66463-199"><xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="66463-199"><xref:System.Collections.Generic.IEnumerable%601></span></span>   
<span data-ttu-id="66463-200"> [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="66463-200"> [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
<span data-ttu-id="66463-201"> [Consultas](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="66463-201"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="66463-202"> [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="66463-202"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="66463-203"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="66463-203"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)</span></span>
