---
title: "if-else (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "if_CSharpKeyword"
  - "else"
  - "else_CSharpKeyword"
  - "if"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave else [C#]"
  - "palavra-chave if [C#]"
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
caps.latest.revision: 32
caps.handback.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# if-else (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um `if` instrução identifica qual instrução ser executada com base no valor de uma `Boolean` expressão. No exemplo a seguir, o `Boolean` variável `result` é definida como `true` e, em seguida, check\-in a `if` instrução. A saída é `The condition is true`.  
  
 [!code-cs[csrefKeywordsSelection#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_1.cs)]  
  
 Você pode executar os exemplos neste tópico, colocando\-os no `Main` método de um aplicativo de console.  
  
 Um `if` instrução em c\# pode ocorrer de duas formas, como mostra o exemplo a seguir.  
  
```c#  
  
// if-else statement if (condition) { then-statement; } else { else-statement; } // Next statement in the program. // if statement without an else if (condition) { then-statement; } // Next statement in the program.  
```  
  
 Em um `if-else` instrução, se `condition` for avaliada como true, o `then-statement` é executado. Se `condition` for false, o `else-statement` é executado. Porque `condition` não pode ser simultaneamente true e false, o `then-statement` e o `else-statement` de um `if-else` instrução nunca ambos pode executar. Depois que o `then-statement` ou o `else-statement` é executado, o controle é transferido para a próxima instrução após o `if` instrução.  
  
 Em um `if` instrução que não inclui um `else` instrução, se `condition` for true, o `then-statement` é executado. Se `condition` for false, o controle é transferido para a próxima instrução após o `if` instrução.  
  
 Tanto o `then-statement` e o `else-statement` pode consistir em uma única instrução ou várias instruções entre chaves \(`{}`\). Para uma única instrução, as chaves são opcionais, mas recomendadas.  
  
 A instrução ou instruções o `then-statement` e o `else-statement` pode ser de qualquer tipo, incluindo outra `if` instrução aninhada em original `if` instrução. Aninhados no `if` instruções, cada `else` cláusula pertence à última `if` que não tem um correspondente `else`. No exemplo a seguir, `Result1` é exibida se `m > 10` e `n > 20` são avaliadas como true. Se `m > 10` for true, mas `n > 20` é false, `Result2` é exibida.  
  
 [!code-cs[csrefKeywordsSelection#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_2.cs)]  
  
 Se, em vez disso, você deseja `Result2` apareça quando `(m > 10)` for false, você pode especificar essa associação usando chaves para estabelecer o início e fim de aninhada `if` instrução, como mostra o exemplo a seguir.  
  
 [!code-cs[csrefKeywordsSelection#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_3.cs)]  
  
 `Result2` será exibido se a condição `(m > 10)` for avaliada como false.  
  
## Exemplo  
 No exemplo a seguir, você insere um caractere do teclado e o programa usa uma construção `if` instrução para determinar se o caractere de entrada é um caractere alfabético. Se o caractere de entrada é um caractere alfabético, o programa verifica se o caractere de entrada é maiúsculas ou minúsculas. Será exibida uma mensagem para cada caso.  
  
 [!code-cs[csrefKeywordsSelection#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_4.cs)]  
  
## Exemplo  
 Você também pode aninhar um `if` instrução dentro de um bloco else, como mostra o código parcial a seguir. O exemplo aninha `if` instruções em dois blocos else e um bloco depois. Os comentários especificam quais condições forem true ou false em cada bloco.  
  
 [!code-cs[csrefKeywordsSelection#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_5.cs)]  
  
## Exemplo  
 O exemplo a seguir determina se um caractere de entrada é um número, uma letra maiúscula ou uma letra minúscula. Se todas as três condições forem falsas, o caractere não é um caractere alfanumérico. O exemplo exibe uma mensagem para cada caso.  
  
 [!code-cs[csrefKeywordsSelection#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_6.cs)]  
  
 Assim como uma instrução no bloco else ou do bloco, em seguida, pode ser qualquer instrução válida, você pode usar qualquer expressão booliana válida para a condição. Você pode usar operadores lógicos como [& &](../../../csharp/language-reference/operators/conditional-and-operator.md), [&](../../../visual-basic/language-reference/operators/and-operator.md), [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) e [\!](../../../csharp/language-reference/operators/logical-negation-operator.md) façam condições compostas. O código a seguir mostra exemplos.  
  
```c#  
// NOT bool result = true; if (!result) { Console.WriteLine("The condition is true (result is false)."); } else { Console.WriteLine("The condition is false (result is true)."); } // Short-circuit AND int m = 9; int n = 7; int p = 5; if (m >= n && m >= p) { Console.WriteLine("Nothing is larger than m."); } // AND and NOT if (m >= n && !(p > m)) { Console.WriteLine("Nothing is larger than m."); } // Short-circuit OR if (m > n || m > p) { Console.WriteLine("m isn't the smallest."); } // NOT and OR m = 4; if (!(m >= n || m >= p)) { Console.WriteLine("Now m is the smallest."); } // Output: // The condition is false (result is true). // Nothing is larger than m. // Nothing is larger than m. // m isn't the smallest. // Now m is the smallest.  
```  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Operador ?:](../../../csharp/language-reference/operators/conditional-operator.md)   
 [Instrução if\-else \(C\+\+\)](/visual-cpp/cpp/if-else-statement-cpp)   
 [switch](../../../csharp/language-reference/keywords/switch.md)