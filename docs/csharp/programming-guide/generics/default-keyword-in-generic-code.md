---
title: "Palavra-chave default em c&#243;digo gen&#233;rico (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "palavra-chave default [C#], programação genérica"
  - "genéricos [C#], palavra-chave default"
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Palavra-chave default em c&#243;digo gen&#233;rico (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Métodos e classes genéricas, um problema que surge é como atribuir um valor padrão para um tipo parametrizado t quando você não souber o seguinte antecipadamente:  
  
-   Se t será um tipo de referência ou um tipo de valor.  
  
-   Se t é um tipo de valor, se ele será um valor numérico ou uma struct.  
  
 Dada uma variável t de tipo parametrizado T, a instrução t \= null é válido somente se t é um tipo de referência e t \= 0 só funcionará para tipos de valor numérico, mas não para structs.  A solução é usar o `default` palavra\-chave, que retornará null para tipos de referência e zero para tipos de valor numérico.  Para structs, ela retornará a cada membro da estrutura inicializada para zero ou nulo, dependendo se elas são tipos de valor ou referência.  Para tipos de valor anulável padrão retorna um <xref:System.Nullable%601?displayProperty=fullName>, que é inicializado como qualquer struct.  
  
 O exemplo a seguir do `GenericList<T>` classe mostra como usar o `default` palavra\-chave.  Para obter mais informações, consulte  [Visão geral de genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md).  
  
 [!code-cs[csProgGuideGenerics#41](../../../csharp/programming-guide/generics/codesnippet/CSharp/default-keyword-in-generic-code_1.cs)]  
  
## Consulte também  
 <xref:System.Collections.Generic>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Genéricos](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Métodos genéricos](../../../csharp/programming-guide/generics/generic-methods.md)   
 [Genéricos](../Topic/Generics%20in%20the%20.NET%20Framework.md)