---
title: "Operador \= | Microsoft Docs"
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
  - "\="
  - "vb.\="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador \= [Visual Basic]"
  - "instruções de atribuição, composto"
  - "instruções de atribuição composta"
  - "Operador \= [Visual Basic]"
  - "instruções [Visual Basic], atribuição composta"
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador \=
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Divide o valor de uma variável ou propriedade pelo valor de uma expressão e atribui o resultado inteiro para a variável ou propriedade.  
  
## Sintaxe  
  
```  
  
variableorproperty \= expression  
```  
  
## Partes  
 `variableorproperty`  
 Necessário.  Qualquer variável numérico ou propriedade .  
  
 `expression`  
 Necessário.  Qualquer expressão numérica.  
  
## Comentários  
 O elemento à esquerda do operador `\=` pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.  A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `\=` operador divide o valor de uma variável ou propriedade na sua esquerda pelo valor à direita e atribui o resultado de inteiro à variável ou propriedade à sua esquerda.  
  
 Para obter mais informações sobre divisão, consulte [Operador \\](../../../visual-basic/language-reference/operators/integer-division-operator.md).  
  
## Sobrecarga  
 O operador `\` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Sobrecarregar o operador `\` afeta o comportamento do operador `\=`.  Se seu código usa `\=` em uma classe ou estrutura que sobrecarrega `\`, certifique\-se de que você entende seu comportamento redefinido.  Para mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo a seguir utiliza o operador `\=` para dividir uma `Integer` variável por um segundo e atribuir a variável primeira o resultado inteiro.  
  
 [!CODE [VbVbalrOperators#19](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#19)]  
  
## Consulte também  
 [Operador \\](../../../visual-basic/language-reference/operators/integer-division-operator.md)   
 [Operador \/\=](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Operadores aritméticos](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)