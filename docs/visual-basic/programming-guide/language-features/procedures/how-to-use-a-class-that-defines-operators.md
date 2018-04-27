---
title: Como usar uma classe que define operadores (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e0bcfaeca638dfabb841a9e935b872f76fdf957
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Como usar uma classe que define operadores (Visual Basic)
Se você estiver usando uma classe ou estrutura que define suas própria operadores, você pode acessar os operadores do Visual Basic.  
  
 Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir acessa a estrutura SQL <xref:System.Data.SqlTypes.SqlString>, que define os operadores de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) em ambas as direções entre uma cadeia de caracteres SQL e uma cadeia de caracteres do Visual Basic. Use `CType(` *expressão de cadeia de caracteres SQL*, `String)` para converter uma cadeia de caracteres SQL em uma cadeia de caracteres do Visual Basic e `CType(` *expressão de cadeia de caracteres do Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` para converter na outra direção.  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 O <xref:System.Data.SqlTypes.SqlString> estrutura define um operador de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) de `String` para <xref:System.Data.SqlTypes.SqlString> e outro de <xref:System.Data.SqlTypes.SqlString> para `String`. A instrução que atribui `title` para `jobTitle` faz uso do operador primeiro e o <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> chamada de função usa a segunda.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Certifique-se de que a classe ou estrutura que você está usando define o operador que você deseja usar. Não suponha que a classe ou estrutura tenha definido cada operador disponível para a sobrecarga. Para obter uma lista de operadores disponíveis, consulte [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Inclua o `Imports` instrução para a cadeia de caracteres SQL no início do seu arquivo de origem (neste caso <xref:System.Data.SqlTypes>).  
  
 O projeto deve ter referências a System. Data e System. XML.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de Operador](./operator-procedures.md)  
 [Como definir um operador](./how-to-define-an-operator.md)  
 [Como definir um operador de conversão](./how-to-define-a-conversion-operator.md)  
 [Como chamar um procedimento de operador](./how-to-call-an-operator-procedure.md)  
 [Ampliação](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Como declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Conversões Implícitas e Explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
