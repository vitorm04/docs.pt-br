---
title: Como definir um operador
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: b99af8ff4d5428f1749bfc1a4c51a136f12405ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344869"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Como definir um operador (Visual Basic)
Se você tiver definido uma classe ou estrutura, poderá definir o comportamento de um operador padrão (como `*`, `<>`ou `And`) quando um ou ambos os operandos forem do tipo de sua classe ou estrutura.  
  
 Defina o operador padrão como um procedimento de operador dentro da classe ou estrutura. Todos os procedimentos de operador devem ser `Public` `Shared`.  
  
 A definição de um operador em uma classe ou estrutura também é chamada de *sobrecarga* do operador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define o operador de `+` para uma estrutura chamada `height`. A estrutura usa alturas medidas em pés e polegadas. Uma *polegada* é de 2,54 centímetros e um *pé* é de 12 polegadas. Para garantir valores normalizados (polegadas < 12,0), o construtor executa aritmética de *módulo* 12. O operador `+` usa o construtor para gerar valores normalizados.  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 Você pode testar a estrutura `height` com o código a seguir.  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a>Consulte também

- [Procedimentos de Operador](./operator-procedures.md)
- [Como definir um operador de conversão](./how-to-define-a-conversion-operator.md)
- [Como chamar um procedimento de operador](./how-to-call-an-operator-procedure.md)
- [Como usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md)
- [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Como declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Operador Mod](../../../../visual-basic/language-reference/operators/mod-operator.md)
