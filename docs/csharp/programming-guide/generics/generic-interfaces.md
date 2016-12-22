---
title: "Interfaces gen&#233;ricas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "Linguagem C#, interfaces genéricas"
  - "genéricos [C#], interfaces"
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Interfaces gen&#233;ricas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Ele geralmente é útil definir interfaces para classes de coleção genérica, ou para as classes genéricas que representam os itens na coleção.  A preferência para classes genéricas é usar interfaces genéricas, como <xref:System.IComparable%601> em vez de <xref:System.IComparable>, para evitar boxing e unboxing operações nos tipos de valor.  A.NET Framework class library define várias interfaces genéricas para uso com as classes de coleção do <xref:System.Collections.Generic> espaço para nome.  
  
 Quando uma interface é especificada como uma restrição em um parâmetro de tipo, somente os tipos que implementam a interface podem ser usados.  O seguinte código exemplo mostra um `SortedList<T>` classe que deriva de `GenericList<T>` classe.  Para obter mais informações, consulte [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md).  `SortedList<T>`Adiciona a restrição `where T : IComparable<T>`.  Isso permite que o `BubbleSort` método na `SortedList<T>` para usar a genérica <xref:System.IComparable%601.CompareTo%2A> método em elementos de lista.  Neste exemplo, elementos de lista são uma classe simples, `Person`, que implementa `IComparable<Person>`.  
  
 [!code-cs[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 Várias interfaces podem ser especificados como restrições de um único tipo, da seguinte maneira:  
  
 [!code-cs[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 Uma interface pode definir mais de um parâmetro de tipo, da seguinte maneira:  
  
 [!code-cs[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 As regras de herança que se aplicam às classes também se aplicam a interfaces:  
  
 [!code-cs[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 Interfaces genéricas podem herdar de interfaces não genéricas, se a interface genérica é compensado\-variant, o que significa que só usa seu parâmetro de tipo como um valor de retorno.  No.Biblioteca de classes, <xref:System.Collections.Generic.IEnumerable%601> herda de <xref:System.Collections.IEnumerable> porque <xref:System.Collections.Generic.IEnumerable%601> usa apenas `T` no valor de retorno de <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> e na <xref:System.Collections.Generic.IEnumerator%601.Current%2A> getter de propriedade.  
  
 Classes concretas podem implementar interfaces construídos fechadas, da seguinte maneira:  
  
 [!code-cs[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 Classes genéricas podem implementar interfaces genéricas ou interfaces construídos fechadas, contanto que a lista de parâmetros de classe fornece todos os argumentos necessários para a interface, da seguinte maneira:  
  
 [!code-cs[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 As regras que controlam a sobrecarga de método são os mesmos métodos em classes genéricas, genérico structs ou interfaces genéricas.  Para obter mais informações, consulte [Métodos genéricos](../../../csharp/programming-guide/generics/generic-methods.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [interface](../../../csharp/language-reference/keywords/interface.md)   
 [Genéricos](../Topic/Generics%20in%20the%20.NET%20Framework.md)