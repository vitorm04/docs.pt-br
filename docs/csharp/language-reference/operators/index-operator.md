---
title: Operador [] – referência do C#
ms.custom: seodec18
ms.date: 01/10/2019
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 9088393f61d300ee76e56e320bec17b4a79bfebb
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835584"
---
# <a name="-operator-c-reference"></a>Operador [] (referência do C#)

Os colchetes, `[]`, normalmente são usados para acesso de elemento de matriz, indexador ou ponteiro.

Para obter mais informações sobre o acesso de elemento de ponteiro, confira [Como acessar um elemento de matriz com um ponteiro](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).

Os colchetes também são usados para especificar [atributos](../../programming-guide/concepts/attributes/index.md):

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="array-access"></a>Acesso de matriz

O exemplo a seguir demonstra como acessar elementos de matriz:

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Arrays)]

Se um índice de matriz estiver fora dos limites da dimensão correspondente de uma matriz, uma <xref:System.IndexOutOfRangeException> será gerada.

Como mostra o exemplo anterior, você também pode usar colchetes na declaração de um tipo de matriz e na criação de instâncias da matriz.

Para obter mais informações sobre matrizes, confira [Matrizes](../../programming-guide/arrays/index.md).

## <a name="indexer-access"></a>Acesso de indexador

O exemplo a seguir usa o tipo <xref:System.Collections.Generic.Dictionary%602> do .NET para demonstrar o acesso de indexador:

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Indexers)]

Os indexadores permitem indexar instâncias de um tipo definido pelo usuário de maneira semelhante à indexação de matriz. Ao contrário dos índices da matriz, que precisam ser um inteiro, os argumentos do indexador podem ser declarados como qualquer tipo.

Para obter mais informações sobre indexadores, confira [Indexadores](../../programming-guide/indexers/index.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

O acesso de elemento `[]` não é considerado um operador que pode ser sobrecarregado. Use [indexadores](../../programming-guide/indexers/index.md) para permitir a indexação com tipos definidos pelo usuário.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seções [Acesso de elemento](~/_csharplang/spec/expressions.md#element-access) e [Acesso de elemento de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-element-access) da [Especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Matrizes](../../programming-guide/arrays/index.md)
- [Indexadores](../../programming-guide/indexers/index.md)
- [Tipos de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Atributos](../../programming-guide/concepts/attributes/index.md)
- [Operadores ?. e ?[]](null-conditional-operators.md)