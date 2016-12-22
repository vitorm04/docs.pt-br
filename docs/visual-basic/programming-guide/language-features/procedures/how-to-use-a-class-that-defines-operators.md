---
title: "Como usar uma classe que define operadores (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "exemplos [Visual Basic], CType"
  - "sobrecarga de operador"
  - "procedimentos de Operador, Chamando "
  - "operadores [Visual Basic], sobrecarga"
  - "procedimentos, Chamando "
  - "procedimentos, operator"
  - "valores de retorno, Procedimentos de Operador"
  - "sintaxe, Procedimentos de Operador"
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como usar uma classe que define operadores (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Se você estiver usando uma classe ou estrutura que define suas própria operadores, você pode acessar os operadores de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 Definir um operador em uma classe ou estrutura também é chamado de *sobrecarregar* o operador.  
  
## Exemplo  
 O exemplo a seguir acessa a estrutura SQL <xref:System.Data.SqlTypes.SqlString>,que define os operadores de conversão \([Função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)\)em ambas as direções entre uma sequência SQL e uma [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sequência de caracteres.  Use `CType(` *expressão de sequência de caracteres SQL*,`String)` para converter uma sequência SQL em uma  sequência de caracteres [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], e `CType(`*expressão de sequência Visual Basic* , <xref:System.Data.SqlTypes.SqlString>`)` para converter na outra direção.  
  
 [!code-vb[VbVbcnProcedures#30](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 A estrutura <xref:System.Data.SqlTypes.SqlString> define um operador de conversão \([Função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)\) de `String` para <xref:System.Data.SqlTypes.SqlString> e outra de <xref:System.Data.SqlTypes.SqlString> para `String`.  A instrução que atribui `title` para `jobTitle` usa o operador first e o <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> chamada de função usa o segundo.  
  
## Compilando o código  
 Certifique\-se de que a classe ou estrutura que você está usando define o operador que você deseja usar.  Não presuma que a classe ou estrutura tenha definido cada operador disponível para a sobrecarga.  Para obter uma lista de operadores disponíveis, consulte [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Inclua a instrução `Imports` apropriada para a sequência SQL no início do seu arquivo de origem \(em <xref:System.Data.SqlTypes> neste caso\).  
  
 Seu projeto deve ter referências a System. Data e System. XML.  
  
## Consulte também  
 [Procedimentos do operador](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Como chamar um procedimento de operador](../Topic/How%20to:%20Call%20an%20Operator%20Procedure%20\(Visual%20Basic\).md)   
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Como declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)