---
title: Operadores C# – Referência de C#
ms.date: 04/30/2019
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
ms.openlocfilehash: 7d8ee9be8f399bca0aace61d344b19094c9518b0
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401462"
---
# <a name="c-operators-c-reference"></a><span data-ttu-id="37063-102">Operadores C# (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="37063-102">C# operators (C# reference)</span></span>

<span data-ttu-id="37063-103">O C# Fornece um número de operadores predefinidos, compatíveis com os tipos internos.</span><span class="sxs-lookup"><span data-stu-id="37063-103">C# provides a number of predefined operators supported by the built-in types.</span></span> <span data-ttu-id="37063-104">Por exemplo, [operadores aritméticos](arithmetic-operators.md) executam operações aritméticas com operandos de tipos numéricos internos e [operadores lógicos boolianos](boolean-logical-operators.md) executam operações lógicas com operandos [bool](../keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="37063-104">For example, [arithmetic operators](arithmetic-operators.md) perform arithmetic operations with operands of built-in numeric types and [Boolean logical operators](boolean-logical-operators.md) perform logical operations with the [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="37063-105">Um tipo definido pelo usuário pode sobrecarregar determinados operadores para definir o comportamento correspondente para os operandos desse tipo.</span><span class="sxs-lookup"><span data-stu-id="37063-105">A user-defined type can overload certain operators to define the corresponding behavior for the operands of that type.</span></span> <span data-ttu-id="37063-106">Para obter mais informações, consulte o artigo com a palavra-chave [operador](../keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="37063-106">For more information, see the [operator](../keywords/operator.md) keyword article.</span></span>

<span data-ttu-id="37063-107">As seções a seguir listam operadores C#, começando com a precedência mais alta para a mais baixa.</span><span class="sxs-lookup"><span data-stu-id="37063-107">The following sections list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="37063-108">Os operadores em cada seção compartilham o mesmo nível de precedência.</span><span class="sxs-lookup"><span data-stu-id="37063-108">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="37063-109">Operadores primários</span><span class="sxs-lookup"><span data-stu-id="37063-109">Primary operators</span></span>

<span data-ttu-id="37063-110">Esses são os operadores de precedência mais alta.</span><span class="sxs-lookup"><span data-stu-id="37063-110">These are the highest precedence operators.</span></span>

<span data-ttu-id="37063-111">[x.y](member-access-operators.md#member-access-operator-) – acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="37063-111">[x.y](member-access-operators.md#member-access-operator-) – member access.</span></span>

<span data-ttu-id="37063-112">[x?.y](member-access-operators.md#null-conditional-operators--and-) – acesso de membro condicional nulo.</span><span class="sxs-lookup"><span data-stu-id="37063-112">[x?.y](member-access-operators.md#null-conditional-operators--and-) – null conditional member access.</span></span> <span data-ttu-id="37063-113">Retornará `null` se o operando esquerdo for avaliado como `null`.</span><span class="sxs-lookup"><span data-stu-id="37063-113">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="37063-114">[x?[y]](member-access-operators.md#null-conditional-operators--and-) – elemento de matriz condicional nula ou acesso ao indexador de tipo.</span><span class="sxs-lookup"><span data-stu-id="37063-114">[x?[y]](member-access-operators.md#null-conditional-operators--and-) - null conditional array element or type indexer access.</span></span> <span data-ttu-id="37063-115">Retornará `null` se o operando esquerdo for avaliado como `null`.</span><span class="sxs-lookup"><span data-stu-id="37063-115">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="37063-116">[f(x)](member-access-operators.md#invocation-operator-) – chamada de método ou invocação de delegado.</span><span class="sxs-lookup"><span data-stu-id="37063-116">[f(x)](member-access-operators.md#invocation-operator-) – method call or delegate invocation.</span></span>

<span data-ttu-id="37063-117">[um&#91;x&#93; ](member-access-operators.md#indexer-operator-) – o elemento de matriz ou tipo de acesso do indexador.</span><span class="sxs-lookup"><span data-stu-id="37063-117">[a&#91;x&#93;](member-access-operators.md#indexer-operator-) – array element or type indexer access.</span></span>

<span data-ttu-id="37063-118">[x++](arithmetic-operators.md#increment-operator-) – incremento de sufixo.</span><span class="sxs-lookup"><span data-stu-id="37063-118">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="37063-119">Retorna o valor de x e, em seguida, atualiza o local de armazenamento com o valor de x que é um número maior (normalmente adiciona o inteiro 1).</span><span class="sxs-lookup"><span data-stu-id="37063-119">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="37063-120">[x--](arithmetic-operators.md#decrement-operator---) – decremento de sufixo.</span><span class="sxs-lookup"><span data-stu-id="37063-120">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="37063-121">Retorna o valor de x e, em seguida, atualiza o local de armazenamento com o valor de x que é um número menor (normalmente subtrai o inteiro 1).</span><span class="sxs-lookup"><span data-stu-id="37063-121">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="37063-122">[new](new-operator.md) – instanciação de tipo.</span><span class="sxs-lookup"><span data-stu-id="37063-122">[new](new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="37063-123">[typeof](type-testing-and-conversion-operators.md#typeof-operator) – retorna o objeto <xref:System.Type> que representa o operando.</span><span class="sxs-lookup"><span data-stu-id="37063-123">[typeof](type-testing-and-conversion-operators.md#typeof-operator) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="37063-124">[checked](../keywords/checked.md) – habilita a verificação de estouro para operações de inteiros.</span><span class="sxs-lookup"><span data-stu-id="37063-124">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="37063-125">[unchecked](../keywords/unchecked.md) – desabilita a verificação de estouro para operações de inteiros.</span><span class="sxs-lookup"><span data-stu-id="37063-125">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="37063-126">Este é o comportamento padrão do compilador.</span><span class="sxs-lookup"><span data-stu-id="37063-126">This is the default compiler behavior.</span></span>

<span data-ttu-id="37063-127">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produz o valor padrão do tipo T.</span><span class="sxs-lookup"><span data-stu-id="37063-127">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="37063-128">[nameof](../keywords/nameof.md) – obtém o nome simples (não qualificado) de uma variável, tipo ou membro como uma cadeia de caracteres constante.</span><span class="sxs-lookup"><span data-stu-id="37063-128">[nameof](../keywords/nameof.md) - obtains the simple (unqualified) name of a variable, type, or member as a constant string.</span></span>

<span data-ttu-id="37063-129">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declara e retorna uma instância delegada.</span><span class="sxs-lookup"><span data-stu-id="37063-129">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="37063-130">[sizeof](../keywords/sizeof.md) – retorna o tamanho em bytes do operando do tipo.</span><span class="sxs-lookup"><span data-stu-id="37063-130">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="37063-131">[stackalloc](stackalloc.md) – aloca um bloco de memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="37063-131">[stackalloc](stackalloc.md) - allocates a block of memory on the stack.</span></span>

<span data-ttu-id="37063-132">[->](pointer-related-operators.md#pointer-member-access-operator--) – indireção de ponteiro combinada com acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="37063-132">[->](pointer-related-operators.md#pointer-member-access-operator--) – pointer indirection combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="37063-133">Operadores unários</span><span class="sxs-lookup"><span data-stu-id="37063-133">Unary operators</span></span>

<span data-ttu-id="37063-134">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-134">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-135">[+x](addition-operator.md) – retorna o valor de x.</span><span class="sxs-lookup"><span data-stu-id="37063-135">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="37063-136">[-x](subtraction-operator.md) – negação numérica.</span><span class="sxs-lookup"><span data-stu-id="37063-136">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="37063-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) – negação lógica.</span><span class="sxs-lookup"><span data-stu-id="37063-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="37063-138">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – complemento bit a bit.</span><span class="sxs-lookup"><span data-stu-id="37063-138">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitwise complement.</span></span>

<span data-ttu-id="37063-139">[++x](arithmetic-operators.md#increment-operator-) – incremento de prefixo.</span><span class="sxs-lookup"><span data-stu-id="37063-139">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="37063-140">Retorna o valor de x depois de atualizar o local de armazenamento com o valor de x que é um número maior (normalmente adiciona o inteiro 1).</span><span class="sxs-lookup"><span data-stu-id="37063-140">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="37063-141">[--x](arithmetic-operators.md#decrement-operator---) – decremento de prefixo.</span><span class="sxs-lookup"><span data-stu-id="37063-141">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="37063-142">Retorna o valor de x depois de atualizar o local de armazenamento com o valor de x que é um número menor (normalmente subtrai o inteiro 1).</span><span class="sxs-lookup"><span data-stu-id="37063-142">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="37063-143">[(T)x](type-testing-and-conversion-operators.md#cast-operator-) – conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="37063-143">[(T)x](type-testing-and-conversion-operators.md#cast-operator-) – type casting.</span></span>

<span data-ttu-id="37063-144">[await](../keywords/await.md) – aguarda um `Task`.</span><span class="sxs-lookup"><span data-stu-id="37063-144">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="37063-145">[&x](pointer-related-operators.md#address-of-operator-) – endereço de uma variável.</span><span class="sxs-lookup"><span data-stu-id="37063-145">[&x](pointer-related-operators.md#address-of-operator-) – address of a variable.</span></span>

<span data-ttu-id="37063-146">[\*x](pointer-related-operators.md#pointer-indirection-operator-) – indireção de ponteiro ou desreferenciar.</span><span class="sxs-lookup"><span data-stu-id="37063-146">[\*x](pointer-related-operators.md#pointer-indirection-operator-) – pointer indirection, or dereference.</span></span>

<span data-ttu-id="37063-147">[operador true](true-false-operators.md) – retorna o valor [bool](../keywords/bool.md) `true` para indicar que um operando é definitivamente true.</span><span class="sxs-lookup"><span data-stu-id="37063-147">[true operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span>

<span data-ttu-id="37063-148">[operador false](true-false-operators.md) – retorna o valor [bool](../keywords/bool.md) `true` para indicar que um operando é definitivamente false.</span><span class="sxs-lookup"><span data-stu-id="37063-148">[false operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="37063-149">Operadores de multiplicação</span><span class="sxs-lookup"><span data-stu-id="37063-149">Multiplicative operators</span></span>

<span data-ttu-id="37063-150">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-150">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplicação.</span><span class="sxs-lookup"><span data-stu-id="37063-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="37063-152">[x / y](arithmetic-operators.md#division-operator-) – divisão.</span><span class="sxs-lookup"><span data-stu-id="37063-152">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="37063-153">Se os operandos forem inteiros, o resultado será um inteiro truncado para zero (por exemplo, `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="37063-153">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="37063-154">[x % y](arithmetic-operators.md#remainder-operator-) – restante.</span><span class="sxs-lookup"><span data-stu-id="37063-154">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="37063-155">Se os operandos forem inteiros, isso retornará o resto da divisão de x por y.</span><span class="sxs-lookup"><span data-stu-id="37063-155">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="37063-156">Se `q = x / y` e `r = x % y`, então `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="37063-156">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="37063-157">Operadores aditivos</span><span class="sxs-lookup"><span data-stu-id="37063-157">Additive operators</span></span>

<span data-ttu-id="37063-158">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-158">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-159">[x + y](arithmetic-operators.md#addition-operator-) – adição.</span><span class="sxs-lookup"><span data-stu-id="37063-159">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="37063-160">[x – y](arithmetic-operators.md#subtraction-operator--) – subtração.</span><span class="sxs-lookup"><span data-stu-id="37063-160">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="37063-161">Operadores shift</span><span class="sxs-lookup"><span data-stu-id="37063-161">Shift operators</span></span>

<span data-ttu-id="37063-162">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-162">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-163">[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) – bits de deslocamento para a esquerda e preenche com zero à direita.</span><span class="sxs-lookup"><span data-stu-id="37063-163">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="37063-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – bits de deslocamento para a direita.</span><span class="sxs-lookup"><span data-stu-id="37063-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – shift bits right.</span></span> <span data-ttu-id="37063-165">Se o operando esquerdo for `int` ou `long`, então, os bits à esquerda serão preenchidos com o bit de sinal.</span><span class="sxs-lookup"><span data-stu-id="37063-165">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="37063-166">Se o operando esquerdo for `uint` ou `ulong`, então, os bits à esquerda serão preenchidos com zero.</span><span class="sxs-lookup"><span data-stu-id="37063-166">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="37063-167">Operadores de teste de tipo e relacional</span><span class="sxs-lookup"><span data-stu-id="37063-167">Relational and type-testing operators</span></span>

<span data-ttu-id="37063-168">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-168">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-169">[x \< y](comparison-operators.md#less-than-operator-) – menor que (verdadeiro se x for menor que y).</span><span class="sxs-lookup"><span data-stu-id="37063-169">[x \< y](comparison-operators.md#less-than-operator-) – less than (true if x is less than y).</span></span>

<span data-ttu-id="37063-170">[x > y](comparison-operators.md#greater-than-operator-) – maior que (verdadeiro se x for maior que y).</span><span class="sxs-lookup"><span data-stu-id="37063-170">[x > y](comparison-operators.md#greater-than-operator-) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="37063-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – menor ou igual a.</span><span class="sxs-lookup"><span data-stu-id="37063-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – less than or equal to.</span></span>

<span data-ttu-id="37063-172">[x > = y](comparison-operators.md#greater-than-or-equal-operator-) – maior que ou igual a.</span><span class="sxs-lookup"><span data-stu-id="37063-172">[x >= y](comparison-operators.md#greater-than-or-equal-operator-) – greater than or equal to.</span></span>

<span data-ttu-id="37063-173">[is](type-testing-and-conversion-operators.md#is-operator) – compatibilidade de tipo.</span><span class="sxs-lookup"><span data-stu-id="37063-173">[is](type-testing-and-conversion-operators.md#is-operator) – type compatibility.</span></span> <span data-ttu-id="37063-174">Retornará `true` se o operando esquerdo avaliado puder ser convertido no tipo especificado pelo operando à direita.</span><span class="sxs-lookup"><span data-stu-id="37063-174">Returns `true` if the evaluated left operand can be cast to the type specified by the right operand.</span></span>

<span data-ttu-id="37063-175">[as](type-testing-and-conversion-operators.md#as-operator) – conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="37063-175">[as](type-testing-and-conversion-operators.md#as-operator) – type conversion.</span></span> <span data-ttu-id="37063-176">Retorna o operando esquerdo convertido para o tipo especificado pelo operando à direita, mas `as` retorna `null`, em que `(T)x` lançaria uma exceção.</span><span class="sxs-lookup"><span data-stu-id="37063-176">Returns the left operand cast to the type specified by the right operand, but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="37063-177">Operadores de igualdade</span><span class="sxs-lookup"><span data-stu-id="37063-177">Equality operators</span></span>

<span data-ttu-id="37063-178">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-178">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-179">[x == y](equality-operators.md#equality-operator-) – igualdade.</span><span class="sxs-lookup"><span data-stu-id="37063-179">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="37063-180">Por padrão, para tipos de referência diferentes de `string`, isso retorna uma igualdade de referência (teste de identidade).</span><span class="sxs-lookup"><span data-stu-id="37063-180">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="37063-181">No entanto, os tipos podem sobrecarregar `==`, portanto, se sua intenção for testar a identidade, é melhor usar o método `ReferenceEquals` em `object`.</span><span class="sxs-lookup"><span data-stu-id="37063-181">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="37063-182">[x != y](equality-operators.md#inequality-operator-) – não é igual.</span><span class="sxs-lookup"><span data-stu-id="37063-182">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="37063-183">Consulte o comentário sobre `==`.</span><span class="sxs-lookup"><span data-stu-id="37063-183">See comment for `==`.</span></span> <span data-ttu-id="37063-184">Se um tipo sobrecarregar `==`, então, ele deverá sobrecarregar `!=`.</span><span class="sxs-lookup"><span data-stu-id="37063-184">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="37063-185">Operador AND lógico</span><span class="sxs-lookup"><span data-stu-id="37063-185">Logical AND operator</span></span>

<span data-ttu-id="37063-186">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-186">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-187">`x & y` – [AND lógico](boolean-logical-operators.md#logical-and-operator-) para os operandos `bool` ou [AND lógico](bitwise-and-shift-operators.md#logical-and-operator-) para os operandos dos tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="37063-187">`x & y` – [logical AND](boolean-logical-operators.md#logical-and-operator-) for the `bool` operands or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) for the operands of the integral types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="37063-188">Operador XOR lógico</span><span class="sxs-lookup"><span data-stu-id="37063-188">Logical XOR operator</span></span>

<span data-ttu-id="37063-189">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-190">`x ^ y` – [XOR lógico](boolean-logical-operators.md#logical-exclusive-or-operator-) para os operandos `bool` ou [XOR lógico](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) para os operandos dos tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="37063-190">`x ^ y` – [logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) for the `bool` operands or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) for the operands of the integral types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="37063-191">Operador lógico OU</span><span class="sxs-lookup"><span data-stu-id="37063-191">Logical OR operator</span></span>

<span data-ttu-id="37063-192">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-192">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-193">`x | y` – [OR lógico](boolean-logical-operators.md#logical-or-operator-) para os operandos `bool` ou [OR lógico](bitwise-and-shift-operators.md#logical-or-operator-) para os operandos dos tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="37063-193">`x | y` – [logical OR](boolean-logical-operators.md#logical-or-operator-) for the `bool` operands or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) for the operands of the integral types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="37063-194">Operador AND condicional</span><span class="sxs-lookup"><span data-stu-id="37063-194">Conditional AND operator</span></span>

<span data-ttu-id="37063-195">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-195">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-196">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – AND lógico.</span><span class="sxs-lookup"><span data-stu-id="37063-196">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="37063-197">Se `x` for avaliado como `false`, `y` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="37063-197">If `x` evaluates to `false`, then `y` is not evaluated.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="37063-198">Operador OR condicional</span><span class="sxs-lookup"><span data-stu-id="37063-198">Conditional OR operator</span></span>

<span data-ttu-id="37063-199">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-199">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-200">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – OR lógico.</span><span class="sxs-lookup"><span data-stu-id="37063-200">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="37063-201">Se `x` for avaliado como `true`, `y` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="37063-201">If `x` evaluates to `true`, then `y` is not evaluated.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="37063-202">Operador de coalescência nula</span><span class="sxs-lookup"><span data-stu-id="37063-202">Null-coalescing operator</span></span>

<span data-ttu-id="37063-203">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-204">[x ?? y](null-coalescing-operator.md) – retornará `x` se for não `null`; caso contrário, retornará `y`.</span><span class="sxs-lookup"><span data-stu-id="37063-204">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="37063-205">Operador condicional</span><span class="sxs-lookup"><span data-stu-id="37063-205">Conditional operator</span></span>

<span data-ttu-id="37063-206">Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-206">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-207">[t ? x : y](conditional-operator.md) – se o teste `t` for avaliado como verdadeiro, então ele avaliará e retornará `x`; caso contrário, avaliará e retornará `y`.</span><span class="sxs-lookup"><span data-stu-id="37063-207">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="37063-208">Operadores de atribuição e lambda</span><span class="sxs-lookup"><span data-stu-id="37063-208">Assignment and lambda operators</span></span>

<span data-ttu-id="37063-209">Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="37063-209">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="37063-210">[x = y](assignment-operator.md) – atribuição.</span><span class="sxs-lookup"><span data-stu-id="37063-210">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="37063-211">[x += y](arithmetic-operators.md#compound-assignment) – incremento.</span><span class="sxs-lookup"><span data-stu-id="37063-211">[x += y](arithmetic-operators.md#compound-assignment) – increment.</span></span> <span data-ttu-id="37063-212">Adicione o valor de `y` para o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="37063-212">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="37063-213">Se `x` designar um [evento](../keywords/event.md), então, `y` deverá ser um método adequado que o C# adiciona como um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="37063-213">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# adds as an event handler.</span></span>

<span data-ttu-id="37063-214">[x -= y](arithmetic-operators.md#compound-assignment) – diminuir.</span><span class="sxs-lookup"><span data-stu-id="37063-214">[x -= y](arithmetic-operators.md#compound-assignment) – decrement.</span></span> <span data-ttu-id="37063-215">Subtraia o valor de `y` do valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="37063-215">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="37063-216">Se `x` designar um [evento](../keywords/event.md), então, `y` deverá ser um método adequado que o C# remove como um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="37063-216">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# removes as an event handler.</span></span>

<span data-ttu-id="37063-217">[x \*= y](arithmetic-operators.md#compound-assignment) – atribuição de multiplicação.</span><span class="sxs-lookup"><span data-stu-id="37063-217">[x \*= y](arithmetic-operators.md#compound-assignment) – multiplication assignment.</span></span> <span data-ttu-id="37063-218">Multiplique o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="37063-218">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="37063-219">[x /= y](arithmetic-operators.md#compound-assignment) – atribuição de divisão.</span><span class="sxs-lookup"><span data-stu-id="37063-219">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="37063-220">Divida o valor de `x` pelo valor de `y`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="37063-220">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="37063-221">[x %= y](arithmetic-operators.md#compound-assignment) – atribuição restante.</span><span class="sxs-lookup"><span data-stu-id="37063-221">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="37063-222">Divida o valor de `x` pelo valor de `y`, armazene o resto em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="37063-222">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="37063-223">[x &= y](boolean-logical-operators.md#compound-assignment) – atribuição AND.</span><span class="sxs-lookup"><span data-stu-id="37063-223">[x &= y](boolean-logical-operators.md#compound-assignment) – AND assignment.</span></span> <span data-ttu-id="37063-224">AND o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="37063-224">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="37063-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – atribuição OR.</span><span class="sxs-lookup"><span data-stu-id="37063-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR assignment.</span></span> <span data-ttu-id="37063-226">OR o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="37063-226">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="37063-227">[x ^= y](boolean-logical-operators.md#compound-assignment) – atribuição XOR.</span><span class="sxs-lookup"><span data-stu-id="37063-227">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR assignment.</span></span> <span data-ttu-id="37063-228">XOR o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="37063-228">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="37063-229">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – atribuição de deslocamento para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="37063-229">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – left-shift assignment.</span></span> <span data-ttu-id="37063-230">Desloque o valor de `x` para a esquerda em `y` casas decimais, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="37063-230">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="37063-231">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – atribuição de deslocamento para a direita.</span><span class="sxs-lookup"><span data-stu-id="37063-231">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – right-shift assignment.</span></span> <span data-ttu-id="37063-232">Desloque o valor de `x` para a direita em `y` casas decimais, armazene o resultado em `x` e retorne o novo valor.</span><span class="sxs-lookup"><span data-stu-id="37063-232">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="37063-233">[=>](lambda-operator.md) – declaração de lambda.</span><span class="sxs-lookup"><span data-stu-id="37063-233">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="37063-234">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37063-234">See also</span></span>

- [<span data-ttu-id="37063-235">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="37063-235">C# reference</span></span>](../index.md)
- [<span data-ttu-id="37063-236">Operadores</span><span class="sxs-lookup"><span data-stu-id="37063-236">Operators</span></span>](../../programming-guide/statements-expressions-operators/operators.md)
- [<span data-ttu-id="37063-237">Operadores sobrecarregáveis</span><span class="sxs-lookup"><span data-stu-id="37063-237">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
