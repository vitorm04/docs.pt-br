---
title: 'Como: passar procedimentos para outro procedimento'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 300489935ce54d78b989d09211a7f6ba95c2f514
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345242"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Como passar procedimentos para outro procedimento no Visual Basic
Este exemplo mostra como usar delegados para passar um procedimento para outro procedimento.  
  
 Um delegado é um tipo que você pode usar como qualquer outro tipo em Visual Basic. O operador `AddressOf` retorna um objeto delegate quando aplicado a um nome de procedimento.  
  
 Este exemplo tem um procedimento com um parâmetro delegado que pode usar uma referência a outro procedimento, obtido com o operador de `AddressOf`.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Criar o delegado e os procedimentos correspondentes  
  
1. Crie um delegado chamado `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. Crie um procedimento chamado `AddNumbers` com parâmetros e valor de retorno que correspondam aos de `MathOperator`, para que as assinaturas correspondam.  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. Crie um procedimento chamado `SubtractNumbers` com uma assinatura que corresponda a `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. Crie um procedimento chamado `DelegateTest` que usa um delegado como parâmetro.  
  
     Esse procedimento pode aceitar uma referência a `AddNumbers` ou `SubtractNumbers`, porque suas assinaturas correspondem à assinatura de `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. Crie um procedimento chamado `Test` que chame `DelegateTest` uma vez com o delegado para `AddNumbers` como um parâmetro e novamente com o delegado para `SubtractNumbers` como um parâmetro.  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     Quando `Test` é chamado, ele primeiro exibe o resultado de `AddNumbers` atuando em `5` e `3`, que é 8. Em seguida, o resultado de `SubtractNumbers` atuando em `9` e `3` é exibido, que é 6.  
  
## <a name="see-also"></a>Consulte também

- [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Operador AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Instrução Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Como invocar um método delegado](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
