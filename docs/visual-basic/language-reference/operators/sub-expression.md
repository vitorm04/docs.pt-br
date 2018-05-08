---
title: Subexpressão (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 602212e664fa3362742fb1ba0dc033610272d3af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="sub-expression-visual-basic"></a>Subexpressão (Visual Basic)
Declara os parâmetros e o código que define uma expressão lambda de sub-rotina.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`parameterlist`|Opcional. Uma lista de nomes de variáveis locais que representam os parâmetros do procedimento. Os parênteses devem estar presentes mesmo quando a lista está vazia. Para obter mais informações, consulte [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`statement`|Obrigatório. Uma única instrução.|  
|`statements`|Obrigatório. Uma lista de instruções.|  
  
## <a name="remarks"></a>Comentários  
 Um *expressão lambda* é uma sub-rotina que não tem um nome e que executa uma ou mais instruções. Você pode usar uma expressão lambda em qualquer lugar que você pode usar um tipo de delegado, exceto como um argumento para `RemoveHandler`. Para obter mais informações sobre delegados e o uso de expressões lambda com delegados, consulte [declaração de delegado](../../../visual-basic/language-reference/statements/delegate-statement.md) e [conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Sintaxe da expressão lambda  
 A sintaxe de uma expressão lambda é semelhante a que uma sub-rotina padrão. As diferenças são da seguinte maneira:  
  
-   Uma expressão lambda não tem um nome.  
  
-   Uma expressão lambda não pode ter um modificador, como `Overloads` ou `Overrides`.  
  
-   O corpo de uma expressão lambda de linha deve ser uma instrução, não é uma expressão. O corpo pode consistir em uma chamada para um procedimento sub, mas não uma chamada para um procedimento function.  
  
-   Em uma expressão lambda, ou todos os parâmetros devem especificar tipos de dados ou todos os parâmetros devem ser inferidos.  
  
-   Opcional e `ParamArray` parâmetros não são permitidos em expressões lambda.  
  
-   Parâmetros genéricos não são permitidos em expressões lambda.  
  
## <a name="example"></a>Exemplo  
 A seguir está um exemplo de uma expressão lambda que grava um valor para o console. O exemplo mostra dois a sintaxe da expressão lambda de linha e de várias linhas de uma sub-rotina. Para obter mais exemplos, consulte [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Conversão de Delegado Reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
