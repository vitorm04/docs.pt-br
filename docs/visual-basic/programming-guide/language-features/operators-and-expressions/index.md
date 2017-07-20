---
title: "Operadores e expressões no Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands, definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 069178fe753c3e09116c8a4845f96faf13eb72ec
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
<a id="operators-and-expressions-in-visual-basic" class="xliff"></a>

# Operadores e expressões no Visual Basic
Um *operador* é um elemento de código que executa uma operação em um ou mais elementos de código que retêm valores. Os elementos de valor incluem variáveis, constantes, literais, propriedades, valores retornados dos procedimentos `Function` e `Operator`, bem como expressões.  
  
 Uma *expressão* é uma série de elementos de valor combinada com operadores, que gera um novo valor. Os operadores agem em elementos de valor executando cálculos, comparações ou outras operações.  
  
<a id="types-of-operators" class="xliff"></a>

## Tipos de operadores  
 O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fornece os seguintes tipos de operadores:  
  
-   Os [operadores aritméticos](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) executam cálculos familiares em valores numéricos, incluindo a mudança dos padrões de bit.  
  
-   Os [operadores de comparação](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) comparam duas expressões e retornam um valor `Boolean` que representa o resultado da comparação.  
  
-   Os [operadores de concatenação](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) unem várias cadeias de caracteres em uma única cadeia de caracteres.  
  
-   Os [operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combinam valores numéricos ou `Boolean` e retornam um resultado do mesmo tipo de dados que os valores.  
  
 Os elementos de valor combinados com um operador são chamados *operandos* desse operador. Os operadores combinados com elementos de valor formam expressões, exceto para o operador de atribuição, que forma uma *instrução*. Para obter mais informações, consulte [Instruções](../../../../visual-basic/programming-guide/language-features/statements.md).  
  
<a id="evaluation-of-expressions" class="xliff"></a>

## Avaliação de expressões  
 O resultado final de uma expressão representa um valor, que normalmente é um tipo de dados familiar, como `Boolean`, `String` ou um tipo numérico.  
  
 Veja a seguir dois exemplos de expressões.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Vários operadores podem executar ações em uma única expressão ou instrução, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#56](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/index_1.vb)]  
  
 No exemplo anterior, o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] executa as operações na expressão à direita do operador de atribuição (`=`) e, em seguida, atribui o valor resultante à variável `x` à esquerda. Não há nenhum limite prático para o número de operadores que podem ser combinados em uma expressão, mas é necessário entender a [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) para assegurar que você obtenha os resultados esperados.  
  
 Para obter mais informações e exemplos, consulte [Sobrecarga de operador no Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
<a id="see-also" class="xliff"></a>

## Consulte também  
 [Operadores](../../../../visual-basic/language-reference/operators/index.md)   
 [Combinação eficiente de operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)   
 [Instruções](../../../../visual-basic/language-reference/statements/index.md)
