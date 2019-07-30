---
title: 'Como: Invocar um método delegate (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: c2bdb65c9d060e854db3319e4aa5b2e93b9681af
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629582"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Como: Invocar um método delegate (Visual Basic)

Este exemplo mostra como associar um método a um delegado e, em seguida, chamar esse método por meio do delegado.

### <a name="create-the-delegate-and-matching-procedures"></a>Criar o delegado e os procedimentos correspondentes

1. Crie um delegado chamado `MySubDelegate`.

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. Declare uma classe que contém um método com a mesma assinatura do delegado.

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. Defina um método que cria uma instância do delegado e invoca o método associado ao delegado chamando o `Invoke` método interno.

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a>Consulte também

- [Instrução Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Aplicativos com Multithread](../../../../standard/threading/using-threads-and-threading.md)
