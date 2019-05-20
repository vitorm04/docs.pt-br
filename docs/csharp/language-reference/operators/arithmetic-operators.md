---
title: Operadores aritméticos – Referência de C#
description: Saiba mais sobre os operadores do C# que executam operações de multiplicação, divisão, resto, adição e subtração com tipos numéricos.
ms.date: 03/27/2019
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: 25f716084c489c834e9242800f4c7e341c41aa58
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880672"
---
# <a name="arithmetic-operators-c-reference"></a>Operadores aritméticos (Referência de C#)

Os seguintes operadores executam operações aritméticas com tipos numéricos:

- Operadores unários [`++` (incremento)](#increment-operator-), [`--` (decremento)](#decrement-operator---), [`+` (adição)](#unary-plus-and-minus-operators) e [`-` (subtração)](#unary-plus-and-minus-operators)
- Operadores binários [`*` (multiplicação)](#multiplication-operator-), [`/` (divisão)](#division-operator-), [`%` (resto)](#remainder-operator-), [`+` (adição)](#addition-operator-) e [`-` (subtração)](#subtraction-operator--)

Esses operadores dão suporte a todos os tipos numéricos [integrais](../keywords/integral-types-table.md) e de [ponto flutuante](../keywords/floating-point-types-table.md).

## <a name="increment-operator-"></a>Operador de incremento ++

O operador de incremento unário `++` incrementa seu operando em 1. O operando precisa ser uma variável, um acesso de [propriedade](../../programming-guide/classes-and-structs/properties.md) ou um acesso de [indexador](../../../csharp/programming-guide/indexers/index.md).

Há duas formas de suporte para o operador de incremento: o operador de incremento pós-fixado, `x++`, e o operador de incremento pré-fixado, `++x`.

### <a name="postfix-increment-operator"></a>Operador de incremento pós-fixado

O resultado de `x++` é o valor de `x` *antes* da operação, como mostra o exemplo a seguir:

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Operador de incremento de prefixo

O resultado de `++x` é o valor de `x` *após* a operação, como mostra o exemplo a seguir:

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Operador de decremento --

O operador de decremento unário `--` decrementa o operando em 1. O operando precisa ser uma variável, um acesso de [propriedade](../../programming-guide/classes-and-structs/properties.md) ou um acesso de [indexador](../../../csharp/programming-guide/indexers/index.md).

Há duas formas de suporte para o operador de decremento: o operador de decremento pós-fixado, `x--`, e o operador de decremento pré-fixado, `--x`.

### <a name="postfix-decrement-operator"></a>Operador de decremento pós-fixado

O resultado de `x--` é o valor de `x` *antes* da operação, como mostra o exemplo a seguir:

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Operador de decremento de prefixo

O resultado de `--x` é o valor de `x` *após* a operação, como mostra o exemplo a seguir:

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Operadores unários de adição e subtração

O operador unário `+` retorna o valor do operando. O operador unário `-` calcula a negação numérica do operando.

[!code-csharp-interactive[unary plus and minus](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

O operador unário `-` não dá suporte ao tipo [ulong](../keywords/ulong.md).

## <a name="multiplication-operator-"></a>Operador de multiplicação *

O operador de multiplicação `*` calcula o produto dos operandos:

[!code-csharp-interactive[multiplication operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

O operador unário `*` é o [operador de indireção de ponteiro](pointer-related-operators.md#pointer-indirection-operator-).

## <a name="division-operator-"></a>Operador de divisão /

O operador de divisão `/` divide o primeiro operando pelo segundo.

### <a name="integer-division"></a>Divisão de inteiros

Para os operandos de tipos inteiros, o resultado do operador `/` é de um tipo inteiro e igual ao quociente dos dois operandos arredondados para zero:

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

Para obter o quociente dos dois operandos como um número de ponto flutuante, use o tipo `float`, `double` ou `decimal`:

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Divisão de ponto flutuante

Para os tipos `float`, `double` e `decimal`, o resultado do operador `/` é o quociente dos dois operandos:

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

Se um dos operandos é `decimal`, outro operando não pode ser `float` nem `double`, porque nem `float` ou `double` é implicitamente conversível para `decimal`. Você deve converter explicitamente o operando `float` ou `double` para o tipo `decimal`. Para saber mais sobre as conversões implícitas entre tipos numéricos, confira a [Tabela de conversões numéricas implícitas](../keywords/implicit-numeric-conversions-table.md).

## <a name="remainder-operator-"></a>Operador de resto %

O operador de resto `%` calcula o resto após dividir o primeiro operando pelo segundo.

### <a name="integer-remainder"></a>Resto inteiro
  
Para os operandos de tipos inteiros, o resultado de `a % b` é o valor produzido por `a - (a / b) * b`. O sinal do resto diferente de zero é o mesmo que o do primeiro operando, conforme mostra o seguinte exemplo:

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

Use o método <xref:System.Math.DivRem%2A?displayProperty=nameWithType> para calcular a divisão de inteiros e os resultados do resto.

### <a name="floating-point-remainder"></a>Resto de ponto flutuante

Para os operandos `float` e `double`, o resultado de `x % y` para o `x` e o `y` finitos é o valor `z` tal que

- O sinal de `z`, se diferente de zero, é o mesmo que o sinal de `x`.
- O valor absoluto de `z` é o valor produzido por `|x| - n * |y|`, em que `n` é o maior inteiro possível que é inferior ou igual a `|x| / |y|`, e `|x|` e `|y|` são os valores absolutos de `x` e `y`, respectivamente.

> [!NOTE]
> Esse método de calcular o resto é semelhante ao usado para operandos inteiros, mas é diferente do IEEE 754. Se precisar da operação de resto em conformidade com o IEEE 754, use o método <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>.

Para saber mais sobre o comportamento do operador `%` com operandos não finitos, confira a seção [Operador de restante](~/_csharplang/spec/expressions.md#remainder-operator) da [especificação da linguagem C#](~/_csharplang/spec/introduction.md).

Para os operandos `decimal`, o operador de resto `%` é equivalente ao [operador de resto](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) do tipo <xref:System.Decimal?displayProperty=nameWithType>.

O seguinte exemplo demonstra o comportamento do operador de resto com os operandos de ponto flutuante:

[!code-csharp-interactive[floating-point remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Operador de adição +

O operador de adição `+` calcula a soma dos operandos:

[!code-csharp-interactive[addition operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

Você também pode usar o operador `+` para a combinação de delegado e concatenação de cadeia de caracteres. Para obter mais informações, confira o artigo [Operador `+`](addition-operator.md).

## <a name="subtraction-operator--"></a>Operador de subtração -

O operador de subtração `-` subtrai o segundo operando do primeiro operando:

[!code-csharp-interactive[subtraction operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

Você também pode usar o operador `-` para a remoção de delegado. Para obter mais informações, confira o artigo [Operador `-`](subtraction-operator.md).

## <a name="compound-assignment"></a>Atribuição composta

Para um operador binário `op`, uma expressão de atribuição composta do formato

```csharp
x op= y
```

equivale a

```csharp
x = x op y
```

exceto que `x` é avaliado apenas uma vez.

O seguinte exemplo demonstra o uso da atribuição composta com operadores aritméticos:

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

Devido a [promoções numéricas](~/_csharplang/spec/expressions.md#numeric-promotions), o resultado da operação `op` pode não ser implicitamente conversível no tipo `T` de `x`. Nesse caso, se `op` for um operador predefinido e o resultado da operação for explicitamente convertido no tipo `T` de `x`, uma expressão de atribuição composta da forma `x op= y` será equivalente a `x = (T)(x op y)`, exceto que `x` será avaliada apenas uma vez. O exemplo a seguir demonstra esse comportamento:

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Use também os operadores `+=` e `-=` para assinar e cancelar a assinatura de [eventos](../keywords/event.md). Para obter mais informações, confira [Como assinar e cancelar a assinatura de eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-precedence-and-associativity"></a>Precedência e associatividade do operador

A seguinte lista ordena os operadores aritméticos da precedência mais alta para a mais baixa:

- Incluir um pós-fixo a operadores de incremento `x++` e decremento `x--`
- Incluir um prefixo a operadores de incremento `++x` e de decremento `--x` e operadores unários `+` e `-`
- Operadores de multiplicação `*`, `/` e `%`
- Operadores de adição `+` e `-`

Operadores aritméticos binários são associativos à esquerda. Ou seja, os operadores com o mesmo nível de precedência são avaliados da esquerda para a direita.

Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência e pela capacidade de associação do operador.

[!code-csharp-interactive[precedence and associativity](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Para obter a lista completa de operadores do C# ordenada pelo nível de precedência, confira [Operadores do C#](index.md).

## <a name="arithmetic-overflow-and-division-by-zero"></a>Estouro aritmético e divisão por zero

Quando o resultado de uma operação aritmética está fora do intervalo de valores finitos possíveis do tipo numérico envolvido, o comportamento de um operador aritmético depende do tipo dos operandos.

### <a name="integer-arithmetic-overflow"></a>Estouro aritmético de inteiros

A divisão de inteiro por zero sempre lança um <xref:System.DivideByZeroException>.

No caso de um estouro aritmético de inteiros, um contexto de verificação de estouro, que pode ser [verificado ou não verificado](../keywords/checked-and-unchecked.md), controla o comportamento resultante:

- Em um contexto verificado, se o estouro acontece em uma expressão de constante, ocorre um erro em tempo de compilação. Caso contrário, quando a operação é executada em tempo de execução, uma <xref:System.OverflowException> é gerada.
- Em um contexto não verificado, o resultado é truncado pelo descarte dos bits de ordem superior que não se ajustam ao tipo de destino.

Juntamente com as instruções [verificadas e não verificadas](../keywords/checked-and-unchecked.md), você pode usar os operadores `checked` e `unchecked` para controlar o contexto de verificação de estouro, no qual uma expressão é avaliada:

[!code-csharp-interactive[checked and unchecked](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

Por padrão, as operações aritméticas ocorrem em um contexto *não verificado*.

### <a name="floating-point-arithmetic-overflow"></a>Estouro aritmético de ponto flutuante

As operações aritméticas com os tipos `float` e `double` nunca geram uma exceção. O resultado de operações aritméticas com esses tipos pode ser um dos valores especiais que representam o infinito e um valor não é um número:

[!code-csharp-interactive[double non-finite values](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

Para os operandos do tipo `decimal`, o estouro aritmético sempre gera uma <xref:System.OverflowException> e a divisão por zero sempre gera uma <xref:System.DivideByZeroException>.

## <a name="round-off-errors"></a>Erros de arredondamento

Devido às limitações gerais de uma representação de ponto flutuante de números reais e da aritmética de ponto flutuante, os erros de arredondamento podem ocorrer em cálculos com tipos de ponto flutuante. Ou seja, o resultado produzido de uma expressão pode diferir do resultado matemático esperado. O seguinte exemplo demonstra vários casos desse tipo:

[!code-csharp-interactive[round-off errors](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

Para obter mais informações, confira os comentários nas páginas de referência [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks) ou [System.Decimal](/dotnet/api/system.decimal#remarks).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Um tipo definido pelo usuário pode [sobrecarregar](../keywords/operator.md) os operadores aritméticos unários (`++`, `--`, `+` e `-`) e binários (`*`, `/`, `%`, `+` e `-`). Quando um operador binário está sobrecarregado, o operador de atribuição composta correspondente também é implicitamente sobrecarregado. Um tipo definido pelo usuário não pode sobrecarregar explicitamente um operador de atribuição composta.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Operadores de incremento e decremento pós-fixados](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Operadores de incremento e decremento pré-fixados](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [Operador unário de adição](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [Operador unário de subtração](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [Operador de multiplicação](~/_csharplang/spec/expressions.md#multiplication-operator)
- [Operador de divisão](~/_csharplang/spec/expressions.md#division-operator)
- [Operador de resto](~/_csharplang/spec/expressions.md#remainder-operator)
- [Operador de adição](~/_csharplang/spec/expressions.md#addition-operator)
- [Operador de subtração](~/_csharplang/spec/expressions.md#subtraction-operator)
- [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment)
- [Os operadores verificados e não verificados](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [Promoções numéricas](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [Numéricos no .NET](../../../standard/numerics.md)
