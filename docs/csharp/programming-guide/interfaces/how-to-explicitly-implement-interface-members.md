---
title: "Como implementar membros de interface explicitamente (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "interfaces [C#], implementando explicitamente"
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como implementar membros de interface explicitamente (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo declara uma  [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`e uma classe, `Box`, que explicitamente implementa os membros de interface `getLength` e `getWidth`.  Os membros são acessados por meio da instância da interface `dimensions`.  
  
## Exemplo  
 [!code-cs[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## Programação robusta  
  
-   Observe que as seguintes linhas, no `Main` método, são comentados como eles iria gerar erros de compilação.  Um membro da interface que é implementado explicitamente não pode ser acessado de um  [classe](../../../csharp/language-reference/keywords/class.md) instância:  
  
     [!code-cs[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   Observe também que as seguintes linhas, o `Main` método, com êxito impressão as dimensões da caixa porque os métodos estão sendo chamados a partir de uma instância da interface:  
  
     [!code-cs[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Como implementar membros de duas interfaces explicitamente](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)