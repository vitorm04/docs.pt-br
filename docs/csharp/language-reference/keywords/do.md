---
title: do (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 5599f079e29fd094c4d6a6a75afba89fb562a166
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="do-c-reference"></a>do (Referência de C#)
A instrução `do` executa uma instrução ou um bloco de instruções repetidamente até que uma expressão especificada seja avaliada como `false`. O corpo do loop deve ser colocado entre chaves, `{}`, a menos que ele consista em uma única instrução. Nesse caso, as chaves são opcionais.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, as instruções de loop `do-while` são executadas desde que a variável `x` seja menor que 5.  
  
 [!code-csharp[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 Diferente da instrução [while](../../../csharp/language-reference/keywords/while.md), um loop `do-while` é executado uma vez antes que a expressão condicional seja avaliada.  
  
 Em qualquer momento no bloco `do-while`, você pode interromper o loop usando a instrução [break](../../../csharp/language-reference/keywords/break.md). Você pode entrar diretamente na instrução de avaliação de expressão `while` usando a instrução [continue](../../../csharp/language-reference/keywords/continue.md). Se a expressão `while` for avaliada como verdadeira, a execução continuará na primeira instrução no loop. Se a expressão for avaliada como falsa, a execução continuará na primeira instrução após o loop `do-while`.  
  
 Um loop `do-while` também pode ser encerrado pelas instruções [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Instrução do-while (C++)](/cpp/cpp/do-while-statement-cpp)  
 [Instruções de iteração](../../../csharp/language-reference/keywords/iteration-statements.md)
