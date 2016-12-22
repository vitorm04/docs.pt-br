---
title: "Operador += (Visual Basic) | Microsoft Docs"
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
  - "vb.+="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador += [Visual Basic]"
  - "Operador += [Visual Basic], acrescentando cadeias de caracteres"
  - "instruções de atribuição, composto"
  - "instruções de atribuição composta"
  - "instruções [Visual Basic], atribuição composta"
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador += (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Adiciona o valor de uma expressão numérica para o valor de uma variável numérica ou uma propriedade e atribui o resultado à variável ou propriedade.  Também pode ser usado para concatenar uma `String` a expressão para um `String` variável ou propriedade e atribuir o resultado para a variável ou propriedade.  
  
## Sintaxe  
  
```  
  
variableorproperty += expression  
```  
  
## Partes  
 `variableorproperty`  
 Obrigatório.  Qualquer numérico ou `String` variável ou propriedade.  
  
 `expression`  
 Obrigatório.  Qualquer numérico ou `String` expressão.  
  
## Comentários  
 O elemento à esquerda do operador `+=` pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.  A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `+=` operador adiciona o valor à direita para a variável ou propriedade na sua esquerda e atribui o resultado à variável ou propriedade na sua esquerda.  O `+=` operador também pode ser usado para concatenar a `String` a expressão à direita para a `String` variável ou propriedade à sua esquerda e atribuir o resultado à variável ou propriedade na sua esquerda.  
  
> [!NOTE]
>  Quando você usa o operador `+=`, talvez não seja possível determinar se a adição ou concatenação de sequência de caracteres ocorrerá.  Use o operador `&=` de concatenação para eliminar ambiguidade e fornecer código autodocumentável.  
  
 Este operador de atribuição implicitamente executa alargamento, mas não restringir conversões, se o ambiente de compilação impõe semântica estrita.  Para obter mais informações sobre essas conversões, consulte [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  Para obter mais informações sobre semântica estrita e permissiva, consulte [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Se forem permitida semântica permissível, a `+=` operador implicitamente executa uma variedade de seqüência de caracteres numéricos e de conversões idênticas àquelas realizadas pelo `+` operador.  Para obter detalhes sobre essas conversões, consulte [Operador \+](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## Sobrecarga  
 O operador `+` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Sobrecarregar o operador `+` afeta o comportamento do operador `+=`.  Se seu código usa `+=` em uma classe ou estrutura que sobrecarrega `+`, certifique\-se de que você entende seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo a seguir usa a `+=` operador para combinar o valor de uma variável com o outro.  A primeira parte usa `+=` com variáveis numéricas para adicionar um valor para outro.  A segunda parte usa `+=` com `String` variáveis para concatenar a um valor com o outro.  Em ambos os casos, o resultado é atribuído à primeira variável.  
  
 [!CODE [VbVbalrOperators#7](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#7)]  
  
 [!CODE [VbVbalrOperators#8](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#8)]  
  
 O valor de `num1` está agora 13 e o valor de `str1` agora está "103".  
  
## Consulte também  
 [Operador \+](../../../visual-basic/language-reference/operators/addition-operator.md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Operadores aritméticos](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operadores de concatenação](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)