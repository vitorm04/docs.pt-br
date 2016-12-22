---
title: "Operador /= (Visual Basic) | Microsoft Docs"
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
  - "vb./="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador /= [Visual Basic]"
  - "instruções de atribuição, composto"
  - "instruções de atribuição composta"
  - "Operador /="
  - "instruções [Visual Basic], atribuição composta"
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador /= (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Divide o valor de uma variável ou propriedade pelo valor de uma expressão e atribui o resultado em ponto flutuante para a variável ou propriedade.  
  
## Sintaxe  
  
```  
  
variableorproperty /= expression  
```  
  
## Partes  
 `variableorproperty`  
 Necessário.  Qualquer variável numérico ou propriedade .  
  
 `expression`  
 Necessário.  Qualquer expressão numérica.  
  
## Comentários  
 O elemento à esquerda do operador `/=` pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.  A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `/=`pela primeira vez, o operador divide o valor da variável ou propriedade \(no lado esquerdo do operador\) pelo valor da expressão \(no lado direito do operador\).   O operador , em seguida, atribui o resultado dessa operação de ponto flutuante para a variável ou propriedade.  
  
 Essa demonstrativo atribui uma `Double` valor à variável ou propriedade , à esquerda.  Se `Option Strict` é `On`, `variableorproperty` deve ser um `Double`.  Se `Option Strict` estiver `Off`, o Visual Basic executará uma conversão implícita e atribuirá o valor resultante para `variableorproperty`, com um possível erro em tempo de execução.  Para obter mais informações, consulte [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## Sobrecarga  
 [Operador \/](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Sobrecarregar o operador `/` afeta o comportamento do operador `/=`.  Se seu código usa `/=` em uma classe ou estrutura que sobrecarrega `/`, certifique\-se de que você entende seu comportamento redefinido.  Para mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo a seguir utiliza o operador `/=` para dividir uma variável `Integer` por um segundo e atribuir a quociente à primeira variável.  
  
 [!CODE [VbVbalrOperators#17](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#17)]  
  
## Consulte também  
 [Operador \/](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)   
 [Operador \\\=](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Operadores aritméticos](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)