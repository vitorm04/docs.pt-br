---
title: try-finally (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 696eb531fe3e340f7fe0ae12483648119cf5a7eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288288"
---
# <a name="try-finally-c-reference"></a>try-finally (Referência de C#)
Usando um bloco `finally`, você pode limpar todos os recursos alocados em um bloco [try](../../../csharp/language-reference/keywords/try-catch.md) e pode executar código mesmo se uma exceção ocorrer no bloco `try`. Normalmente, as instruções de um bloco `finally` são executadas quando o controle deixa uma instrução `try`. A transferência de controle pode ocorrer como resultado da execução normal, da execução de uma instrução `break`, `continue`, `goto` ou `return`, ou da propagação de uma exceção para fora da instrução `try`.  
  
 Dentro de uma exceção tratada, é garantido que o bloco `finally` será executado. No entanto, se a exceção não for tratada, a execução do bloco `finally` depende de como a operação de desenrolamento da exceção é disparada. Isso, por sua vez, depende da configuração do seu computador.
  
 Normalmente, quando uma exceção sem tratamento encerra um aplicativo, não é importante se o bloco `finally` é executado. No entanto, se você tiver instruções em um bloco `finally` que devem ser executadas mesmo nesse caso, uma solução é adicionar um bloco `catch` à instrução `try`-`finally`. Como alternativa, você pode detectar a exceção que pode ser gerada no bloco `try` de uma instrução `try`-`finally` em posição superior na pilha de chamadas. Ou seja, você pode detectar a exceção no método que chama o método que contém a instrução `try`-`finally` ou no método que chama esse método ou em qualquer método na pilha de chamadas. Se a exceção não for detectada, a execução do bloco `finally` dependerá do sistema operacional escolher disparar uma operação de desenrolamento de exceção.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, uma instrução de conversão inválida causa uma exceção `System.InvalidCastException`. A exceção não é tratada.  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 No exemplo a seguir, uma exceção do método `TryCast` ocorre em um método mais para cima na pilha de chamadas.  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 Para obter mais informações sobre `finally`, consulte [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
 C# também contém a [instrução using](../../../csharp/language-reference/keywords/using-statement.md), que fornece uma funcionalidade semelhante para objetos <xref:System.IDisposable> em uma sintaxe conveniente.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Instruções try, throw e catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [Instruções para manipulação de exceções](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [throw](../../../csharp/language-reference/keywords/throw.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [Como gerar exceções explicitamente](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
