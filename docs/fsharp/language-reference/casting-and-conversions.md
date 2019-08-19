---
title: Conversões cast e conversões
description: Saiba como a F# linguagem de programação fornece operadores de conversão para conversões aritméticas entre vários tipos primitivos.
ms.date: 05/16/2016
ms.openlocfilehash: ee4df588caabf58c7b9e18961e217ef8f15fcf93
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630427"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="a0380-103">Conversões cast e conversões (F#)</span><span class="sxs-lookup"><span data-stu-id="a0380-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="a0380-104">Este tópico descreve o suporte para conversões de tipo F#no.</span><span class="sxs-lookup"><span data-stu-id="a0380-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="a0380-105">Tipos aritméticos</span><span class="sxs-lookup"><span data-stu-id="a0380-105">Arithmetic Types</span></span>

<span data-ttu-id="a0380-106">F#fornece operadores de conversão para conversões aritméticas entre vários tipos primitivos, como entre os tipos de ponto flutuante e inteiro.</span><span class="sxs-lookup"><span data-stu-id="a0380-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="a0380-107">Os operadores de conversão integral e Char marcaram e desmarcaram formulários; os operadores de ponto flutuante e `enum` o operador de conversão não.</span><span class="sxs-lookup"><span data-stu-id="a0380-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="a0380-108">Os formulários desmarcados são definidos no `Microsoft.FSharp.Core.Operators` e os formulários marcados são definidos em `Microsoft.FSharp.Core.Operators.Checked`.</span><span class="sxs-lookup"><span data-stu-id="a0380-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="a0380-109">Os formulários marcados verificam o estouro e geram uma exceção de tempo de execução se o valor resultante exceder os limites do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="a0380-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="a0380-110">Cada um desses operadores tem o mesmo nome que o nome do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="a0380-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="a0380-111">Por exemplo, no código a seguir, no qual os tipos são anotados explicitamente, `byte` aparece com dois significados diferentes.</span><span class="sxs-lookup"><span data-stu-id="a0380-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="a0380-112">A primeira ocorrência é o tipo e o segundo é o operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="a0380-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="a0380-113">A tabela a seguir mostra os operadores de F#conversão definidos no.</span><span class="sxs-lookup"><span data-stu-id="a0380-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="a0380-114">Operador</span><span class="sxs-lookup"><span data-stu-id="a0380-114">Operator</span></span>|<span data-ttu-id="a0380-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0380-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="a0380-116">Converter em byte, um tipo sem sinal de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="a0380-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="a0380-117">Converter em byte assinado.</span><span class="sxs-lookup"><span data-stu-id="a0380-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="a0380-118">Converter em um inteiro com sinal de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="a0380-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="a0380-119">Converta em um inteiro de 16 bits sem sinal.</span><span class="sxs-lookup"><span data-stu-id="a0380-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="a0380-120">Converter em um número inteiro de 32 bits assinado.</span><span class="sxs-lookup"><span data-stu-id="a0380-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="a0380-121">Converter em um inteiro sem sinal de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="a0380-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="a0380-122">Converter em um número inteiro de 64 bits assinado.</span><span class="sxs-lookup"><span data-stu-id="a0380-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="a0380-123">Converter em um inteiro sem sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="a0380-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="a0380-124">Converter em um inteiro nativo.</span><span class="sxs-lookup"><span data-stu-id="a0380-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="a0380-125">Converter em um inteiro nativo não assinado.</span><span class="sxs-lookup"><span data-stu-id="a0380-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="a0380-126">Converter em um número de ponto flutuante IEEE de precisão dupla de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="a0380-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="a0380-127">Converter em um número de ponto flutuante IEEE de precisão simples de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="a0380-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="a0380-128">Converter em `System.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a0380-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="a0380-129">Converter em `System.Char`, um caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="a0380-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="a0380-130">Converter em um tipo enumerado.</span><span class="sxs-lookup"><span data-stu-id="a0380-130">Convert to an enumerated type.</span></span>|

<span data-ttu-id="a0380-131">Além dos tipos primitivos internos, você pode usar esses operadores com tipos que implementam `op_Explicit` ou `op_Implicit` métodos com assinaturas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="a0380-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="a0380-132">Por exemplo, o `int` operador de conversão funciona com qualquer tipo que fornece um método `op_Explicit` estático que usa o tipo como um parâmetro e `int`retorna.</span><span class="sxs-lookup"><span data-stu-id="a0380-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="a0380-133">Como uma exceção especial para a regra geral que os métodos não podem ser sobrecarregados por tipo de retorno, você pode `op_Explicit` fazer `op_Implicit`isso para e.</span><span class="sxs-lookup"><span data-stu-id="a0380-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="a0380-134">Tipos enumerados</span><span class="sxs-lookup"><span data-stu-id="a0380-134">Enumerated Types</span></span>

<span data-ttu-id="a0380-135">O `enum` operador é um operador genérico que usa um parâmetro de tipo que representa o tipo de `enum` para o qual converter.</span><span class="sxs-lookup"><span data-stu-id="a0380-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="a0380-136">Quando ele é convertido em um tipo enumerado, a inferência de tipos tenta determinar o `enum` tipo do que você deseja converter.</span><span class="sxs-lookup"><span data-stu-id="a0380-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="a0380-137">No exemplo a seguir, a variável `col1` não é anotada explicitamente, mas seu tipo é inferido do teste de igualdade posterior.</span><span class="sxs-lookup"><span data-stu-id="a0380-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="a0380-138">Portanto, o compilador pode deduzir que você está convertendo para `Color` uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="a0380-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="a0380-139">Como alternativa, você pode fornecer uma anotação de tipo, como `col2` no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0380-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

<span data-ttu-id="a0380-140">Você também pode especificar o tipo de enumeração de destino explicitamente como um parâmetro de tipo, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="a0380-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="a0380-141">Observe que as conversões de enumeração só funcionam se o tipo subjacente da enumeração for compatível com o tipo que está sendo convertido.</span><span class="sxs-lookup"><span data-stu-id="a0380-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="a0380-142">No código a seguir, a conversão não é compilada devido à incompatibilidade `int32` entre `uint32`e.</span><span class="sxs-lookup"><span data-stu-id="a0380-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="a0380-143">Para obter mais informações, consulte [enumerações](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="a0380-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="a0380-144">Convertendo tipos de objeto</span><span class="sxs-lookup"><span data-stu-id="a0380-144">Casting Object Types</span></span>

<span data-ttu-id="a0380-145">A conversão entre os tipos em uma hierarquia de objetos é fundamental para a programação orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="a0380-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="a0380-146">Há dois tipos básicos de conversões: a conversão (upmissing) e a conversão para baixo (Downcasting).</span><span class="sxs-lookup"><span data-stu-id="a0380-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="a0380-147">A conversão de uma hierarquia significa converter de uma referência de objeto derivado para uma referência de objeto base.</span><span class="sxs-lookup"><span data-stu-id="a0380-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="a0380-148">Essa conversão é garantida para funcionar contanto que a classe base esteja na hierarquia de herança da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="a0380-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="a0380-149">A projeção de uma hierarquia, de uma referência de objeto base para uma referência de objeto derivado, só terá sucesso se o objeto realmente for uma instância do tipo de destino (derivado) correto ou um tipo derivado do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="a0380-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="a0380-150">F#fornece operadores para esses tipos de conversões.</span><span class="sxs-lookup"><span data-stu-id="a0380-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="a0380-151">O `:>` operador faz a conversão da hierarquia e o `:?>` operador faz a conversão na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="a0380-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="a0380-152">Convertendo</span><span class="sxs-lookup"><span data-stu-id="a0380-152">Upcasting</span></span>

<span data-ttu-id="a0380-153">Em muitas linguagens orientadas a objeto, a reformulação é implícita; no F#, as regras são um pouco diferentes.</span><span class="sxs-lookup"><span data-stu-id="a0380-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="a0380-154">A conversão é aplicada automaticamente quando você passa argumentos para métodos em um tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="a0380-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="a0380-155">No entanto, para as funções que permitem associar em um módulo, a conversão não é automática, a menos que o tipo de parâmetro seja declarado como um tipo flexível.</span><span class="sxs-lookup"><span data-stu-id="a0380-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="a0380-156">Para obter mais informações, consulte [tipos flexíveis](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="a0380-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="a0380-157">O `:>` operador executa uma conversão estática, o que significa que o sucesso da conversão é determinado no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="a0380-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="a0380-158">Se uma conversão que usa `:>` compila com êxito, é uma conversão válida e não tem chance de falha no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a0380-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="a0380-159">Você também pode usar o `upcast` operador para executar tal conversão.</span><span class="sxs-lookup"><span data-stu-id="a0380-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="a0380-160">A expressão a seguir especifica uma conversão na hierarquia:</span><span class="sxs-lookup"><span data-stu-id="a0380-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="a0380-161">Quando você usa o operador upcast, o compilador tenta inferir o tipo que você está convertendo do contexto.</span><span class="sxs-lookup"><span data-stu-id="a0380-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="a0380-162">Se o compilador não puder determinar o tipo de destino, o compilador relatará um erro.</span><span class="sxs-lookup"><span data-stu-id="a0380-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="a0380-163">Downcasting</span><span class="sxs-lookup"><span data-stu-id="a0380-163">Downcasting</span></span>

<span data-ttu-id="a0380-164">O `:?>` operador executa uma conversão dinâmica, o que significa que o sucesso da conversão é determinado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a0380-164">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="a0380-165">Uma conversão que usa o `:?>` operador não é verificada no momento da compilação; mas no tempo de execução, é feita uma tentativa de conversão para o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="a0380-165">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="a0380-166">Se o objeto for compatível com o tipo de destino, a conversão será realizada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="a0380-166">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="a0380-167">Se o objeto não for compatível com o tipo de destino, o tempo de `InvalidCastException`execução gerará um.</span><span class="sxs-lookup"><span data-stu-id="a0380-167">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="a0380-168">Você também pode usar o `downcast` operador para executar uma conversão dinâmica de tipo.</span><span class="sxs-lookup"><span data-stu-id="a0380-168">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="a0380-169">A expressão a seguir especifica uma conversão na hierarquia para um tipo inferido do contexto do programa:</span><span class="sxs-lookup"><span data-stu-id="a0380-169">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="a0380-170">Como para o `upcast` operador, se o compilador não puder inferir um tipo de destino específico do contexto, ele relatará um erro.</span><span class="sxs-lookup"><span data-stu-id="a0380-170">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="a0380-171">O código a seguir ilustra o uso dos `:>` operadores `:?>` e.</span><span class="sxs-lookup"><span data-stu-id="a0380-171">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="a0380-172">O código ilustra que o `:?>` operador é melhor usado quando você sabe que a conversão terá êxito, pois ela `InvalidCastException` gera se a conversão falha.</span><span class="sxs-lookup"><span data-stu-id="a0380-172">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="a0380-173">Se você não souber que uma conversão terá sucesso, um teste de tipo que usa uma `match` expressão é melhor porque evita a sobrecarga de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="a0380-173">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="a0380-174">Como os operadores `downcast` genéricos `upcast` e contam com a inferência de tipos para determinar o argumento e o tipo de retorno, no código acima, você pode substituir</span><span class="sxs-lookup"><span data-stu-id="a0380-174">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="a0380-175">with</span><span class="sxs-lookup"><span data-stu-id="a0380-175">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="a0380-176">No código anterior, o tipo de argumento e os tipos de `Derived1` retorno `Base1`são e, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a0380-176">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="a0380-177">Para obter mais informações sobre testes de tipo, consulte [Match Expressions](match-Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a0380-177">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0380-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0380-178">See also</span></span>

- [<span data-ttu-id="a0380-179">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="a0380-179">F# Language Reference</span></span>](index.md)
