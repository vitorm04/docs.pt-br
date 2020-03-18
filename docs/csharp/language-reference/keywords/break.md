---
title: Instrução break – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713760"
---
# <a name="break-c-reference"></a>break (Referência de C#)

A instrução `break` termina o loop delimitador mais próximo ou a instrução [switch](./switch.md) na qual ele aparece. Controle é passado para a instrução que segue a instrução encerrada, se houver.

## <a name="example"></a>Exemplo

Neste exemplo, a instrução condicional tem um contador que deveria contar de 1 a 100. No entanto, a instrução `break` encerra o loop após 4 contagens.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Exemplo

Este exemplo demonstra o uso de `break` em uma instrução [switch](./switch.md).

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Se você digitou `4`, a saída seria:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a>Exemplo

Neste exemplo, a instrução `break` é usada para interromper um loop aninhado interno e retornar o controle para o loop externo. O controle _só_ é devolvido um nível acima nos loops aninhados.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Exemplo

Neste exemplo, `break` a declaração só é usada para sair do ramo atual durante cada iteração do loop. O loop em si não `break` é afetado pelas instâncias que pertencem à declaração de [switch](./switch.md) aninhada.

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [Palavras-chave do C#](./index.md)
- [Interruptor](./switch.md)
