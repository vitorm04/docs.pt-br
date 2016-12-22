---
title: "Tipos aninhados (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "tipos aninhados [C#]"
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Tipos aninhados (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um tipo definido dentro de uma [classe](../../../csharp/language-reference/keywords/class.md) ou [estrutura](../../../csharp/language-reference/keywords/struct.md) é chamado de tipo aninhado.  Por exemplo:  
  
 [!code-cs[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
 Independentemente do tipo externo ser uma classe ou estrutura, o padrão dos tipos aninhados é [particular](../../../csharp/language-reference/keywords/private.md), mas pode ser tornado [público](../../../csharp/language-reference/keywords/public.md), protegido interno, [protegido](../../../csharp/language-reference/keywords/protected.md), [interno](../../../csharp/language-reference/keywords/internal.md), ou [particular](../../../csharp/language-reference/keywords/private.md).  No exemplo anterior, `Nested` é inacessível para tipos externos, mas pode ser tornado público como este:  
  
 [!code-cs[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 O tipo aninhado ou interno pode acessar o tipo externo ou recipiente.  Para acessar o tipo recipiente, passe\-o como um construtor para o tipo aninhado.  Por exemplo:  
  
 [!code-cs[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 Um tipo aninhado tem acesso a todos os membros que são acessíveis ao seu tipo recipiente.  Pode acessar membros particulares e protegidos do tipo recipiente, incluindo todos os membros protegidos herdados.  
  
 Na declaração anterior, o nome completo da classe `Nested` é `Container.Nested`.  Este é o nome usado para criar uma nova instância da classe aninhada, como a seguir:  
  
 [!code-cs[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)