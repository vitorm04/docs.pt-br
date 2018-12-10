---
title: try-catch-finally (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 18625838bd36d9d32079b7c72ded7ed660b8cf3a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130657"
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
- [Instruções para manipulação de exceções](exception-handling-statements.md)
- [throw](throw.md)
- [Como gerar exceções explicitamente](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [Instrução using](using-statement.md)