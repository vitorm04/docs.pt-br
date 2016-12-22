---
title: "Como determinar se dois objetos s&#227;o id&#234;nticos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variáveis de objeto, determinando a identidade"
  - "objetos [Visual Basic], comparando"
  - "testando, Objetos "
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como determinar se dois objetos s&#227;o id&#234;nticos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Na [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], duas referências de variáveis são consideradas idênticas se os ponteiros forem iguais, ou seja, se ambas as variáveis apontar para a mesma instância de classe na memória.  Por exemplo, em um aplicativo Windows Forms, talvez você queira fazer uma comparação para determinar se a instância atual \(`Me`\) é o mesmo que uma instância específica, como `Form2`.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece dois operadores para comparar ponteiros.  O [Operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) retorna `True` se os objetos são idênticos, e o [Operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) retorna `True` se eles não são.  
  
## Determinando se Dois Objetos São Idênticos  
  
#### Para determinar se dois objetos são idênticos  
  
1.  Organize uma expressão `Boolean` para testar os dois objetos.  
  
2.  Na sua expressão de teste, use o operador `Is` com os dois objetos como operandos.  
  
     `Is` retorna `True` se os dois objetos apontam para a mesma instância de classe.  
  
## Determinando se Dois Objetos Não São Idênticos  
 Às vezes você deseja realizar uma ação se dois objetos não são idênticos, e pode ser complicado combinar `Not` e `Is`, por exemplo `If Not obj1 Is obj2`.  Em tal caso você pode usar o operador `IsNot`.  
  
#### Para determinar se dois objetos não são idênticos  
  
1.  Organize uma expressão `Boolean` para testar os dois objetos.  
  
2.  Na sua expressão de teste, use o operador `IsNot` com os dois objetos como operandos.  
  
     `IsNot` retorna `True` se os objetos não apontam para mesma instância de classe.  
  
## Exemplo  
 O exemplo a seguir testa pares de variáveis `Object` para ver se eles apontam para a mesma instância de classe.  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 O exemplo precedente exibe a seguinte saída.  
  
 `objA different from objB?  True`  
  
 `objA identical to objC?  True`  
  
## Consulte também  
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Valores de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Operador Is](../../../../visual-basic/language-reference/operators/is-operator.md)   
 [Operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Como determinar se dois objetos estão relacionados](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)