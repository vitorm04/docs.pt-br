---
title: "Gen&#233;ricos e matrizes (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "matrizes [C#], Genéricos"
  - "genéricos [C#], matrizes"
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Gen&#233;ricos e matrizes (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Implementarem a matrizes unidimensionais que têm um limite inferior zero automaticamente no C\# 2.0 e posterior, <xref:System.Collections.Generic.IList%601>.  Isso permite que você crie métodos genéricos que podem usar o mesmo código para iterar por meio de arrays e outros tipos de coleção.  Essa técnica é útil principalmente para leitura de dados em coleções.  O <xref:System.Collections.Generic.IList%601> interface não pode ser usado para adicionar ou remover elementos de uma matriz.  Uma exceção será lançada se você tentar chamar um <xref:System.Collections.Generic.IList%601> método, como <xref:System.Collections.Generic.IList%601.RemoveAt%2A> em um array neste contexto.  
  
 O exemplo de código a seguir demonstra como um único método genérico que leva um <xref:System.Collections.Generic.IList%601> parâmetro de entrada pode iterar por meio de uma lista e uma matriz, neste caso uma matriz de inteiros.  
  
 [!code-cs[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## Consulte também  
 <xref:System.Collections.Generic>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Genéricos](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)   
 [Genéricos](../Topic/Generics%20in%20the%20.NET%20Framework.md)