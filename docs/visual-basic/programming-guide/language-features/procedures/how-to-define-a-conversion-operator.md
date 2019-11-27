---
title: Como definir um operador de conversão
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 0ff95390206947e5a28f7a5b85547b496746a9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344894"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Como definir um operador de conversão (Visual Basic)
Se você tiver definido uma classe ou estrutura, poderá definir um operador de conversão de tipo entre o tipo de sua classe ou estrutura e outro tipo de dados (como `Integer`, `Double`ou `String`).  
  
 Defina a conversão de tipo como um procedimento de [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) dentro da classe ou estrutura. Todos os procedimentos de conversão devem ser `Public Shared`e cada um deve especificar o [alargamento](../../../../visual-basic/language-reference/modifiers/widening.md) ou a [restrição](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 A definição de um operador em uma classe ou estrutura também é chamada de *sobrecarga* do operador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define os operadores de conversão entre uma estrutura chamada `digit` e uma `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 Você pode testar a estrutura `digit` com o código a seguir.  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos de Operador](./operator-procedures.md)
- [Como definir um operador](./how-to-define-an-operator.md)
- [Como chamar um procedimento de operador](./how-to-call-an-operator-procedure.md)
- [Como usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md)
- [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Como declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Conversões Implícitas e Explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
