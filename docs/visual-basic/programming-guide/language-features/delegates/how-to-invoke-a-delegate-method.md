---
title: Como invocar um método delegado (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: c50a32d300aaf52efe0c55cef69d5793a98305ac
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204598"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="458be-102">Como invocar um método delegado (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="458be-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>
<span data-ttu-id="458be-103">Este exemplo mostra como associar um método com um delegado e, em seguida, chama esse método por meio do delegado.</span><span class="sxs-lookup"><span data-stu-id="458be-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="458be-104">Criar o delegado e procedimentos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="458be-104">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="458be-105">Criar um delegado chamado `MySubDelegate`.</span><span class="sxs-lookup"><span data-stu-id="458be-105">Create a delegate named `MySubDelegate`.</span></span>  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  <span data-ttu-id="458be-106">Declare uma classe que contém um método com a mesma assinatura que o delegado.</span><span class="sxs-lookup"><span data-stu-id="458be-106">Declare a class that contains a method with the same signature as the delegate.</span></span>  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  <span data-ttu-id="458be-107">Definir um método que cria uma instância do delegado e invoca o método associado com o delegado, chamando o interno `Invoke` método.</span><span class="sxs-lookup"><span data-stu-id="458be-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="458be-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="458be-108">See also</span></span>

- [<span data-ttu-id="458be-109">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="458be-109">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
- [<span data-ttu-id="458be-110">Delegados</span><span class="sxs-lookup"><span data-stu-id="458be-110">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
- [<span data-ttu-id="458be-111">Eventos</span><span class="sxs-lookup"><span data-stu-id="458be-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
- [<span data-ttu-id="458be-112">Aplicativos com Multithread</span><span class="sxs-lookup"><span data-stu-id="458be-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
