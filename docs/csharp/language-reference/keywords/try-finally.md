---
title: try-finally – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: a8d18a6ae8b3f8f6cde76b1b296ac6a317ca1ed1
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168575"
---
# <a name="try-finally-c-reference"></a>try-finally (Referência de C#)

Usando um bloco `finally`, você pode limpar todos os recursos alocados em um bloco [try](try-catch.md) e pode executar código mesmo se uma exceção ocorrer no bloco `try`. Normalmente, as instruções de um bloco `finally` são executadas quando o controle deixa uma instrução `try`. A transferência de controle pode ocorrer como resultado da execução normal, da execução de uma instrução `break`, `continue`, `goto` ou `return`, ou da propagação de uma exceção para fora da instrução `try`.

Dentro de uma exceção tratada, é garantido que o bloco `finally` será executado. No entanto, se a exceção não for tratada, a execução do bloco `finally` depende de como a operação de desenrolamento da exceção é disparada. Isso, por sua vez, depende da configuração do seu computador.

Normalmente, quando uma exceção sem tratamento encerra um aplicativo, não é importante se o bloco `finally` é executado. No entanto, se você tiver instruções em um bloco `finally` que devem ser executadas mesmo nesse caso, uma solução é adicionar um bloco `catch` à instrução `try`-`finally`. Como alternativa, você pode detectar a exceção que pode ser gerada no bloco `try` de uma instrução `try`-`finally` em posição superior na pilha de chamadas. Ou seja, você pode detectar a exceção no método que chama o método que contém a instrução `try`-`finally` ou no método que chama esse método ou em qualquer método na pilha de chamadas. Se a exceção não for detectada, a execução do bloco `finally` dependerá do sistema operacional escolher disparar uma operação de desenrolamento de exceção.

## <a name="example"></a>Exemplo

No exemplo a seguir, uma instrução de conversão inválida causa uma exceção `System.InvalidCastException`. A exceção não é tratada.

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

No exemplo a seguir, uma exceção do método `TryCast` ocorre em um método mais para cima na pilha de chamadas.

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

Para obter mais informações sobre `finally`, consulte [try-catch-finally](try-catch-finally.md).

C# também contém a [instrução using](using-statement.md), que fornece uma funcionalidade semelhante para objetos <xref:System.IDisposable> em uma sintaxe conveniente.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira a seção [A instrução try](~/_csharplang/spec/statements.md#the-try-statement) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Instruções try, throw e catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-catch](try-catch.md)
- [Como: Gerar exceções explicitamente](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
