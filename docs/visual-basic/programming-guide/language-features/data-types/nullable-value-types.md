---
title: Tipos de valor que permitem valor nulo
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
ms.openlocfilehash: beed8262c50dc68330b8f03aa3d864ed2f8df0d5
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249676"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="3fca0-102">Tipos de valor que permitem valor nulo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fca0-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="3fca0-103">Às vezes você trabalha com um tipo de valor que não tem um valor definido em certas circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="3fca0-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="3fca0-104">Por exemplo, um campo em um banco de dados pode ter que distinguir entre ter um valor atribuído que seja significativo e não ter um valor atribuído.</span><span class="sxs-lookup"><span data-stu-id="3fca0-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="3fca0-105">Os tipos de valor podem ser estendidos para levar seus valores normais ou um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="3fca0-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="3fca0-106">Tal extensão é chamada de *tipo nulo.*</span><span class="sxs-lookup"><span data-stu-id="3fca0-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="3fca0-107">Cada tipo de valor anulado é <xref:System.Nullable%601> construído a partir da estrutura genérica.</span><span class="sxs-lookup"><span data-stu-id="3fca0-107">Each nullable value type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="3fca0-108">Considere um banco de dados que rastreie atividades relacionadas ao trabalho.</span><span class="sxs-lookup"><span data-stu-id="3fca0-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="3fca0-109">O exemplo a seguir `Boolean` constrói um tipo anulado e declara uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="3fca0-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="3fca0-110">Você pode escrever a declaração de três maneiras:</span><span class="sxs-lookup"><span data-stu-id="3fca0-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="3fca0-111">A `ridesBusToWork` variável pode conter `True`um valor `False`de , um valor de , ou nenhum valor em tudo.</span><span class="sxs-lookup"><span data-stu-id="3fca0-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="3fca0-112">Seu valor inicial de inadimplência não é nenhum valor, o que neste caso pode significar que as informações ainda não foram obtidas para essa pessoa.</span><span class="sxs-lookup"><span data-stu-id="3fca0-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="3fca0-113">Em contrapartida, `False` pode significar que as informações foram obtidas e a pessoa não anda de ônibus para o trabalho.</span><span class="sxs-lookup"><span data-stu-id="3fca0-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="3fca0-114">Você pode declarar variáveis e propriedades com tipos de valor anulados, e você pode declarar uma matriz com elementos de um tipo de valor anulado.</span><span class="sxs-lookup"><span data-stu-id="3fca0-114">You can declare variables and properties with nullable value types, and you can declare an array with elements of a nullable value type.</span></span> <span data-ttu-id="3fca0-115">Você pode declarar procedimentos com tipos de valor anulados como parâmetros, e você pode retornar um tipo de valor anulado de um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="3fca0-115">You can declare procedures with nullable value types as parameters, and you can return a nullable value type from a `Function` procedure.</span></span>

<span data-ttu-id="3fca0-116">Você não pode construir um tipo anulado em um `String`tipo de referência, como uma matriz, a ou uma classe.</span><span class="sxs-lookup"><span data-stu-id="3fca0-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="3fca0-117">O tipo subjacente deve ser um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="3fca0-117">The underlying type must be a value type.</span></span> <span data-ttu-id="3fca0-118">Para obter mais informações, consulte [Tipos de valor e tipos de referência](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="3fca0-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="3fca0-119">Usando uma variável de tipo anulado</span><span class="sxs-lookup"><span data-stu-id="3fca0-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="3fca0-120">Os membros mais importantes de um <xref:System.Nullable%601.HasValue%2A> tipo <xref:System.Nullable%601.Value%2A> de valor anulado são suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="3fca0-120">The most important members of a nullable value type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="3fca0-121">Para uma variável de um <xref:System.Nullable%601.HasValue%2A> tipo de valor anulado, informa se a variável contém um valor definido.</span><span class="sxs-lookup"><span data-stu-id="3fca0-121">For a variable of a nullable value type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="3fca0-122">Se <xref:System.Nullable%601.HasValue%2A> `True`for, você pode <xref:System.Nullable%601.Value%2A>ler o valor de .</span><span class="sxs-lookup"><span data-stu-id="3fca0-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="3fca0-123">Note que <xref:System.Nullable%601.HasValue%2A> <xref:System.Nullable%601.Value%2A> ambos `ReadOnly` e são propriedades.</span><span class="sxs-lookup"><span data-stu-id="3fca0-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="3fca0-124">Valores padrão</span><span class="sxs-lookup"><span data-stu-id="3fca0-124">Default Values</span></span>

<span data-ttu-id="3fca0-125">Quando você declara uma variável com um <xref:System.Nullable%601.HasValue%2A> tipo de valor `False`anulado, sua propriedade tem um valor padrão de .</span><span class="sxs-lookup"><span data-stu-id="3fca0-125">When you declare a variable with a nullable value type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="3fca0-126">Isso significa que, por padrão, a variável não tem valor definido, em vez do valor padrão de seu tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="3fca0-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="3fca0-127">No exemplo a seguir, a variável `numberOfChildren` inicialmente não tem `Integer` valor definido, embora o valor padrão do tipo seja 0.</span><span class="sxs-lookup"><span data-stu-id="3fca0-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="3fca0-128">Um valor nulo é útil para indicar um valor indefinido ou desconhecido.</span><span class="sxs-lookup"><span data-stu-id="3fca0-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="3fca0-129">Se `numberOfChildren` tivesse sido `Integer`declarado como , não haveria valor que poderia indicar que as informações não estão disponíveis no momento.</span><span class="sxs-lookup"><span data-stu-id="3fca0-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="3fca0-130">Armazenamento de valores</span><span class="sxs-lookup"><span data-stu-id="3fca0-130">Storing Values</span></span>

<span data-ttu-id="3fca0-131">Você armazena um valor em uma variável ou propriedade de um tipo de valor anulado da maneira típica.</span><span class="sxs-lookup"><span data-stu-id="3fca0-131">You store a value in a variable or property of a nullable value type in the typical way.</span></span> <span data-ttu-id="3fca0-132">O exemplo a seguir atribui `numberOfChildren` um valor à variável declarada no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="3fca0-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="3fca0-133">Se uma variável ou propriedade de um tipo de valor anulado contiver um valor definido, você pode fazê-lo reverter ao seu estado inicial de não ter um valor atribuído.</span><span class="sxs-lookup"><span data-stu-id="3fca0-133">If a variable or property of a nullable value type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="3fca0-134">Você faz isso definindo a `Nothing`variável ou propriedade para , como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3fca0-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="3fca0-135">Embora você possa `Nothing` atribuir a uma variável de um tipo `Nothing` de valor anulado, você não pode testá-lo usando o sinal de igual.</span><span class="sxs-lookup"><span data-stu-id="3fca0-135">Although you can assign `Nothing` to a variable of a nullable value type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="3fca0-136">Comparação que usa o `someVar = Nothing`sinal de `Nothing`igual, sempre avalia para .</span><span class="sxs-lookup"><span data-stu-id="3fca0-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="3fca0-137">Você pode testar a <xref:System.Nullable%601.HasValue%2A> propriedade `False`da variável para `Is` `IsNot` , ou testar usando o ou operador.</span><span class="sxs-lookup"><span data-stu-id="3fca0-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="3fca0-138">Recuperando valores</span><span class="sxs-lookup"><span data-stu-id="3fca0-138">Retrieving Values</span></span>

<span data-ttu-id="3fca0-139">Para recuperar o valor de uma variável de um tipo <xref:System.Nullable%601.HasValue%2A> de valor anulado, você deve primeiro testar sua propriedade para confirmar que ela tem um valor.</span><span class="sxs-lookup"><span data-stu-id="3fca0-139">To retrieve the value of a variable of a nullable value type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="3fca0-140">Se você tentar ler <xref:System.Nullable%601.HasValue%2A> o `False`valor quando <xref:System.InvalidOperationException> é , Visual Basic lança uma exceção.</span><span class="sxs-lookup"><span data-stu-id="3fca0-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="3fca0-141">O exemplo a seguir mostra a `numberOfChildren` maneira recomendada de ler a variável dos exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="3fca0-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="3fca0-142">Comparando tipos anulados</span><span class="sxs-lookup"><span data-stu-id="3fca0-142">Comparing Nullable Types</span></span>

<span data-ttu-id="3fca0-143">Quando `Boolean` variáveis anuladas são usadas em expressões booleanas, o resultado pode ser `True`, `False`ou `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="3fca0-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="3fca0-144">A seguir está a `And` `Or`tabela da verdade para e .</span><span class="sxs-lookup"><span data-stu-id="3fca0-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="3fca0-145">Porque `b1` `b2` e agora tem três valores possíveis, há nove combinações para avaliar.</span><span class="sxs-lookup"><span data-stu-id="3fca0-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="3fca0-146">b1</span><span class="sxs-lookup"><span data-stu-id="3fca0-146">b1</span></span>|<span data-ttu-id="3fca0-147">B2</span><span class="sxs-lookup"><span data-stu-id="3fca0-147">b2</span></span>|<span data-ttu-id="3fca0-148">b1 E b2</span><span class="sxs-lookup"><span data-stu-id="3fca0-148">b1 And b2</span></span>|<span data-ttu-id="3fca0-149">b1 ou b2</span><span class="sxs-lookup"><span data-stu-id="3fca0-149">b1 Or b2</span></span>|
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

<span data-ttu-id="3fca0-150">Quando o valor de uma variável `Nothing`ou expressão `true` `false`booleana é, não é nem nem .</span><span class="sxs-lookup"><span data-stu-id="3fca0-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="3fca0-151">Considere o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3fca0-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="3fca0-152">Neste exemplo, `b1 And b2` avalia-se para `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="3fca0-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="3fca0-153">Como resultado, `Else` a cláusula é `If` executada em cada declaração, e a saída é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="3fca0-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="3fca0-154">`AndAlso`e `OrElse`, que utilizam avaliação de curto-circuito, devem avaliar seus `Nothing`segundo operadores quando o primeiro avaliar para .</span><span class="sxs-lookup"><span data-stu-id="3fca0-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="3fca0-155">Propagação</span><span class="sxs-lookup"><span data-stu-id="3fca0-155">Propagation</span></span>

<span data-ttu-id="3fca0-156">Se um ou ambos os operands de uma operação aritmética, comparação, turno ou tipo for um tipo de valor anulado, o resultado da operação também é um tipo de valor anulado.</span><span class="sxs-lookup"><span data-stu-id="3fca0-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is a nullable value type, the result of the operation is also a nullable value type.</span></span> <span data-ttu-id="3fca0-157">Se ambos os operands `Nothing`tiverem valores que não são, a operação é realizada nos valores subjacentes dos operands, como se nenhum deles fosse um tipo de valor anulado.</span><span class="sxs-lookup"><span data-stu-id="3fca0-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable value type.</span></span> <span data-ttu-id="3fca0-158">No exemplo a seguir, variáveis `compare1` e `sum1` são digitadas implicitamente.</span><span class="sxs-lookup"><span data-stu-id="3fca0-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="3fca0-159">Se você descansar o ponteiro do mouse sobre eles, você verá que o compilador infere tipos de valor anulados para ambos.</span><span class="sxs-lookup"><span data-stu-id="3fca0-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable value types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="3fca0-160">Se um ou ambos os operands tiverem um valor de `Nothing`, o resultado será `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="3fca0-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="3fca0-161">Usando tipos anulados com dados</span><span class="sxs-lookup"><span data-stu-id="3fca0-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="3fca0-162">Um banco de dados é um dos lugares mais importantes para usar tipos de valor anulados.</span><span class="sxs-lookup"><span data-stu-id="3fca0-162">A database is one of the most important places to use nullable value types.</span></span> <span data-ttu-id="3fca0-163">Nem todos os objetos de banco de dados suportam atualmente tipos de valor anulados, mas os adaptadores de tabela gerados pelo designer suportam.</span><span class="sxs-lookup"><span data-stu-id="3fca0-163">Not all database objects currently support nullable value types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="3fca0-164">Consulte [o suporte tableAdapter para tipos anulados](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span><span class="sxs-lookup"><span data-stu-id="3fca0-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="3fca0-165">Confira também</span><span class="sxs-lookup"><span data-stu-id="3fca0-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="3fca0-166">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="3fca0-166">Data Types</span></span>](index.md)
- [<span data-ttu-id="3fca0-167">Tipos de valor e tipos de referência</span><span class="sxs-lookup"><span data-stu-id="3fca0-167">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="3fca0-168">Solução de problemas de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="3fca0-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="3fca0-169">Preencher conjuntos de dados usando TableAdapters</span><span class="sxs-lookup"><span data-stu-id="3fca0-169">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="3fca0-170">Operador If</span><span class="sxs-lookup"><span data-stu-id="3fca0-170">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="3fca0-171">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="3fca0-171">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="3fca0-172">Operador Is</span><span class="sxs-lookup"><span data-stu-id="3fca0-172">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="3fca0-173">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="3fca0-173">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="3fca0-174">Tipos de valor anulados (C#)</span><span class="sxs-lookup"><span data-stu-id="3fca0-174">Nullable Value Types (C#)</span></span>](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
