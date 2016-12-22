---
title: "Matrizes denteadas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "matrizes [C#], denteadas"
  - "matrizes denteadas [C#]"
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Matrizes denteadas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma matriz denteada é uma matriz cujos elementos são matrizes.  Os elementos de uma matriz denteada podem ser de tamanhos e dimensões diferentes.  Uma matriz denteada às vezes é chamada de uma "matriz de matrizes". Os exemplos a seguir mostram como declarar, inicializar e acesso irregulares arrays.  
  
 A seguir está uma declaração de uma matriz unidimensional que possui três elementos, cada um deles é uma matriz unidimensional de inteiros:  
  
 [!code-cs[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 Antes de usar `jaggedArray`, seus elementos devem ser inicializados.  Você pode inicializar os elementos como este:  
  
 [!code-cs[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 Cada um dos elementos é uma matriz unidimensional de inteiros.  O primeiro elemento é uma matriz de inteiros de 5, o segundo é uma matriz de inteiros de 4 e o terceiro é uma matriz de inteiros de 2.  
  
 Também é possível usar os inicializadores para preencher os elementos da matriz com valores, caso em que você não precisa que o tamanho da matriz.  Por exemplo:  
  
 [!code-cs[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 Você também pode inicializar a matriz na declaração como este:  
  
 [!code-cs[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 Você pode usar o seguinte formulário de forma abreviada.  Observe que você não pode omitir a `new` o operador da inicialização de elementos porque não há nenhuma inicialização padrão para os elementos:  
  
 [!code-cs[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 Uma matriz denteada é uma matriz de matrizes e, portanto, seus elementos são tipos de referência e são inicializados para `null`.  
  
 Você pode acessar os elementos individuais da matriz como nestes exemplos:  
  
 [!code-cs[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 É possível misturar arrays irregulares e multidimensionais.  A seguir está uma declaração e a inicialização de uma matriz unidimensional irregular que contém três elementos de matriz bidimensional de tamanhos diferentes.  Para obter mais informações sobre matrizes bidimensionais, consulte [Matrizes multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).  
  
 [!code-cs[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 Você pode acessar os elementos individuais como mostrado neste exemplo, que exibe o valor do elemento `[1,0]` da primeira matriz \(valor `5`\):  
  
 [!code-cs[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 O método `Length` retorna o número de arrays contido na matriz irregular.  Por exemplo, supondo que você tenha declarado a matriz anterior, esta linha:  
  
 [!code-cs[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 Retorna um valor 3.  
  
## Exemplo  
 Este exemplo cria uma matriz cujos elementos são os próprios arrays.  Cada um dos elementos de matriz tem um tamanho diferente.  
  
 [!code-cs[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## Consulte também  
 <xref:System.Array>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)   
 [Matrizes unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [Matrizes multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)