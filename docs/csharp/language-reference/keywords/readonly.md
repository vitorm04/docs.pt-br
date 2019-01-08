---
title: Palavra-chave readonly – Referência de C#
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: dfbeb5ff94f39e8d8df03feea9ff55db748d2182
ms.sourcegitcommit: deb9225a55485a5a6e6c7914deb30ccfceb69d3f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2019
ms.locfileid: "54058575"
---
# <a name="readonly-c-reference"></a>readonly (Referência de C#)

A palavra-chave `readonly` é um modificador que pode ser usado em três contextos:

- Em uma [declaração de campo](#readonly-field-example), `readonly` indica que a atribuição ao campo só pode ocorrer como parte da declaração ou em um construtor na mesma classe.
- Em uma [definição `readonly struct`](#readonly-struct-example), `readonly` indica que o `struct` é imutável.
- Em um [retorno de método `ref readonly`](#ref-readonly-return-example), o modificador `readonly` indica que o método retorna uma referência e que as gravações não são permitidas para essa referência.

Os dois contextos finais foram adicionados no C# 7.2.

## <a name="readonly-field-example"></a>Exemplo de campo readonly

Neste exemplo, o valor do campo `year` não pode ser alterado no método `ChangeYear`, ainda que seja atribuído a ele um valor no construtor da classe:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Você pode atribuir um valor a um campo `readonly` apenas nos seguintes contextos:

- Quando a variável é inicializada na declaração, por exemplo:

```csharp
public readonly int y = 5;
```

- Em um construtor de instância da classe que contém a declaração de campo de instância.
- No construtor estático da classe que contém a declaração do campo estático.

Esses contextos de construtor também são os únicos em que é válido passar um campo `readonly` como um parâmetro [out](out-parameter-modifier.md) ou [ref](ref.md).

> [!NOTE]
> A palavra-chave `readonly` é diferente da palavra-chave [const](const.md). O campo `const` pode ser inicializado apenas na declaração do campo. Um campo `readonly` pode ser atribuído várias vezes na declaração do campo e em qualquer construtor. Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado. Além disso, enquanto um campo `const` é uma constante em tempo de compilação, o campo `readonly` pode ser usado para constantes de tempo de execução, como no exemplo a seguir:

```csharp
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

No exemplo anterior, se você usar uma instrução semelhante ao seguinte exemplo:

`p2.y = 66;        // Error`

você receberá a mensagem de erro do compilador:

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a>Exemplo de struct readonly

O modificador `readonly` em uma definição `struct` declara que o struct é **imutável**. Cada campo da instância de `struct` precisa ser marcado como `readonly`, conforme é mostrado no exemplo a seguir:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

O exemplo anterior usa as [propriedades automáticas de readonly](../../properties.md#read-only) para declarar seu armazenamento. Isso instrui o compilador a criar campos de suporte `readonly` para essas propriedades. Você também pode declarar campos `readonly` diretamente:

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

Adicionar um campo `readonly` não marcado gera o erro do compilador `CS8340`: "Campos de instância de structs somente leitura devem ser somente leitura."

## <a name="ref-readonly-return-example"></a>Exemplo de retorno de readonly de ref

O modificador `readonly` em um `ref return` indica que a referência retornada não pode ser modificada. O exemplo a seguir retorna uma referência para a origem. Ele usa o modificador `readonly` para indicar que os chamadores não podem modificar a origem:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
O tipo retornado não precisa ser um `readonly struct`. Qualquer tipo que possa ser retornado por `ref` pode ser retornado por `ref readonly`

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Modificadores](modifiers.md)
- [const](const.md)
- [Campos](../../programming-guide/classes-and-structs/fields.md)
