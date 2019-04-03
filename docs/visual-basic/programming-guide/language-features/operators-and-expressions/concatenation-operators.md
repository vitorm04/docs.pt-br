---
title: Operadores de concatenação no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: 124f0ca0cd01d7fd218fd89dfb78e70fe8aad9e4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835720"
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
 O [operador +](../../../../visual-basic/language-reference/operators/addition-operator.md) tem a finalidade principal de adicionar dois números. Entretanto, ele pode também concatenar operandos numéricos com operandos de cadeia de caracteres. O operador `+` possui um conjunto complexo de regras que determinam se adicionam, concatenam, sinalizam um erro do compilador ou emitem uma exceção <xref:System.InvalidCastException> de tempo de execução.  
  
 O [& operador](../../../../visual-basic/language-reference/operators/concatenation-operator.md) é definido somente para `String` operandos e ele sempre amplia seus operandos para `String`, independentemente da configuração de `Option Strict`. O operador `&` é recomendado para concatenação de cadeia de caracteres por ser definido exclusivamente para cadeias de caracteres e reduz suas chances de gerar uma conversão indesejada.  
  
## <a name="performance-string-and-stringbuilder"></a>Desempenho: String e StringBuilder  
 Se você realizar um número significativo de manipulações em uma cadeia de caracteres, como concatenações, exclusões e substituições, seu desempenho poderá se beneficiar da classe <xref:System.Text.StringBuilder> no namespace <xref:System.Text>. Ela usa uma instrução extra para criar e inicializar um objeto <xref:System.Text.StringBuilder> e outra instrução para converter seu valor final em uma `String`, mas você pode recuperar esse tempo, pois <xref:System.Text.StringBuilder> pode ser executado com mais rapidez.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Tipos de métodos de manipulação de cadeia de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [Operadores aritméticos no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
