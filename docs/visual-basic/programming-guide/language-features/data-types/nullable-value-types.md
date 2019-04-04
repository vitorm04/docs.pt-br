---
title: Tipos de valor anulável - Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: d17d2ad3fd99c6d563c21ddd646396ccb1c1ca48
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921306"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="901b5-102">Tipos de valor que permitem valor nulo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="901b5-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="901b5-103">Às vezes, você trabalha com um tipo de valor que não tem um valor definido em determinadas circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="901b5-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="901b5-104">Por exemplo, um campo em um banco de dados pode ter que distinguir entre ter um valor atribuído que seja significativo e não ter um valor atribuído.</span><span class="sxs-lookup"><span data-stu-id="901b5-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="901b5-105">Tipos de valor podem ser estendidos para levar seus valores de normais ou um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="901b5-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="901b5-106">Uma extensão desse tipo é chamada um *tipo anulável*.</span><span class="sxs-lookup"><span data-stu-id="901b5-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="901b5-107">Cada tipo anulável é construído a partir genérica <xref:System.Nullable%601> estrutura.</span><span class="sxs-lookup"><span data-stu-id="901b5-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="901b5-108">Considere um banco de dados que rastreia atividades relacionadas ao trabalho.</span><span class="sxs-lookup"><span data-stu-id="901b5-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="901b5-109">O exemplo a seguir constrói um valor anulável `Boolean` e declara uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="901b5-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="901b5-110">Você pode escrever a declaração de três maneiras:</span><span class="sxs-lookup"><span data-stu-id="901b5-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="901b5-111">A variável `ridesBusToWork` pode conter um valor de `True`, um valor de `False`, ou nenhum valor.</span><span class="sxs-lookup"><span data-stu-id="901b5-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="901b5-112">Seu valor inicial padrão não é nenhum valor, que nesse caso, pode significar que as informações ainda não foi obtidas para essa pessoa.</span><span class="sxs-lookup"><span data-stu-id="901b5-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="901b5-113">Em contraste, `False` pode significar que a informação foi obtida e a pessoa não pretendem ir de ônibus para o trabalho.</span><span class="sxs-lookup"><span data-stu-id="901b5-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="901b5-114">Você pode declarar variáveis e propriedades com tipos anuláveis, e você pode declarar uma matriz com elementos de um tipo anulável.</span><span class="sxs-lookup"><span data-stu-id="901b5-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="901b5-115">Você pode declarar procedimentos com tipos anuláveis como parâmetros, e você pode retornar um tipo anulável de um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="901b5-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>

<span data-ttu-id="901b5-116">Não é possível construir um tipo anulável em um tipo de referência como uma matriz, um `String`, ou uma classe.</span><span class="sxs-lookup"><span data-stu-id="901b5-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="901b5-117">O tipo subjacente deve ser um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="901b5-117">The underlying type must be a value type.</span></span> <span data-ttu-id="901b5-118">Para obter mais informações, consulte [tipos de valor e tipos de referência](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="901b5-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="901b5-119">Usando uma variável de tipo anulável</span><span class="sxs-lookup"><span data-stu-id="901b5-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="901b5-120">Os membros mais importantes de um tipo anulável são suas <xref:System.Nullable%601.HasValue%2A> e <xref:System.Nullable%601.Value%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="901b5-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="901b5-121">Para uma variável de um tipo anulável, <xref:System.Nullable%601.HasValue%2A> informa se a variável contém um valor definido.</span><span class="sxs-lookup"><span data-stu-id="901b5-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="901b5-122">Se <xref:System.Nullable%601.HasValue%2A> está `True`, você pode ler o valor de <xref:System.Nullable%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="901b5-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="901b5-123">Observe que ambos <xref:System.Nullable%601.HasValue%2A> e <xref:System.Nullable%601.Value%2A> são `ReadOnly` propriedades.</span><span class="sxs-lookup"><span data-stu-id="901b5-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="901b5-124">Valores padrão</span><span class="sxs-lookup"><span data-stu-id="901b5-124">Default Values</span></span>

<span data-ttu-id="901b5-125">Quando você declara uma variável com um tipo anulável, sua <xref:System.Nullable%601.HasValue%2A> propriedade tem um valor padrão de `False`.</span><span class="sxs-lookup"><span data-stu-id="901b5-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="901b5-126">Isso significa que, por padrão, a variável não tem nenhum valor definido, em vez do valor padrão de seu tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="901b5-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="901b5-127">No exemplo a seguir, a variável `numberOfChildren` inicialmente não tem valor definido, mesmo que o valor padrão de `Integer` tipo é 0.</span><span class="sxs-lookup"><span data-stu-id="901b5-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="901b5-128">Um valor nulo é útil para indicar um valor desconhecido ou indefinido.</span><span class="sxs-lookup"><span data-stu-id="901b5-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="901b5-129">Se `numberOfChildren` tivesse sido declarado como `Integer`, não haveria nenhum valor que pode indicar que as informações não estão disponíveis no momento.</span><span class="sxs-lookup"><span data-stu-id="901b5-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="901b5-130">Armazenando valores</span><span class="sxs-lookup"><span data-stu-id="901b5-130">Storing Values</span></span>

<span data-ttu-id="901b5-131">Você pode armazenar um valor em uma variável ou propriedade de um tipo que permite valor nulo em uma forma comum de.</span><span class="sxs-lookup"><span data-stu-id="901b5-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="901b5-132">O exemplo a seguir atribui um valor à variável `numberOfChildren` declarada no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="901b5-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="901b5-133">Se uma variável ou propriedade de um tipo anulável contiver um valor definido, você poderá revertê-la para seu estado inicial de não ter um valor atribuído.</span><span class="sxs-lookup"><span data-stu-id="901b5-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="901b5-134">Você pode fazer isso definindo a variável ou propriedade a ser `Nothing`, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="901b5-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="901b5-135">Embora você possa atribuir `Nothing` a uma variável de um tipo anulável, você não é possível testá-lo para `Nothing` usando o sinal de igual.</span><span class="sxs-lookup"><span data-stu-id="901b5-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="901b5-136">Comparação que usa o sinal de igual `someVar = Nothing`, sempre é avaliada como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="901b5-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="901b5-137">Você pode testar a variável <xref:System.Nullable%601.HasValue%2A> propriedade para `False`, ou de teste usando o `Is` ou `IsNot` operador.</span><span class="sxs-lookup"><span data-stu-id="901b5-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="901b5-138">Recuperando valores</span><span class="sxs-lookup"><span data-stu-id="901b5-138">Retrieving Values</span></span>

<span data-ttu-id="901b5-139">Para recuperar o valor de uma variável de um tipo anulável, primeiro você deve testar seu <xref:System.Nullable%601.HasValue%2A> propriedade para confirmar se ele tem um valor.</span><span class="sxs-lookup"><span data-stu-id="901b5-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="901b5-140">Se você tentar ler o valor quando <xref:System.Nullable%601.HasValue%2A> está `False`, Visual Basic gera um <xref:System.InvalidOperationException> exceção.</span><span class="sxs-lookup"><span data-stu-id="901b5-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="901b5-141">O exemplo a seguir mostra a maneira recomendada para ler a variável `numberOfChildren` dos exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="901b5-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="901b5-142">Comparando tipos anuláveis</span><span class="sxs-lookup"><span data-stu-id="901b5-142">Comparing Nullable Types</span></span>

<span data-ttu-id="901b5-143">Quando for anulável `Boolean` as variáveis são usadas em expressões booleanas, o resultado pode ser `True`, `False`, ou `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="901b5-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="901b5-144">A seguir está a tabela de verdade para `And` e `Or`.</span><span class="sxs-lookup"><span data-stu-id="901b5-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="901b5-145">Porque `b1` e `b2` agora tem três valores possíveis, existem nove combinações para avaliar.</span><span class="sxs-lookup"><span data-stu-id="901b5-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="901b5-146">b1</span><span class="sxs-lookup"><span data-stu-id="901b5-146">b1</span></span>|<span data-ttu-id="901b5-147">b2</span><span class="sxs-lookup"><span data-stu-id="901b5-147">b2</span></span>|<span data-ttu-id="901b5-148">B1 e b2</span><span class="sxs-lookup"><span data-stu-id="901b5-148">b1 And b2</span></span>|<span data-ttu-id="901b5-149">B1 ou b2</span><span class="sxs-lookup"><span data-stu-id="901b5-149">b1 Or b2</span></span>|
|--------|--------|---------------|--------------|
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|
|`Nothing`|`True`|`Nothing`|`True`|
|`Nothing`|`False`|`False`|`Nothing`|
|`True`|`Nothing`|`Nothing`|`True`|
|`True`|`True`|`True`|`True`|
|`True`|`False`|`False`|`True`|
|`False`|`Nothing`|`False`|`Nothing`|
|`False`|`True`|`False`|`True`|
|`False`|`False`|`False`|`False`|

<span data-ttu-id="901b5-150">Quando o valor de uma variável ou expressão booleana for `Nothing`, ele não é nem `true` nem `false`.</span><span class="sxs-lookup"><span data-stu-id="901b5-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="901b5-151">Considere o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="901b5-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="901b5-152">Neste exemplo, `b1 And b2` for avaliada como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="901b5-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="901b5-153">Como resultado, o `Else` cláusula é executada em cada `If` instrução e a saída é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="901b5-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso` <span data-ttu-id="901b5-154">e `OrElse`, que usam curto-circuito avaliação, deve avaliar seus operandos segundo quando o primeiro é avaliada como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="901b5-154">and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="901b5-155">Propagação</span><span class="sxs-lookup"><span data-stu-id="901b5-155">Propagation</span></span>

<span data-ttu-id="901b5-156">Se um ou ambos os operandos de uma aritmética, comparação, shift ou operação de tipo for anulável, o resultado da operação também é anulável.</span><span class="sxs-lookup"><span data-stu-id="901b5-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="901b5-157">Se os dois operandos tiverem valores que não são `Nothing`, a operação é executada nos valores subjacentes dos operandos, como se nenhum deles fosse um tipo anulável.</span><span class="sxs-lookup"><span data-stu-id="901b5-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="901b5-158">No exemplo a seguir, as variáveis `compare1` e `sum1` são de tipo implícito.</span><span class="sxs-lookup"><span data-stu-id="901b5-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="901b5-159">Se você posicionar o ponteiro do mouse sobre eles, você verá que o compilador infere os tipos que permitem valor nulos para os dois.</span><span class="sxs-lookup"><span data-stu-id="901b5-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="901b5-160">Se um ou ambos os operandos têm um valor de `Nothing`, o resultado será `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="901b5-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="901b5-161">Usando tipos anuláveis com dados</span><span class="sxs-lookup"><span data-stu-id="901b5-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="901b5-162">Um banco de dados é um dos locais mais importantes para usar tipos anuláveis.</span><span class="sxs-lookup"><span data-stu-id="901b5-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="901b5-163">Nem todos os objetos de banco de dados atualmente dão suporte a tipos anuláveis, mas os adaptadores de tabelas gerado pelo designer.</span><span class="sxs-lookup"><span data-stu-id="901b5-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="901b5-164">Ver [suporte do TableAdapter para tipos anuláveis](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span><span class="sxs-lookup"><span data-stu-id="901b5-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="901b5-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="901b5-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="901b5-166">Usando tipos anuláveis</span><span class="sxs-lookup"><span data-stu-id="901b5-166">Using Nullable Types</span></span>](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [<span data-ttu-id="901b5-167">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="901b5-167">Data Types</span></span>](index.md)
- [<span data-ttu-id="901b5-168">Tipos de valor e referência</span><span class="sxs-lookup"><span data-stu-id="901b5-168">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="901b5-169">Solucionando problemas de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="901b5-169">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="901b5-170">Preencher conjuntos de dados usando TableAdapters</span><span class="sxs-lookup"><span data-stu-id="901b5-170">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="901b5-171">Operador If</span><span class="sxs-lookup"><span data-stu-id="901b5-171">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="901b5-172">Inferência de tipo local</span><span class="sxs-lookup"><span data-stu-id="901b5-172">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="901b5-173">Operador Is</span><span class="sxs-lookup"><span data-stu-id="901b5-173">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="901b5-174">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="901b5-174">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)