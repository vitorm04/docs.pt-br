---
title: Operador => – referência do C#
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 15c02e11610866f359e3e3a7e2751ded918154b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846240"
---
# <a name="-operator-c-reference"></a>Operador => (referência do C#)

O `=>` token é suportado em duas formas: como [operador de lambda](#lambda-operator) e como separador de um nome de membro e a implementação do membro em uma [definição de corpo de expressão](#expression-body-definition).

## <a name="lambda-operator"></a>Operador lambda

Em [expressões lambda,](../../programming-guide/statements-expressions-operators/lambda-expressions.md)o `=>` operador lambda separa os parâmetros de entrada do lado esquerdo do corpo lambda do lado direito.

O seguinte exemplo usa o recurso [LINQ](../../programming-guide/concepts/linq/index.md) com a sintaxe de método para demonstrar o uso de expressões lambda:

[!code-csharp-interactive[infer types of input variables](snippets/LambdaOperator.cs#InferredTypes)]

Os parâmetros de entrada de uma expressão lambda são fortemente digitados no momento da compilação. Quando o compilador pode inferir os tipos de parâmetros de entrada, como no exemplo anterior, você pode omiti-lo declarações de tipo. Se você precisar especificar o tipo de parâmetros de entrada, você deve fazer isso para cada parâmetro, como mostra o exemplo a seguir:

[!code-csharp-interactive[specify types of input variables](snippets/LambdaOperator.cs#ExplicitTypes)]

O exemplo a seguir mostra como definir uma expressão lambda sem parâmetros de entrada:

[!code-csharp-interactive[without input variables](snippets/LambdaOperator.cs#WithoutInput)]

Para obter mais informações, consulte [expressões Lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>Definição de corpo da expressão

Uma definição de corpo da expressão tem a seguinte sintaxe geral:

```csharp
member => expression;
```

em que `expression` é uma expressão válida. O tipo de retorno de `expression` deve ser implicitamente conversível para o tipo de retorno do membro. Se o tipo de `void` devolução do membro for ou se o membro `set` for `expression` um construtor, um finalizador ou um acessório de propriedade, deve ser uma expressão de [*declaração*](~/_csharplang/spec/statements.md#expression-statements), que pode ser de qualquer tipo.

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

As definições do corpo de expressão para métodos, operadores e propriedades somente leitura são suportadas a partir de C # 6. As definições de corpo de expressão para construtores, finalizadores e acessórios de propriedade e indexadores são suportadas a partir de C# 7.0.

Para obter mais informações, consulte [Membros aptos para expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

O operador `=>` não pode ser sobrecarregado.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações sobre o operador lambda, consulte a seção [expressões](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de função Anônima da especificação do [idioma C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
