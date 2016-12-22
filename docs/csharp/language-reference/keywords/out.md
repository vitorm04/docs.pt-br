---
title: "out (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "out_CSharpKeyword"
  - "out"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "out [C#]"
  - "palavra-chave out [C#]"
ms.assetid: 7e911a0c-3f98-4536-87be-d539b7536ca8
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# out (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode usar a palavra\-chave contextual `out` em dois contextos \(cada um deles é um link para obtenção de informações detalhadas\), como um [modificador de parâmetro](../../../csharp/language-reference/keywords/out-parameter-modifier.md) ou em [declarações de parâmetro de tipo genérico](../../../csharp/language-reference/keywords/out-generic-modifier.md) em interfaces e delegados.  Este tópico discute o modificador de parâmetro, mas você pode ver [este outro tópico](../../../csharp/language-reference/keywords/out-generic-modifier.md) para obter informações sobre as declarações de parâmetro de tipo genérico.  
  
 A palavra\-chave `out` faz com que os argumentos sejam passados por referência.  Isso é como a palavra\-chave [ref](../../../csharp/language-reference/keywords/ref.md), exceto que `ref` requer que a variável seja inicializada antes de ser passada.  Para usar um parâmetro `out`, a definição do método e o método de chamada devem usar explicitamente a palavra\-chave `out`.  Por exemplo:  
  
 [!CODE [csrefKeywordsMethodParams#1](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#1)]  
  
 Embora as variáveis passadas como argumentos `out` não precisem ser inicializadas antes de serem passadas, o método chamado é necessário para atribuir um valor antes de o método retornar.  
  
 Embora as palavras\-chave `ref` e `out` causem comportamento de tempo de execução diferente, elas não são consideradas parte da assinatura do método no momento da compilação.  Portanto, os métodos não poderão ser sobrecarregados se a única diferença for que um método terá um argumento `ref` e o outro utilizará um argumento `out`.  Por exemplo, o código a seguir, não será compilado:  
  
 [!CODE [csrefKeywordsMethodParams#2](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#2)]  
  
 No entanto, poderá haver sobrecarga se um método tiver um argumento `ref` ou `out` e o outro não usar nenhum, como por exemplo:  
  
 [!CODE [csrefKeywordsMethodParams#3](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#3)]  
  
 Propriedades não são variáveis e portanto não podem ser passadas como parâmetros `out`.  
  
 Para obter informações sobre como passar matrizes, consulte [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Não é possível usar as palavras\-chave `ref` e `out` para os seguintes tipos de métodos:  
  
-   Métodos assíncronos, que você define usando o modificador [async](../../../visual-basic/language-reference/modifiers/async.md).  
  
-   Métodos de iterador, que incluem uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.  
  
## Exemplo  
 Declarar um método `out` é útil quando você deseja que um método retorne vários valores.  O exemplo a seguir usa `out` para retornar três variáveis com uma única chamada de método.  Observe que o terceiro argumento é atribuído a null.  Isso permite que os métodos retornem valores opcionalmente.  
  
 [!CODE [csrefKeywordsMethodParams#4](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#4)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)