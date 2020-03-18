---
title: Instrução goto – Referência em C#
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715279"
---
# <a name="goto-c-reference"></a>goto (Referência de C#)

A declaração `goto` transfere o controle do programa diretamente para uma instrução rotulada.

Um uso comum de `goto` é a transferência do controle para um rótulo de caso de opção específico ou para o rótulo padrão em uma instrução `switch`.

A instrução `goto` também é útil para sair de loops profundamente aninhados.

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra o uso de `goto` em uma instrução [switch](switch.md).

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra o uso de `goto` para sair de loops aninhados.

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Instrução goto (C++)](/cpp/cpp/goto-statement-cpp)
