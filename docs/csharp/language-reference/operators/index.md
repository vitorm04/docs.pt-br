---
title: Operadores C#
ms.date: 04/04/2018
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 4958f3e28b80fca2086d45827df1ced8fc26bd8e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672284"
---
# <a name="c-operators"></a><span data-ttu-id="1b694-102">Operadores C#</span><span class="sxs-lookup"><span data-stu-id="1b694-102">C# operators</span></span>

<span data-ttu-id="1b694-103">O C# fornece muitos operadores, que são símbolos que especificam as operações (matemática, indexação, chamada de função, etc.) para executar em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="1b694-103">C# provides many operators, which are symbols that specify which operations (math, indexing, function call, etc.) to perform in an expression.</span></span> <span data-ttu-id="1b694-104">Você pode [sobrecarregar](../../programming-guide/statements-expressions-operators/overloadable-operators.md) muitos operadores para alterar seu significado quando aplicados a um tipo definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="1b694-104">You can [overload](../../programming-guide/statements-expressions-operators/overloadable-operators.md) many operators to change their meaning when applied to a user-defined type.</span></span>

<span data-ttu-id="1b694-105">As operações em tipos integrais (como `==`, `!=`, `<`, `>`, `&`, `|`) geralmente são permitidas em tipos de enumeração (`enum`).</span><span class="sxs-lookup"><span data-stu-id="1b694-105">Operations on integral types (such as `==`, `!=`, `<`, `>`, `&`, `|`) are generally allowed on enumeration (`enum`) types.</span></span>

<span data-ttu-id="1b694-106">As seções abaixo listam os operadores em C# da precedência mais alta para a mais baixa.</span><span class="sxs-lookup"><span data-stu-id="1b694-106">The sections below list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="1b694-107">Os operadores em cada seção compartilham o mesmo nível de precedência.</span><span class="sxs-lookup"><span data-stu-id="1b694-107">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="1b694-108">Operadores primários</span><span class="sxs-lookup"><span data-stu-id="1b694-108">Primary operators</span></span>

<span data-ttu-id="1b694-109">Esses são os operadores de precedência mais alta.</span><span class="sxs-lookup"><span data-stu-id="1b694-109">These are the highest precedence operators.</span></span>

<span data-ttu-id="1b694-110">[x.y](member-access-operator.md) – acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="1b694-110">[x.y](member-access-operator.md) – member access.</span></span>

<span data-ttu-id="1b694-111">[x?.y](null-conditional-operators.md) – acesso de membro condicional nulo.</span><span class="sxs-lookup"><span data-stu-id="1b694-111">[x?.y](null-conditional-operators.md) – null conditional member access.</span></span> <span data-ttu-id="1b694-112">Retornará `null` se o operando esquerdo for avaliado como `null`.</span><span class="sxs-lookup"><span data-stu-id="1b694-112">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="1b694-113">[x?[y]](null-conditional-operators.md) – acesso de índice condicional nulo.</span><span class="sxs-lookup"><span data-stu-id="1b694-113">[x?[y]](null-conditional-operators.md) - null conditional index access.</span></span> <span data-ttu-id="1b694-114">Retornará `null` se o operando esquerdo for avaliado como `null`.</span><span class="sxs-lookup"><span data-stu-id="1b694-114">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="1b694-115">[f(x)](invocation-operator.md) – invocação de função.</span><span class="sxs-lookup"><span data-stu-id="1b694-115">[f(x)](invocation-operator.md) – function invocation.</span></span>

<span data-ttu-id="1b694-116">[a&#91;x&#93;](index-operator.md) – indexação de objeto de agregação.</span><span class="sxs-lookup"><span data-stu-id="1b694-116">[a&#91;x&#93;](index-operator.md) – aggregate object indexing.</span></span>

<span data-ttu-id="1b694-117">[x++](arithmetic-operators.md#increment-operator-) – incremento de sufixo.</span><span class="sxs-lookup"><span data-stu-id="1b694-117">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="1b694-118">Retorna o valor de x e, em seguida, atualiza o local de armazenamento com o valor de x que é um número maior (normalmente adiciona o inteiro 1).</span><span class="sxs-lookup"><span data-stu-id="1b694-118">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="1b694-119">[x--](arithmetic-operators.md#decrement-operator---) – decremento de sufixo.</span><span class="sxs-lookup"><span data-stu-id="1b694-119">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="1b694-120">Retorna o valor de x e, em seguida, atualiza o local de armazenamento com o valor de x que é um número menor (normalmente subtrai o inteiro 1).</span><span class="sxs-lookup"><span data-stu-id="1b694-120">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="1b694-121">[new](../keywords/new-operator.md) – instanciação de tipo.</span><span class="sxs-lookup"><span data-stu-id="1b694-121">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="1b694-122">[typeof](../keywords/typeof.md) – retorna o objeto <xref:System.Type> que representa o operando.</span><span class="sxs-lookup"><span data-stu-id="1b694-122">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="1b694-123">[checked](../keywords/checked.md) – habilita a verificação de estouro para operações de inteiros.</span><span class="sxs-lookup"><span data-stu-id="1b694-123">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="1b694-124">[unchecked](../keywords/unchecked.md) – desabilita a verificação de estouro para operações de inteiros.</span><span class="sxs-lookup"><span data-stu-id="1b694-124">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="1b694-125">Este é o comportamento padrão do compilador.</span><span class="sxs-lookup"><span data-stu-id="1b694-125">This is the default compiler behavior.</span></span>

<span data-ttu-id="1b694-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produz o valor padrão do tipo T.</span><span class="sxs-lookup"><span data-stu-id="1b694-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="1b694-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declara e retorna uma instância delegada.</span><span class="sxs-lookup"><span data-stu-id="1b694-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="1b694-128">[sizeof](../keywords/sizeof.md) – retorna o tamanho em bytes do operando do tipo.</span><span class="sxs-lookup"><span data-stu-id="1b694-128">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="1b694-129">[->](dereference-operator.md) – desreferência de ponteiro combinada com acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="1b694-129">[->](dereference-operator.md) – pointer dereferencing combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="1b694-130">Operadores unários</span><span class="sxs-lookup"><span data-stu-id="1b694-130">Unary operators</span></span>

<span data-ttu-id="1b694-131">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-131">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-132">[+x](addition-operator.md) – retorna o valor de x.</span><span class="sxs-lookup"><span data-stu-id="1b694-132">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="1b694-133">[-x](subtraction-operator.md) – negação numérica.</span><span class="sxs-lookup"><span data-stu-id="1b694-133">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="1b694-134">[\!x](boolean-logical-operators.md#logical-negation-operator-) – negação lógica.</span><span class="sxs-lookup"><span data-stu-id="1b694-134">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="1b694-135">[~x](bitwise-complement-operator.md) – complemento bit a bit.</span><span class="sxs-lookup"><span data-stu-id="1b694-135">[~x](bitwise-complement-operator.md) – bitwise complement.</span></span>

<span data-ttu-id="1b694-136">[++x](arithmetic-operators.md#increment-operator-) – incremento de prefixo.</span><span class="sxs-lookup"><span data-stu-id="1b694-136">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="1b694-137">Retorna o valor de x depois de atualizar o local de armazenamento com o valor de x que é um número maior (normalmente adiciona o inteiro 1).</span><span class="sxs-lookup"><span data-stu-id="1b694-137">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="1b694-138">[--x](arithmetic-operators.md#decrement-operator---) – decremento de prefixo.</span><span class="sxs-lookup"><span data-stu-id="1b694-138">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="1b694-139">Retorna o valor de x depois de atualizar o local de armazenamento com o valor de x que é um número menor (normalmente subtrai o inteiro 1).</span><span class="sxs-lookup"><span data-stu-id="1b694-139">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="1b694-140">[(T)x](invocation-operator.md) – conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="1b694-140">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="1b694-141">[await](../keywords/await.md) – aguarda um `Task`.</span><span class="sxs-lookup"><span data-stu-id="1b694-141">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="1b694-142">[&x](and-operator.md) – endereço.</span><span class="sxs-lookup"><span data-stu-id="1b694-142">[&x](and-operator.md) – address of.</span></span>

<span data-ttu-id="1b694-143">[\*x](multiplication-operator.md) – desreferenciamento.</span><span class="sxs-lookup"><span data-stu-id="1b694-143">[\*x](multiplication-operator.md) – dereferencing.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="1b694-144">Operadores de multiplicação</span><span class="sxs-lookup"><span data-stu-id="1b694-144">Multiplicative operators</span></span>

<span data-ttu-id="1b694-145">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-145">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-146">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplicação.</span><span class="sxs-lookup"><span data-stu-id="1b694-146">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="1b694-147">[x / y](arithmetic-operators.md#division-operator-) – divisão.</span><span class="sxs-lookup"><span data-stu-id="1b694-147">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="1b694-148">Se os operandos forem inteiros, o resultado será um inteiro truncado para zero (por exemplo, `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="1b694-148">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="1b694-149">[x % y](arithmetic-operators.md#remainder-operator-) – restante.</span><span class="sxs-lookup"><span data-stu-id="1b694-149">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="1b694-150">Se os operandos forem inteiros, isso retornará o resto da divisão de x por y.</span><span class="sxs-lookup"><span data-stu-id="1b694-150">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="1b694-151">Se `q = x / y` e `r = x % y`, então `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="1b694-151">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="1b694-152">Operadores aditivos</span><span class="sxs-lookup"><span data-stu-id="1b694-152">Additive operators</span></span>

<span data-ttu-id="1b694-153">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-153">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-154">[x + y](arithmetic-operators.md#addition-operator-) – adição.</span><span class="sxs-lookup"><span data-stu-id="1b694-154">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="1b694-155">[x – y](arithmetic-operators.md#subtraction-operator--) – subtração.</span><span class="sxs-lookup"><span data-stu-id="1b694-155">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="1b694-156">Operadores shift</span><span class="sxs-lookup"><span data-stu-id="1b694-156">Shift operators</span></span>

<span data-ttu-id="1b694-157">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-157">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-158">[x <\< y](left-shift-operator.md) – bits de deslocamento para a esquerda e preenche com zero à direita.</span><span class="sxs-lookup"><span data-stu-id="1b694-158">[x <\<  y](left-shift-operator.md) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="1b694-159">[x >> y](right-shift-operator.md) – bits de deslocamento para a direita.</span><span class="sxs-lookup"><span data-stu-id="1b694-159">[x >> y](right-shift-operator.md) – shift bits right.</span></span> <span data-ttu-id="1b694-160">Se o operando esquerdo for `int` ou `long`, então, os bits à esquerda serão preenchidos com o bit de sinal.</span><span class="sxs-lookup"><span data-stu-id="1b694-160">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="1b694-161">Se o operando esquerdo for `uint` ou `ulong`, então, os bits à esquerda serão preenchidos com zero.</span><span class="sxs-lookup"><span data-stu-id="1b694-161">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="1b694-162">Operadores de teste de tipo e relacional</span><span class="sxs-lookup"><span data-stu-id="1b694-162">Relational and type-testing operators</span></span>

<span data-ttu-id="1b694-163">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-163">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-164">[x \< y](less-than-operator.md) – menor que (verdadeiro se x for menor que y).</span><span class="sxs-lookup"><span data-stu-id="1b694-164">[x \< y](less-than-operator.md) – less than (true if x is less than y).</span></span>

<span data-ttu-id="1b694-165">[x > y](greater-than-operator.md) – maior que (verdadeiro se x for maior que y).</span><span class="sxs-lookup"><span data-stu-id="1b694-165">[x > y](greater-than-operator.md) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="1b694-166">[x \<= y](less-than-equal-operator.md) – menor ou igual a.</span><span class="sxs-lookup"><span data-stu-id="1b694-166">[x \<= y](less-than-equal-operator.md) – less than or equal to.</span></span>

<span data-ttu-id="1b694-167">[x > = y](greater-than-equal-operator.md) – maior que ou igual a.</span><span class="sxs-lookup"><span data-stu-id="1b694-167">[x >= y](greater-than-equal-operator.md) – greater than or equal to.</span></span>

<span data-ttu-id="1b694-168">[is](../keywords/is.md) – compatibilidade de tipo.</span><span class="sxs-lookup"><span data-stu-id="1b694-168">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="1b694-169">Retornará true se o operando esquerdo avaliado puder ser convertido no tipo especificado no operando à direita (um tipo estático).</span><span class="sxs-lookup"><span data-stu-id="1b694-169">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="1b694-170">[as](../keywords/as.md) – conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="1b694-170">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="1b694-171">Retorna o operando esquerdo convertido para o tipo especificado pelo operando à direita (um tipo estático), mas `as` retorna `null` em que `(T)x` lançaria uma exceção.</span><span class="sxs-lookup"><span data-stu-id="1b694-171">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="1b694-172">Operadores de igualdade</span><span class="sxs-lookup"><span data-stu-id="1b694-172">Equality operators</span></span>

<span data-ttu-id="1b694-173">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-173">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-174">[x == y](equality-operators.md#equality-operator-) – igualdade.</span><span class="sxs-lookup"><span data-stu-id="1b694-174">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="1b694-175">Por padrão, para tipos de referência diferentes de `string`, isso retorna uma igualdade de referência (teste de identidade).</span><span class="sxs-lookup"><span data-stu-id="1b694-175">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="1b694-176">No entanto, os tipos podem sobrecarregar `==`, portanto, se sua intenção for testar a identidade, é melhor usar o método `ReferenceEquals` em `object`.</span><span class="sxs-lookup"><span data-stu-id="1b694-176">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="1b694-177">[x != y](equality-operators.md#inequality-operator-) – não é igual.</span><span class="sxs-lookup"><span data-stu-id="1b694-177">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="1b694-178">Consulte o comentário sobre `==`.</span><span class="sxs-lookup"><span data-stu-id="1b694-178">See comment for `==`.</span></span> <span data-ttu-id="1b694-179">Se um tipo sobrecarregar `==`, então, ele deverá sobrecarregar `!=`.</span><span class="sxs-lookup"><span data-stu-id="1b694-179">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="1b694-180">Operador AND lógico</span><span class="sxs-lookup"><span data-stu-id="1b694-180">Logical AND operator</span></span>

<span data-ttu-id="1b694-181">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-181">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-182">[x & y](and-operator.md) – AND lógico ou bit a bit.</span><span class="sxs-lookup"><span data-stu-id="1b694-182">[x & y](and-operator.md) – logical or bitwise AND.</span></span> <span data-ttu-id="1b694-183">Geralmente, você pode usar isso com tipos de inteiro e tipos `enum`.</span><span class="sxs-lookup"><span data-stu-id="1b694-183">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="1b694-184">Operador XOR lógico</span><span class="sxs-lookup"><span data-stu-id="1b694-184">Logical XOR operator</span></span>

<span data-ttu-id="1b694-185">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-185">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-186">[x ^ y](xor-operator.md) – XOR lógico ou bit a bit.</span><span class="sxs-lookup"><span data-stu-id="1b694-186">[x ^ y](xor-operator.md) – logical or bitwise XOR.</span></span> <span data-ttu-id="1b694-187">Geralmente, você pode usar isso com tipos de inteiro e tipos `enum`.</span><span class="sxs-lookup"><span data-stu-id="1b694-187">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="1b694-188">Operador lógico OU</span><span class="sxs-lookup"><span data-stu-id="1b694-188">Logical OR operator</span></span>

<span data-ttu-id="1b694-189">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-190">[x &#124; y](or-operator.md) – OR lógico ou bit a bit.</span><span class="sxs-lookup"><span data-stu-id="1b694-190">[x &#124; y](or-operator.md) – logical or bitwise OR.</span></span> <span data-ttu-id="1b694-191">Geralmente, você pode usar isso com tipos de inteiro e tipos `enum`.</span><span class="sxs-lookup"><span data-stu-id="1b694-191">You can generally use this with integer types and `enum` types.</span></span>

## <a name="true-operator"></a><span data-ttu-id="1b694-192">Operador true</span><span class="sxs-lookup"><span data-stu-id="1b694-192">True operator</span></span>

<span data-ttu-id="1b694-193">O operador [true](../keywords/true-false-operators.md) retorna o valor [bool](../keywords/bool.md) `true` para indicar que um operando é definitivamente verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="1b694-193">The [true](../keywords/true-false-operators.md) operator returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span> 

## <a name="false-operator"></a><span data-ttu-id="1b694-194">Operador false</span><span class="sxs-lookup"><span data-stu-id="1b694-194">False operator</span></span>

<span data-ttu-id="1b694-195">O operador [false](../keywords/true-false-operators.md) retorna o valor [bool](../keywords/bool.md) `true` para indicar que um operando é definitivamente falso.</span><span class="sxs-lookup"><span data-stu-id="1b694-195">The [false](../keywords/true-false-operators.md) operator returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span> 

## <a name="conditional-and-operator"></a><span data-ttu-id="1b694-196">Operador AND condicional</span><span class="sxs-lookup"><span data-stu-id="1b694-196">Conditional AND operator</span></span>

<span data-ttu-id="1b694-197">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-197">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-198">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – AND lógico.</span><span class="sxs-lookup"><span data-stu-id="1b694-198">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="1b694-199">Se o primeiro operando for avaliado como falso, então o C# não avaliará o segundo operando.</span><span class="sxs-lookup"><span data-stu-id="1b694-199">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="1b694-200">Operador OR condicional</span><span class="sxs-lookup"><span data-stu-id="1b694-200">Conditional OR operator</span></span>

<span data-ttu-id="1b694-201">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-201">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-202">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – OR lógico.</span><span class="sxs-lookup"><span data-stu-id="1b694-202">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="1b694-203">Se o primeiro operando for avaliado como verdadeiro, então o C# não avaliará o segundo operando.</span><span class="sxs-lookup"><span data-stu-id="1b694-203">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="1b694-204">Operador de coalescência nula</span><span class="sxs-lookup"><span data-stu-id="1b694-204">Null-coalescing operator</span></span>

<span data-ttu-id="1b694-205">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-205">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-206">[x ?? y](null-coalescing-operator.md) – retornará `x` se for não `null`; caso contrário, retornará `y`.</span><span class="sxs-lookup"><span data-stu-id="1b694-206">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="1b694-207">Operador condicional</span><span class="sxs-lookup"><span data-stu-id="1b694-207">Conditional operator</span></span>

<span data-ttu-id="1b694-208">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-208">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-209">[t ? x : y](conditional-operator.md) – se o teste `t` for avaliado como verdadeiro, então ele avaliará e retornará `x`; caso contrário, avaliará e retornará `y`.</span><span class="sxs-lookup"><span data-stu-id="1b694-209">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="1b694-210">Atribuição e operadores de Lambda</span><span class="sxs-lookup"><span data-stu-id="1b694-210">Assignment and Lambda operators</span></span>

<span data-ttu-id="1b694-211">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1b694-211">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b694-212">[x = y](assignment-operator.md) – atribuição.</span><span class="sxs-lookup"><span data-stu-id="1b694-212">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="1b694-213">[x += y](addition-assignment-operator.md) – incremento.</span><span class="sxs-lookup"><span data-stu-id="1b694-213">[x += y](addition-assignment-operator.md) – increment.</span></span> <span data-ttu-id="1b694-214">Adicione o valor de `y` para o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="1b694-214">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="1b694-215">Se `x` designar um `event`, então, `y` deverá ser uma função adequada que o C# adiciona como um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="1b694-215">If `x` designates an `event`, then `y` must be an appropriate function that C# adds as an event handler.</span></span>

<span data-ttu-id="1b694-216">[x -= y](subtraction-assignment-operator.md) – diminuir.</span><span class="sxs-lookup"><span data-stu-id="1b694-216">[x -= y](subtraction-assignment-operator.md) – decrement.</span></span> <span data-ttu-id="1b694-217">Subtraia o valor de `y` do valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="1b694-217">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="1b694-218">Se `x` designar um `event`, então, `y` deverá ser uma função adequada que o C# remove como um manipulador de eventos</span><span class="sxs-lookup"><span data-stu-id="1b694-218">If `x` designates an `event`, then `y` must be an appropriate function that C# removes as an event handler</span></span>

<span data-ttu-id="1b694-219">[x \*= y](multiplication-assignment-operator.md) – atribuição de multiplicação.</span><span class="sxs-lookup"><span data-stu-id="1b694-219">[x \*= y](multiplication-assignment-operator.md) – multiplication assignment.</span></span> <span data-ttu-id="1b694-220">Multiplique o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="1b694-220">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b694-221">[x /= y](arithmetic-operators.md#compound-assignment) – atribuição de divisão.</span><span class="sxs-lookup"><span data-stu-id="1b694-221">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="1b694-222">Divida o valor de `x` pelo valor de `y`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="1b694-222">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b694-223">[x %= y](arithmetic-operators.md#compound-assignment) – atribuição restante.</span><span class="sxs-lookup"><span data-stu-id="1b694-223">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="1b694-224">Divida o valor de `x` pelo valor de `y`, armazene o resto em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="1b694-224">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="1b694-225">[x &= y](and-assignment-operator.md) – atribuição AND.</span><span class="sxs-lookup"><span data-stu-id="1b694-225">[x &= y](and-assignment-operator.md) – AND assignment.</span></span> <span data-ttu-id="1b694-226">AND o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="1b694-226">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b694-227">[x &#124;= y](or-assignment-operator.md) – atribuição OR.</span><span class="sxs-lookup"><span data-stu-id="1b694-227">[x &#124;= y](or-assignment-operator.md) – OR assignment.</span></span> <span data-ttu-id="1b694-228">OR o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="1b694-228">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b694-229">[x ^= y](xor-assignment-operator.md) – atribuição XOR.</span><span class="sxs-lookup"><span data-stu-id="1b694-229">[x ^= y](xor-assignment-operator.md) – XOR assignment.</span></span> <span data-ttu-id="1b694-230">XOR o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="1b694-230">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b694-231">[x <<= y](left-shift-assignment-operator.md) – atribuição de deslocamento para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="1b694-231">[x <<= y](left-shift-assignment-operator.md) – left-shift assignment.</span></span> <span data-ttu-id="1b694-232">Desloque o valor de `x` para a esquerda em `y` casas decimais, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="1b694-232">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b694-233">[x >>= y](right-shift-assignment-operator.md) – atribuição de deslocamento para a direita.</span><span class="sxs-lookup"><span data-stu-id="1b694-233">[x >>= y](right-shift-assignment-operator.md) – right-shift assignment.</span></span> <span data-ttu-id="1b694-234">Desloque o valor de `x` para a direita em `y` casas decimais, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="1b694-234">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b694-235">[=>](lambda-operator.md) – declaração de lambda.</span><span class="sxs-lookup"><span data-stu-id="1b694-235">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b694-236">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b694-236">See also</span></span>

- [<span data-ttu-id="1b694-237">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1b694-237">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1b694-238">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1b694-238">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1b694-239">C#</span><span class="sxs-lookup"><span data-stu-id="1b694-239">C#</span></span>](../../index.md)
- [<span data-ttu-id="1b694-240">Operadores sobrecarregáveis</span><span class="sxs-lookup"><span data-stu-id="1b694-240">Overloadable Operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="1b694-241">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="1b694-241">C# Keywords</span></span>](../keywords/index.md)
