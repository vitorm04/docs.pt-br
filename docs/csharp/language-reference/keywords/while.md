---
title: "while (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords: while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 420b409689d877c3e1ac744e8d7a65500cf8f964
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="while-c-reference"></a>while (Referência de C#)
A instrução `while` executa uma instrução ou um bloco de instruções até que uma expressão especificada seja avaliada como `false`.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a>Exemplo  
 Uma vez que o teste da expressão `while` ocorre antes de cada execução do loop, um loop `while` é executado zero ou mais vezes. Isso difere do loop [do](../../../csharp/language-reference/keywords/do.md), que é executado uma ou mais vezes.  
  
 Um loop `while` pode ser finalizado quando uma instrução [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md) transfere o controle para fora do loop. Para passar o controle para a próxima iteração sem sair do loop, use a instrução [continue](../../../csharp/language-reference/keywords/continue.md). Observe a diferença na saída nos três exemplos anteriores, dependendo de onde `int n` é incrementado. No exemplo abaixo, nenhuma saída é gerada.  
  
 [!code-csharp[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Instrução while (C++)](/cpp/cpp/while-statement-cpp)  
 [Instruções de iteração](../../../csharp/language-reference/keywords/iteration-statements.md)
