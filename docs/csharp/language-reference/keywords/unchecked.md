---
title: "unchecked (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "unchecked_CSharpKeyword"
  - "unchecked"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave unchecked [C#]"
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# unchecked (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `unchecked` palavra\-chave é usada para suprimir a verificação de estouro para operações aritméticas de tipo integral e conversões.  
  
 Em um contexto desmarcado, se uma expressão produz um valor que está fora do intervalo do tipo de destino, o estouro não está sinalizado.  Por exemplo, porque o cálculo no exemplo a seguir é executado em um `unchecked` bloco ou expressão, o fato de que o resultado é muito grande para um número inteiro é ignorado, e `int1` recebe o valor\-2,147,483,639.  
  
 [!code-cs[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 Se a `unchecked` ambiente for removido, ocorre um erro de compilação.  O estouro pode ser detectado no momento da compilação, porque todos os termos da expressão são constantes.  
  
 Expressões que contenham os termos não constante estão desmarcadas por padrão em tempo de compilação e tempo de execução.  Consulte [checked](../../../csharp/language-reference/keywords/checked.md) para obter informações sobre como habilitar um ambiente marcado.  
  
 Como a verificação de estouro leva tempo, o uso do código não verificado em situações onde não há perigo de estouro pode melhorar o desempenho.  No entanto, se o estouro é uma possibilidade, um ambiente marcado deve ser usado.  
  
## Exemplo  
 Este exemplo mostra como usar o `unchecked` palavra\-chave.  
  
 [!code-cs[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Contexto verificado e não verificado](../../../csharp/language-reference/keywords/checked-and-unchecked.md)   
 [checked](../../../csharp/language-reference/keywords/checked.md)