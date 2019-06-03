---
title: try-catch-finally – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 787005ec09a2c5c4f0e5033c83fd6a7ab7875b7e
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422161"
---
# <a name="try-catch-finally-c-reference"></a>try-catch-finally (Referência de C#)

Um uso comum de `catch` e `finally` juntos é obter e usar recursos em um bloco `try`, lidar com circunstâncias excepcionais em um bloco `catch` e liberar os recursos no bloco `finally`.

 Para obter mais informações e exemplos sobre como lançar exceções, consulte [try-catch](try-catch.md) e [Lançando exceções](../../../standard/exceptions/index.md). Para obter mais informações sobre o bloco `finally`, consulte [try-finally](try-finally.md).

## <a name="example"></a>Exemplo

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Instruções try, throw e catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [Como: Gerar exceções explicitamente](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [Instrução using](using-statement.md)
