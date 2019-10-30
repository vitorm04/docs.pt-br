---
title: Operador => – referência do C#
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: b8d1a4e3971eb30e76bf543497931ce029c5541d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036373"
---
# <a name="-operator-c-reference"></a>Operador => (referência do C#)

O token de `=>` tem suporte em duas formas: como o [operador lambda](#lambda-operator) e como um separador de um nome de membro e a implementação de membro em uma [definição de corpo de expressão](#expression-body-definition).

## <a name="lambda-operator"></a>Operador lambda

Em [expressões lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md), o operador lambda `=>` separa os parâmetros de entrada no lado esquerdo do corpo lambda no lado direito.

O seguinte exemplo usa o recurso [LINQ](../../programming-guide/concepts/linq/index.md) com a sintaxe de método para demonstrar o uso de expressões lambda:

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

Os parâmetros de entrada de uma expressão lambda são fortemente tipados no momento da compilação. Quando o compilador pode inferir os tipos de parâmetros de entrada, como no exemplo anterior, você pode omitir declarações de tipo. Se você precisar especificar o tipo de parâmetros de entrada, deverá fazer isso para cada parâmetro, como mostra o exemplo a seguir:

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

O exemplo a seguir mostra como definir uma expressão lambda sem parâmetros de entrada:

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

Para obter mais informações, confira [Expressões lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>Definição de corpo da expressão

Uma definição de corpo da expressão tem a seguinte sintaxe geral:

```csharp
member => expression;
```

em que `expression` é uma expressão válida. O tipo de retorno de `expression` deve ser implicitamente conversível para o tipo de retorno do membro. Se o tipo de retorno do membro for `void` ou se o membro for um construtor, um finalizador ou uma propriedade `set` acessador, `expression` deverá ser uma [*expressão de instrução*](~/_csharplang/spec/statements.md#expression-statements), que pode ser de qualquer tipo.

O seguinte exemplo mostra uma definição de corpo da expressão para um método `Person.ToString`:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

É uma versão abreviada da seguinte definição de método:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

As definições de corpo de expressão para métodos, operadores e propriedades somente leitura têm suporte a C# partir de 6. As definições de corpo de expressão para construtores, finalizadores e acessadores de propriedade e indexador têm C# suporte a partir de 7,0.

Para obter mais informações, consulte [Membros aptos para expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

O operador `=>` não pode ser sobrecarregado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações sobre o operador lambda, consulte a seção [expressões de função anônimas](~/_csharplang/spec/expressions.md#anonymous-function-expressions) da [ C# especificação da linguagem](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
