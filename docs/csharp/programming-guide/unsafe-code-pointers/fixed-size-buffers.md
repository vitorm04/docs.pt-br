---
title: Buffers de tamanho fixo (Guia de Programação em C#)
ms.date: 04/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9158550885ea0a95a56f318362b21db48e648234
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Buffers de tamanho fixo (Guia de Programação em C#)

No C#, você pode usar a instrução [fixed](../../language-reference/keywords/fixed-statement.md) para criar um buffer com uma matriz de tamanho fixo em uma estrutura de dados. Os buffers de tamanho fixo são úteis ao escrever métodos que interoperam com fontes de dados de outras linguagens ou plataformas. A matriz fixa pode usar qualquer atributo ou modificador que for permitido para membros de struct regulares. A única restrição é que o tipo da matriz deve ser `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Comentários

No código de seguro, um struct C# que contém uma matriz não contém os elementos da matriz. Em vez disso, o struct contém uma referência aos elementos. Você pode inserir uma matriz de tamanho fixo em um [struct](../../language-reference/keywords/struct.md) quando ele é usado em um bloco de código [não seguro](../../language-reference/keywords/unsafe.md).

O seguinte `struct` tem 8 bytes de tamanho. A matriz `pathName` é uma referência:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

Um `struct` pode conter uma matriz inserida em código não seguro. No exemplo a seguir, a matriz `fixedBuffer` tem tamanho fixo. É possível uma instrução `fixed` para estabelecer um ponteiro para o primeiro elemento. Os elementos da matriz são acessados por este ponteiro. A instrução `fixed` fixa o campo da instância `fixedBuffer` em um local específico na memória.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

O tamanho da matriz `char` de 128 elementos é 256 bytes. Buffers de [char](../../language-reference/keywords/char.md) de tamanho fixo sempre têm dois bytes por caractere, independentemente da codificação. Isso vale mesmo quando os buffers de char passam por marshaling para structs ou métodos de API com `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`. Para obter mais informações, consulte <xref:System.Runtime.InteropServices.CharSet>.

O exemplo anterior demonstra o acesso a campos `fixed` sem fixação, que estão disponíveis começando com o C# 7.3.

Outra matriz de tamanho fixo comum é a matriz [bool](../../language-reference/keywords/bool.md). Os elementos em uma matriz `bool` sempre têm um byte de tamanho. Matrizes `bool` não são adequadas para criar buffers ou matrizes de bits.

> [!NOTE]
> Exceto pela memória criada usando [stackalloc](../../language-reference/keywords/stackalloc.md), o compilador C# e o CLR (Common Language Runtime) não executam nenhuma verificação de estouro de buffer de segurança. Assim como acontece com qualquer código não seguro, tenha cuidado.

Buffers não seguros diferem de matrizes regulares das seguintes maneiras:

- Você só pode usar buffers não seguros em um contexto não seguro.
- Buffers não seguros sempre são vetores ou matrizes unidimensionais.
- A declaração de matriz deve incluir uma contagem, como `char id[8]`. Não é possível usar `char id[]`.
- Buffers não seguros só podem ser structs ou campos de instância em um contexto não seguro.

## <a name="see-also"></a>Consulte também

[Guia de Programação em C#](../index.md)  
[Código não seguro e ponteiros](index.md)  
[Instrução fixed](../../language-reference/keywords/fixed-statement.md)  
[Interoperabilidade](../interop/index.md)
