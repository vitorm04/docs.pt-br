---
title: Conversões cast e conversões
description: Saiba como o F# linguagem de programação fornece operadores de conversão para conversões aritméticas entre vários tipos primitivos.
ms.date: 05/16/2016
ms.openlocfilehash: 2a12d48106a267edfc67c9e7b3d3a7bd41d8261c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966603"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="83ec4-103">Conversões cast e conversões (F#)</span><span class="sxs-lookup"><span data-stu-id="83ec4-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="83ec4-104">Este tópico descreve o suporte para conversões de tipo no F#.</span><span class="sxs-lookup"><span data-stu-id="83ec4-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="83ec4-105">Tipos aritméticos</span><span class="sxs-lookup"><span data-stu-id="83ec4-105">Arithmetic Types</span></span>

<span data-ttu-id="83ec4-106">F#Fornece operadores de conversão para conversões aritméticas entre vários tipos primitivos, como entre inteiro e tipos de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="83ec4-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="83ec4-107">Os operadores de conversão integral e char verificou e formulários desmarcados; o ponto flutuante operadores e a `enum` operador de conversão não fizer isso.</span><span class="sxs-lookup"><span data-stu-id="83ec4-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="83ec4-108">Os formulários não verificados são definidos no `Microsoft.FSharp.Core.Operators` e os formulários verificados são definidos em `Microsoft.FSharp.Core.Operators.Checked`.</span><span class="sxs-lookup"><span data-stu-id="83ec4-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="83ec4-109">Os formulários verificados procurar estouro e geram uma exceção de tempo de execução se o valor resultante exceder os limites do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="83ec4-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="83ec4-110">Cada um desses operadores tem o mesmo nome que o nome do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="83ec4-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="83ec4-111">Por exemplo, no código a seguir, no qual os tipos explicitamente são anotados, `byte` aparece com dois significados diferentes.</span><span class="sxs-lookup"><span data-stu-id="83ec4-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="83ec4-112">A primeira ocorrência é o tipo e o segundo é o operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="83ec4-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="83ec4-113">A tabela a seguir mostra os operadores de conversão definidos em F#.</span><span class="sxs-lookup"><span data-stu-id="83ec4-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="83ec4-114">Operador</span><span class="sxs-lookup"><span data-stu-id="83ec4-114">Operator</span></span>|<span data-ttu-id="83ec4-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="83ec4-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="83ec4-116">Converta em bytes, um tipo sem sinal de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="83ec4-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="83ec4-117">Converta em byte assinado.</span><span class="sxs-lookup"><span data-stu-id="83ec4-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="83ec4-118">Converta em um inteiro com sinal de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="83ec4-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="83ec4-119">Converta em um inteiro sem sinal de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="83ec4-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="83ec4-120">Converta em um inteiro com sinal de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="83ec4-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="83ec4-121">Converta em um inteiro sem sinal de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="83ec4-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="83ec4-122">Converta em um inteiro com sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="83ec4-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="83ec4-123">Converta em um inteiro sem sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="83ec4-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="83ec4-124">Converta em um inteiro nativo.</span><span class="sxs-lookup"><span data-stu-id="83ec4-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="83ec4-125">Converta em um inteiro sem sinal de nativo.</span><span class="sxs-lookup"><span data-stu-id="83ec4-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="83ec4-126">Converta em um IEEE de precisão dupla de 64 bits número de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="83ec4-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="83ec4-127">Converta em um IEEE de precisão simples de 32 bits número de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="83ec4-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="83ec4-128">Converter em `System.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="83ec4-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="83ec4-129">Converter em `System.Char`, um caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="83ec4-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="83ec4-130">Converta em um tipo enumerado.</span><span class="sxs-lookup"><span data-stu-id="83ec4-130">Convert to an enumerated type.</span></span>|

<span data-ttu-id="83ec4-131">Além dos tipos primitivos internos, você pode usar esses operadores com tipos que implementam `op_Explicit` ou `op_Implicit` métodos com assinaturas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="83ec4-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="83ec4-132">Por exemplo, o `int` operador de conversão funciona com qualquer tipo que fornece um método estático `op_Explicit` que usa o tipo como um parâmetro e retorna `int`.</span><span class="sxs-lookup"><span data-stu-id="83ec4-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="83ec4-133">Como uma exceção especial para a regra geral que os métodos não podem ser sobrecarregados pelo tipo de retorno, você pode fazer isso para `op_Explicit` e `op_Implicit`.</span><span class="sxs-lookup"><span data-stu-id="83ec4-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="83ec4-134">Tipos enumerados</span><span class="sxs-lookup"><span data-stu-id="83ec4-134">Enumerated Types</span></span>

<span data-ttu-id="83ec4-135">O `enum` operador é um operador genérico que assume um parâmetro de tipo que representa o tipo do `enum` para converter em.</span><span class="sxs-lookup"><span data-stu-id="83ec4-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="83ec4-136">Quando ele converte em um tipo enumerado, digite as tentativas para determinar o tipo de inferência de tipos de `enum` que você deseja converter.</span><span class="sxs-lookup"><span data-stu-id="83ec4-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="83ec4-137">No exemplo a seguir, a variável `col1` não é anotado explicitamente, mas seu tipo é inferido do teste de igualdade posterior.</span><span class="sxs-lookup"><span data-stu-id="83ec4-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="83ec4-138">Portanto, o compilador pode deduzir que você está convertendo para uma `Color` enumeração.</span><span class="sxs-lookup"><span data-stu-id="83ec4-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="83ec4-139">Como alternativa, você pode fornecer uma anotação de tipo, assim como acontece com `col2` no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="83ec4-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

<span data-ttu-id="83ec4-140">Você também pode especificar o tipo de enumeração de destino explicitamente como um parâmetro de tipo, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="83ec4-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="83ec4-141">Observe que a enumeração converte trabalho somente se o tipo subjacente da enumeração é compatível com o tipo que está sendo convertido.</span><span class="sxs-lookup"><span data-stu-id="83ec4-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="83ec4-142">No código a seguir, a conversão Falha na compilação devido a incompatibilidade entre `int32` e `uint32`.</span><span class="sxs-lookup"><span data-stu-id="83ec4-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="83ec4-143">Para obter mais informações, consulte [enumerações](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="83ec4-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="83ec4-144">Conversão de tipos de objeto</span><span class="sxs-lookup"><span data-stu-id="83ec4-144">Casting Object Types</span></span>

<span data-ttu-id="83ec4-145">Conversão entre tipos em uma hierarquia de objetos é fundamental para programação orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="83ec4-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="83ec4-146">Há dois tipos básicos de conversões: conversão para cima (upcasting) e de conversão para baixo (Baixar).</span><span class="sxs-lookup"><span data-stu-id="83ec4-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="83ec4-147">Conversão de uma hierarquia significa que a conversão de uma referência de objeto derivado de uma referência ao objeto base.</span><span class="sxs-lookup"><span data-stu-id="83ec4-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="83ec4-148">Uma conversão é garantida para funcionar, contanto que a classe base está na hierarquia de herança da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="83ec4-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="83ec4-149">Conversão de uma hierarquia, de uma referência de objeto base para uma referência de objeto derivado, só terá sucesso se o objeto é, na verdade, uma instância do tipo de destino correto (derivado) ou um tipo derivado do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="83ec4-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="83ec4-150">F#Fornece operadores para esses tipos de conversões.</span><span class="sxs-lookup"><span data-stu-id="83ec4-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="83ec4-151">O `:>` operador converte até a hierarquia e o `:?>` operador converte abaixo na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="83ec4-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="83ec4-152">Upcasting</span><span class="sxs-lookup"><span data-stu-id="83ec4-152">Upcasting</span></span>

<span data-ttu-id="83ec4-153">Em muitas linguagens orientadas a objeto, upcasting é implícita; no F#, as regras são ligeiramente diferentes.</span><span class="sxs-lookup"><span data-stu-id="83ec4-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="83ec4-154">Upcasting é aplicada automaticamente quando você passar argumentos para métodos em um tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="83ec4-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="83ec4-155">No entanto, para as funções permitem a associação em um módulo, upcasting não é automática, a menos que o tipo de parâmetro é declarado como um tipo flexível.</span><span class="sxs-lookup"><span data-stu-id="83ec4-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="83ec4-156">Para obter mais informações, consulte [tipos flexíveis](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="83ec4-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="83ec4-157">O `:>` operador executa um estático cast, o que significa que o sucesso da conversão é determinado em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="83ec4-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="83ec4-158">Se uma conversão que usa `:>` será compilado com êxito, ele é uma conversão válida e não tem nenhuma possibilidade de falha em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="83ec4-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="83ec4-159">Você também pode usar o `upcast` operador para realizar essa conversão.</span><span class="sxs-lookup"><span data-stu-id="83ec4-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="83ec4-160">A expressão a seguir especifica uma conversão até a hierarquia:</span><span class="sxs-lookup"><span data-stu-id="83ec4-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="83ec4-161">Quando você usa o operador upcast, o compilador tentará inferir o tipo que você estiver convertendo a partir do contexto.</span><span class="sxs-lookup"><span data-stu-id="83ec4-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="83ec4-162">Se o compilador não puder determinar o tipo de destino, o compilador relatará um erro.</span><span class="sxs-lookup"><span data-stu-id="83ec4-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="83ec4-163">Baixar</span><span class="sxs-lookup"><span data-stu-id="83ec4-163">Downcasting</span></span>

<span data-ttu-id="83ec4-164">O `:?>` operador executa dinâmico cast, o que significa que o sucesso da conversão é determinado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="83ec4-164">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="83ec4-165">Uma conversão que usa o `:?>` operador não é verificado em tempo de compilação, mas em tempo de execução é feita uma tentativa de converter no tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="83ec4-165">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="83ec4-166">Se o objeto é compatível com o tipo de destino, a conversão for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="83ec4-166">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="83ec4-167">Se o objeto não é compatível com o tipo de destino, o tempo de execução gera uma `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="83ec4-167">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="83ec4-168">Você também pode usar o `downcast` operador para executar uma conversão de tipo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="83ec4-168">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="83ec4-169">A expressão a seguir especifica uma conversão de toda a hierarquia para um tipo que é inferido do contexto do programa:</span><span class="sxs-lookup"><span data-stu-id="83ec4-169">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="83ec4-170">Para o `upcast` operador, se o compilador não é possível inferir um tipo de destino específico do contexto, ele relatará um erro.</span><span class="sxs-lookup"><span data-stu-id="83ec4-170">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="83ec4-171">O código a seguir ilustra o uso do `:>` e `:?>` operadores.</span><span class="sxs-lookup"><span data-stu-id="83ec4-171">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="83ec4-172">O código ilustra que o `:?>` operador é melhor usado quando você sabe que a conversão seja bem-sucedida, porque ele gerará `InvalidCastException` se a conversão falhar.</span><span class="sxs-lookup"><span data-stu-id="83ec4-172">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="83ec4-173">Se você não souber que uma conversão seja bem-sucedida, um teste de tipo que usa um `match` expressão é melhor porque evita a sobrecarga de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="83ec4-173">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="83ec4-174">Porque os operadores genéricos `downcast` e `upcast` dependem a inferência de tipo para determinar o tipo de argumento e retornam, no código acima, você pode substituir</span><span class="sxs-lookup"><span data-stu-id="83ec4-174">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="83ec4-175">with</span><span class="sxs-lookup"><span data-stu-id="83ec4-175">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="83ec4-176">No código anterior, o tipo de argumento e os tipos de retorno são `Derived1` e `Base1`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="83ec4-176">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="83ec4-177">Para obter mais informações sobre testes de tipo, consulte [expressões de correspondência](match-Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="83ec4-177">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="83ec4-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83ec4-178">See also</span></span>

- [<span data-ttu-id="83ec4-179">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="83ec4-179">F# Language Reference</span></span>](index.md)
