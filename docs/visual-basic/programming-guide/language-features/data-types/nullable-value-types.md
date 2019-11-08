---
title: Tipos de valor anulável-Visual Basic
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
ms.openlocfilehash: 1fb8f8d1657b8eab6b15858c2a6607cbde82e542
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732930"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="70200-102">Tipos de valor que permitem valor nulo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70200-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="70200-103">Às vezes, você trabalha com um tipo de valor que não tem um valor definido em determinadas circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="70200-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="70200-104">Por exemplo, um campo em um banco de dados pode ter que distinguir entre ter um valor atribuído que seja significativo e não tenha um valor atribuído.</span><span class="sxs-lookup"><span data-stu-id="70200-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="70200-105">Os tipos de valor podem ser estendidos para obter seus valores normais ou um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="70200-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="70200-106">Essa extensão é chamada de *tipo anulável*.</span><span class="sxs-lookup"><span data-stu-id="70200-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="70200-107">Cada tipo anulável é construído a partir da estrutura de <xref:System.Nullable%601> genérica.</span><span class="sxs-lookup"><span data-stu-id="70200-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="70200-108">Considere um banco de dados que controla atividades relacionadas ao trabalho.</span><span class="sxs-lookup"><span data-stu-id="70200-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="70200-109">O exemplo a seguir constrói um tipo de `Boolean` anulável e declara uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="70200-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="70200-110">Você pode escrever a declaração de três maneiras:</span><span class="sxs-lookup"><span data-stu-id="70200-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="70200-111">A variável `ridesBusToWork` pode conter um valor de `True`, um valor de `False`ou nenhum valor.</span><span class="sxs-lookup"><span data-stu-id="70200-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="70200-112">Seu valor padrão inicial não é nenhum valor, que nesse caso pode significar que as informações ainda não foram obtidas para essa pessoa.</span><span class="sxs-lookup"><span data-stu-id="70200-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="70200-113">Por outro lado, `False` pode significar que as informações foram obtidas e a pessoa não tem o barramento funcionar.</span><span class="sxs-lookup"><span data-stu-id="70200-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="70200-114">Você pode declarar variáveis e propriedades com tipos anuláveis, e pode declarar uma matriz com elementos de um tipo anulável.</span><span class="sxs-lookup"><span data-stu-id="70200-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="70200-115">Você pode declarar procedimentos com tipos anuláveis como parâmetros e pode retornar um tipo anulável de um procedimento `Function`.</span><span class="sxs-lookup"><span data-stu-id="70200-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>

<span data-ttu-id="70200-116">Você não pode construir um tipo anulável em um tipo de referência, como uma matriz, uma `String`ou uma classe.</span><span class="sxs-lookup"><span data-stu-id="70200-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="70200-117">O tipo subjacente deve ser um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="70200-117">The underlying type must be a value type.</span></span> <span data-ttu-id="70200-118">Para obter mais informações, consulte [tipos de valor e tipos de referência](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="70200-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="70200-119">Usando uma variável de tipo anulável</span><span class="sxs-lookup"><span data-stu-id="70200-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="70200-120">Os membros mais importantes de um tipo anulável são suas propriedades <xref:System.Nullable%601.HasValue%2A> e <xref:System.Nullable%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="70200-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="70200-121">Para uma variável de um tipo anulável, <xref:System.Nullable%601.HasValue%2A> informa se a variável contém um valor definido.</span><span class="sxs-lookup"><span data-stu-id="70200-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="70200-122">Se <xref:System.Nullable%601.HasValue%2A> for `True`, você poderá ler o valor de <xref:System.Nullable%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="70200-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="70200-123">Observe que tanto <xref:System.Nullable%601.HasValue%2A> quanto <xref:System.Nullable%601.Value%2A> são `ReadOnly` Propriedades.</span><span class="sxs-lookup"><span data-stu-id="70200-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="70200-124">Valores padrão</span><span class="sxs-lookup"><span data-stu-id="70200-124">Default Values</span></span>

<span data-ttu-id="70200-125">Quando você declara uma variável com um tipo anulável, sua propriedade <xref:System.Nullable%601.HasValue%2A> tem um valor padrão de `False`.</span><span class="sxs-lookup"><span data-stu-id="70200-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="70200-126">Isso significa que, por padrão, a variável não tem nenhum valor definido, em vez do valor padrão de seu tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="70200-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="70200-127">No exemplo a seguir, a variável `numberOfChildren` inicialmente não tem nenhum valor definido, embora o valor padrão do tipo `Integer` seja 0.</span><span class="sxs-lookup"><span data-stu-id="70200-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="70200-128">Um valor nulo é útil para indicar um valor indefinido ou desconhecido.</span><span class="sxs-lookup"><span data-stu-id="70200-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="70200-129">Se `numberOfChildren` tiver sido declarada como `Integer`, não haveria nenhum valor que possa indicar que as informações não estão disponíveis no momento.</span><span class="sxs-lookup"><span data-stu-id="70200-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="70200-130">Armazenando valores</span><span class="sxs-lookup"><span data-stu-id="70200-130">Storing Values</span></span>

<span data-ttu-id="70200-131">Você armazena um valor em uma variável ou propriedade de um tipo anulável da maneira típica.</span><span class="sxs-lookup"><span data-stu-id="70200-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="70200-132">O exemplo a seguir atribui um valor à variável `numberOfChildren` declarado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="70200-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="70200-133">Se uma variável ou propriedade de um tipo anulável contiver um valor definido, você poderá fazer com que ele reverta para seu estado inicial de não ter um valor atribuído.</span><span class="sxs-lookup"><span data-stu-id="70200-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="70200-134">Você faz isso definindo a variável ou a propriedade como `Nothing`, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="70200-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="70200-135">Embora você possa atribuir `Nothing` a uma variável de um tipo anulável, não é possível testá-la para `Nothing` usando o sinal de igual.</span><span class="sxs-lookup"><span data-stu-id="70200-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="70200-136">Comparação que usa o sinal de igual, `someVar = Nothing`, sempre é avaliada como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="70200-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="70200-137">Você pode testar a propriedade de <xref:System.Nullable%601.HasValue%2A> da variável para `False`ou testar usando o operador `Is` ou `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="70200-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="70200-138">Recuperando valores</span><span class="sxs-lookup"><span data-stu-id="70200-138">Retrieving Values</span></span>

<span data-ttu-id="70200-139">Para recuperar o valor de uma variável de um tipo anulável, você deve primeiro testar sua propriedade <xref:System.Nullable%601.HasValue%2A> para confirmar que ela tem um valor.</span><span class="sxs-lookup"><span data-stu-id="70200-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="70200-140">Se você tentar ler o valor quando <xref:System.Nullable%601.HasValue%2A> for `False`, Visual Basic lançará uma exceção de <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="70200-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="70200-141">O exemplo a seguir mostra a maneira recomendada para ler a variável `numberOfChildren` dos exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="70200-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="70200-142">Comparando tipos anuláveis</span><span class="sxs-lookup"><span data-stu-id="70200-142">Comparing Nullable Types</span></span>

<span data-ttu-id="70200-143">Quando variáveis de `Boolean` anuláveis são usadas em expressões booleanas, o resultado pode ser `True`, `False`ou `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="70200-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="70200-144">A seguir está a tabela verdade para `And` e `Or`.</span><span class="sxs-lookup"><span data-stu-id="70200-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="70200-145">Como `b1` e `b2` agora têm três valores possíveis, há nove combinações a serem avaliadas.</span><span class="sxs-lookup"><span data-stu-id="70200-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="70200-146">B1</span><span class="sxs-lookup"><span data-stu-id="70200-146">b1</span></span>|<span data-ttu-id="70200-147">B2</span><span class="sxs-lookup"><span data-stu-id="70200-147">b2</span></span>|<span data-ttu-id="70200-148">B1 e B2</span><span class="sxs-lookup"><span data-stu-id="70200-148">b1 And b2</span></span>|<span data-ttu-id="70200-149">B1 ou B2</span><span class="sxs-lookup"><span data-stu-id="70200-149">b1 Or b2</span></span>|
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

<span data-ttu-id="70200-150">Quando o valor de uma variável ou expressão booliana é `Nothing`, ele não é `true` nem `false`.</span><span class="sxs-lookup"><span data-stu-id="70200-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="70200-151">Considere o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="70200-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="70200-152">Neste exemplo, `b1 And b2` é avaliada como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="70200-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="70200-153">Como resultado, a cláusula `Else` é executada em cada instrução `If` e a saída é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="70200-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="70200-154">`AndAlso` e `OrElse`, que usam a avaliação de circuito curto, devem avaliar seus segundos operando quando o primeiro é avaliado como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="70200-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="70200-155">Propagação</span><span class="sxs-lookup"><span data-stu-id="70200-155">Propagation</span></span>

<span data-ttu-id="70200-156">Se um ou ambos os operandos de uma operação aritmética, de comparação, de deslocamento ou de tipo for anulável, o resultado da operação também será anulável.</span><span class="sxs-lookup"><span data-stu-id="70200-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="70200-157">Se ambos os operandos tiverem valores que não são `Nothing`, a operação será executada nos valores subjacentes dos operandos, como se nenhum deles fosse um tipo anulável.</span><span class="sxs-lookup"><span data-stu-id="70200-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="70200-158">No exemplo a seguir, as variáveis `compare1` e `sum1` são digitadas implicitamente.</span><span class="sxs-lookup"><span data-stu-id="70200-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="70200-159">Se você posicionar o ponteiro do mouse sobre eles, verá que o compilador infere os tipos anuláveis para ambos.</span><span class="sxs-lookup"><span data-stu-id="70200-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="70200-160">Se um ou ambos os operandos tiverem um valor de `Nothing`, o resultado será `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="70200-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="70200-161">Usando tipos anuláveis com dados</span><span class="sxs-lookup"><span data-stu-id="70200-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="70200-162">Um banco de dados é um dos lugares mais importantes para usar tipos anuláveis.</span><span class="sxs-lookup"><span data-stu-id="70200-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="70200-163">Nem todos os objetos de banco de dados dão suporte a tipos anuláveis atualmente, mas os adaptadores de tabela gerados pelo designer fazem.</span><span class="sxs-lookup"><span data-stu-id="70200-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="70200-164">Consulte [suporte do TableAdapter para tipos anuláveis](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span><span class="sxs-lookup"><span data-stu-id="70200-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="70200-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70200-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="70200-166">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="70200-166">Data Types</span></span>](index.md)
- [<span data-ttu-id="70200-167">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="70200-167">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="70200-168">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="70200-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="70200-169">Preencher conjuntos de dados usando TableAdapters</span><span class="sxs-lookup"><span data-stu-id="70200-169">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="70200-170">Operador If</span><span class="sxs-lookup"><span data-stu-id="70200-170">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="70200-171">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="70200-171">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="70200-172">Operador Is</span><span class="sxs-lookup"><span data-stu-id="70200-172">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="70200-173">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="70200-173">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="70200-174">Tipos de valor AnulávelC#()</span><span class="sxs-lookup"><span data-stu-id="70200-174">Nullable Value Types (C#)</span></span>](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
