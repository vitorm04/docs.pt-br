---
title: 'Como: Usar uma classe que define operadores (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: bd512adf2f06ed0fbd3d36ed3175a0928bf1c57c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829402"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Como: Usar uma classe que define operadores (Visual Basic)
Se você estiver usando uma classe ou estrutura que define seus próprio operadores, você pode acessar os operadores do Visual Basic.  
  
 Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir acessa a estrutura SQL <xref:System.Data.SqlTypes.SqlString>, que define os operadores de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) em ambas as direções entre uma cadeia de caracteres SQL e uma cadeia de caracteres do Visual Basic. Use `CType(` *expressão de cadeia de caracteres SQL*, `String)` para converter uma cadeia de caracteres SQL em uma cadeia de caracteres do Visual Basic, e `CType(` *expressão de cadeia de caracteres do Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` converter na outra direção.  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 O <xref:System.Data.SqlTypes.SqlString> estrutura define um operador de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) de `String` para <xref:System.Data.SqlTypes.SqlString> e outra de <xref:System.Data.SqlTypes.SqlString> para `String`. A instrução que atribui `title` à `jobTitle` usa o operador first e o <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> chamada de função usa o segundo.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Certifique-se de que a classe ou estrutura que você está usando define o operador que você deseja usar. Não presuma que a classe ou estrutura definiu todo disponível para a sobrecarga de operador. Para obter uma lista de operadores disponíveis, consulte [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Inclua o `Imports` instrução para a cadeia de caracteres SQL no início do seu arquivo de origem (nesse caso, <xref:System.Data.SqlTypes>).  
  
 Seu projeto deve ter referências a System. Data e System. XML.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos de Operador](./operator-procedures.md)
- [Como: Definir um operador](./how-to-define-an-operator.md)
- [Como: Definir um operador de conversão](./how-to-define-a-conversion-operator.md)
- [Como: Chamar um procedimento de operador](./how-to-call-an-operator-procedure.md)
- [Ampliação](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Conversões Implícitas e Explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
