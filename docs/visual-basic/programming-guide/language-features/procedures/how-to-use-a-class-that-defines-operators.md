---
title: 'Como: usar uma classe que define operadores (Visual Basic) | Documentos do Microsoft'
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
- operator procedures, calling
- procedures, operator
- procedures, calling
- examples [Visual Basic], CType
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: 21
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: b1db7c0b2a6fd8160baa48892b5f2214df24674e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Como usar uma classe que define operadores (Visual Basic)
Se você estiver usando uma classe ou estrutura que define suas própria operadores, você pode acessar os operadores de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir acessa a estrutura SQL <xref:System.Data.SqlTypes.SqlString>, que define os operadores de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) em ambas as direções entre uma cadeia de caracteres SQL e um [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] string.</xref:System.Data.SqlTypes.SqlString> Use `CType(` *expressão de cadeia de caracteres SQL*, `String)` para converter uma cadeia de caracteres SQL para uma [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cadeia de caracteres, e `CType(` *expressão de cadeia de caracteres do Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` para converter na outra direção.</xref:System.Data.SqlTypes.SqlString>  
  
 [!code-vb[30 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures&#31;](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 O <xref:System.Data.SqlTypes.SqlString>estrutura define um operador de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) do `String` para <xref:System.Data.SqlTypes.SqlString>e outra de <xref:System.Data.SqlTypes.SqlString>para `String`.</xref:System.Data.SqlTypes.SqlString> </xref:System.Data.SqlTypes.SqlString> </xref:System.Data.SqlTypes.SqlString> A instrução que atribui `title` para `jobTitle` usa o operador first e o <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>chamada de função usa a segunda.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Certifique-se de que a classe ou estrutura que você está usando define o operador que você deseja usar. Não presuma que a classe ou estrutura tenha definido cada operador disponível para a sobrecarga. Para obter uma lista de operadores disponíveis, consulte [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Incluir apropriado `Imports` instrução para a cadeia de caracteres SQL no início do seu arquivo de origem (neste caso <xref:System.Data.SqlTypes>).</xref:System.Data.SqlTypes>  
  
 Seu projeto deve ter referências a System. Data e System. XML.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de operador](./operator-procedures.md)   
 [Como: definir um operador](./how-to-define-an-operator.md)   
 [Como: definir um operador de conversão](./how-to-define-a-conversion-operator.md)   
 [Como: chamar um procedimento de operador](./how-to-call-an-operator-procedure.md)   
 [Ampliação](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
