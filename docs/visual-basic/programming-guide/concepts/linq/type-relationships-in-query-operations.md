---
title: Relacionamentos entre tipos em operações de consulta
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: 73a287541ddf115510bf6ab5c830eafac370cc3a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406723"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="69554-102">Relacionamentos de tipo em operações de consulta (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69554-102">Type Relationships in Query Operations (Visual Basic)</span></span>

<span data-ttu-id="69554-103">As variáveis usadas em operações de consulta do LINQ (consulta integrada à linguagem) são fortemente tipadas e devem ser compatíveis entre si.</span><span class="sxs-lookup"><span data-stu-id="69554-103">Variables used in Language-Integrated Query (LINQ) query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="69554-104">A tipagem forte é usada na fonte de dados, na própria consulta e na execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="69554-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="69554-105">A ilustração a seguir identifica os termos usados para descrever uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="69554-105">The following illustration identifies terms used to describe a LINQ query.</span></span> <span data-ttu-id="69554-106">Para obter mais informações sobre as partes de uma consulta, consulte [Basic Query Operations (Visual Basic)](basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="69554-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](basic-query-operations.md).</span></span>

![Captura de tela mostrando uma consulta de pseudocódigo com elementos realçados.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

<span data-ttu-id="69554-108">O tipo da variável de intervalo na consulta deve ser compatível com o tipo dos elementos na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="69554-108">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="69554-109">O tipo da variável de consulta deve ser compatível com o elemento Sequence definido na `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="69554-109">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="69554-110">Por fim, o tipo dos elementos de sequência também deve ser compatível com o tipo da variável de controle de loop que é usada na `For Each` instrução que executa a consulta.</span><span class="sxs-lookup"><span data-stu-id="69554-110">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="69554-111">Essa tipagem forte facilita a identificação de erros de tipo no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="69554-111">This strong typing facilitates identification of type errors at compile time.</span></span>

<span data-ttu-id="69554-112">Visual Basic facilita a digitação de rigidez, implementando a inferência de tipo local, também conhecida como *digitação implícita*.</span><span class="sxs-lookup"><span data-stu-id="69554-112">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="69554-113">Esse recurso é usado no exemplo anterior e você verá que ele é usado em todos os exemplos e documentação do LINQ.</span><span class="sxs-lookup"><span data-stu-id="69554-113">That feature is used in the previous example, and you will see it used throughout the LINQ samples and documentation.</span></span> <span data-ttu-id="69554-114">Em Visual Basic, a inferência de tipo local é realizada simplesmente usando uma `Dim` instrução sem uma `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="69554-114">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="69554-115">No exemplo a seguir, `city` é fortemente tipado como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="69554-115">In the following example, `city` is strongly typed as a string.</span></span>

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="69554-116">A inferência de tipo local só funciona quando `Option Infer` é definido como `On` .</span><span class="sxs-lookup"><span data-stu-id="69554-116">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="69554-117">Para obter mais informações, consulte [instrução Option Infer](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="69554-117">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>

<span data-ttu-id="69554-118">No entanto, mesmo se você usar a inferência de tipo local em uma consulta, as mesmas relações de tipo estarão presentes entre as variáveis na fonte de dados, a variável de consulta e o loop de execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="69554-118">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="69554-119">É útil ter um entendimento básico dessas relações de tipo quando você estiver escrevendo consultas LINQ ou trabalhando com exemplos e códigos de exemplo na documentação.</span><span class="sxs-lookup"><span data-stu-id="69554-119">It is useful to have a basic understanding of these type relationships when you are writing LINQ queries, or working with the samples and code examples in the documentation.</span></span>

<span data-ttu-id="69554-120">Talvez seja necessário especificar um tipo explícito para uma variável de intervalo que não corresponda ao tipo retornado da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="69554-120">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="69554-121">Você pode especificar o tipo da variável de intervalo usando uma `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="69554-121">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="69554-122">No entanto, isso resultará em um erro se a conversão for uma [conversão de restrição](../../language-features/data-types/widening-and-narrowing-conversions.md) e `Option Strict` for definida como `On` .</span><span class="sxs-lookup"><span data-stu-id="69554-122">However, this results in an error if the conversion is a [narrowing conversion](../../language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="69554-123">Portanto, recomendamos que você execute a conversão nos valores recuperados da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="69554-123">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="69554-124">Você pode converter os valores da fonte de dados para o tipo de variável de intervalo explícito usando o <xref:System.Linq.Enumerable.Cast%2A> método.</span><span class="sxs-lookup"><span data-stu-id="69554-124">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="69554-125">Você também pode converter os valores selecionados na `Select` cláusula para um tipo explícito que seja diferente do tipo da variável de intervalo.</span><span class="sxs-lookup"><span data-stu-id="69554-125">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="69554-126">Esses pontos são ilustrados no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="69554-126">These points are illustrated in the following code.</span></span>

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="69554-127">Consultas que retornam elementos inteiros dos dados de origem</span><span class="sxs-lookup"><span data-stu-id="69554-127">Queries That Return Entire Elements of the Source Data</span></span>

<span data-ttu-id="69554-128">O exemplo a seguir mostra uma operação de consulta LINQ que retorna uma sequência de elementos selecionados a partir dos dados de origem.</span><span class="sxs-lookup"><span data-stu-id="69554-128">The following example shows a LINQ query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="69554-129">A origem, `names` , contém uma matriz de cadeias de caracteres e a saída da consulta é uma sequência que contém cadeias de caracteres que começam com a letra M.</span><span class="sxs-lookup"><span data-stu-id="69554-129">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

<span data-ttu-id="69554-130">Isso é equivalente ao código a seguir, mas é muito mais curto e mais fácil de escrever.</span><span class="sxs-lookup"><span data-stu-id="69554-130">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="69554-131">A dependência da inferência de tipo local em consultas é o estilo preferencial em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="69554-131">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

<span data-ttu-id="69554-132">As relações a seguir existem nos dois exemplos de código anteriores, independentemente de os tipos serem determinados implicitamente ou explicitamente.</span><span class="sxs-lookup"><span data-stu-id="69554-132">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>

1. <span data-ttu-id="69554-133">O tipo dos elementos na fonte de dados, `names` , é o tipo da variável de intervalo, `name` , na consulta.</span><span class="sxs-lookup"><span data-stu-id="69554-133">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>

2. <span data-ttu-id="69554-134">O tipo do objeto selecionado, `name` , determina o tipo da variável de consulta, `mNames` .</span><span class="sxs-lookup"><span data-stu-id="69554-134">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="69554-135">Aqui `name` está uma cadeia de caracteres, portanto, a variável de consulta é IEnumerable (Of String) em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="69554-135">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>

3. <span data-ttu-id="69554-136">A consulta definida em `mNames` é executada no `For Each` loop.</span><span class="sxs-lookup"><span data-stu-id="69554-136">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="69554-137">O loop itera sobre o resultado da execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="69554-137">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="69554-138">Como `mNames` , quando é executado, retornará uma sequência de cadeias de caracteres, a variável de iteração de loop, `nm` , também é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="69554-138">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>

## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="69554-139">Consultas que retornam um campo dos elementos selecionados</span><span class="sxs-lookup"><span data-stu-id="69554-139">Queries That Return One Field from Selected Elements</span></span>

<span data-ttu-id="69554-140">O exemplo a seguir mostra uma [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operação de consulta que retorna uma sequência contendo apenas uma parte de cada elemento selecionado na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="69554-140">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="69554-141">A consulta usa uma coleção de `Customer` objetos como sua fonte de dados e projeta apenas a `Name` propriedade no resultado.</span><span class="sxs-lookup"><span data-stu-id="69554-141">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="69554-142">Como o nome do cliente é uma cadeia de caracteres, a consulta produz uma sequência de cadeias de caracteres como saída.</span><span class="sxs-lookup"><span data-stu-id="69554-142">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim custNames = From cust In customers
                Where cust.City = "London"
                Select cust.Name

For Each custName In custNames
    Console.WriteLine(custName)
Next
```

<span data-ttu-id="69554-143">As relações entre as variáveis são como as do exemplo mais simples.</span><span class="sxs-lookup"><span data-stu-id="69554-143">The relationships between variables are like those in the simpler example.</span></span>

1. <span data-ttu-id="69554-144">O tipo dos elementos na fonte de dados, `customers` , é o tipo da variável de intervalo, `cust` , na consulta.</span><span class="sxs-lookup"><span data-stu-id="69554-144">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="69554-145">Neste exemplo, esse tipo é `Customer` .</span><span class="sxs-lookup"><span data-stu-id="69554-145">In this example, that type is `Customer`.</span></span>

2. <span data-ttu-id="69554-146">A `Select` instrução retorna a `Name` propriedade de cada `Customer` objeto em vez de todo o objeto.</span><span class="sxs-lookup"><span data-stu-id="69554-146">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="69554-147">Como `Name` é uma cadeia de caracteres, a variável de consulta, `custNames` , novamente será IEnumerable (Of String), não de `Customer` .</span><span class="sxs-lookup"><span data-stu-id="69554-147">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>

3. <span data-ttu-id="69554-148">Como `custNames` representa uma sequência de cadeias de caracteres, a `For Each` variável de iteração do loop, `custName` , deve ser uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="69554-148">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>

<span data-ttu-id="69554-149">Sem a inferência de tipo local, o exemplo anterior seria mais complicado de escrever e entender, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="69554-149">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()
 Dim custNames As IEnumerable(Of String) =
     From cust As Customer In customers
     Where cust.City = "London"
     Select cust.Name

 For Each custName As String In custNames
     Console.WriteLine(custName)
 Next
```

## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="69554-150">Consultas que exigem tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="69554-150">Queries That Require Anonymous Types</span></span>

<span data-ttu-id="69554-151">O exemplo a seguir mostra uma situação mais complexa.</span><span class="sxs-lookup"><span data-stu-id="69554-151">The following example shows a more complex situation.</span></span> <span data-ttu-id="69554-152">No exemplo anterior, era inconveniente especificar tipos para todas as variáveis explicitamente.</span><span class="sxs-lookup"><span data-stu-id="69554-152">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="69554-153">Neste exemplo, é impossível.</span><span class="sxs-lookup"><span data-stu-id="69554-153">In this example, it is impossible.</span></span> <span data-ttu-id="69554-154">Em vez de selecionar `Customer` elementos inteiros da fonte de dados, ou um único campo de cada elemento, a `Select` cláusula nessa consulta retorna duas propriedades do objeto original `Customer` : `Name` e `City` .</span><span class="sxs-lookup"><span data-stu-id="69554-154">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="69554-155">Em resposta à `Select` cláusula, o compilador define um tipo anônimo que contém essas duas propriedades.</span><span class="sxs-lookup"><span data-stu-id="69554-155">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="69554-156">O resultado da execução `nameCityQuery` no `For Each` loop é uma coleção de instâncias do novo tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="69554-156">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="69554-157">Como o tipo anônimo não tem nome utilizável, você não pode especificar o tipo de `nameCityQuery` ou `custInfo` explicitamente.</span><span class="sxs-lookup"><span data-stu-id="69554-157">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="69554-158">Ou seja, com um tipo anônimo, você não tem nenhum nome de tipo a ser usado no lugar do `String` `IEnumerable(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="69554-158">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="69554-159">Para obter mais informações, consulte [Tipos Anônimos](../../language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="69554-159">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim nameCityQuery = From cust In customers
                    Where cust.City = "London"
                    Select cust.Name, cust.City

For Each custInfo In nameCityQuery
    Console.WriteLine(custInfo.Name)
Next
```

<span data-ttu-id="69554-160">Embora não seja possível especificar tipos para todas as variáveis no exemplo anterior, as relações permanecem as mesmas.</span><span class="sxs-lookup"><span data-stu-id="69554-160">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>

1. <span data-ttu-id="69554-161">O tipo dos elementos na fonte de dados é novamente o tipo da variável de intervalo na consulta.</span><span class="sxs-lookup"><span data-stu-id="69554-161">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="69554-162">Neste exemplo, `cust` é uma instância do `Customer` .</span><span class="sxs-lookup"><span data-stu-id="69554-162">In this example, `cust` is an instance of `Customer`.</span></span>

2. <span data-ttu-id="69554-163">Como a `Select` instrução produz um tipo anônimo, a variável de consulta, `nameCityQuery` , deve ser digitada implicitamente como um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="69554-163">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="69554-164">Um tipo anônimo não tem nome utilizável e, portanto, não pode ser especificado explicitamente.</span><span class="sxs-lookup"><span data-stu-id="69554-164">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>

3. <span data-ttu-id="69554-165">O tipo da variável de iteração no `For Each` loop é o tipo anônimo criado na etapa 2.</span><span class="sxs-lookup"><span data-stu-id="69554-165">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="69554-166">Como o tipo não tem nenhum nome utilizável, o tipo da variável de iteração de loop deve ser determinado implicitamente.</span><span class="sxs-lookup"><span data-stu-id="69554-166">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>

## <a name="see-also"></a><span data-ttu-id="69554-167">Confira também</span><span class="sxs-lookup"><span data-stu-id="69554-167">See also</span></span>

- [<span data-ttu-id="69554-168">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69554-168">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="69554-169">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="69554-169">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="69554-170">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="69554-170">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="69554-171">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69554-171">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="69554-172">LINQ</span><span class="sxs-lookup"><span data-stu-id="69554-172">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="69554-173">Consultas</span><span class="sxs-lookup"><span data-stu-id="69554-173">Queries</span></span>](../../../language-reference/queries/index.md)
