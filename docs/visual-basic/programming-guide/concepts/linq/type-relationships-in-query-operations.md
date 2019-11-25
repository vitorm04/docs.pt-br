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
ms.openlocfilehash: 8c201abef924766d52b1adb084970a24ebea2b50
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350561"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="9312e-102">Relacionamentos de tipo em operações de consulta (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9312e-102">Type Relationships in Query Operations (Visual Basic)</span></span>

<span data-ttu-id="9312e-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span><span class="sxs-lookup"><span data-stu-id="9312e-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="9312e-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span><span class="sxs-lookup"><span data-stu-id="9312e-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="9312e-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span><span class="sxs-lookup"><span data-stu-id="9312e-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="9312e-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9312e-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>

![Screenshot showing a pseudocode query with elements highlighted.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

<span data-ttu-id="9312e-108">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span><span class="sxs-lookup"><span data-stu-id="9312e-108">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="9312e-109">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span><span class="sxs-lookup"><span data-stu-id="9312e-109">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="9312e-110">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span><span class="sxs-lookup"><span data-stu-id="9312e-110">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="9312e-111">This strong typing facilitates identification of type errors at compile time.</span><span class="sxs-lookup"><span data-stu-id="9312e-111">This strong typing facilitates identification of type errors at compile time.</span></span>

<span data-ttu-id="9312e-112">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span><span class="sxs-lookup"><span data-stu-id="9312e-112">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="9312e-113">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span><span class="sxs-lookup"><span data-stu-id="9312e-113">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span></span> <span data-ttu-id="9312e-114">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span><span class="sxs-lookup"><span data-stu-id="9312e-114">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="9312e-115">In the following example, `city` is strongly typed as a string.</span><span class="sxs-lookup"><span data-stu-id="9312e-115">In the following example, `city` is strongly typed as a string.</span></span>

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="9312e-116">Local type inference works only when `Option Infer` is set to `On`.</span><span class="sxs-lookup"><span data-stu-id="9312e-116">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="9312e-117">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9312e-117">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>

<span data-ttu-id="9312e-118">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span><span class="sxs-lookup"><span data-stu-id="9312e-118">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="9312e-119">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span><span class="sxs-lookup"><span data-stu-id="9312e-119">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span></span>

<span data-ttu-id="9312e-120">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span><span class="sxs-lookup"><span data-stu-id="9312e-120">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="9312e-121">You can specify the type of the range variable by using an `As` clause.</span><span class="sxs-lookup"><span data-stu-id="9312e-121">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="9312e-122">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span><span class="sxs-lookup"><span data-stu-id="9312e-122">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="9312e-123">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span><span class="sxs-lookup"><span data-stu-id="9312e-123">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="9312e-124">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span><span class="sxs-lookup"><span data-stu-id="9312e-124">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="9312e-125">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span><span class="sxs-lookup"><span data-stu-id="9312e-125">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="9312e-126">These points are illustrated in the following code.</span><span class="sxs-lookup"><span data-stu-id="9312e-126">These points are illustrated in the following code.</span></span>

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="9312e-127">Queries That Return Entire Elements of the Source Data</span><span class="sxs-lookup"><span data-stu-id="9312e-127">Queries That Return Entire Elements of the Source Data</span></span>

<span data-ttu-id="9312e-128">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span><span class="sxs-lookup"><span data-stu-id="9312e-128">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="9312e-129">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span><span class="sxs-lookup"><span data-stu-id="9312e-129">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

<span data-ttu-id="9312e-130">This is equivalent to the following code, but is much shorter and easier to write.</span><span class="sxs-lookup"><span data-stu-id="9312e-130">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="9312e-131">Reliance on local type inference in queries is the preferred style in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9312e-131">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

<span data-ttu-id="9312e-132">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span><span class="sxs-lookup"><span data-stu-id="9312e-132">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>

1. <span data-ttu-id="9312e-133">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span><span class="sxs-lookup"><span data-stu-id="9312e-133">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>

2. <span data-ttu-id="9312e-134">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span><span class="sxs-lookup"><span data-stu-id="9312e-134">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="9312e-135">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9312e-135">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>

3. <span data-ttu-id="9312e-136">The query defined in `mNames` is executed in the `For Each` loop.</span><span class="sxs-lookup"><span data-stu-id="9312e-136">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="9312e-137">The loop iterates over the result of executing the query.</span><span class="sxs-lookup"><span data-stu-id="9312e-137">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="9312e-138">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span><span class="sxs-lookup"><span data-stu-id="9312e-138">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>

## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="9312e-139">Queries That Return One Field from Selected Elements</span><span class="sxs-lookup"><span data-stu-id="9312e-139">Queries That Return One Field from Selected Elements</span></span>

<span data-ttu-id="9312e-140">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span><span class="sxs-lookup"><span data-stu-id="9312e-140">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="9312e-141">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span><span class="sxs-lookup"><span data-stu-id="9312e-141">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="9312e-142">Because the customer name is a string, the query produces a sequence of strings as output.</span><span class="sxs-lookup"><span data-stu-id="9312e-142">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>

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

<span data-ttu-id="9312e-143">The relationships between variables are like those in the simpler example.</span><span class="sxs-lookup"><span data-stu-id="9312e-143">The relationships between variables are like those in the simpler example.</span></span>

1. <span data-ttu-id="9312e-144">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span><span class="sxs-lookup"><span data-stu-id="9312e-144">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="9312e-145">In this example, that type is `Customer`.</span><span class="sxs-lookup"><span data-stu-id="9312e-145">In this example, that type is `Customer`.</span></span>

2. <span data-ttu-id="9312e-146">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span><span class="sxs-lookup"><span data-stu-id="9312e-146">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="9312e-147">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span><span class="sxs-lookup"><span data-stu-id="9312e-147">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>

3. <span data-ttu-id="9312e-148">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span><span class="sxs-lookup"><span data-stu-id="9312e-148">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>

<span data-ttu-id="9312e-149">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="9312e-149">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>

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

## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="9312e-150">Queries That Require Anonymous Types</span><span class="sxs-lookup"><span data-stu-id="9312e-150">Queries That Require Anonymous Types</span></span>

<span data-ttu-id="9312e-151">The following example shows a more complex situation.</span><span class="sxs-lookup"><span data-stu-id="9312e-151">The following example shows a more complex situation.</span></span> <span data-ttu-id="9312e-152">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span><span class="sxs-lookup"><span data-stu-id="9312e-152">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="9312e-153">In this example, it is impossible.</span><span class="sxs-lookup"><span data-stu-id="9312e-153">In this example, it is impossible.</span></span> <span data-ttu-id="9312e-154">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span><span class="sxs-lookup"><span data-stu-id="9312e-154">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="9312e-155">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span><span class="sxs-lookup"><span data-stu-id="9312e-155">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="9312e-156">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span><span class="sxs-lookup"><span data-stu-id="9312e-156">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="9312e-157">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span><span class="sxs-lookup"><span data-stu-id="9312e-157">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="9312e-158">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="9312e-158">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="9312e-159">Para obter mais informações, consulte [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="9312e-159">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

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

<span data-ttu-id="9312e-160">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span><span class="sxs-lookup"><span data-stu-id="9312e-160">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>

1. <span data-ttu-id="9312e-161">The type of the elements in the data source is again the type of the range variable in the query.</span><span class="sxs-lookup"><span data-stu-id="9312e-161">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="9312e-162">In this example, `cust` is an instance of `Customer`.</span><span class="sxs-lookup"><span data-stu-id="9312e-162">In this example, `cust` is an instance of `Customer`.</span></span>

2. <span data-ttu-id="9312e-163">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span><span class="sxs-lookup"><span data-stu-id="9312e-163">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="9312e-164">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span><span class="sxs-lookup"><span data-stu-id="9312e-164">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>

3. <span data-ttu-id="9312e-165">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span><span class="sxs-lookup"><span data-stu-id="9312e-165">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="9312e-166">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span><span class="sxs-lookup"><span data-stu-id="9312e-166">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>

## <a name="see-also"></a><span data-ttu-id="9312e-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9312e-167">See also</span></span>

- [<span data-ttu-id="9312e-168">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9312e-168">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="9312e-169">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="9312e-169">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="9312e-170">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="9312e-170">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="9312e-171">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9312e-171">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="9312e-172">LINQ</span><span class="sxs-lookup"><span data-stu-id="9312e-172">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="9312e-173">Consultas</span><span class="sxs-lookup"><span data-stu-id="9312e-173">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
