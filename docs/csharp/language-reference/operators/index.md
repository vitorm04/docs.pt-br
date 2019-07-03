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
# <a name="c-operators-c-reference"></a>Operadores C# (Referência de C#)

O C# Fornece um número de operadores predefinidos, compatíveis com os tipos internos. Por exemplo, [operadores aritméticos](arithmetic-operators.md) executam operações aritméticas com operandos de tipos numéricos internos e [operadores lógicos boolianos](boolean-logical-operators.md) executam operações lógicas com operandos [bool](../keywords/bool.md).

Um tipo definido pelo usuário pode sobrecarregar determinados operadores para definir o comportamento correspondente para os operandos desse tipo. Para obter mais informações, consulte o artigo com a palavra-chave [operador](../keywords/operator.md).

As seções a seguir listam operadores C#, começando com a precedência mais alta para a mais baixa. Os operadores em cada seção compartilham o mesmo nível de precedência.

## <a name="primary-operators"></a>Operadores primários

Esses são os operadores de precedência mais alta.

[x.y](member-access-operators.md#member-access-operator-) – acesso de membro.

[x?.y](member-access-operators.md#null-conditional-operators--and-) – acesso de membro condicional nulo. Retornará `null` se o operando esquerdo for avaliado como `null`.

[x?[y]](member-access-operators.md#null-conditional-operators--and-) – elemento de matriz condicional nula ou acesso ao indexador de tipo. Retornará `null` se o operando esquerdo for avaliado como `null`.

[f(x)](member-access-operators.md#invocation-operator-) – chamada de método ou invocação de delegado.

[um&#91;x&#93; ](member-access-operators.md#indexer-operator-) – o elemento de matriz ou tipo de acesso do indexador.

[x++](arithmetic-operators.md#increment-operator-) – incremento de sufixo. Retorna o valor de x e, em seguida, atualiza o local de armazenamento com o valor de x que é um número maior (normalmente adiciona o inteiro 1).

[x--](arithmetic-operators.md#decrement-operator---) – decremento de sufixo. Retorna o valor de x e, em seguida, atualiza o local de armazenamento com o valor de x que é um número menor (normalmente subtrai o inteiro 1).

[new](new-operator.md) – instanciação de tipo.

[typeof](type-testing-and-conversion-operators.md#typeof-operator) – retorna o objeto <xref:System.Type> que representa o operando.

[checked](../keywords/checked.md) – habilita a verificação de estouro para operações de inteiros.

[unchecked](../keywords/unchecked.md) – desabilita a verificação de estouro para operações de inteiros. Este é o comportamento padrão do compilador.

[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produz o valor padrão do tipo T.

[nameof](../keywords/nameof.md) – obtém o nome simples (não qualificado) de uma variável, tipo ou membro como uma cadeia de caracteres constante.

[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declara e retorna uma instância delegada.

[sizeof](../keywords/sizeof.md) – retorna o tamanho em bytes do operando do tipo.

[stackalloc](stackalloc.md) – aloca um bloco de memória na pilha.

[->](pointer-related-operators.md#pointer-member-access-operator--) – indireção de ponteiro combinada com acesso de membro.

## <a name="unary-operators"></a>Operadores unários

Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.

[+x](addition-operator.md) – retorna o valor de x.

[-x](subtraction-operator.md) – negação numérica.

[\!x](boolean-logical-operators.md#logical-negation-operator-) – negação lógica.

[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – complemento bit a bit.

[++x](arithmetic-operators.md#increment-operator-) – incremento de prefixo. Retorna o valor de x depois de atualizar o local de armazenamento com o valor de x que é um número maior (normalmente adiciona o inteiro 1).

[--x](arithmetic-operators.md#decrement-operator---) – decremento de prefixo. Retorna o valor de x depois de atualizar o local de armazenamento com o valor de x que é um número menor (normalmente subtrai o inteiro 1).

[(T)x](type-testing-and-conversion-operators.md#cast-operator-) – conversão de tipo.

[await](../keywords/await.md) – aguarda um `Task`.

[&x](pointer-related-operators.md#address-of-operator-) – endereço de uma variável.

[*x](pointer-related-operators.md#pointer-indirection-operator-) – indireção de ponteiro ou desreferenciar.

[operador true](true-false-operators.md) – retorna o valor [bool](../keywords/bool.md) `true` para indicar que um operando é definitivamente true.

[operador false](true-false-operators.md) – retorna o valor [bool](../keywords/bool.md) `true` para indicar que um operando é definitivamente false.

## <a name="multiplicative-operators"></a>Operadores de multiplicação

Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.

[x * y](arithmetic-operators.md#multiplication-operator-) – multiplicação.

[x / y](arithmetic-operators.md#division-operator-) – divisão. Se os operandos forem inteiros, o resultado será um inteiro truncado para zero (por exemplo, `-7 / 2 is -3`).

[x % y](arithmetic-operators.md#remainder-operator-) – restante. Se os operandos forem inteiros, isso retornará o resto da divisão de x por y.  Se `q = x / y` e `r = x % y`, então `x = q * y + r`.

## <a name="additive-operators"></a>Operadores aditivos

Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.

[x + y](arithmetic-operators.md#addition-operator-) – adição.

[x – y](arithmetic-operators.md#subtraction-operator--) – subtração.

## <a name="shift-operators"></a>Operadores shift

Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.

[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) – bits de deslocamento para a esquerda e preenche com zero à direita.

[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – bits de deslocamento para a direita. Se o operando esquerdo for `int` ou `long`, então, os bits à esquerda serão preenchidos com o bit de sinal. Se o operando esquerdo for `uint` ou `ulong`, então, os bits à esquerda serão preenchidos com zero.

## <a name="relational-and-type-testing-operators"></a>Operadores de teste de tipo e relacional

Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.

[x \< y](comparison-operators.md#less-than-operator-) – menor que (verdadeiro se x for menor que y).

[x > y](comparison-operators.md#greater-than-operator-) – maior que (verdadeiro se x for maior que y).

[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – menor ou igual a.

[x > = y](comparison-operators.md#greater-than-or-equal-operator-) – maior que ou igual a.

[is](type-testing-and-conversion-operators.md#is-operator) – compatibilidade de tipo. Retornará `true` se o operando esquerdo avaliado puder ser convertido no tipo especificado pelo operando à direita.

[as](type-testing-and-conversion-operators.md#as-operator) – conversão de tipo. Retorna o operando esquerdo convertido para o tipo especificado pelo operando à direita, mas `as` retorna `null`, em que `(T)x` lançaria uma exceção.

## <a name="equality-operators"></a>Operadores de igualdade

Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.

[x == y](equality-operators.md#equality-operator-) – igualdade. Por padrão, para tipos de referência diferentes de `string`, isso retorna uma igualdade de referência (teste de identidade). No entanto, os tipos podem sobrecarregar `==`, portanto, se sua intenção for testar a identidade, é melhor usar o método `ReferenceEquals` em `object`.

[x != y](equality-operators.md#inequality-operator-) – não é igual. Consulte o comentário sobre `==`. Se um tipo sobrecarregar `==`, então, ele deverá sobrecarregar `!=`.

## <a name="logical-and-operator"></a>Operador AND lógico

Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.

`x & y` – [AND lógico](boolean-logical-operators.md#logical-and-operator-) para os operandos `bool` ou [AND lógico](bitwise-and-shift-operators.md#logical-and-operator-) para os operandos dos tipos integrais.

## <a name="logical-xor-operator"></a>Operador XOR lógico

Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.

`x ^ y` – [XOR lógico](boolean-logical-operators.md#logical-exclusive-or-operator-) para os operandos `bool` ou [XOR lógico](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) para os operandos dos tipos integrais.

## <a name="logical-or-operator"></a>Operador lógico OU

Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.

`x | y` – [OR lógico](boolean-logical-operators.md#logical-or-operator-) para os operandos `bool` ou [OR lógico](bitwise-and-shift-operators.md#logical-or-operator-) para os operandos dos tipos integrais.

## <a name="conditional-and-operator"></a>Operador AND condicional

Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.

[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – AND lógico. Se `x` for avaliado como `false`, `y` não será avaliado.

## <a name="conditional-or-operator"></a>Operador OR condicional

Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.

[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – OR lógico. Se `x` for avaliado como `true`, `y` não será avaliado.

## <a name="null-coalescing-operator"></a>Operador de coalescência nula

Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.

[x ?? y](null-coalescing-operator.md) – retornará `x` se for não `null`; caso contrário, retornará `y`.

## <a name="conditional-operator"></a>Operador condicional

Esse operador tem precedência maior do que a próxima seção e precedência menor que a seção anterior.

[t ? x : y](conditional-operator.md) – se o teste `t` for avaliado como verdadeiro, então ele avaliará e retornará `x`; caso contrário, avaliará e retornará `y`.

## <a name="assignment-and-lambda-operators"></a>Operadores de atribuição e lambda

Esses operadores têm precedência maior do que a próxima seção e precedência menor que a seção anterior.

[x = y](assignment-operator.md) – atribuição.

[x += y](arithmetic-operators.md#compound-assignment) – incremento. Adicione o valor de `y` para o valor de `x`, armazene o resultado em `x` e retorne o novo valor. Se `x` designar um [evento](../keywords/event.md), então, `y` deverá ser um método adequado que o C# adiciona como um manipulador de eventos.

[x -= y](arithmetic-operators.md#compound-assignment) – diminuir. Subtraia o valor de `y` do valor de `x`, armazene o resultado em `x` e retorne o novo valor. Se `x` designar um [evento](../keywords/event.md), então, `y` deverá ser um método adequado que o C# remove como um manipulador de eventos.

[x *= y](arithmetic-operators.md#compound-assignment) – atribuição de multiplicação. Multiplique o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.

[x /= y](arithmetic-operators.md#compound-assignment) – atribuição de divisão. Divida o valor de `x` pelo valor de `y`, armazene o resultado em `x` e retorne o novo valor.

[x %= y](arithmetic-operators.md#compound-assignment) – atribuição restante. Divida o valor de `x` pelo valor de `y`, armazene o resto em `x` e retorne o novo valor.

[x &= y](boolean-logical-operators.md#compound-assignment) – atribuição AND. AND o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.

[x &#124;= y](boolean-logical-operators.md#compound-assignment) – atribuição OR. OR o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.

[x ^= y](boolean-logical-operators.md#compound-assignment) – atribuição XOR. XOR o valor de `y` com o valor de `x`, armazene o resultado em `x` e retorne o novo valor.

[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – atribuição de deslocamento para a esquerda. Desloque o valor de `x` para a esquerda em `y` casas decimais, armazene o resultado em `x` e retorne o novo valor.

[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – atribuição de deslocamento para a direita. Desloque o valor de `x` para a direita em `y` casas decimais, armazene o resultado em `x` e retorne o novo valor.

[=>](lambda-operator.md) – declaração de lambda.

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores](../../programming-guide/statements-expressions-operators/operators.md)
- [Operadores sobrecarregáveis](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
