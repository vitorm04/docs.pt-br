---
title: "Operador &lt;&lt;= (Visual Basic) | Microsoft Docs"
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
  - "vb.<<="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador <<= [Visual Basic]"
  - "instruções de atribuição, composto"
  - "instruções de atribuição composta"
  - "Operador <<="
  - "operator<<="
  - "instruções [Visual Basic], atribuição composta"
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador &lt;&lt;= (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Executa um deslocamento aritmético à direita sobre o valor de uma variável ou propriedade e atribui o resultado de volta a variável ou propriedade.  
  
## Sintaxe  
  
```  
  
variableorproperty <<= amount  
```  
  
## Partes  
 `variableorproperty`  
 Necessário.  Variável ou propriedade de um tipo integral \(`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`\).  
  
 `amount`  
 Necessário.  Expressão numérica de um tipo de dados que amplia para `Integer`.  
  
## Comentários  
 O elemento à esquerda do operador `<<=` pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.  A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `<<=`primeiro, o operador executa uma aritmética deslocar .   O operador , em seguida, atribui o resultado dessa operação volta para essa variável ou propriedade.  
  
 Shifts aritméticos são não circulares, que significa que os bits deslocados de uma extremidade do resultado não são reintroduzidos na outra extremidade.  Em um deslocamento aritmético à esquerda, os bits deslocados fora do intervalo de tipo de dados o resultado são descartados, e as posições vagas de bits no lado direito estão definidas como zero.  
  
## Sobrecarga  
 [Operador \<\<](../../../visual-basic/language-reference/operators/left-shift-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Sobrecarregar o operador `<<` afeta o comportamento do operador `<<=`.  Se seu código usa `<<=` em uma classe ou estrutura que sobrecarrega `<<`, certifique\-se de que você entende seu comportamento redefinido.  Para mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O seguinte exemplo usa o operador `<<=` para deslocar à direita o padrão de bits de uma variável `Integer` pela quantidade especificada e atribui o resultado à variável.  
  
 [!CODE [VbVbalrOperators#13](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#13)]  
  
## Consulte também  
 [Operador \<\<](../../../visual-basic/language-reference/operators/left-shift-operator.md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Operadores Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)