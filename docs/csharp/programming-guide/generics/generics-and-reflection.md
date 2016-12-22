---
title: "Gen&#233;ricos e reflex&#227;o (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "genéricos [C#], reflexão"
  - "reflexão [C#], tipos genéricos"
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Gen&#233;ricos e reflex&#227;o (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Porque o tempo de execução de linguagem comum \(CLR\) tem acesso às informações de tipo genérico em tempo de execução, você pode usar a reflexão para obter informações sobre tipos genéricos da mesma forma como para tipos não genéricos.  Para obter mais informações, consulte [Genéricos em tempo de execução](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 No [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] vários novos membros foram adicionados para o <xref:System.Type> classe para habilitar as informações de tempo de execução para tipos genéricos.  Consulte a documentação dessas classes para obter mais informações sobre como usar os métodos e propriedades. O <xref:System.Reflection.Emit> namespace também contém novos membros que suportam a genéricos.  Consulte [Como definir um tipo genérico com a emissão de reflexão](../Topic/How%20to:%20Define%20a%20Generic%20Type%20with%20Reflection%20Emit.md).  
  
 Para obter uma lista das condições invariável para termos usados na reflexo genérico, consulte o <xref:System.Type.IsGenericType%2A> propriedade comentários.  
  
|Nome do membro Type|Descrição|  
|-------------------------|---------------|  
|<xref:System.Type.IsGenericType%2A>|Retorna true se um tipo é genérico.|  
|<xref:System.Type.GetGenericArguments%2A>|Retorna uma matriz de `Type` objetos que representam os argumentos de tipo fornecido para um tipo construído ou tipo de parâmetros de uma definição de tipo genérico.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Retorna a definição de tipo genérico subjacente para o tipo construído atual.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Retorna uma matriz de `Type` parâmetro de tipo de objetos que representam as restrições a atual genérica.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Retorna true se o tipo ou qualquer uma das suas delimitador tipos ou métodos contêm parâmetros de tipo para o qual tipos específicos não foram fornecidos.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Obtém uma combinação de `GenericParameterAttributes` parâmetro de tipo de sinalizadores que descrevem as restrições especiais de genérico atual.|  
|<xref:System.Type.GenericParameterPosition%2A>|Para um `Type` o objeto que representa um parâmetro de tipo, obtém a posição do parâmetro de tipo na lista de parâmetros de tipo da definição de tipo genérico ou método genérico que declarado o parâmetro de tipo.|  
|<xref:System.Type.IsGenericParameter%2A>|Obtém um valor que indica se o atual `Type` representa um parâmetro de tipo de uma definição de tipo ou método genérico.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Obtém um valor que indica se o atual <xref:System.Type> representa uma definição de tipo genérico, do qual podem ser construídos outros tipos genéricos.  Retorna true se o tipo representa a definição de um tipo genérico.|  
|<xref:System.Type.DeclaringMethod%2A>|Retorna o método genérico que definiu a atual genérica parâmetro de tipo ou nulo se o parâmetro de tipo não foi definido por um método genérico.|  
|<xref:System.Type.MakeGenericType%2A>|Substitui os elementos de uma matriz de tipos para os parâmetros de tipo de definição de tipo genérico atual e retorna um <xref:System.Type> que representa o resultante construído o tipo de objeto.|  
  
 Além disso, os novos membros foram adicionados para o <xref:System.Reflection.MethodInfo> classe para habilitar as informações de tempo de execução para métodos genéricos.  Consulte o <xref:System.Reflection.MethodInfo.IsGenericMethod%2A> comentários de propriedade para obter uma lista das condições invariável para termos usados para refletir sobre os métodos genéricos.  
  
|Nome do membro System.Reflection.MemberInfo|Descrição|  
|-------------------------------------------------|---------------|  
|<xref:System.Reflection.MethodInfo.IsGenericMethod%2A>|Retorna true se um método é genérico.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Retorna uma matriz de objetos do tipo que representam os argumentos de tipo de um método genérico construído ou os parâmetros de tipo de uma definição de método genérico.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Retorna a definição de método genérico subjacente para o método construído atual.|  
|<xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A>|Retorna true se o método ou qualquer de seus tipos de delimitadoras contêm qualquer parâmetro de tipo para o qual tipos específicos não foram fornecidos.|  
|<xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A>|Retorna VERDADEIRO se o atual <xref:System.Reflection.MethodInfo> representa a definição de um método genérico.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Substitui os elementos de uma matriz de tipos para os parâmetros de tipo de definição de método genérico atual e retorna um <xref:System.Reflection.MethodInfo> que representa o resultante construído um método de objeto.|  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Genéricos](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Reflexão e tipos genéricos](../Topic/Reflection%20and%20Generic%20Types.md)   
 [Genéricos](../Topic/Generics%20in%20the%20.NET%20Framework.md)