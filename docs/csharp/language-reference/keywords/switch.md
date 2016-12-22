---
title: "switch (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "switch_CSharpKeyword"
  - "switch"
  - "case"
  - "case_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "instrução switch [C#]"
  - "palavra-chave switch [C#]"
  - "instrução case [C#]"
  - "palavra-chave default [C#]"
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
caps.latest.revision: 47
caps.handback.revision: 47
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# switch (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A declaração de `switch` é uma declaração de controle que seleciona *uma seção de opção* para executar a partir de uma lista de candidatos.  
  
 Uma instrução de `switch` inclui uma ou mais seções de opção.  Cada seção de troca contém um ou mais *rótulos de caso* seguidos por uma ou mais instruções.  O exemplo a seguir mostra uma instrução `switch` simples que tem três seções de alternância.  Cada seção de troca tem um rótulo de caso, como `case 1`, e duas instruções.  
  
 [!code-cs[csrefKeywordsSelection#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/switch_1.cs)]  
  
## Comentários  
 Cada rótulo de caso especifica um valor constante.  A expressão de opção transfere o controle para a seção de opção cujo rótulo de caso corresponde ao valor da *expressão de opção* \(`caseSwitch` no exemplo\).  Se nenhum rótulo de caso contiver um valor correspondente, o controle será transferido para a seção `default`, se houver.  Se não houver nenhuma seção `default`, nenhuma ação será tomada e o controle será transferido para fora da instrução `switch`.  No exemplo anterior, as instruções na primeira seção de opção são executadas porque `case 1` corresponde ao valor de `caseSwitch`.  
  
 Uma instrução de `switch` pode incluir qualquer número de seções de opção, e cada seção pode ter um ou mais rótulos de caso \(conforme mostrado no exemplo de rótulos de caso de cadeia de caracteres abaixo\).  No entanto, nenhum rótulo de dois casos pode conter o mesmo valor constante.  
  
 A execução da lista de instrução na seção de opção selecionada começa com a primeira instrução e continua pela lista de instrução, normalmente até que uma instrução ignorar seja alcançada, como `break`, `goto case`, `return` ou `throw`.  Nesse ponto, o controle é transferido fora da declaração de `switch` ou a outro rótulo de caso.  
  
 Ao contrário do C\+\+, C\# não permite que a execução continue de uma seção de opção para a próxima.  O código a seguir causa um erro.  
  
```c#  
switch (caseSwitch)  
{  
    // The following switch section causes an error.  
    case 1:  
        Console.WriteLine("Case 1...");  
        // Add a break or other jump statement here.  
    case 2:  
        Console.WriteLine("... and/or Case 2");  
        break;  
}  
```  
  
 C\# requer o fim das seções de opção, incluindo a final, para ser inacessível.  Isto é, diferentemente de alguns outros idiomas, seu código por não cair completamente na próxima seção de troca.  Embora esse requisito seja atendido geralmente usando uma instrução `break`, o seguinte caso também é válido, porque o fim da lista de instrução não pode ser alcançado.  
  
```c#  
case 4:  
    while (true)  
        Console.WriteLine("Endless looping. . . .");  
```  
  
## Exemplo  
 O exemplo a seguir ilustra os requisitos e recursos de uma instrução `switch`.  
  
 [!code-cs[csrefKeywordsSelection#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/switch_2.cs)]  
  
## Exemplo  
 No exemplo final, a variável de cadeia de caracteres, `str`, e os rótulos dos casos de cadeia de caracteres controlam o fluxo de execução.  
  
 [!code-cs[csrefKeywordsSelection#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/switch_3.cs)]  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Instrução switch \(C\+\+\)](/visual-cpp/cpp/switch-statement-cpp)   
 [if\-else](../../../csharp/language-reference/keywords/if-else.md)