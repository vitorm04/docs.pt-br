---
title: "Operador * (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "*_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador * [C#]"
  - "Operador de multiplicação (*) [C#]"
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador * (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador de multiplicação \(`*`\), que calcula o produto dos operandos.      **\*** \), Além disso, o operador dereference que permite leitura e gravação para um ponteiro.  
  
## Comentários  
 Todos os tipos numéricos têm predefinidos operadores de multiplicação.  
  
 O `*` operador também é usado para declarar os tipos de ponteiro e a referência ponteiros.  Este operador só pode ser usado em contextos inseguros, indicados pelo uso da  [não seguros](../../../csharp/language-reference/keywords/unsafe.md) palavra\-chave e exigindo o  [\/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) opção de compilador.  O operador dereference é também conhecido como o operador Indirection.  
  
 Tipos definidos pelo usuário podem sobrecarregar o binário `*` operador \(consulte  [operador](../../../csharp/language-reference/keywords/operator.md)\).  Se houver, quando um operador binário está sobrecarregado, o operador de atribuição correspondente, também será implicitamente sobrecarregado.  
  
## Exemplo  
 [!CODE [csRefOperators#50](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#50)]  
  
## Exemplo  
 [!CODE [csRefOperators#51](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#51)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)