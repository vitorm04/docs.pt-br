---
title: "Operador &amp;= (Visual Basic) | Microsoft Docs"
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
  - "vb.&="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador &= [Visual Basic]"
  - "instruções de atribuição, composto"
  - "instruções de atribuição composta"
  - "Operador &="
  - "instruções [Visual Basic], atribuição composta"
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador &amp;= (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Concatena uma expressão `String` a uma variável ou propriedade `String` e atribui o resultado à variável ou propriedade.  
  
## Sintaxe  
  
```  
  
variableorproperty &= expression  
```  
  
## Partes  
 `variableorproperty`  
 Obrigatório.  Qualquer variável ou propriedade `String`.  
  
 `expression`  
 Obrigatório.  Qualquer expressão `String`.  
  
## Comentários  
 O elemento à esquerda do operador `&=` pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.  A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  O `&=` operador concatena a `String` a expressão à direita para a `String` variável ou propriedade na sua esquerda e atribui o resultado à variável ou propriedade na sua esquerda.  
  
## Sobrecarga  
 [Operador &](../../../visual-basic/language-reference/operators/concatenation-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Sobrecarregar o operador `&` afeta o comportamento do operador `&=`.  Se seu código usa `&=` em uma classe ou estrutura que sobrecarrega `&`, certifique\-se de que você entende seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo a seguir usa o operador `&=` para concatenar duas variáveis `String` e atribuir o resultado à primeira variável.  
  
 [!CODE [VbVbalrOperators#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#3)]  
  
## Consulte também  
 [Operador &](../../../visual-basic/language-reference/operators/concatenation-operator.md)   
 [Operador \+\=](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Operadores de concatenação](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)