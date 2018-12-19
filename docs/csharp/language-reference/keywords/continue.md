---
title: Instrução continue – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: fbb5d170f10c0a4b6c6edeae6c3f4a549de65525
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243888"
---
# <a name="continue-c-reference"></a>continue (Referência de C#)

A instrução `continue` passa o controle para a próxima iteração da instrução de circunscrição [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md) ou [foreach](../../../csharp/language-reference/keywords/foreach-in.md) na qual ela aparece.

## <a name="example"></a>Exemplo

Neste exemplo, um contador é inicializado para a contagem de 1 a 10. Ao usar a instrução `continue` junto com a expressão `(i < 9)`, as instruções entre `continue` e o término do corpo `for` serão ignoradas.

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
- [Instrução Break](/cpp/cpp/break-statement-cpp)  
- [Instruções de atalho](../../../csharp/language-reference/keywords/jump-statements.md)