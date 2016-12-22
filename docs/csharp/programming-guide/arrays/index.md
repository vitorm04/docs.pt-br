---
title: "Matrizes (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "matrizes [C#]"
  - "Linguagem C#, matrizes"
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
caps.latest.revision: 33
caps.handback.revision: 33
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Matrizes (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

É possível armazenar diversas variáveis do mesmo tipo em uma estrutura de dados de matriz.  Declare uma matriz especificando o tipo de seus elementos.  
  
 `type[] arrayName;`  
  
 Os exemplos a seguir criam matrizes de dimensão única, multidimensionais e denteadas:  
  
 [!code-cs[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## Visão geral de matriz  
 Uma matriz tem as seguintes propriedades:  
  
-   Uma matriz pode ser [Unidimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) ou [Denteada](../../../csharp/programming-guide/arrays/jagged-arrays.md).  
  
-   O número de dimensões e o comprimento de cada dimensão são estabelecidos quando a instância da matriz é criada.  Esses valores não podem ser alterados durante o tempo de vida da instância.  
  
-   Os valores padrão dos elementos numéricos da matriz são definidos como zero e fazem referência a elementos definidos como nulos.  
  
-   Uma matriz denteada é uma matriz de matrizes e, portanto, seus elementos são tipos de referência e são inicializados para `null`.  
  
-   Matrizes são indexadas por zero: uma matriz com elementos `n` é indexada de `0` a `n-1`.  
  
-   Os elementos da matriz podem ser de qualquer tipo, incluindo um tipo de matriz.  
  
-   Tipos de matriz são [tipos de referência](../../../csharp/language-reference/keywords/reference-types.md) derivados do tipo de base abstrata <xref:System.Array>.  Como esse tipo implementa <xref:System.Collections.IEnumerable> e <xref:System.Collections.Generic.IEnumerable%601>, você pode usar a iteração [foreach](../../../csharp/language-reference/keywords/foreach-in.md) em todas as matrizes no C\#.  
  
## Seções relacionadas  
  
-   [Matrizes como objetos](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [Usando foreach com matrizes](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [Passando matrizes como argumentos](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)  
  
-   [Mais sobre Variáveis](http://go.microsoft.com/fwlink/?LinkId=221230) em [Iniciando o Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Coleções](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [Array Collection Type](http://msdn.microsoft.com/pt-br/8a9964de-8941-47b1-a3cf-a01bc88db9e8)