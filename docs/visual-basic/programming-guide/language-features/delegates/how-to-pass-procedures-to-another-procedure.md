---
title: 'Como: Passar procedimentos para outro procedimento no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 312c0e0f100e85256ad4ca856ccf7f35dbaa36dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305241"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Como: Passar procedimentos para outro procedimento no Visual Basic
Este exemplo mostra como usar delegados para passar um procedimento para outro procedimento.  
  
 Um delegado é um tipo que você pode usar como qualquer outro tipo no Visual Basic. O `AddressOf` operador retorna um objeto delegado quando aplicado a um nome de procedimento.  
  
 Este exemplo tem um procedimento com um parâmetro delegado que pode levar a uma referência a outro procedimento, obtida com o `AddressOf` operador.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Criar o delegado e procedimentos correspondentes.  
  
1. Criar um delegado chamado `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. Criar um procedimento denominado `AddNumbers` com parâmetros e valor de retorno que correspondam do `MathOperator`, de modo que as assinaturas forem correspondentes.  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. Criar um procedimento denominado `SubtractNumbers` com uma assinatura que corresponde ao `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. Crie um procedimento chamado `DelegateTest` que aceita um delegado como um parâmetro.  
  
     Esse procedimento pode aceitar uma referência a `AddNumbers` ou `SubtractNumbers`, porque suas assinaturas correspondem a `MathOperator` assinatura.  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. Criar um procedimento denominado `Test` que chama `DelegateTest` uma vez com o representante `AddNumbers` como um parâmetro e, novamente com o delegado para `SubtractNumbers` como um parâmetro.  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     Quando `Test` é chamado, ele primeiro mostra o resultado da `AddNumbers` atuando em `5` e `3`, que é 8. Em seguida, o resultado de `SubtractNumbers` atuando em `9` e `3` for exibida, que é 6.  
  
## <a name="see-also"></a>Consulte também

- [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Operador AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Instrução Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Como: Invocar um método delegado](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
