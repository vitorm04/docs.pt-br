---
title: "checked (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "checked_CSharpKeyword"
  - "checked"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave checked [C#]"
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# checked (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `checked` palavra\-chave é usada para permitir explicitamente a verificação de tipo integral operações aritméticas e conversões de estouro.  
  
 Por padrão, uma expressão que contém somente valores constantes causa um erro do compilador se a expressão produz um valor que está fora do intervalo do tipo de destino.  Se a expressão contém um ou mais valores não constante, o compilador não detecta o estouro.  Avaliar a expressão atribuída a `i2` no exemplo a seguir não causa um erro do compilador.  
  
 [!code-cs[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 Por padrão, essas expressões não constante não são verificados para estouro em tempo de execução, e elas não geram exceções de estouro.  O exemplo anterior exibe\-2,147,483,639 como a soma de dois inteiros positivos.  
  
 Verificação de estouro pode ser habilitado por opções do compilador, a configuração do ambiente ou o uso da `checked` palavra\-chave.  Os exemplos a seguir demonstram como usar um `checked` expressão ou um `checked` bloco para detectar o estouro produzido pela soma anterior no tempo de execução.  Ambos os exemplos elevar uma exceção de estouro.  
  
 [!code-cs[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 O  [não verificado](../../../csharp/language-reference/keywords/unchecked.md) palavra\-chave pode ser usada para evitar a verificação de estouro.  
  
## Exemplo  
 Este exemplo mostra como usar `checked` para habilitar a verificação em tempo de execução de estouro.  
  
 [!code-cs[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Contexto verificado e não verificado](../../../csharp/language-reference/keywords/checked-and-unchecked.md)   
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md)