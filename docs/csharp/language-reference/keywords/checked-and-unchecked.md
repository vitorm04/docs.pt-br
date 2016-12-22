---
title: "Contexto verificado e n&#227;o verificado (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "instrução checked [C#]"
  - "exceções [C#], verificação de estouro"
  - "operadores [C#], checked e unchecked"
  - "verificação de estouro [C#]"
  - "instruções [C#], checked e unchecked"
  - "instrução unchecked [C#]"
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Contexto verificado e n&#227;o verificado (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Instruções C\# podem ser executadas em contexto marcado ou desmarcado.  Em um contexto marcado, o estouro aritmético gera uma exceção.  Em um contexto desmarcado, o estouro aritmético é ignorado e o resultado é truncado.  
  
-   [marcado](../../../csharp/language-reference/keywords/checked.md) Especificar contexto marcado.  
  
-   [desmarcado](../../../csharp/language-reference/keywords/unchecked.md) Especificar contexto desmarcado.  
  
 Se nem `checked` nem `unchecked` forem especificados, o contexto padrão dependerá de fatores externos, tais como as opções do compilador.  
  
 As seguintes operações são afetadas pela verificação de estouro:  
  
-   Expressões que usam os seguintes operadores predefinidos em tipos integrais:  
  
     `++`  `--` \- \(unário\)   `+` \-   `*` `/`  
  
-   Conversões numéricas explícitas entre tipos integrais.  
  
 A opção de compilador [\/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) permite especificar contexto marcado ou desmarcado para todas as instruções aritméticas de inteiros que não estão explicitamente no escopo de uma palavra\-chave `checked` ou `unchecked`.  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Palavras\-chave de instrução](../../../csharp/language-reference/keywords/statement-keywords.md)