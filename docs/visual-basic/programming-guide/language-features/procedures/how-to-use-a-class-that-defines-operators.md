---
title: Como usar uma classe que define operadores
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
ms.openlocfilehash: 9ec4b4c07910100dd02cc86e882b44aa7dbd2ced
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346045"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Como usar uma classe que define operadores (Visual Basic)
Se você estiver usando uma classe ou estrutura que define seus próprios operadores, poderá acessar esses operadores de Visual Basic.  
  
 A definição de um operador em uma classe ou estrutura também é chamada de *sobrecarga* do operador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir acessa a estrutura SQL <xref:System.Data.SqlTypes.SqlString>, que define os operadores de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) em ambas as direções entre uma cadeia de caracteres SQL e uma Visual Basic Cadeia de caracteres. Use `CType(`*expressão de cadeia de caracteres SQL*, `String)` para converter uma cadeia de caracteres SQL em uma cadeia de caracteres de Visual Basic e `CType(`*expressão de cadeia de caracteres*de Visual Basic <xref:System.Data.SqlTypes.SqlString>para converter na outra direção.`)`  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 A estrutura de <xref:System.Data.SqlTypes.SqlString> define um operador de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) de `String` para <xref:System.Data.SqlTypes.SqlString> e outro de <xref:System.Data.SqlTypes.SqlString> para `String`. A instrução que atribui `title` a `jobTitle` faz uso do primeiro operador e a chamada de função <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> usa a segunda.  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Certifique-se de que a classe ou estrutura que você está usando define o operador que você deseja usar. Não presuma que a classe ou estrutura tenha definido todos os operadores disponíveis para sobrecarga. Para obter uma lista de operadores disponíveis, consulte a [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Inclua a instrução de `Imports` apropriada para a cadeia de caracteres SQL no início do seu arquivo de origem (nesse caso <xref:System.Data.SqlTypes>).  
  
 Seu projeto deve ter referências a System. Data e System. XML.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos de Operador](./operator-procedures.md)
- [Como definir um operador](./how-to-define-an-operator.md)
- [Como definir um operador de conversão](./how-to-define-a-conversion-operator.md)
- [Como chamar um procedimento de operador](./how-to-call-an-operator-procedure.md)
- [Ampliação](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Como declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Conversões Implícitas e Explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
