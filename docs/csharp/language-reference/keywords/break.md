---
title: Instrução break (Referência do C#)
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 987ee1ca5601b3dd105412bf0fa18361c57a95fd
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315232"
---
# <a name="break-c-reference"></a>break (Referência de C#)

A instrução `break` termina o loop delimitador mais próximo ou a instrução [switch](../../../csharp/language-reference/keywords/switch.md) na qual ele aparece. Controle é passado para a instrução que segue a instrução encerrada, se houver.

## <a name="example"></a>Exemplo

Neste exemplo, a instrução condicional tem um contador que deveria contar de 1 a 100. No entanto, a instrução `break` encerra o loop após 4 contagens.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Exemplo

Neste exemplo, a instrução `break` é usada para interromper um loop aninhado interno e retornar o controle para o loop externo.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Exemplo

Este exemplo demonstra o uso de `break` em uma instrução [switch](../../../csharp/language-reference/keywords/switch.md).

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Se você digitou `4`, a saída seria:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

[Referência de C#](../../../csharp/language-reference/index.md)  
[Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
[Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
[switch](../../../csharp/language-reference/keywords/switch.md)  
[Instruções de atalho](../../../csharp/language-reference/keywords/jump-statements.md)  
[Instruções de iteração](../../../csharp/language-reference/keywords/iteration-statements.md)
