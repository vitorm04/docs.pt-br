---
title: "Operadores de concatenação no Visual Basic | Documentos do Microsoft"
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
- '& operator [Visual Basic], concatenation'
- concatenation operators
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators, Visual Basic strings
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fa11f1dcff2c333861596cbac03391403cf962c1
ms.lasthandoff: 03/13/2017

---
# <a name="concatenation-operators-in-visual-basic"></a>Operadores de concatenação no Visual Basic
Os operadores de concatenação unem várias cadeias de caracteres em uma única cadeia de caracteres. Existem dois operadores de concatenação, `+` e `&`. Ambos realizam a operação de concatenação básica, como mostra o exemplo a seguir.  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 Esses operadores também podem concatenar variáveis `String`, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators&#76;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a>Diferenças entre os dois operadores de concatenação  
 O [operador +](../../../../visual-basic/language-reference/operators/addition-operator.md) tem o objetivo principal de adicionar dois números. Entretanto, ele pode também concatenar operandos numéricos com operandos de cadeia de caracteres. O `+` operador tem um conjunto complexo de regras que determinam se adicionar, concatenar, sinalizar um erro do compilador ou lançar um tempo de execução <xref:System.InvalidCastException>exceção.</xref:System.InvalidCastException>  
  
 O [< / operador](../../../../visual-basic/language-reference/operators/concatenation-operator.md) é definido somente para `String` operandos e ele sempre amplia seus operandos para `String`, independentemente da configuração da `Option Strict`. O operador `&` é recomendado para concatenação de cadeia de caracteres por ser definido exclusivamente para cadeias de caracteres e reduz suas chances de gerar uma conversão indesejada.  
  
## <a name="performance-string-and-stringbuilder"></a>Desempenho: String e StringBuilder  
 Se você fizer um número significativo de manipulações em uma cadeia de caracteres, como concatenações, exclusões e substituições, seu desempenho poderá se beneficiar de <xref:System.Text.StringBuilder>classe o <xref:System.Text>namespace.</xref:System.Text> </xref:System.Text.StringBuilder> Ele usa uma instrução extra para criar e inicializar um <xref:System.Text.StringBuilder>objeto e outra instrução para converter o valor final para um `String`, mas você pode recuperar esse tempo porque <xref:System.Text.StringBuilder>pode ser executado mais rapidamente.</xref:System.Text.StringBuilder> </xref:System.Text.StringBuilder>  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Tipos de métodos de manipulação de cadeia de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)   
 [Operadores aritméticos em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operadores de comparação em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
