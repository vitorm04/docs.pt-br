---
title: Palavra-chave unsafe – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: aa22eac9d4ae06753bbed1fd5733eddeddd81a46
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422267"
---
# <a name="unsafe-c-reference"></a>unsafe (Referência de C#)

A palavra-chave `unsafe` denota um contexto inseguro, que é necessário para qualquer operação que envolva ponteiros. Para obter mais informações, consulte [Código não seguro e ponteiros](../../programming-guide/unsafe-code-pointers/index.md).

Você pode usar o modificador `unsafe` na declaração de um tipo ou membro. Toda a extensão textual do tipo ou membro é, portanto, considerada um contexto inseguro. Por exemplo, a seguir está um método declarado com o modificador `unsafe`:

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

O escopo do contexto inseguro se estende da lista de parâmetros até o final do método, portanto, os ponteiros também podem ser usados na lista de parâmetros:

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

Você também pode usar um bloco não seguro para habilitar o uso de um código não seguro dentro desse bloco. Por exemplo:

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

Para compilar o código não seguro, você deve especificar a opção do compilador [`-unsafe`](../compiler-options/unsafe-compiler-option.md). O código não seguro não é verificável pelo Common Language Runtime.

## <a name="example"></a>Exemplo

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para saber mais, confira [código unsafe](~/_csharplang/spec/unsafe-code.md) na [Especificação da Linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Instrução fixed](fixed-statement.md)
- [Código não seguro e ponteiros](../../programming-guide/unsafe-code-pointers/index.md)
- [Buffers de tamanho fixo](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
