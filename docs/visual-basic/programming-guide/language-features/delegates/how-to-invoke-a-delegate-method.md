---
title: Como invocar um método delegado
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: f319727c007b93c7b334af0598f1b9f7c034144d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410715"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="9ab2f-102">Como invocar um método delegado (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ab2f-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>

<span data-ttu-id="9ab2f-103">Este exemplo mostra como associar um método a um delegado e, em seguida, chamar esse método por meio do delegado.</span><span class="sxs-lookup"><span data-stu-id="9ab2f-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>

### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="9ab2f-104">Criar o delegado e os procedimentos correspondentes</span><span class="sxs-lookup"><span data-stu-id="9ab2f-104">Create the delegate and matching procedures</span></span>

1. <span data-ttu-id="9ab2f-105">Crie um delegado chamado `MySubDelegate` .</span><span class="sxs-lookup"><span data-stu-id="9ab2f-105">Create a delegate named `MySubDelegate`.</span></span>

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. <span data-ttu-id="9ab2f-106">Declare uma classe que contém um método com a mesma assinatura do delegado.</span><span class="sxs-lookup"><span data-stu-id="9ab2f-106">Declare a class that contains a method with the same signature as the delegate.</span></span>

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. <span data-ttu-id="9ab2f-107">Defina um método que cria uma instância do delegado e invoca o método associado ao delegado chamando o `Invoke` método interno.</span><span class="sxs-lookup"><span data-stu-id="9ab2f-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a><span data-ttu-id="9ab2f-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="9ab2f-108">See also</span></span>

- [<span data-ttu-id="9ab2f-109">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="9ab2f-109">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="9ab2f-110">Delegados</span><span class="sxs-lookup"><span data-stu-id="9ab2f-110">Delegates</span></span>](index.md)
- [<span data-ttu-id="9ab2f-111">Eventos</span><span class="sxs-lookup"><span data-stu-id="9ab2f-111">Events</span></span>](../events/index.md)
- [<span data-ttu-id="9ab2f-112">Aplicativos multi-threaded</span><span class="sxs-lookup"><span data-stu-id="9ab2f-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
