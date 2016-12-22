---
title: "Operador ^= (Visual Basic) | Microsoft Docs"
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
  - "vb.^="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador ^= [Visual Basic]"
  - "instruções de atribuição, composto"
  - "instruções de atribuição composta"
  - "instruções [Visual Basic], atribuição composta"
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador ^= (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Eleva o valor de uma variável ou propriedade à potência de uma expressão e atribui o resultado de volta à variável ou propriedade.  
  
## Sintaxe  
  
```  
  
variableorproperty ^= expression  
```  
  
## Partes  
 `variableorproperty`  
 Necessário.  Qualquer variável numérico ou propriedade .  
  
 `expression`  
 Necessário.  Qualquer expressão numérica.  
  
## Comentários  
 O elemento à esquerda do operador `^=` pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.  A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `^=`pela primeira vez, o operador gerará o valor da variável ou propriedade \(no lado esquerdo do operador\) à potência de que o valor da expressão \(no lado direito do operador\).   O operador , em seguida, atribui o resultado dessa operação volta para a variável ou propriedade.  
  
 Visual Basic sempre executa exponenciação no [Tipo de dados double](../../../visual-basic/language-reference/data-types/double-data-type.md).  Os operandos de qualquer outro tipo são convertidos em `Double`, e o resultado é sempre `Double`.  
  
 O valor de `expression` pode ser fracionário, negativo, ou ambos.  
  
## Sobrecarga  
 [Operador ^](../../../visual-basic/language-reference/operators/exponentiation-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Sobrecarregar o operador `^` afeta o comportamento do operador `^=`.  Se seu código usa `^=` em uma classe ou estrutura que sobrecarrega `^`, certifique\-se de que você entende seu comportamento redefinido.  Para mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo a seguir utiliza o operador `^=` para aumentar o valor de uma   variável `Integer` à potência de uma segunda variável e atribuir o resultado para a primeira variável.  
  
 [!CODE [VbVbalrOperators#21](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#21)]  
  
## Consulte também  
 [Operador ^](../../../visual-basic/language-reference/operators/exponentiation-operator.md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Operadores aritméticos](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)