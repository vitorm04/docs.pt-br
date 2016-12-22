---
title: "Operador &gt;&gt;= (Visual Basic) | Microsoft Docs"
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
  - "vb.>>="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador >>= [Visual Basic]"
  - "instruções de atribuição, composto"
  - "instruções de atribuição composta"
  - "Operador >>= [Visual Basic]"
  - "instruções [Visual Basic], atribuição composta"
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador &gt;&gt;= (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Executa um Shift aritmético à direita sobre o valor de uma variável ou propriedade e atribui o resultado de volta a variável ou propriedade.  
  
## Sintaxe  
  
```  
  
variableorproperty >>= amount  
```  
  
## Partes  
 `variableorproperty`  
 Necessário.  Variável ou propriedade de um tipo integral \(`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`\).  
  
 `amount`  
 Necessário.  Expressão numérica de um tipo de dados que amplia para `Integer`.  
  
## Comentários  
 O elemento à esquerda do operador `>>=` pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.  A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `>>=`primeiro, o operador executa uma certa aritmético deslocar no valor da variável ou propriedade.   O operador , em seguida, atribui o resultado dessa operação volta para a variável ou propriedade.  
  
 Shifts aritméticos são não circulares, que significa que os bits deslocados de uma extremidade do resultado não são reintroduzidos na outra extremidade.  Em um Shift aritmético à direita, os bits deslocados além da posição mais à direita de bits são descartados, e o bit mais à esquerda é propagado para as posições de bits vagas à esquerda.  Isso significa que se `variableorproperty` tiver um valor negativo, as posições vagas são definidas como um.  Se `variableorproperty` for positivo, ou se seu tipo de dados é um tipo sem sinal, as posições livres são definidas como zero.  
  
## Sobrecarga  
 O operador [Operador \>\>](../Topic/%3E%3E%20Operator%20\(Visual%20Basic\).md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Sobrecarregar o operador `>>` afeta o comportamento do operador `>>=`.  Se seu código usa `>>=` em uma classe ou estrutura que sobrecarrega `>>`, certifique\-se de que você entende seu comportamento redefinido.  Para mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O seguinte exemplo usa o operador `>>=` para deslocar à direita o padrão de bits de uma variável `Integer` pela quantidade especificada e atribui o resultado à variável.  
  
 [!CODE [VbVbalrOperators#15](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#15)]  
  
## Consulte também  
 [Operador \>\>](../Topic/%3E%3E%20Operator%20\(Visual%20Basic\).md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Operadores Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)