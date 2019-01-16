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
ms.openlocfilehash: 6380fa4ec99f598be0d01db1061900520e94d5f1
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333402"
---
# <a name="c-operators"></a><span data-ttu-id="889c2-102">Operadores C#</span><span class="sxs-lookup"><span data-stu-id="889c2-102">C# operators</span></span>

<span data-ttu-id="889c2-103">O C# fornece muitos operadores, que são símbolos que especificam as operações (matemática, indexação, chamada de função, etc.) para executar em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="889c2-103">C# provides many operators, which are symbols that specify which operations (math, indexing, function call, etc.) to perform in an expression.</span></span> <span data-ttu-id="889c2-104">Você pode [sobrecarregar](../../programming-guide/statements-expressions-operators/overloadable-operators.md) muitos operadores para alterar seu significado quando aplicados a um tipo definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="889c2-104">You can [overload](../../programming-guide/statements-expressions-operators/overloadable-operators.md) many operators to change their meaning when applied to a user-defined type.</span></span>

<span data-ttu-id="889c2-105">As operações em tipos integrais (como `==`, `!=`, `<`, `>`, `&`, `|`) geralmente são permitidas em tipos de enumeração (`enum`).</span><span class="sxs-lookup"><span data-stu-id="889c2-105">Operations on integral types (such as `==`, `!=`, `<`, `>`, `&`, `|`) are generally allowed on enumeration (`enum`) types.</span></span>

<span data-ttu-id="889c2-106">As seções abaixo listam os operadores em C# da precedência mais alta para a mais baixa.</span><span class="sxs-lookup"><span data-stu-id="889c2-106">The sections below list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="889c2-107">Os operadores em cada seção compartilham o mesmo nível de precedência.</span><span class="sxs-lookup"><span data-stu-id="889c2-107">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="889c2-108">Operadores primários</span><span class="sxs-lookup"><span data-stu-id="889c2-108">Primary operators</span></span>

<span data-ttu-id="889c2-109">Esses são os operadores de precedência mais alta.</span><span class="sxs-lookup"><span data-stu-id="889c2-109">These are the highest precedence operators.</span></span>

<span data-ttu-id="889c2-110">[x.y](member-access-operator.md) – acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="889c2-110">[x.y](member-access-operator.md) – member access.</span></span>

<span data-ttu-id="889c2-111">[x?.y](null-conditional-operators.md) – acesso de membro condicional nulo.</span><span class="sxs-lookup"><span data-stu-id="889c2-111">[x?.y](null-conditional-operators.md) – null conditional member access.</span></span> <span data-ttu-id="889c2-112">Retornará `null` se o operando esquerdo for avaliado como `null`.</span><span class="sxs-lookup"><span data-stu-id="889c2-112">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="889c2-113">[x?[y]](null-conditional-operators.md) – acesso de índice condicional nulo.</span><span class="sxs-lookup"><span data-stu-id="889c2-113">[x?[y]](null-conditional-operators.md) - null conditional index access.</span></span> <span data-ttu-id="889c2-114">Retornará `null` se o operando esquerdo for avaliado como `null`.</span><span class="sxs-lookup"><span data-stu-id="889c2-114">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="889c2-115">[f(x)](invocation-operator.md) – invocação de função.</span><span class="sxs-lookup"><span data-stu-id="889c2-115">[f(x)](invocation-operator.md) – function invocation.</span></span>

<span data-ttu-id="889c2-116">[a&#91;x&#93;](index-operator.md) – indexação de objeto de agregação.</span><span class="sxs-lookup"><span data-stu-id="889c2-116">[a&#91;x&#93;](index-operator.md) – aggregate object indexing.</span></span>

<span data-ttu-id="889c2-117">[x++](increment-operator.md) – incremento de sufixo.</span><span class="sxs-lookup"><span data-stu-id="889c2-117">[x++](increment-operator.md) – postfix increment.</span></span> <span data-ttu-id="889c2-118">Retorna o valor de x e, em seguida, atualiza o local de armazenamento com o valor de x que é um número maior (normalmente adiciona o inteiro 1).</span><span class="sxs-lookup"><span data-stu-id="889c2-118">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="889c2-119">[x--](decrement-operator.md) – decremento de sufixo.</span><span class="sxs-lookup"><span data-stu-id="889c2-119">[x--](decrement-operator.md) –  postfix decrement.</span></span> <span data-ttu-id="889c2-120">Retorna o valor de x e, em seguida, atualiza o local de armazenamento com o valor de x que é um número menor (normalmente subtrai o inteiro 1).</span><span class="sxs-lookup"><span data-stu-id="889c2-120">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="889c2-121">[new](../keywords/new-operator.md) – instanciação de tipo.</span><span class="sxs-lookup"><span data-stu-id="889c2-121">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="889c2-122">[typeof](../keywords/typeof.md) – retorna o objeto <xref:System.Type> que representa o operando.</span><span class="sxs-lookup"><span data-stu-id="889c2-122">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="889c2-123">[checked](../keywords/checked.md) – habilita a verificação de estouro para operações de inteiros.</span><span class="sxs-lookup"><span data-stu-id="889c2-123">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="889c2-124">[unchecked](../keywords/unchecked.md) – desabilita a verificação de estouro para operações de inteiros.</span><span class="sxs-lookup"><span data-stu-id="889c2-124">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="889c2-125">Este é o comportamento padrão do compilador.</span><span class="sxs-lookup"><span data-stu-id="889c2-125">This is the default compiler behavior.</span></span>

<span data-ttu-id="889c2-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produz o valor padrão do tipo T.</span><span class="sxs-lookup"><span data-stu-id="889c2-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="889c2-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declara e retorna uma instância delegada.</span><span class="sxs-lookup"><span data-stu-id="889c2-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="889c2-128">[sizeof](../keywords/sizeof.md) – retorna o tamanho em bytes do operando do tipo.</span><span class="sxs-lookup"><span data-stu-id="889c2-128">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="889c2-129">[->](dereference-operator.md) – desreferência de ponteiro combinada com acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="889c2-129">[->](dereference-operator.md) – pointer dereferencing combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="889c2-130">Operadores unários</span><span class="sxs-lookup"><span data-stu-id="889c2-130">Unary operators</span></span>

<span data-ttu-id="889c2-131">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-131">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-132">[+x](addition-operator.md) – retorna o valor de x.</span><span class="sxs-lookup"><span data-stu-id="889c2-132">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="889c2-133">[-x](subtraction-operator.md) – negação numérica.</span><span class="sxs-lookup"><span data-stu-id="889c2-133">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="889c2-134">[\!x](logical-negation-operator.md) – negação lógica.</span><span class="sxs-lookup"><span data-stu-id="889c2-134">[\!x](logical-negation-operator.md) – logical negation.</span></span>

<span data-ttu-id="889c2-135">[~x](bitwise-complement-operator.md) – complemento bit a bit.</span><span class="sxs-lookup"><span data-stu-id="889c2-135">[~x](bitwise-complement-operator.md) – bitwise complement.</span></span>

<span data-ttu-id="889c2-136">[++x](increment-operator.md) – incremento de prefixo.</span><span class="sxs-lookup"><span data-stu-id="889c2-136">[++x](increment-operator.md) – prefix increment.</span></span> <span data-ttu-id="889c2-137">Retorna o valor de x depois de atualizar o local de armazenamento com o valor de x que é um número maior (normalmente adiciona o inteiro 1).</span><span class="sxs-lookup"><span data-stu-id="889c2-137">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="889c2-138">[--x](decrement-operator.md) – decremento de prefixo.</span><span class="sxs-lookup"><span data-stu-id="889c2-138">[--x](decrement-operator.md) – prefix decrement.</span></span> <span data-ttu-id="889c2-139">Retorna o valor de x depois de atualizar o local de armazenamento com o valor de x que é um número menor (normalmente subtrai o inteiro 1).</span><span class="sxs-lookup"><span data-stu-id="889c2-139">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="889c2-140">[(T)x](invocation-operator.md) – conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="889c2-140">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="889c2-141">[await](../keywords/await.md) – aguarda um `Task`.</span><span class="sxs-lookup"><span data-stu-id="889c2-141">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="889c2-142">[&x](and-operator.md) – endereço.</span><span class="sxs-lookup"><span data-stu-id="889c2-142">[&x](and-operator.md) – address of.</span></span>

<span data-ttu-id="889c2-143">[\*x](multiplication-operator.md) – desreferenciamento.</span><span class="sxs-lookup"><span data-stu-id="889c2-143">[\*x](multiplication-operator.md) – dereferencing.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="889c2-144">Operadores de multiplicação</span><span class="sxs-lookup"><span data-stu-id="889c2-144">Multiplicative operators</span></span>

<span data-ttu-id="889c2-145">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-145">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-146">[x \* y](multiplication-operator.md) – multiplicação.</span><span class="sxs-lookup"><span data-stu-id="889c2-146">[x \* y](multiplication-operator.md) – multiplication.</span></span>

<span data-ttu-id="889c2-147">[x / y](division-operator.md) – divisão.</span><span class="sxs-lookup"><span data-stu-id="889c2-147">[x / y](division-operator.md) – division.</span></span> <span data-ttu-id="889c2-148">Se os operandos forem inteiros, o resultado será um inteiro truncado para zero (por exemplo, `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="889c2-148">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="889c2-149">[x % y](remainder-operator.md) – restante.</span><span class="sxs-lookup"><span data-stu-id="889c2-149">[x % y](remainder-operator.md) – remainder.</span></span> <span data-ttu-id="889c2-150">Se os operandos forem inteiros, isso retornará o resto da divisão de x por y.</span><span class="sxs-lookup"><span data-stu-id="889c2-150">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="889c2-151">Se `q = x / y` e `r = x % y`, então `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="889c2-151">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="889c2-152">Operadores aditivos</span><span class="sxs-lookup"><span data-stu-id="889c2-152">Additive operators</span></span>

<span data-ttu-id="889c2-153">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-153">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-154">[x + y](addition-operator.md) – adição.</span><span class="sxs-lookup"><span data-stu-id="889c2-154">[x + y](addition-operator.md) – addition.</span></span>

<span data-ttu-id="889c2-155">[x – y](subtraction-operator.md) – subtração.</span><span class="sxs-lookup"><span data-stu-id="889c2-155">[x – y](subtraction-operator.md) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="889c2-156">Operadores shift</span><span class="sxs-lookup"><span data-stu-id="889c2-156">Shift operators</span></span>

<span data-ttu-id="889c2-157">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-157">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-158">[x <\< y](left-shift-operator.md) – bits de deslocamento para a esquerda e preenche com zero à direita.</span><span class="sxs-lookup"><span data-stu-id="889c2-158">[x <\<  y](left-shift-operator.md) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="889c2-159">[x >> y](right-shift-operator.md) – bits de deslocamento para a direita.</span><span class="sxs-lookup"><span data-stu-id="889c2-159">[x >> y](right-shift-operator.md) – shift bits right.</span></span> <span data-ttu-id="889c2-160">Se o operando esquerdo for `int` ou `long`, então, os bits à esquerda serão preenchidos com o bit de sinal.</span><span class="sxs-lookup"><span data-stu-id="889c2-160">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="889c2-161">Se o operando esquerdo for `uint` ou `ulong`, então, os bits à esquerda serão preenchidos com zero.</span><span class="sxs-lookup"><span data-stu-id="889c2-161">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="889c2-162">Operadores de teste de tipo e relacional</span><span class="sxs-lookup"><span data-stu-id="889c2-162">Relational and type-testing operators</span></span>

<span data-ttu-id="889c2-163">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-163">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-164">[x \< y](less-than-operator.md) – menor que (verdadeiro se x for menor que y).</span><span class="sxs-lookup"><span data-stu-id="889c2-164">[x \< y](less-than-operator.md) – less than (true if x is less than y).</span></span>

<span data-ttu-id="889c2-165">[x > y](greater-than-operator.md) – maior que (verdadeiro se x for maior que y).</span><span class="sxs-lookup"><span data-stu-id="889c2-165">[x > y](greater-than-operator.md) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="889c2-166">[x \<= y](less-than-equal-operator.md) – menor ou igual a.</span><span class="sxs-lookup"><span data-stu-id="889c2-166">[x \<= y](less-than-equal-operator.md) – less than or equal to.</span></span>

<span data-ttu-id="889c2-167">[x > = y](greater-than-equal-operator.md) – maior que ou igual a.</span><span class="sxs-lookup"><span data-stu-id="889c2-167">[x >= y](greater-than-equal-operator.md) – greater than or equal to.</span></span>

<span data-ttu-id="889c2-168">[is](../keywords/is.md) – compatibilidade de tipo.</span><span class="sxs-lookup"><span data-stu-id="889c2-168">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="889c2-169">Retornará true se o operando esquerdo avaliado puder ser convertido no tipo especificado no operando à direita (um tipo estático).</span><span class="sxs-lookup"><span data-stu-id="889c2-169">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="889c2-170">[as](../keywords/as.md) – conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="889c2-170">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="889c2-171">Retorna o operando esquerdo convertido para o tipo especificado pelo operando à direita (um tipo estático), mas `as` retorna `null` em que `(T)x` lançaria uma exceção.</span><span class="sxs-lookup"><span data-stu-id="889c2-171">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="889c2-172">Operadores de igualdade</span><span class="sxs-lookup"><span data-stu-id="889c2-172">Equality operators</span></span>

<span data-ttu-id="889c2-173">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-173">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-174">[x == y](equality-comparison-operator.md) – igualdade.</span><span class="sxs-lookup"><span data-stu-id="889c2-174">[x == y](equality-comparison-operator.md) – equality.</span></span> <span data-ttu-id="889c2-175">Por padrão, para tipos de referência diferentes de `string`, isso retorna uma igualdade de referência (teste de identidade).</span><span class="sxs-lookup"><span data-stu-id="889c2-175">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="889c2-176">No entanto, os tipos podem sobrecarregar `==`, portanto, se sua intenção for testar a identidade, é melhor usar o método `ReferenceEquals` em `object`.</span><span class="sxs-lookup"><span data-stu-id="889c2-176">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="889c2-177">[x != y](not-equal-operator.md) – não é igual.</span><span class="sxs-lookup"><span data-stu-id="889c2-177">[x != y](not-equal-operator.md) – not equal.</span></span> <span data-ttu-id="889c2-178">Consulte o comentário sobre `==`.</span><span class="sxs-lookup"><span data-stu-id="889c2-178">See comment for `==`.</span></span> <span data-ttu-id="889c2-179">Se um tipo sobrecarregar `==`, então, ele deverá sobrecarregar `!=`.</span><span class="sxs-lookup"><span data-stu-id="889c2-179">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="889c2-180">Operador AND lógico</span><span class="sxs-lookup"><span data-stu-id="889c2-180">Logical AND operator</span></span>

<span data-ttu-id="889c2-181">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-181">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-182">[x & y](and-operator.md) – AND lógico ou bit a bit.</span><span class="sxs-lookup"><span data-stu-id="889c2-182">[x & y](and-operator.md) – logical or bitwise AND.</span></span> <span data-ttu-id="889c2-183">Geralmente, você pode usar isso com tipos de inteiro e tipos `enum`.</span><span class="sxs-lookup"><span data-stu-id="889c2-183">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="889c2-184">Operador XOR lógico</span><span class="sxs-lookup"><span data-stu-id="889c2-184">Logical XOR operator</span></span>

<span data-ttu-id="889c2-185">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-185">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-186">[x ^ y](xor-operator.md) – XOR lógico ou bit a bit.</span><span class="sxs-lookup"><span data-stu-id="889c2-186">[x ^ y](xor-operator.md) – logical or bitwise XOR.</span></span> <span data-ttu-id="889c2-187">Geralmente, você pode usar isso com tipos de inteiro e tipos `enum`.</span><span class="sxs-lookup"><span data-stu-id="889c2-187">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="889c2-188">Operador lógico OU</span><span class="sxs-lookup"><span data-stu-id="889c2-188">Logical OR operator</span></span>

<span data-ttu-id="889c2-189">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-190">[x &#124; y](or-operator.md) – OR lógico ou bit a bit.</span><span class="sxs-lookup"><span data-stu-id="889c2-190">[x &#124; y](or-operator.md) – logical or bitwise OR.</span></span> <span data-ttu-id="889c2-191">Geralmente, você pode usar isso com tipos de inteiro e tipos `enum`.</span><span class="sxs-lookup"><span data-stu-id="889c2-191">You can generally use this with integer types and `enum` types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="889c2-192">Operador AND condicional</span><span class="sxs-lookup"><span data-stu-id="889c2-192">Conditional AND operator</span></span>

<span data-ttu-id="889c2-193">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-193">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-194">[x && y](conditional-and-operator.md) – AND lógico.</span><span class="sxs-lookup"><span data-stu-id="889c2-194">[x && y](conditional-and-operator.md) – logical AND.</span></span> <span data-ttu-id="889c2-195">Se o primeiro operando for avaliado como falso, então o C# não avaliará o segundo operando.</span><span class="sxs-lookup"><span data-stu-id="889c2-195">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="889c2-196">Operador OR condicional</span><span class="sxs-lookup"><span data-stu-id="889c2-196">Conditional OR operator</span></span>

<span data-ttu-id="889c2-197">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-197">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-198">[x &#124;&#124; y](conditional-or-operator.md) – OR lógico.</span><span class="sxs-lookup"><span data-stu-id="889c2-198">[x &#124;&#124; y](conditional-or-operator.md) – logical OR.</span></span> <span data-ttu-id="889c2-199">Se o primeiro operando for avaliado como verdadeiro, então o C# não avaliará o segundo operando.</span><span class="sxs-lookup"><span data-stu-id="889c2-199">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="889c2-200">Operador de coalescência nula</span><span class="sxs-lookup"><span data-stu-id="889c2-200">Null-coalescing operator</span></span>

<span data-ttu-id="889c2-201">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-201">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-202">[x ?? y](null-coalescing-operator.md) – retornará `x` se for não `null`; caso contrário, retornará `y`.</span><span class="sxs-lookup"><span data-stu-id="889c2-202">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="889c2-203">Operador condicional</span><span class="sxs-lookup"><span data-stu-id="889c2-203">Conditional operator</span></span>

<span data-ttu-id="889c2-204">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-204">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-205">[t ? x : y](conditional-operator.md) – se o teste `t` for avaliado como verdadeiro, então ele avaliará e retornará `x`; caso contrário, avaliará e retornará `y`.</span><span class="sxs-lookup"><span data-stu-id="889c2-205">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="889c2-206">Atribuição e operadores de Lambda</span><span class="sxs-lookup"><span data-stu-id="889c2-206">Assignment and Lambda operators</span></span>

<span data-ttu-id="889c2-207">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="889c2-207">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="889c2-208">[x = y](assignment-operator.md) – atribuição.</span><span class="sxs-lookup"><span data-stu-id="889c2-208">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="889c2-209">[x += y](addition-assignment-operator.md) – incremento.</span><span class="sxs-lookup"><span data-stu-id="889c2-209">[x += y](addition-assignment-operator.md) – increment.</span></span> <span data-ttu-id="889c2-210">Adicione o valor de `y` para o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="889c2-210">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="889c2-211">Se `x` designar um `event`, então, `y` deverá ser uma função adequada que o C# adiciona como um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="889c2-211">If `x` designates an `event`, then `y` must be an appropriate function that C# adds as an event handler.</span></span>

<span data-ttu-id="889c2-212">[x -= y](subtraction-assignment-operator.md) – diminuir.</span><span class="sxs-lookup"><span data-stu-id="889c2-212">[x -= y](subtraction-assignment-operator.md) – decrement.</span></span> <span data-ttu-id="889c2-213">Subtraia o valor de `y` do valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="889c2-213">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="889c2-214">Se `x` designar um `event`, então, `y` deverá ser uma função adequada que o C# remove como um manipulador de eventos</span><span class="sxs-lookup"><span data-stu-id="889c2-214">If `x` designates an `event`, then `y` must be an appropriate function that C# removes as an event handler</span></span>

<span data-ttu-id="889c2-215">[x \*= y](multiplication-assignment-operator.md) – atribuição de multiplicação.</span><span class="sxs-lookup"><span data-stu-id="889c2-215">[x \*= y](multiplication-assignment-operator.md) – multiplication assignment.</span></span> <span data-ttu-id="889c2-216">Multiplique o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="889c2-216">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="889c2-217">[x /= y](division-assignment-operator.md) – atribuição de divisão.</span><span class="sxs-lookup"><span data-stu-id="889c2-217">[x /= y](division-assignment-operator.md) – division assignment.</span></span> <span data-ttu-id="889c2-218">Divida o valor de `x` pelo valor de `y`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="889c2-218">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="889c2-219">[x %= y](remainder-assignment-operator.md) – atribuição restante.</span><span class="sxs-lookup"><span data-stu-id="889c2-219">[x %= y](remainder-assignment-operator.md) – remainder assignment.</span></span> <span data-ttu-id="889c2-220">Divida o valor de `x` pelo valor de `y`, armazene o resto em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="889c2-220">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="889c2-221">[x &= y](and-assignment-operator.md) – atribuição AND.</span><span class="sxs-lookup"><span data-stu-id="889c2-221">[x &= y](and-assignment-operator.md) – AND assignment.</span></span> <span data-ttu-id="889c2-222">AND o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="889c2-222">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="889c2-223">[x &#124;= y](or-assignment-operator.md) – atribuição OR.</span><span class="sxs-lookup"><span data-stu-id="889c2-223">[x &#124;= y](or-assignment-operator.md) – OR assignment.</span></span> <span data-ttu-id="889c2-224">OR o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="889c2-224">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="889c2-225">[x ^= y](xor-assignment-operator.md) – atribuição XOR.</span><span class="sxs-lookup"><span data-stu-id="889c2-225">[x ^= y](xor-assignment-operator.md) – XOR assignment.</span></span> <span data-ttu-id="889c2-226">XOR o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="889c2-226">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="889c2-227">[x <<= y](left-shift-assignment-operator.md) – atribuição de deslocamento para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="889c2-227">[x <<= y](left-shift-assignment-operator.md) – left-shift assignment.</span></span> <span data-ttu-id="889c2-228">Desloque o valor de `x` para a esquerda em `y` casas decimais, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="889c2-228">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="889c2-229">[x >>= y](right-shift-assignment-operator.md) – atribuição de deslocamento para a direita.</span><span class="sxs-lookup"><span data-stu-id="889c2-229">[x >>= y](right-shift-assignment-operator.md) – right-shift assignment.</span></span> <span data-ttu-id="889c2-230">Desloque o valor de `x` para a direita em `y` casas decimais, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="889c2-230">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="889c2-231">[=>](lambda-operator.md) – declaração de lambda.</span><span class="sxs-lookup"><span data-stu-id="889c2-231">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="arithmetic-overflow"></a><span data-ttu-id="889c2-232">Estouro aritmético</span><span class="sxs-lookup"><span data-stu-id="889c2-232">Arithmetic overflow</span></span>

<span data-ttu-id="889c2-233">Os operadores aritméticos ([+](addition-operator.md), [-](subtraction-operator.md), [\*](multiplication-operator.md), [/](division-operator.md)) podem produzir resultados que estão fora do intervalo de valores possíveis para o tipo numérico envolvido.</span><span class="sxs-lookup"><span data-stu-id="889c2-233">The arithmetic operators ([+](addition-operator.md), [-](subtraction-operator.md), [\*](multiplication-operator.md), [/](division-operator.md)) can produce results that are outside the range of possible values for the numeric type involved.</span></span> <span data-ttu-id="889c2-234">Consulte a seção sobre um operador específico para obter detalhes, mas, em geral:</span><span class="sxs-lookup"><span data-stu-id="889c2-234">You should refer to the section on a particular operator for details, but in general:</span></span>

- <span data-ttu-id="889c2-235">O estouro aritmético de inteiros lança uma <xref:System.OverflowException> ou descarta os bits mais significativos do resultado.</span><span class="sxs-lookup"><span data-stu-id="889c2-235">Integer arithmetic overflow either throws an <xref:System.OverflowException> or discards the most significant bits of the result.</span></span> <span data-ttu-id="889c2-236">A divisão de inteiro por zero sempre lança um <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="889c2-236">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

   <span data-ttu-id="889c2-237">Quando ocorre um estouro de inteiro, o que acontece depende do contexto de execução, que pode ser [verificação ou não verificado](../keywords/checked-and-unchecked.md).</span><span class="sxs-lookup"><span data-stu-id="889c2-237">When integer overflow occurs, what happens depends on the execution context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="889c2-238">Em um contexto marcado, uma <xref:System.OverflowException> é lançada.</span><span class="sxs-lookup"><span data-stu-id="889c2-238">In a checked context, an <xref:System.OverflowException> is thrown.</span></span> <span data-ttu-id="889c2-239">Em um contexto não verificado, os bits mais significativos do resultado são descartados e a execução continua.</span><span class="sxs-lookup"><span data-stu-id="889c2-239">In an unchecked context, the most significant bits of the result are discarded and execution continues.</span></span> <span data-ttu-id="889c2-240">Assim, C# oferece a opção para tratar ou ignorar o estouro.</span><span class="sxs-lookup"><span data-stu-id="889c2-240">Thus, C# gives you the choice of handling or ignoring overflow.</span></span> <span data-ttu-id="889c2-241">Por padrão, as operações aritméticas ocorrem em um contexto *não verificado*.</span><span class="sxs-lookup"><span data-stu-id="889c2-241">By default, arithmetic operations occur in an *unchecked* context.</span></span>

   <span data-ttu-id="889c2-242">Além das operações aritméticas, as conversões de tipo integral para integral tipo podem causar estouro (como quando você converte um [longo](../keywords/long.md) para um [int](../keywords/int.md)) e estão sujeitas à execução verificada ou não verificada.</span><span class="sxs-lookup"><span data-stu-id="889c2-242">In addition to the arithmetic operations, integral-type to integral-type casts can cause overflow (such as when you cast a [long](../keywords/long.md) to an [int](../keywords/int.md)), and are subject to checked or unchecked execution.</span></span> <span data-ttu-id="889c2-243">No entanto, operadores bit a bit e operadores de deslocamento nunca causam estouro.</span><span class="sxs-lookup"><span data-stu-id="889c2-243">However, bitwise operators and shift operators never cause overflow.</span></span>

- <span data-ttu-id="889c2-244">O estouro aritmético de ponto flutuante ou a divisão por zero nunca gera uma exceção, pois os tipos de ponto flutuante são baseados em IEEE 754 e têm provisões para representar o infinito e NaN (não um número).</span><span class="sxs-lookup"><span data-stu-id="889c2-244">Floating-point arithmetic overflow or division by zero never throws an exception, because floating-point types are based on IEEE 754 and so have provisions for representing infinity and NaN (Not a Number).</span></span>

- <span data-ttu-id="889c2-245">Um estouro aritmético[Decimal](../keywords/decimal.md) sempre lança uma <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="889c2-245">[Decimal](../keywords/decimal.md) arithmetic overflow always throws an <xref:System.OverflowException>.</span></span> <span data-ttu-id="889c2-246">A divisão decimal por zero sempre lança uma <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="889c2-246">Decimal division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="889c2-247">Consulte também</span><span class="sxs-lookup"><span data-stu-id="889c2-247">See also</span></span>

- [<span data-ttu-id="889c2-248">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="889c2-248">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="889c2-249">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="889c2-249">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="889c2-250">C#</span><span class="sxs-lookup"><span data-stu-id="889c2-250">C#</span></span>](../../index.md)
- [<span data-ttu-id="889c2-251">Operadores sobrecarregáveis</span><span class="sxs-lookup"><span data-stu-id="889c2-251">Overloadable Operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="889c2-252">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="889c2-252">C# Keywords</span></span>](../keywords/index.md)