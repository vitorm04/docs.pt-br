---
title: Instrução return – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: a845ce257bf7f0cf0e64d6815b2278f6cec946e7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661611"
---
# <a name="return-c-reference"></a>return (Referência de C#)

A instrução `return` finaliza a execução do método em que aparece e retorna o controle para o método de chamada. Ela também pode retornar um valor opcional. Se o método for um tipo `void`, a instrução `return` poderá ser omitida.

 Se a instrução return estiver dentro de um bloco `try`, o bloco `finally`, se houver, será executado antes que o controle retorne para o método de chamada.

## <a name="example"></a>Exemplo

 No exemplo a seguir, o método `CalculateArea()` retorna a variável local `area` como um valor `double`.

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Instrução return](/cpp/cpp/return-statement-cpp)
