---
title: Como invocar um método delegado (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: aca87dd9fa1990d44c99aab7753f2fd7d508adc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646946"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="ddddf-102">Como invocar um método delegado (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddddf-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>
<span data-ttu-id="ddddf-103">Este exemplo mostra como associar um método um delegado e depois chama esse método por meio do representante.</span><span class="sxs-lookup"><span data-stu-id="ddddf-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="ddddf-104">Crie o delegado e procedimentos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="ddddf-104">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="ddddf-105">Cria um delegado de nome `MySubDelegate`.</span><span class="sxs-lookup"><span data-stu-id="ddddf-105">Create a delegate named `MySubDelegate`.</span></span>  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  <span data-ttu-id="ddddf-106">Declare uma classe que contém um método com a mesma assinatura do delegado.</span><span class="sxs-lookup"><span data-stu-id="ddddf-106">Declare a class that contains a method with the same signature as the delegate.</span></span>  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  <span data-ttu-id="ddddf-107">Definir um método que cria uma instância do delegado e invoca o método associado com o delegado chamando o interno `Invoke` método.</span><span class="sxs-lookup"><span data-stu-id="ddddf-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ddddf-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ddddf-108">See Also</span></span>  
 [<span data-ttu-id="ddddf-109">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="ddddf-109">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="ddddf-110">Delegados</span><span class="sxs-lookup"><span data-stu-id="ddddf-110">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="ddddf-111">Eventos</span><span class="sxs-lookup"><span data-stu-id="ddddf-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="ddddf-112">Aplicativos com Multithread</span><span class="sxs-lookup"><span data-stu-id="ddddf-112">Multithreaded Applications</span></span>](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)
