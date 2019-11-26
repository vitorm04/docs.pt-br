---
title: Operadores de concatenação
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: f86245c649647be4e040a61083d8b93eee4d7422
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353685"
---
# <a name="concatenation-operators-in-visual-basic"></a>Operadores de concatenação no Visual Basic

Os operadores de concatenação unem várias cadeias de caracteres em uma única cadeia de caracteres. Existem dois operadores de concatenação, `+` e `&`. Ambos realizam a operação de concatenação básica, como mostra o exemplo a seguir.

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

Esses operadores também podem concatenar variáveis `String`, como mostra o exemplo a seguir.

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a>Diferenças entre os dois operadores de concatenação

The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers. Entretanto, ele pode também concatenar operandos numéricos com operandos de cadeia de caracteres. O operador `+` possui um conjunto complexo de regras que determinam se adicionam, concatenam, sinalizam um erro do compilador ou emitem uma exceção <xref:System.InvalidCastException> de tempo de execução.

The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`. O operador `&` é recomendado para concatenação de cadeia de caracteres por ser definido exclusivamente para cadeias de caracteres e reduz suas chances de gerar uma conversão indesejada.

## <a name="performance-string-and-stringbuilder"></a>Desempenho: String e StringBuilder

Se você realizar um número significativo de manipulações em uma cadeia de caracteres, como concatenações, exclusões e substituições, seu desempenho poderá se beneficiar da classe <xref:System.Text.StringBuilder> no namespace <xref:System.Text>. Ela usa uma instrução extra para criar e inicializar um objeto <xref:System.Text.StringBuilder> e outra instrução para converter seu valor final em uma `String`, mas você pode recuperar esse tempo, pois <xref:System.Text.StringBuilder> pode ser executado com mais rapidez.

## <a name="see-also"></a>Consulte também

- [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Types of String Manipulation Methods in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
