---
title: "do (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
dev_langs:
- CSharp
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
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
ms.openlocfilehash: 58a9361c440bc1b17c5ab929ff7b45ba71ce50a4
ms.contentlocale: pt-br
ms.lasthandoff: 09/25/2017

---
# <a name="do-c-reference"></a>do (Referência de C#)
A instrução `do` executa uma instrução ou um bloco de instruções repetidamente até que uma expressão especificada seja avaliada como `false`. O corpo do loop deve ser colocado entre chaves, `{}`, a menos que ele consista em uma única instrução. Nesse caso, as chaves são opcionais.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, as instruções de loop `do-while` são executadas desde que a variável `x` seja menor que 5.  
  
 [!code-cs[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 Diferente da instrução [while](../../../csharp/language-reference/keywords/while.md), um loop `do-while` é executado uma vez antes que a expressão condicional seja avaliada.  
  
 Em qualquer momento no bloco `do-while`, você pode interromper o loop usando a instrução [break](../../../csharp/language-reference/keywords/break.md). Você pode entrar diretamente na instrução de avaliação de expressão `while` usando a instrução [continue](../../../csharp/language-reference/keywords/continue.md). Se a expressão `while` for avaliada como verdadeira, a execução continuará na primeira instrução no loop. Se a expressão for avaliada como falsa, a execução continuará na primeira instrução após o loop `do-while`.  
  
 Um loop `do-while` também pode ser encerrado pelas instruções [goto](../../../csharp/language-reference/keywords/goto.md), [retorn](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Instrução do-while (C++)](/cpp/cpp/do-while-statement-cpp)   
 [Instruções de iteração](../../../csharp/language-reference/keywords/iteration-statements.md)

