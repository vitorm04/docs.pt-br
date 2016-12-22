---
title: "Modificador de par&#226;metro out (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "parâmetros out [C#]"
  - "parâmetros [C#], out"
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Modificador de par&#226;metro out (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A palavra\-chave `out` causa dos argumentos para ser passados por referência.  Isso é como a palavra\-chave de [referência](../../../csharp/language-reference/keywords/ref.md) , exceto que `ref` requer que a variável é inicializado antes de ser passado.  Para usar um parâmetro de `out` , a definição do método e o método de chamada devem explicitamente usar a palavra\-chave de `out` .  Por exemplo:  
  
 [!CODE [csrefKeywordsMethodParams#1](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#1)]  
  
 Embora as variáveis passados como argumentos de `out` não precisem ser inicializados antes de ser passado, o método chamado é necessário atribuir um valor antes que o método retorna.  
  
 Embora as palavras\-chave de `ref` e de `out` farão com que o comportamento diferente de tempo de execução, não são considerados parte da assinatura do método em tempo de compilação.  Portanto, os métodos não podem ser sobrecarregados se a única diferença é que um método aceita um argumento de `ref` e o outro utiliza um argumento de `out` .  O código a seguir, por exemplo, não será compilado:  
  
 [!CODE [csrefKeywordsMethodParams#2](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#2)]  
  
 Sobrecarregar pode ser feito, o entanto, se um método utiliza `ref` ou argumento de `out` e o outro não usa nenhum, assim:  
  
 [!CODE [csrefKeywordsMethodParams#3](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#3)]  
  
 As propriedades não são variáveis e portanto não podem ser passados como parâmetros de `out` .  
  
 Para obter informações sobre passar matrizes, consulte [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Você não pode usar as palavras\-chave de `ref` e de `out` para os seguintes tipos de métodos:  
  
-   Métodos de Async, que você define usando o modificador de [async](../../../visual-basic/language-reference/modifiers/async.md) .  
  
-   Métodos de iterador, que inclui uma instrução de [retorno de produzir](../../../csharp/language-reference/keywords/yield.md) ou de `yield break` .  
  
## Exemplo  
 Declare um método de `out` é útil quando você deseja um método para retornar vários valores.  O exemplo a seguir usa `out` para retornar três variáveis com uma única chamada de método.  Observe que o segundo argumento é atribuído ao zero.  Isso permite métodos para retornar valores opcionalmente.  
  
 [!CODE [csrefKeywordsMethodParams#4](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#4)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Parâmetros de método](../../../csharp/language-reference/keywords/method-parameters.md)