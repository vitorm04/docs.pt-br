---
title: "object (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "object_CSharpKeyword"
  - "object"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave object [C#]"
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# object (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `object` o tipo é um alias para <xref:System.Object> na.NET Framework.  No sistema unificado de tipos de C\#, todos os tipos, tipos de referência predefinidas e definidas pelo usuário e tipos de valor, herdar direta ou indiretamente, de <xref:System.Object>.  Você pode atribuir valores de qualquer tipo a variáveis do tipo `object`.  Quando uma variável de um tipo valor é convertido em objeto, ele é chamado  de *Boxed*.  Quando uma variável do tipo  object é convertida em um tipo de valor, ele é chamado servidor a ser *unboxed*.  Para obter mais informações, consulte  [Boxing e Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## Exemplo  
 O seguinte exemplo mostra como variáveis do tipo `object` pode aceitar valores de qualquer tipo de dados e como variáveis do tipo `object` pode usar os métodos em <xref:System.Object> da.NET Framework.  
  
 [!CODE [csrefKeywordsTypes#16](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#16)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md)   
 [Tipos de valor](../../../csharp/language-reference/keywords/value-types.md)