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
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="31da7-102">Como: Invocar um método delegate (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31da7-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>

<span data-ttu-id="31da7-103">Este exemplo mostra como associar um método a um delegado e, em seguida, chamar esse método por meio do delegado.</span><span class="sxs-lookup"><span data-stu-id="31da7-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>

### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="31da7-104">Criar o delegado e os procedimentos correspondentes</span><span class="sxs-lookup"><span data-stu-id="31da7-104">Create the delegate and matching procedures</span></span>

1. <span data-ttu-id="31da7-105">Crie um delegado chamado `MySubDelegate`.</span><span class="sxs-lookup"><span data-stu-id="31da7-105">Create a delegate named `MySubDelegate`.</span></span>

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. <span data-ttu-id="31da7-106">Declare uma classe que contém um método com a mesma assinatura do delegado.</span><span class="sxs-lookup"><span data-stu-id="31da7-106">Declare a class that contains a method with the same signature as the delegate.</span></span>

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. <span data-ttu-id="31da7-107">Defina um método que cria uma instância do delegado e invoca o método associado ao delegado chamando o `Invoke` método interno.</span><span class="sxs-lookup"><span data-stu-id="31da7-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a><span data-ttu-id="31da7-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31da7-108">See also</span></span>

- [<span data-ttu-id="31da7-109">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="31da7-109">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="31da7-110">Delegados</span><span class="sxs-lookup"><span data-stu-id="31da7-110">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="31da7-111">Eventos</span><span class="sxs-lookup"><span data-stu-id="31da7-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="31da7-112">Aplicativos com Multithread</span><span class="sxs-lookup"><span data-stu-id="31da7-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
