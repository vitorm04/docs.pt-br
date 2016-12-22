---
title: "partial (tipo) (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "partialtype"
  - "partialtype_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "tipos parciais [C#]"
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# partial (tipo) (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Definições de tipo parcial permitem a definição de uma classe, struct ou interface para ser dividido em vários arquivos.  
  
 No File1.cs:  
  
 [!code-cs[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 No File2.cs da declaração:  
  
 [!code-cs[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## Comentários  
 A divisão de uma classe, struct ou interface tipo ao longo de vários arquivos pode ser útil quando você estiver trabalhando com projetos grandes, ou com o código gerado automaticamente, como a fornecida pelo [Windows Forms Designer](http://msdn.microsoft.com/pt-br/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  Um tipo parcial pode conter um  [método parcial](../../../csharp/language-reference/keywords/partial-method.md).  Para obter mais informações, consulte [Classes e métodos partial](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)