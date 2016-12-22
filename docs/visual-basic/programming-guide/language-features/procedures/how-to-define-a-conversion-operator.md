---
title: "Como definir um operador de convers&#227;o (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "sobrecarga de operador"
  - "operadores [Visual Basic], definindo"
  - "operadores [Visual Basic], sobrecarga"
  - "procedimentos, definindo"
  - "procedimentos, operator"
  - "valores de retorno, Procedimentos de Operador"
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como definir um operador de convers&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Se você tiver definido uma classe ou estrutura, você pode definir um operador de conversão de tipos entre o tipo de sua classe ou estrutura e outro tipo de dados \(como `Integer`,`Double`, ou `String`\) .  
  
 Defina a conversão de tipos como um procedimento [Função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) dentro da classe ou estrutura.  Todos os procedimentos de conversão devem ser `Public Shared`, e cada um deles deve especificar ou [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) ou [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 Definir um operador em uma classe ou estrutura também é chamado de *sobrecarregar* o operador.  
  
## Exemplo  
 O exemplo a seguir define os operadores de conversão entre uma estrutura chamada  `digit`  e um `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 Você pode testar a estrutura `digit` com o seguinte código:  
  
 [!code-vb[VbVbcnProcedures#28](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## Consulte também  
 [Procedimentos do operador](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como chamar um procedimento de operador](../Topic/How%20to:%20Call%20an%20Operator%20Procedure%20\(Visual%20Basic\).md)   
 [Como usar uma classe que define operadores](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)   
 [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Como declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)