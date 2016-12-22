---
title: "Delegados gen&#233;ricos (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "delegados [C#], genérico"
  - "genéricos [C#], delegados"
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Delegados gen&#233;ricos (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A  [delegar](../../../csharp/language-reference/keywords/delegate.md) pode definir seus próprios parâmetros de tipo.  Código que referências o delegado genérico pode especificar o argumento de tipo para criar um tipo construído fechado, assim como quando instanciar uma classe genérica ou chamar um método genérico, como mostrado no exemplo a seguir:  
  
 [!code-cs[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 C\# versão 2.0 tem um novo recurso chamado conversão de grupo de método, que se aplica a tipos delegate concreto, bem como genéricos e permite que você escreva na linha anterior com essa sintaxe simplificada:  
  
 [!code-cs[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 Delegados definidos dentro de uma classe genérica podem usar os parâmetros de tipo de classe genérica da mesma forma que os métodos de classe.  
  
 [!code-cs[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 Código que referencia o delegado deve especificar o argumento do tipo da classe que contém, da seguinte maneira:  
  
 [!code-cs[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 Representantes genéricos são especialmente úteis na definição de eventos com base no padrão de design típico, porque o argumento sender fortemente tipado e não tem mais ser convertido de e para <xref:System.Object>.  
  
 [!code-cs[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## Consulte também  
 <xref:System.Collections.Generic>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Métodos genéricos](../../../csharp/programming-guide/generics/generic-methods.md)   
 [Classes genéricas](../../../csharp/programming-guide/generics/generic-classes.md)   
 [Interfaces genéricas](../../../csharp/programming-guide/generics/generic-interfaces.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)   
 [Genéricos](../Topic/Generics%20in%20the%20.NET%20Framework.md)