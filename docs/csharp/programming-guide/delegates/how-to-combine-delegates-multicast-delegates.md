---
title: "Como combinar delegados (delegados multicast) (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "delegados [C#], combinando"
  - "delegados multicast [C#]"
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como combinar delegados (delegados multicast) (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo demonstra como criar representantes de difusão seletiva.  Uma propriedade útil do  [delegar](../../../csharp/language-reference/keywords/delegate.md) objects é que vários objetos podem ser atribuídos a instância de um delegado usando o `+` operador.  O delegado multicast contém uma lista de delegados atribuídos.  Quando o delegado multicast é chamado, ele invoca os delegados na lista, em ordem.  Somente os representantes do mesmo tipo podem ser combinados.  
  
 O `-` pode ser usado para remover um delegado do componente de um delegado multicast.  
  
## Exemplo  
 [!code-cs[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## Consulte também  
 <xref:System.MulticastDelegate>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Eventos](../../../csharp/programming-guide/events/index.md)