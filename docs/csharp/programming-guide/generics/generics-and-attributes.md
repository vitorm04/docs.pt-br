---
title: "Gen&#233;ricos e atributos (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "atributos [C#], com genéricos"
  - "genéricos [C#], atributos"
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Gen&#233;ricos e atributos (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Atributos podem ser aplicados para tipos genéricos, da mesma forma como os tipos não genéricos.  Para obter mais informações sobre a aplicação de atributos, consulte [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Atributos personalizados são permitidos somente para fazer referência a tipos genéricos abertos, que são fornecidos para os qual nenhum tipo de argumentos de tipos genéricos e fechados construídos tipos genérico, que fornecem os argumentos para todos os parâmetros de tipo.  
  
 Os exemplos seguintes usam esse atributo personalizado:  
  
 [!code-cs[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 Um atributo pode fazer referência a um tipo genérico aberto:  
  
 [!code-cs[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 Especifica vários parâmetros de tipo usando o número apropriado de vírgulas.  Neste exemplo, `GenericClass2` tem dois parâmetros de tipo:  
  
 [!code-cs[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 Um atributo pode fazer referência a um tipo de genérico construído fechado:  
  
 [!code-cs[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 Um atributo que faz referência a um parâmetro de tipo genérico causará um erro de tempo de compilação:  
  
 [!code-cs[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 Um tipo genérico não pode herdar de <xref:System.Attribute>:  
  
 [!code-cs[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 Para obter informações sobre um tipo genérico ou o parâmetro de tipo em tempo de execução, você pode usar os métodos de <xref:System.Reflection>.  Para mais informações, consulte: [Genéricos e reflexão](../../../csharp/programming-guide/generics/generics-and-reflection.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Genéricos](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Atributos](../Topic/Extending%20Metadata%20Using%20Attributes.md)