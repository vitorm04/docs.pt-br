---
title: "while (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
dev_langs:
- CSharp
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ed531c83dba02b38576bf8354b1ff92f075048bc
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="while-c-reference"></a>while (Referência de C#)
A instrução `while` executa uma instrução ou um bloco de instruções até que uma expressão especificada seja avaliada como `false`.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a>Exemplo  
 Uma vez que o teste da expressão `while` ocorre antes de cada execução do loop, um loop `while` é executado zero ou mais vezes. Isso difere do loop [do](../../../csharp/language-reference/keywords/do.md), que é executado uma ou mais vezes.  
  
 Um loop `while` pode ser finalizado quando uma instrução [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md) transfere o controle para fora do loop. Para passar o controle para a próxima iteração sem sair do loop, use a instrução [continue](../../../csharp/language-reference/keywords/continue.md). Observe a diferença na saída nos três exemplos anteriores, dependendo de onde `int n` é incrementado. No exemplo abaixo, nenhuma saída é gerada.  
  
 [!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Instrução while (C++)](/cpp/cpp/while-statement-cpp)   
 [Instruções de iteração](../../../csharp/language-reference/keywords/iteration-statements.md)

