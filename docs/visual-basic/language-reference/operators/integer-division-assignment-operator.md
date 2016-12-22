---
title: "Operador -= (Visual Basic) | Microsoft Docs"
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
  - "vb.-="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador -= [Visual Basic]"
  - "instruções de atribuição, composto"
  - "instruções de atribuição composta"
  - "Operador -="
  - "instruções [Visual Basic], atribuição composta"
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador -= (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Subtrai o valor de uma expressão do valor de uma variável ou propriedade e atribui o resultado à variável ou propriedade.  
  
## Sintaxe  
  
```  
  
variableorproperty -= expression  
```  
  
## Partes  
 `variableorproperty`  
 Necessário.  Qualquer variável numérico ou propriedade .  
  
 `expression`  
 Necessário.  Qualquer expressão numérica.  
  
## Comentários  
 O elemento à esquerda do operador `-=` pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.  A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `-=`pela primeira vez, o operador subtrai o valor da expressão \(no lado direito do operador\) do valor da variável ou propriedade \(no lado esquerdo do operador\).   O operador , em seguida, atribui o resultado dessa operação para a variável ou propriedade.  
  
## Sobrecarga  
 O operador [Operador \-](../../../visual-basic/language-reference/operators/subtraction-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Sobrecarregar o operador `-` afeta o comportamento do operador `-=`.  Se seu código usa `-=` em uma classe ou estrutura que sobrecarrega `-`, certifique\-se de que você entende seu comportamento redefinido.  Para mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O seguinte exemplo usa o operador `-=` para subtrair uma variável `Integer` de outra e atribuir o resultado à esta outra.  
  
 [!CODE [VbVbalrOperators#11](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#11)]  
  
## Consulte também  
 [Operador \-](../../../visual-basic/language-reference/operators/subtraction-operator.md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Operadores aritméticos](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)