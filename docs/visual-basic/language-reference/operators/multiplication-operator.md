---
title: "Operador * (Visual Basic) | Microsoft Docs"
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
  - "vb.*"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador * [Visual Basic]"
  - "Operadores aritméticos, multiplicação"
  - "operadores matemáticos"
  - "Operador de multiplicação, sintaxe"
  - "operadores [Visual Basic], multiplicação"
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador * (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Multiplica dois números.  
  
## Sintaxe  
  
```  
  
number1 * number2  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`number1`|Obrigatório.  Qualquer expressão numérica.|  
|`number2`|Obrigatório.  Qualquer expressão numérica.|  
  
## Resultado  
 O resultado é o produto de `number1` e `number2`.  
  
## Os tipos suportados  
 Todos os tipos numéricos, incluindo os tipos unsigned e ponto\-flutuante e `Decimal`  
  
## Comentários  
 O tipo de dados do resultado depende do tipo dos operandos.  A tabela a seguir mostra como o tipo de dados do resultado é determinado.  
  
|||  
|-|-|  
|Tipo de dados dos operandos|Tipo de dados do resultado|  
|As duas expressões dão tipos de dados integrais \([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)\).|Um tipo de dados numéricos apropriado para os tipos de dados de `number1` e `number2`.  Veja as tabelas de "Aritmética de Inteiros" em [Tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)|  
|As duas expressões são [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|As duas expressões são [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|Uma das expressões é um tipo de dados de ponto flutuante \(`Single` ou  [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)\), mas não ambos `Single` \(nota `Decimal` não é um tipo de dados de ponto flutuante\)|`Double`|  
  
 Se uma expressão avalia [Nulo](../../../visual-basic/language-reference/nothing.md), é tratado como zero.  
  
## Sobrecarga  
 O operador `*` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Se seu código usa esse operador em tal classe ou estrutura, esteja certo que entende seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 Esse exemplo usa o operador `*` para multiplicar dois números.  O resultado é o produto dos dois operandos.  
  
 [!CODE [VbVbalrOperators#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#4)]  
  
## Consulte também  
 [Operador \*\=](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)   
 [Operadores aritméticos](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)