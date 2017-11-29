---
title: "Operadores de concatenação no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a444cca76fbc41807b0c8b69bcbaedbd75c36eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="concatenation-operators-in-visual-basic"></a>Operadores de concatenação no Visual Basic
Os operadores de concatenação unem várias cadeias de caracteres em uma única cadeia de caracteres. Existem dois operadores de concatenação, `+` e `&`. Ambos realizam a operação de concatenação básica, como mostra o exemplo a seguir.  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 Esses operadores também podem concatenar variáveis `String`, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a>Diferenças entre os dois operadores de concatenação  
 O [operador +](../../../../visual-basic/language-reference/operators/addition-operator.md) tem o objetivo principal de adição de dois números. Entretanto, ele pode também concatenar operandos numéricos com operandos de cadeia de caracteres. O operador `+` possui um conjunto complexo de regras que determinam se adicionam, concatenam, sinalizam um erro do compilador ou emitem uma exceção <xref:System.InvalidCastException> de tempo de execução.  
  
 O [& operador](../../../../visual-basic/language-reference/operators/concatenation-operator.md) é definida somente para `String` operandos e ele sempre será ampliada operandos para `String`, independentemente da configuração de `Option Strict`. O operador `&` é recomendado para concatenação de cadeia de caracteres por ser definido exclusivamente para cadeias de caracteres e reduz suas chances de gerar uma conversão indesejada.  
  
## <a name="performance-string-and-stringbuilder"></a>Desempenho: String e StringBuilder  
 Se você realizar um número significativo de manipulações em uma cadeia de caracteres, como concatenações, exclusões e substituições, seu desempenho poderá se beneficiar da classe <xref:System.Text.StringBuilder> no namespace <xref:System.Text>. Ela usa uma instrução extra para criar e inicializar um objeto <xref:System.Text.StringBuilder> e outra instrução para converter seu valor final em uma `String`, mas você pode recuperar esse tempo, pois <xref:System.Text.StringBuilder> pode ser executado com mais rapidez.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Tipos de métodos de manipulação de cadeia de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)  
 [Operadores aritméticos no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
