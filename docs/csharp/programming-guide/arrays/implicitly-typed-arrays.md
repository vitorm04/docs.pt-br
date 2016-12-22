---
title: "Matrizes de tipo impl&#237;cito (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "matrizes [C#], tipada implicitamente"
  - "Linguagem C#, matrizes tipadas implicitamente"
  - "matrizes tipadas implicitamente [C#]"
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Matrizes de tipo impl&#237;cito (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode criar uma matriz do tipo implícito no qual o tipo de ocorrência de array é inferido de elementos especificados no inicializador de matriz.  As regras para qualquer variável de tipo implícito também se aplicam a matrizes do tipo implícito.  Para obter mais informações, consulte [Variáveis locais de tipo implícito](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Matrizes do tipo implícito geralmente são usados em expressões de consulta, juntamente com os tipos anônimos e inicializadores de objeto e coleção.  
  
 Os exemplos a seguir mostram como criar uma matriz de tipo implícito:  
  
 [!code-cs[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 No exemplo anterior, observe que, com matrizes de tipo implícito, sem colchetes são usadas no lado esquerdo da instrução de inicialização.  Observe também que as matrizes denteadas são inicializados usando `new []` como matrizes de dimensão única.  
  
## Matrizes de tipo implícito no inicializadores de objeto  
 Quando você cria um tipo anônimo que contém uma matriz, a matriz deve ser digitada implicitamente no inicializador de objeto do tipo.  No exemplo a seguir, `contacts` é uma matriz tipo implícito de tipos anônimos, cada qual contendo uma matriz chamada `PhoneNumbers`.  Observe que o `var` palavra\-chave não é usado nos inicializadores de objeto.  
  
 [!code-cs[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Variáveis locais de tipo implícito](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)   
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)   
 [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [var](../../../csharp/language-reference/keywords/var.md)   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)