---
title: Buffers de tamanho fixo – Guia de Programação em C#
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 5920dd125ded34969d60feb299568b56402056ab
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140550"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Buffers de tamanho fixo (Guia de Programação em C#)

No C#, você pode usar a instrução [fixed](../../language-reference/keywords/fixed-statement.md) para criar um buffer com uma matriz de tamanho fixo em uma estrutura de dados. Os buffers de tamanho fixo são úteis ao escrever métodos que interoperam com fontes de dados de outras linguagens ou plataformas. A matriz fixa pode usar qualquer atributo ou modificador que for permitido para membros de struct regulares. A única restrição é que o tipo da matriz deve ser `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Comentários

No código de seguro, um struct C# que contém uma matriz não contém os elementos da matriz. Em vez disso, o struct contém uma referência aos elementos. Você pode inserir uma matriz de tamanho fixo em um [struct](../../language-reference/builtin-types/struct.md) quando ele é usado em um bloco de código [não seguro](../../language-reference/keywords/unsafe.md).

O tamanho dos itens `struct` a seguir não depende do número de elementos na matriz, pois `pathName` é uma referência:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

Um `struct` pode conter uma matriz inserida em código não seguro. No exemplo a seguir, a matriz `fixedBuffer` tem tamanho fixo. É possível uma instrução `fixed` para estabelecer um ponteiro para o primeiro elemento. Os elementos da matriz são acessados por este ponteiro. A instrução `fixed` fixa o campo da instância `fixedBuffer` em um local específico na memória.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

O tamanho da matriz `char` de 128 elementos é 256 bytes. Buffers de [char](../../language-reference/builtin-types/char.md) de tamanho fixo sempre têm dois bytes por caractere, independentemente da codificação. Isso vale mesmo quando os buffers de char passam por marshaling para structs ou métodos de API com `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`. Para obter mais informações, consulte <xref:System.Runtime.InteropServices.CharSet>.

O exemplo anterior demonstra o acesso a campos `fixed` sem fixação, que estão disponíveis a partir do C# 7.3.

Outra matriz de tamanho fixo comum é a matriz [bool](../../language-reference/builtin-types/bool.md). Os elementos em uma matriz `bool` sempre têm um byte de tamanho. Matrizes `bool` não são adequadas para criar buffers ou matrizes de bits.

Buffers de tamanho fixo são compilados <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>com o, que instrui o Common Language Runtime (CLR) de que um tipo contém uma matriz não gerenciada que potencialmente pode exceder. Isso é semelhante à memória criada usando [stackalloc](../../language-reference/operators/stackalloc.md), que habilita automaticamente os recursos de detecção de saturação de buffer no CLR. O exemplo anterior mostra como um buffer de tamanho fixo pode existir em `unsafe struct`um.

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

O compilador gerou C# para `Buffer`, é atribuído da seguinte maneira:

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

Buffers de tamanho fixo diferem de matrizes regulares das seguintes maneiras:

- Só pode ser usado em um contexto sem [segurança](../../language-reference/keywords/unsafe.md) .
- Só podem ser campos de instância de structs.
- Eles são sempre vetores ou matrizes unidimensionais.
- A declaração deve incluir o comprimento, como `fixed char id[8]`. Não é possível usar `fixed char id[]`.

## <a name="see-also"></a>Veja também

- [Guia de programação C#](../index.md)
- [Código não seguro e ponteiros](index.md)
- [Instrução fixed](../../language-reference/keywords/fixed-statement.md)
- [Interoperabilidade](../interop/index.md)
