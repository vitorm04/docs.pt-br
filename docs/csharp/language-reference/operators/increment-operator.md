---
title: "Operador ++ (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "++_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador ++ [C#]"
  - "Operador de incremento (++) [C#]"
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador ++ (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador de incremento \(`++`\) o operando é incrementado em 1. O operador de incremento pode aparecer antes ou depois de seu operando: `++variable` e `variable++`.  
  
## Comentários  
 A primeira forma é uma operação de incremento de prefixo. O resultado da operação é o valor do operando após foi incrementado.  
  
 A segunda forma é uma operação de incremento de sufixo. O resultado da operação é o valor do operando antes que ele foi incrementado.  
  
 Tipos numéricos e de enumeração predefinida operadores de incremento. Tipos definidos pelo usuário podem sobrecarregar o `++` operador. Operações em tipos integrais geralmente são permitidas na enumeração.  
  
## Exemplo  
 [!CODE [csRefOperators#3](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#3)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)