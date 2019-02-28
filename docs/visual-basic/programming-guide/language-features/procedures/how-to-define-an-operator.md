---
title: 'Como: Definir um operador (Visual Basic)'
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
ms.openlocfilehash: 1e7d767b1ba370ac7303abfd8aa3606a43c33de9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973282"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Como: Definir um operador (Visual Basic)
Se você tiver definido uma classe ou estrutura, você pode definir o comportamento de um operador padrão (como `*`, `<>`, ou `And`) quando um ou ambos os operandos é do tipo de sua classe ou estrutura.  
  
 Defina o operador padrão como um procedimento de operador dentro da classe ou estrutura. Todos os procedimentos de operador devem ser `Public` `Shared`.  
  
 Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define o `+` chamado de operador para uma estrutura `height`. A estrutura usa a altura é medida em pés e polegadas. Uma *polegada* é 2,54 centímetros e uma *pés* é 12 polegadas. Para garantir que os valores normalizados (polegadas < 12.0), o construtor executa *módulo* 12 aritmético. O `+` operador usa o construtor para gerar valores normalizados.  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 Você pode testar a estrutura `height` com o código a seguir.  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  
  
  
## <a name="see-also"></a>Consulte também
- [Procedimentos de Operador](./operator-procedures.md)
- [Como: Definir um operador de conversão](./how-to-define-a-conversion-operator.md)
- [Como: Chamar um procedimento de operador](./how-to-call-an-operator-procedure.md)
- [Como: Usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md)
- [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Operador Mod](../../../../visual-basic/language-reference/operators/mod-operator.md)
