---
title: Como definir um operador de conversão (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 24bbe41af67f757cae661a78d482a423ff0ffd85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Como definir um operador de conversão (Visual Basic)
Se você tiver definido uma classe ou estrutura, você pode definir um operador de conversão de tipo entre o tipo de sua classe ou estrutura e outro tipo de dados (como `Integer`, `Double`, ou `String`).  
  
 Defina a conversão de tipo como um [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) procedimento dentro da classe ou estrutura. Todos os procedimentos de conversão devem ser `Public Shared`, e cada um deles deve especificar ou [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) ou [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define os operadores de conversão entre uma estrutura chamada `digit` e um `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 Você pode testar a estrutura `digit` com o código a seguir.  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de Operador](./operator-procedures.md)  
 [Como definir um operador](./how-to-define-an-operator.md)  
 [Como chamar um procedimento de operador](./how-to-call-an-operator-procedure.md)  
 [Como usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md)  
 [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Como declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Conversões Implícitas e Explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
