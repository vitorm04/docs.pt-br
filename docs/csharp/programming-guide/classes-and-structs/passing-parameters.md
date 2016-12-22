---
title: "Passando par&#226;metros (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "argumentos [C#]"
  - "Linguagem C#, parâmetros de método"
  - "métodos [C#], passando parâmetros"
  - "parâmetros [C#], passando"
  - "passando parâmetros [C#]"
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Passando par&#226;metros (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em C\#, podem ser passados argumentos aos parâmetros por valor ou por referência.  Passagem por referência permite que membros da função, métodos, propriedades, indexadores, operadores e construtores para alterar o valor dos parâmetros e fazer essa alteração persistirem no ambiente de chamada.  Para passar um parâmetro por referência, use o `ref` ou `out` palavra\-chave.  Para simplificar, apenas o `ref` palavra\-chave é usada nos exemplos neste tópico.  Para obter mais informações sobre a diferença entre `ref` e `out`, consulte [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md), e [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 O exemplo a seguir ilustra a diferença entre os parâmetros de referência e valor.  
  
 [!code-cs[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 Para obter mais informações, consulte os seguintes tópicos:  
  
-   [Passando parâmetros de tipo de valor](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [Passando parâmetros de tipo de referência](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Métodos](../../../fsharp/language-reference/members/methods.md)