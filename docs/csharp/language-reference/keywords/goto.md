---
title: Instrução goto – Referência em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: e4642d0e43a538217493298b58d572e435db5dae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645321"
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

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Instrução goto (C++)](/cpp/cpp/goto-statement-cpp)
- [Instruções de atalho](jump-statements.md)
