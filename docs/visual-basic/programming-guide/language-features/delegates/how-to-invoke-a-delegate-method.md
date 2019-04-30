---
title: 'Como: Invocar um método delegado (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: ac3e32010e7c20ba76e39915d694b11ab3a65d40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973323"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Como: Invocar um método delegado (Visual Basic)
Este exemplo mostra como associar um método com um delegado e, em seguida, chama esse método por meio do delegado.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Criar o delegado e procedimentos correspondentes.  
  
1. Criar um delegado chamado `MySubDelegate`.  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2. Declare uma classe que contém um método com a mesma assinatura que o delegado.  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3. Definir um método que cria uma instância do delegado e invoca o método associado com o delegado, chamando o interno `Invoke` método.  
  
    ```  
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
