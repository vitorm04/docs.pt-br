---
title: Operadores de conversão e teste de tipo - Referência de C#
description: Saiba mais sobre os operadores do C# que você pode usar para verificar o tipo de um resultado de expressão e convertê-lo para outro tipo, se necessário.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: a9e5139e6d650aa6935bff934ca25502fdc14775
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744074"
---
# <a name="type-testing-and-conversion-operators-c-reference"></a>Operadores de conversão e teste de tipo (Referência de C#)

Você pode usar os seguintes operadores para executar a verificação de tipo ou conversão de tipo:

- [operador is](#is-operator): para verificar se o tipo de tempo de execução de uma expressão é compatível com um determinado tipo
- [operador as](#as-operator): para converter explicitamente uma expressão em um determinado tipo, se o tipo de tempo de execução for compatível com esse tipo
- [operador cast ()](#cast-operator-): para executar uma conversão explícita
- [operador typeof](#typeof-operator): para obter a instância <xref:System.Type?displayProperty=nameWithType> para um tipo

## <a name="is-operator"></a>Operador is

O operador `is` verifica se o tipo de tempo de execução de um resultado de expressão é compatível com um determinado tipo. A partir do C# 7.0, o operador `is` também testa um resultado de expressão em relação a um padrão.

A expressão com o operador `is` de teste de tipo tem o seguinte formato

```csharp
E is T
```

em que `E` é uma expressão que retorna um valor e `T` é o nome de um tipo ou um parâmetro de tipo. `E` não pode ser um método anônimo ou uma expressão lambda.

A expressão `E is T` retorna `true` se o resultado de `E` não for nulo e puder ser convertido para o tipo `T` por uma conversão de referência, uma conversão boxing ou uma conversão unboxing; caso contrário, retorna `false`. O operador `is` não considera conversões definidas pelo usuário.

O exemplo a seguir demonstra que o operador `is` retorna `true` se o tipo de tempo de execução de um resultado da expressão é derivado de um determinado tipo, ou seja, existe uma conversão de referência entre tipos:

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

O próximo exemplo mostra que o operador `is` leva em conta conversões boxing e unboxing, mas não considera conversões numéricas:

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

Para saber mais sobre conversões em C#, confira o capítulo [Conversões](~/_csharplang/spec/conversions.md) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

### <a name="type-testing-with-pattern-matching"></a>Teste de tipo com correspondência de padrões

A partir do C# 7.0, o operador `is` também testa um resultado de expressão em relação a um padrão. Em particular, ele dá suporte ao padrão de tipo da seguinte forma:

```csharp
E is T v
```

em que `E` é uma expressão que retorna um valor, `T` é o nome de um tipo ou um parâmetro de tipo, e `v` é uma nova variável local do tipo `T`. Se o resultado de `E` não for nulo e puder ser convertido para `T` por uma conversão de referência, boxing ou unboxing, a expressão `E is T v` retornará `true` e o valor convertido do resultado de `E`será atribuído à variável `v`.

O exemplo a seguir demonstra o uso do operador `is` com um padrão de tipo:

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Para saber mais sobre o padrão de tipos e outros padrões com suporte, confira [Correspondência de padrões com is](../keywords/is.md#pattern-matching-with-is).

## <a name="as-operator"></a>Operador as

O operador `as` converte explicitamente o resultado de uma expressão para uma determinada referência ou tipo de valor anulável. Se a conversão não for possível, o operador `as` retorna `null`. Ao contrário do [operador cast ()](#cast-operator-), o operador `as` nunca lança uma exceção.

A expressão da forma

```csharp
E as T
```

em que `E` é uma expressão que retorna um valor e `T` é o nome de um tipo ou um parâmetro de tipo, produz o mesmo resultado que

```csharp
E is T ? (T)(E) : (T)null
```

exceto que `E` é avaliado apenas uma vez.

O operador `as` considera apenas as conversões de referência, anulável, boxing e unboxing. Não é possível usar o operador `as` para executar uma conversão definida pelo usuário. Para fazer isso, use o operador [cast ()](#cast-operator-).

O exemplo a seguir demonstra o uso do operador `as`:

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Como mostrado no exemplo anterior, você precisa comparar o resultado da expressão `as` com `null` para verificar se uma conversão foi bem-sucedida. A partir do C# 7.0, você pode usar o [operador is](#type-testing-with-pattern-matching) para testar se a conversão foi bem-sucedida e, se for bem-sucedida, atribuir seu resultado a uma nova variável.

## <a name="cast-operator-"></a>Operador cast ()

Uma expressão de conversão do formulário `(T)E` realiza uma conversão explícita do resultado da expressão `E` para o tipo `T`. Se não existir nenhuma conversão explícita do tipo `E` para o tipo `T`, ocorrerá um erro em tempo de compilação. No tempo de execução, uma conversão explícita pode não ter êxito e uma expressão de conversão pode lançar uma exceção.

O exemplo a seguir demonstra conversões numéricas e de referência explícitas:

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

Para saber mais sobre conversões explícitas sem suporte, confira a seção [Conversões explícitas](~/_csharplang/spec/conversions.md#explicit-conversions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md). Para saber mais sobre como definir uma conversão de tipo explícito ou implícito personalizado, confira [Operadores de conversão definidos pelo usuário](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>Outros usos de ()

Você também usa parênteses para [ chamar um método ou chamar um delegado ](member-access-operators.md#invocation-operator-).

Outro uso dos parênteses é especificar a ordem na qual as operações em uma expressão são avaliadas. Para obter mais informações, confira a seção [Adicionando parênteses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) o artigo [Operadores](../../programming-guide/statements-expressions-operators/operators.md). Para obter a lista de operadores ordenada pelo nível de precedência, confira [Operadores do C#](index.md).

## <a name="typeof-operator"></a>Operador typeof

O operador `typeof` obtém a instância <xref:System.Type?displayProperty=nameWithType> para um tipo. Um argumento do operador `typeof` deve ser o nome de um tipo ou um parâmetro de tipo, como mostra o exemplo a seguir:

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

Você também pode usar o operador `typeof` com tipos genéricos não associados. O nome de um tipo genérico não associado deve conter o número apropriado de vírgulas, que é um a menos que o número de parâmetros de tipo. O exemplo a seguir mostra o uso do operador `typeof` com um tipo genérico não associado:

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Uma expressão não pode ser um argumento do operador `typeof`. Para obter a instância <xref:System.Type?displayProperty=nameWithType> para o tipo de tempo de execução do resultado da expressão, use o método <xref:System.Object.GetType%2A?displayProperty=nameWithType>.

### <a name="type-testing-with-the-typeof-operator"></a>Teste de tipo com o operador `typeof`

Use o operador `typeof` para verificar se o tipo de tempo de execução do resultado da expressão corresponde exatamente a um determinado tipo. O exemplo a seguir demonstra a diferença entre a verificação de tipo executada com o operador `typeof` e o [operador is](#is-operator):

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Os operadores `is`, `as` e `typeof` não são sobrecarregados.

Um tipo definido pelo usuário não pode sobrecarregar o operador `()`, mas pode definir conversões de tipo customizado que podem ser executadas por uma expressão de conversão. Para saber mais, confira [Operadores de conversão definidos pelo usuário](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Operador is](~/_csharplang/spec/expressions.md#the-is-operator)
- [Operador as](~/_csharplang/spec/expressions.md#the-as-operator)
- [Expressões cast](~/_csharplang/spec/expressions.md#cast-expressions)
- [Operador typeof](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [Como converter com segurança usando a correspondência de padrões e os operadores is e as](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
