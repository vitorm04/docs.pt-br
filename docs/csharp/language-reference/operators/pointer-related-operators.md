---
title: Operadores relacionados a ponteiro – referência do C#
description: Saiba mais sobre operadores C# que você pode usar ao trabalhar com indicadores.
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 50243f148f37f5f33f0c69ddd896549e7aea9462
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025112"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="4ec78-103">Operadores relacionados a ponteiro (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="4ec78-103">Pointer related operators (C# reference)</span></span>

<span data-ttu-id="4ec78-104">Você pode usar os operadores a seguir para trabalhar com ponteiros:</span><span class="sxs-lookup"><span data-stu-id="4ec78-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="4ec78-105">Operador unário [`&` (address-of)](#address-of-operator-): para obter o endereço de uma variável</span><span class="sxs-lookup"><span data-stu-id="4ec78-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="4ec78-106">Operador unário [`*` (indireção de ponteiro)](#pointer-indirection-operator-): para obter a variável apontada por um ponteiro</span><span class="sxs-lookup"><span data-stu-id="4ec78-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="4ec78-107">Os operadores [`->` (acesso de membro)](#pointer-member-access-operator--) e [`[]` (acesso de elemento)](#pointer-element-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="4ec78-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="4ec78-108">Operadores aritméticos [`+`, `-`, `++` e `--`](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="4ec78-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="4ec78-109">Operadores de comparação [`==`, `!=`, `<`, `>`, `<=` e `>=`](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="4ec78-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="4ec78-110">Para obter informações sobre tipos de ponteiros, veja [Tipos de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="4ec78-110">For information about pointer types, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4ec78-111">Qualquer operação com ponteiros exige um contexto [unsafe](../keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="4ec78-111">Any operation with pointers requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="4ec78-112">O código que contém blocos não seguros deve ser compilado com a opção do compilador [`-unsafe`](../compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4ec78-112">The code that contains unsafe blocks must be compiled with the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

## <a name="address-of-operator-amp"></a><span data-ttu-id="4ec78-113">Operador address-of &amp;</span><span class="sxs-lookup"><span data-stu-id="4ec78-113">Address-of operator &amp;</span></span>

<span data-ttu-id="4ec78-114">O operador unário `&` retorna o endereço de seu operando:</span><span class="sxs-lookup"><span data-stu-id="4ec78-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

<span data-ttu-id="4ec78-115">O operando do operador `&` deve ser uma variável fixa.</span><span class="sxs-lookup"><span data-stu-id="4ec78-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="4ec78-116">Variáveis *fixas* são variáveis que residem em locais de armazenamento não afetados pela operação do [coletor de lixo](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="4ec78-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="4ec78-117">No exemplo anterior, a variável local `number` é uma variável fixa, pois reside na pilha.</span><span class="sxs-lookup"><span data-stu-id="4ec78-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="4ec78-118">Variáveis que residem em locais de armazenamento que podem ser afetados pelo coletor de lixo (por exemplo, realocado) são chamadas de variáveis *móveis*.</span><span class="sxs-lookup"><span data-stu-id="4ec78-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="4ec78-119">Campos de objeto e elementos de matriz são exemplos de variáveis móveis.</span><span class="sxs-lookup"><span data-stu-id="4ec78-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="4ec78-120">Você poderá obter o endereço de uma variável móvel se a "firmar" ou "fixar" com a instrução [fixed](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4ec78-120">You can get the address of a movable variable if you "fix", or "pin", it with the [fixed](../keywords/fixed-statement.md) statement.</span></span> <span data-ttu-id="4ec78-121">O endereço obtido é válido somente pela duração do bloco de instrução `fixed`.</span><span class="sxs-lookup"><span data-stu-id="4ec78-121">The obtained address is valid only for the duration of the `fixed` statement block.</span></span> <span data-ttu-id="4ec78-122">O exemplo a seguir mostra como usar a instrução `fixed` e o operador `&`:</span><span class="sxs-lookup"><span data-stu-id="4ec78-122">The following example shows how to use the `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="4ec78-123">Não é possível obter o endereço de uma constante nem de um valor.</span><span class="sxs-lookup"><span data-stu-id="4ec78-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="4ec78-124">Para obter mais informações sobre variáveis fixas e móveis, veja a seção [Variáveis fixas e móveis](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) da [Especificação de linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="4ec78-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="4ec78-125">O operador binário `&` computa o [AND lógico](boolean-logical-operators.md#logical-and-operator-) de seus operandos Boolianos ou o [AND lógico bit a bit](bitwise-and-shift-operators.md#logical-and-operator-) de seus operandos integrais.</span><span class="sxs-lookup"><span data-stu-id="4ec78-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="4ec78-126">Operador de indireção de ponteiro\*</span><span class="sxs-lookup"><span data-stu-id="4ec78-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="4ec78-127">O operador unário de indireção de ponteiro `*` obtém a variável para a qual o operando aponta.</span><span class="sxs-lookup"><span data-stu-id="4ec78-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="4ec78-128">Também é conhecido como o operador de desreferenciar.</span><span class="sxs-lookup"><span data-stu-id="4ec78-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="4ec78-129">O operando do operador `*` deve ser de um tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="4ec78-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="4ec78-130">Não é possível aplicar o operador `*` a uma expressão do tipo `void*`.</span><span class="sxs-lookup"><span data-stu-id="4ec78-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="4ec78-131">O operador binário `*` computa o [produto](arithmetic-operators.md#multiplication-operator-) de seus operandos numéricos.</span><span class="sxs-lookup"><span data-stu-id="4ec78-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="4ec78-132">Operador de acesso a membro do ponteiro -></span><span class="sxs-lookup"><span data-stu-id="4ec78-132">Pointer member access operator -></span></span>

<span data-ttu-id="4ec78-133">O operador `->` combina [indireção do ponteiro](#pointer-indirection-operator-) e [acesso de membro](member-access-operators.md#member-access-operator-).</span><span class="sxs-lookup"><span data-stu-id="4ec78-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-operator-).</span></span> <span data-ttu-id="4ec78-134">Ou seja, se `x` for um ponteiro do tipo `T*` e `y` for um membro acessível de `T`, uma expressão do formulário</span><span class="sxs-lookup"><span data-stu-id="4ec78-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="4ec78-135">equivale a</span><span class="sxs-lookup"><span data-stu-id="4ec78-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="4ec78-136">O exemplo a seguir demonstra o uso do operador `->`:</span><span class="sxs-lookup"><span data-stu-id="4ec78-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="4ec78-137">Não é possível aplicar o operador `->` a uma expressão do tipo `void*`.</span><span class="sxs-lookup"><span data-stu-id="4ec78-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="4ec78-138">Operador de acesso a elemento do ponteiro []</span><span class="sxs-lookup"><span data-stu-id="4ec78-138">Pointer element access operator []</span></span>

<span data-ttu-id="4ec78-139">Para uma expressão `p` de um tipo de ponteiro, um acesso de elemento de ponteiro da forma `p[n]` é avaliado como `*(p + n)`, em que `n` deve ser do tipo implicitamente conversível em `int`, `uint`, `long` ou `ulong`.</span><span class="sxs-lookup"><span data-stu-id="4ec78-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="4ec78-140">Para obter informações sobre o comportamento do operador `+` com ponteiros, veja a seção [Adição ou subtração de um valor integral para ou de um ponteiro](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer).</span><span class="sxs-lookup"><span data-stu-id="4ec78-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="4ec78-141">O exemplo a seguir demonstra como acessar elementos da matriz com um ponteiro e o operador `[]`:</span><span class="sxs-lookup"><span data-stu-id="4ec78-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="4ec78-142">O exemplo usa o [operador `stackalloc`](stackalloc.md) para alocar um bloco de memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="4ec78-142">The example uses the [`stackalloc` operator](stackalloc.md) to allocate a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="4ec78-143">O operador de acesso de elemento de ponteiro não verifica se há erros fora dos limites.</span><span class="sxs-lookup"><span data-stu-id="4ec78-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="4ec78-144">Não é possível usar `[]` para acesso de elemento de ponteiro com uma expressão do tipo `void*`.</span><span class="sxs-lookup"><span data-stu-id="4ec78-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="4ec78-145">Você também pode usar o operador `[]` para [acesso de indexador ou elemento de matriz](member-access-operators.md#indexer-operator-).</span><span class="sxs-lookup"><span data-stu-id="4ec78-145">You also can use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="4ec78-146">Operadores aritméticos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="4ec78-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="4ec78-147">Você pode executar as seguintes operações aritméticas com ponteiros:</span><span class="sxs-lookup"><span data-stu-id="4ec78-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="4ec78-148">Adicionar ou subtrair um valor integral de ou para um ponteiro</span><span class="sxs-lookup"><span data-stu-id="4ec78-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="4ec78-149">Subtrair dois ponteiros</span><span class="sxs-lookup"><span data-stu-id="4ec78-149">Subtract two pointers</span></span>
- <span data-ttu-id="4ec78-150">Incrementar ou decrementar um ponteiro</span><span class="sxs-lookup"><span data-stu-id="4ec78-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="4ec78-151">Você não pode executar essas operações com ponteiros do tipo `void*`.</span><span class="sxs-lookup"><span data-stu-id="4ec78-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="4ec78-152">Para obter informações sobre operações aritméticas com suporte com tipos numéricos, veja [Operadores aritméticos](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="4ec78-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="4ec78-153">Adição ou subtração de um valor integral a ou de um ponteiro</span><span class="sxs-lookup"><span data-stu-id="4ec78-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="4ec78-154">Para um ponteiro `p` do tipo `T*` e uma expressão `n` de um tipo implicitamente conversível em `int`, `uint`, `long` ou `ulong`, adição e subtração são definidas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4ec78-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="4ec78-155">As expressões `p + n` e `n + p` produzem um ponteiro do tipo `T*` que resulta da adição de `n * sizeof(T)` ao endereço fornecido pelo `p`.</span><span class="sxs-lookup"><span data-stu-id="4ec78-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="4ec78-156">A expressão `p - n` produz um ponteiro do tipo `T*` que resulta da subtração de `n * sizeof(T)` ao endereço fornecido pelo `p`.</span><span class="sxs-lookup"><span data-stu-id="4ec78-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="4ec78-157">O [operador `sizeof`](../keywords/sizeof.md) obtém o tamanho de um tipo em bytes.</span><span class="sxs-lookup"><span data-stu-id="4ec78-157">The [`sizeof` operator](../keywords/sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="4ec78-158">O exemplo a seguir demonstra o uso do operador `+` com um ponteiro:</span><span class="sxs-lookup"><span data-stu-id="4ec78-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="4ec78-159">Subtração de ponteiro</span><span class="sxs-lookup"><span data-stu-id="4ec78-159">Pointer subtraction</span></span>

<span data-ttu-id="4ec78-160">Para dois ponteiros `p1` e `p2` do tipo `T*`, a expressão `p1 - p2` produz a diferença entre os endereços dados por `p1` e `p2` divididos por `sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="4ec78-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="4ec78-161">O tipo de resultado é `long`.</span><span class="sxs-lookup"><span data-stu-id="4ec78-161">The type of the result is `long`.</span></span> <span data-ttu-id="4ec78-162">Ou seja, `p1 - p2` é computado como `((long)(p1) - (long)(p2)) / sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="4ec78-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="4ec78-163">O exemplo a seguir demonstra a subtração de ponteiro:</span><span class="sxs-lookup"><span data-stu-id="4ec78-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="4ec78-164">Incrementar e decrementar ponteiros</span><span class="sxs-lookup"><span data-stu-id="4ec78-164">Pointer increment and decrement</span></span>

<span data-ttu-id="4ec78-165">O operador de incremento `++` [adiciona](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 ao operando do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="4ec78-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="4ec78-166">O operador de decremento `--` [subtrai](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 do operando do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="4ec78-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="4ec78-167">Os dois operadores têm suporte em duas formas: sufixo (`p++` e `p--`) e prefixo (`++p` e `--p`).</span><span class="sxs-lookup"><span data-stu-id="4ec78-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="4ec78-168">O resultado de `p++` e `p--` é o valor de `p` *antes* da operação.</span><span class="sxs-lookup"><span data-stu-id="4ec78-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="4ec78-169">O resultado de `++p` e `--p` é o valor de `p` *depois* da operação.</span><span class="sxs-lookup"><span data-stu-id="4ec78-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="4ec78-170">O exemplo a seguir demonstra o comportamento dos operadores de incremento de sufixo e prefixo:</span><span class="sxs-lookup"><span data-stu-id="4ec78-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="4ec78-171">Operadores de comparação de ponteiro</span><span class="sxs-lookup"><span data-stu-id="4ec78-171">Pointer comparison operators</span></span>

<span data-ttu-id="4ec78-172">Você pode usar os operadores `==`, `!=`, `<`, `>`, `<=` e `>=` para comparar os operandos de qualquer tipo de ponteiro, incluindo `void*`.</span><span class="sxs-lookup"><span data-stu-id="4ec78-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="4ec78-173">Esses operadores comparam os endereços fornecidos pelos dois operandos como se fossem inteiros sem sinal.</span><span class="sxs-lookup"><span data-stu-id="4ec78-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="4ec78-174">Para obter informações sobre o comportamento desses operadores para operandos de outros tipos, veja os artigos [Operadores de igualdade](equality-operators.md) e [Operadores de comparação](comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="4ec78-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="4ec78-175">Precedência do operador</span><span class="sxs-lookup"><span data-stu-id="4ec78-175">Operator precedence</span></span>

<span data-ttu-id="4ec78-176">A lista a seguir ordena operadores relacionados a ponteiro começando da precedência mais alta até a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="4ec78-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="4ec78-177">Operadores de incremento `x++` e decremento `x--` sufixados e os operadores `->` e `[]`</span><span class="sxs-lookup"><span data-stu-id="4ec78-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="4ec78-178">Operadores de incremento `++x` e decremento `--x` prefixados e os operadores `&` e `*`</span><span class="sxs-lookup"><span data-stu-id="4ec78-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="4ec78-179">Operadores de adição `+` e `-`</span><span class="sxs-lookup"><span data-stu-id="4ec78-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="4ec78-180">Operadores de comparação `<`, `>`, `<=` e `>=`</span><span class="sxs-lookup"><span data-stu-id="4ec78-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="4ec78-181">Operadores de igualdade `==` e `!=`</span><span class="sxs-lookup"><span data-stu-id="4ec78-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="4ec78-182">Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência do operador.</span><span class="sxs-lookup"><span data-stu-id="4ec78-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="4ec78-183">Para obter a lista completa de operadores do C# ordenada pelo nível de precedência, confira [Operadores do C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="4ec78-183">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4ec78-184">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="4ec78-184">Operator overloadability</span></span>

<span data-ttu-id="4ec78-185">Um tipo definido pelo usuário não pode sobrecarregar operadores relacionados a ponteiro `&`, `*`, `->` e `[]`.</span><span class="sxs-lookup"><span data-stu-id="4ec78-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4ec78-186">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="4ec78-186">C# language specification</span></span>

<span data-ttu-id="4ec78-187">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="4ec78-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="4ec78-188">Variáveis fixas e móveis</span><span class="sxs-lookup"><span data-stu-id="4ec78-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="4ec78-189">O operador address-of</span><span class="sxs-lookup"><span data-stu-id="4ec78-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="4ec78-190">Indireção de ponteiro</span><span class="sxs-lookup"><span data-stu-id="4ec78-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="4ec78-191">Acesso de membro do ponteiro</span><span class="sxs-lookup"><span data-stu-id="4ec78-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="4ec78-192">Acesso de elemento do ponteiro</span><span class="sxs-lookup"><span data-stu-id="4ec78-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="4ec78-193">Aritmética do ponteiro</span><span class="sxs-lookup"><span data-stu-id="4ec78-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="4ec78-194">Incrementar e decrementar ponteiros</span><span class="sxs-lookup"><span data-stu-id="4ec78-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="4ec78-195">Comparação de ponteiros</span><span class="sxs-lookup"><span data-stu-id="4ec78-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="4ec78-196">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ec78-196">See also</span></span>

- [<span data-ttu-id="4ec78-197">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="4ec78-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4ec78-198">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="4ec78-198">C# operators</span></span>](index.md)
- [<span data-ttu-id="4ec78-199">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="4ec78-199">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="4ec78-200">Palavra-chave unsafe</span><span class="sxs-lookup"><span data-stu-id="4ec78-200">unsafe keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="4ec78-201">Palavra-chave fixed</span><span class="sxs-lookup"><span data-stu-id="4ec78-201">fixed keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="4ec78-202">Operador stackalloc</span><span class="sxs-lookup"><span data-stu-id="4ec78-202">stackalloc operator</span></span>](stackalloc.md)
- [<span data-ttu-id="4ec78-203">Operador sizeof</span><span class="sxs-lookup"><span data-stu-id="4ec78-203">sizeof operator</span></span>](../keywords/sizeof.md)
