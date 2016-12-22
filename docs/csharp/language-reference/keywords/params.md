---
title: "params (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "params_CSharpKeyword"
  - "params"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "parâmetros [c#], params"
  - "palavra-chave params [C#]"
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# params (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Usando a palavra\-chave `params` , você pode especificar um [parâmetro do método](../../../csharp/language-reference/keywords/method-parameters.md) que usa um número variável de argumentos.  
  
 É possível enviar uma lista separada por vírgulas de argumentos de tipo especificado na declaração de parâmetro ou em uma matriz de argumentos de tipo especificado.  Você também pode não enviar nenhum argumento.  Se você não enviar argumentos, o comprimento da lista `params` será zero.  
  
 Nenhum parâmetro adicional é permitido após a palavra\-chave `params` em uma declaração de método, e somente uma palavra\-chave `params` é permitida em uma declaração de método.  
  
## Exemplo  
 O exemplo a seguir demonstra várias maneiras em que os argumentos podem ser enviados para um parâmetro `params` .  
  
 [!CODE [csrefKeywordsMethodParams#5](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#5)]  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Parâmetros de método](../../../csharp/language-reference/keywords/method-parameters.md)