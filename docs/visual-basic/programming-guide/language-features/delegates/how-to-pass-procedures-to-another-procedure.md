---
title: 'Como: passar procedimentos para outro procedimento no Visual Basic | Documentos do Microsoft'
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
- AddressOf operator
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 9865e2d7d3786d289add3fa63b3db777317facdf
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Como passar procedimentos para outro procedimento no Visual Basic
Este exemplo mostra como usar delegados para passar um procedimento para outro procedimento.  
  
 Um delegado é um tipo que você pode usar como qualquer outro tipo em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. O `AddressOf` operador retorna um objeto delegado quando aplicado a um nome de procedimento.  
  
 Este exemplo tem um procedimento com um parâmetro delegado que pode levar a uma referência a outro procedimento, obtida com o `AddressOf` operador.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Crie o delegado e procedimentos correspondentes.  
  
1.  Criar um delegado chamado `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates n º&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  Crie um procedimento chamado `AddNumbers` com parâmetros e valor de retorno que correspondem do `MathOperator`, de modo que as assinaturas forem correspondentes.  
  
     [!code-vb[VbVbalrDelegates n º&2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  Crie um procedimento chamado `SubtractNumbers` com uma assinatura que corresponde a `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates n º&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  Criar um procedimento denominado `DelegateTest` que pega um delegado como parâmetro.  
  
     Esse procedimento pode aceitar uma referência a `AddNumbers` ou `SubtractNumbers`, porque suas assinaturas correspondem a `MathOperator` assinatura.  
  
     [!code-vb[VbVbalrDelegates n º&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  Crie um procedimento chamado `Test` que chama `DelegateTest` uma vez com o delegado para `AddNumbers` como um parâmetro e, novamente com o delegado para `SubtractNumbers` como um parâmetro.  
  
     [!code-vb[VbVbalrDelegates n º&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     Quando `Test` é chamado, ele primeiro mostra o resultado de `AddNumbers` atuando em `5` e `3`, que é 8. Em seguida, o resultado de `SubtractNumbers` atuando em `9` e `3` for exibido, que é 6.  
  
## <a name="see-also"></a>Consulte também  
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Operador AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Instrução delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Como invocar um método delegado](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
