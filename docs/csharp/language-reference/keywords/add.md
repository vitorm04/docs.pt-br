---
title: "add (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "add_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "acessador de evento add [C#]"
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# add (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `add` palavra\-chave contextual é usado para definir um acessador de evento personalizado que é chamado quando o código do cliente se inscreve para seu  [evento](../../../csharp/language-reference/keywords/event.md).  Se você fornecer um personalizado `add` acessador, também deverá fornecer um  [Remover](../../../csharp/language-reference/keywords/remove.md) acessador.  
  
## Exemplo  
 O exemplo a seguir mostra um evento que tenha personalizado `add` e  [Remover](../../../csharp/language-reference/keywords/remove.md) acessadores.  Para o exemplo completo, consulte [Como implementar eventos de interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-cs[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/add_1.cs)]  
  
 Normalmente, não é necessário fornecer seus próprios acessadores de evento personalizado.  Os acessadores que são gerados automaticamente pelo compilador quando você declara um evento são suficientes para a maioria dos cenários.  
  
## Consulte também  
 [Eventos](../../../csharp/programming-guide/events/index.md)