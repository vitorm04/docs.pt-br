---
title: "Operador = (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Assign"
  - "vb.="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instruções de atribuição = [Visual Basic]"
  - "Operador = [Visual Basic]"
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador = (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Atribui um valor para uma variável ou propriedade.  
  
## Sintaxe  
  
```  
  
variableorproperty = value  
```  
  
## Partes  
 `variableorproperty`  
 Qualquer variável ou propriedade gravável .  
  
 `value`  
 Qualquer literal, constante, ou expressão.  
  
## Comentários  
 O elemento à esquerda do operador `=` pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.  A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  O operador `=` atribui o valor à sua direita à variável ou propriedade à sua esquerda.  
  
> [!NOTE]
>  O operador `=` é usado também com um operador de comparação.  Para obter detalhes, consulte:[Operadores de comparação](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## Sobrecarga  
 O operador `=` pode ser sobrecarregado somente como um operador relacional, não como um operador de atribuição.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O provedor exemplo demonstra o operador de atribuição.  O valor na direita é atribuído à variável na esquerda.  
  
 [!CODE [VbVbalrOperators#9](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#9)]  
  
## Consulte também  
 [Operador &\=](../../../visual-basic/language-reference/operators/and-assignment-operator.md)   
 [Operador \*\=](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)   
 [Operador \+\=](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)   
 [Operador \-\=](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)   
 [Operador \/\=](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [Operador \\\=](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)   
 [Operador ^\=](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Operadores de comparação](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)   
 [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)