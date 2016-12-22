---
title: "Diferen&#231;as entre modelos C++ e gen&#233;ricos C# (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "genéricos [C#], vs. modelos C++"
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Diferen&#231;as entre modelos C++ e gen&#233;ricos C# (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os modelos de C\# genéricos e C\+\+ são ambos os recursos de linguagem que oferecem suporte para tipos parametrizados.  No entanto, há muitas diferenças entre os dois.  No nível da sintaxe, C\# os genéricos são uma abordagem mais simples para tipos parametrizados sem a complexidade de modelos C\+\+.  Além disso, C\# não tenta fornecer toda a funcionalidade que fornecem a modelos C\+\+.  No nível de implementação, a principal diferença é que as substituições de tipo genérico C\# são realizadas em tempo de execução e informações de tipo genérico, assim, são preservadas para objetos instanciados.  Para obter mais informações, consulte [Genéricos em tempo de execução](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 Estas são as principais diferenças entre modelos de C\+\+ e C\# genéricos:  
  
-   C\# os genéricos não fornecem a mesma quantidade de flexibilidade como modelos C\+\+.  Por exemplo, não é possível chamar os operadores aritméticos em uma C\# classe genérica, embora seja possível chamar os operadores definidos pelo usuário.  
  
-   C\# não aceita parâmetros de tipo não modelo, como `template C<int i> {}`.  
  
-   C\# não oferece suporte a especialização explícita; ou seja, uma implementação personalizada de um modelo para um tipo específico.  
  
-   C\# não oferece suporte a especialização parcial: uma implementação personalizada para um subconjunto dos argumentos de tipo.  
  
-   C\# não aceita o parâmetro de tipo a ser usado como a classe base para o tipo genérico.  
  
-   C\# não aceita parâmetros de tipo ter tipos padrão.  
  
-   No C\#, um parâmetro de tipo genérico não pode ser um genérico, embora construídos tipos podem ser usados como genéricos.  C\+\+ permitem que os parâmetros de modelo.  
  
-   C\+\+ permite que o código que pode não ser válido para todos os parâmetros de tipo no modelo, em seguida, é verificado para o tipo específico usado como o parâmetro de tipo.  C\# requer o código em uma classe para ser escrito de forma que ele funcionará com qualquer tipo que satisfaça as restrições.  Por exemplo, em C\+\+ é possível escrever uma função que usa os operadores aritméticos `+` e `-` em objetos do parâmetro de tipo, que produzirá um erro no momento da instanciação do modelo com um tipo que não oferece suporte a esses operadores.  Não C\# permite isso. as construções de linguagem única permitidas são aqueles que pode ser deduzido a partir de restrições.  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Modelos](/visual-cpp/cpp/templates-cpp)