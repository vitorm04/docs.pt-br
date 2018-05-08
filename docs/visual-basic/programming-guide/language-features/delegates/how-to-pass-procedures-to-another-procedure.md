---
title: Como passar procedimentos para outro procedimento no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: c28ac7a640ec863b37bd7407d0273a1918964ac4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Como passar procedimentos para outro procedimento no Visual Basic
Este exemplo mostra como usar delegados para passar um procedimento para outro procedimento.  
  
 Um delegado é um tipo que você pode usar como qualquer outro tipo no Visual Basic. O `AddressOf` operador retorna um objeto delegado quando aplicado a um nome de procedimento.  
  
 Este exemplo tem um procedimento com um parâmetro delegado que pode levar a uma referência a outro procedimento, obtida com o `AddressOf` operador.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Crie o delegado e procedimentos correspondentes.  
  
1.  Cria um delegado de nome `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  Criar um procedimento denominado `AddNumbers` com parâmetros e valor de retorno que correspondem do `MathOperator`, de modo que as assinaturas forem correspondentes.  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  Criar um procedimento denominado `SubtractNumbers` com uma assinatura que corresponde a `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  Criar um procedimento denominado `DelegateTest` que usa um delegado como um parâmetro.  
  
     Esse procedimento pode aceitar uma referência a `AddNumbers` ou `SubtractNumbers`, porque suas assinaturas correspondem a `MathOperator` assinatura.  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  Criar um procedimento denominado `Test` que chama `DelegateTest` uma vez com o representante para `AddNumbers` como um parâmetro e, novamente com o delegado para `SubtractNumbers` como um parâmetro.  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     Quando `Test` é chamado, ele primeiro mostra o resultado de `AddNumbers` atuando em `5` e `3`, que é 8. Em seguida, o resultado de `SubtractNumbers` atuando em `9` e `3` for exibido, que é 6.  
  
## <a name="see-also"></a>Consulte também  
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Operador AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Instrução Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Como invocar um método delegado](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
