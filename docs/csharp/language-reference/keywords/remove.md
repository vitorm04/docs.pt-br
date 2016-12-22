---
title: "remove (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "remove_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "acessador de evento remove [C#]"
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# remove (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `remove` palavra\-chave contextual é usado para definir um acessador de evento personalizado que é chamado quando o código do cliente cancela a inscrição de seu  [evento](../../../csharp/language-reference/keywords/event.md).  Se você fornecer um personalizado `remove` acessador, também deverá fornecer um  [Adicionar](../../../csharp/language-reference/keywords/add.md) acessador.  
  
## Exemplo  
 O exemplo a seguir mostra um evento com personalizado  [Adicionar](../../../csharp/language-reference/keywords/add.md) e `remove` acessadores.  Para o exemplo completo, consulte [Como implementar eventos de interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-cs[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 Normalmente, não é necessário fornecer seus próprios acessadores de evento personalizado.  Os acessadores que são gerados automaticamente pelo compilador quando você declara um evento são suficientes para a maioria dos cenários.  
  
## Consulte também  
 [Eventos](../../../csharp/programming-guide/events/index.md)