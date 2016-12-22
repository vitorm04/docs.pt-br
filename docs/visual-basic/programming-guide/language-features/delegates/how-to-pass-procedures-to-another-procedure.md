---
title: "Como passar procedimentos para outro procedimento no Visual Basic | Microsoft Docs"
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
  - "Operador AddressOf"
  - "delegados [Visual Basic], transmitindo procedimentos"
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como passar procedimentos para outro procedimento no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como usar delegados para passar um procedimento para outro procedimento.  
  
 Um delegado é um tipo que você pode usar como qualquer outro tipo em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  O operador `AddressOf` retorna um objeto delegado quando aplicado a um nome de procedimento.  
  
 Este exemplo tem um procedimento um parâmetro delegado que pode receber uma refer6encia para outro procedimento, obtida com o operador `AddressOf`.  
  
### Crie o delegado e procedimentos correspondentes.  
  
1.  Cria um delegado de nome `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  Crie um procedimento de nome `AddNumbers` com parâmetros e valor de retorno que correspondem àqueles do `MathOperator`, de modo que as assinaturas coincidam.  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  Crie um procedimento de nome `SubtractNumbers` com uma assinatura que corresponde ao `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  Crie um procedimento de nome `DelegateTest` que tome um delegado como parâmetro.  
  
     Este procedimetno pode aceitar uma referência a `AddNumbers` ou `SubtractNumbers`, porque suas assinaturas correspondem à assinatura do `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  Crie um procedimento de nome `Test` que chame `DelegateTest` uma vez com o delegado como parâmetro de `AddNumbers`, e de novo com o delegado como parâmetro de `SubtractNumbers`.  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     Quando `Test` é chamado, ele primeiro exibe o resultado de `AddNumbers` atuante em `5` e `3`, que é 8.  Em seguida, o resultado de `SubtractNumbers` atuando em `9` e `3` for exibida, que é 6.  
  
## Consulte também  
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Operador AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Instrução Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Como invocar um método delegado](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)