---
title: "Usando variação em delegações (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 620fd61000e42d68f566e441d023d73a036000ae
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="c4ee4-102">Usando variação em delegações (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4ee4-102">Using Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="c4ee4-103">Quando você atribui um método a um delegado, *covariância* e *contravariância* fornecem flexibilidade para corresponder a um tipo de delegado com uma assinatura de método.</span><span class="sxs-lookup"><span data-stu-id="c4ee4-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="c4ee4-104">Covariância permite que um método para ter o tipo de retorno que seja mais derivado daquele definido no delegado.</span><span class="sxs-lookup"><span data-stu-id="c4ee4-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="c4ee4-105">Contravariância permite que um método que possui tipos de parâmetro que são menos derivados no tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="c4ee4-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="c4ee4-106">Exemplo 1: covariância</span><span class="sxs-lookup"><span data-stu-id="c4ee4-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="c4ee4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4ee4-107">Description</span></span>  
 <span data-ttu-id="c4ee4-108">Este exemplo demonstra como delegados podem ser usados com métodos que têm tipos de retorno que são derivados do tipo de retorno na assinatura do delegado.</span><span class="sxs-lookup"><span data-stu-id="c4ee4-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="c4ee4-109">O tipo de dados retornado por `DogsHandler` é do tipo `Dogs`, que deriva de `Mammals` tipo definido no delegado.</span><span class="sxs-lookup"><span data-stu-id="c4ee4-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c4ee4-110">Código</span><span class="sxs-lookup"><span data-stu-id="c4ee4-110">Code</span></span>  
  
```vb  
Class Mammals  
End Class  
  
Class Dogs  
    Inherits Mammals  
End Class  
Class Test  
    Public Delegate Function HandlerMethod() As Mammals  
    Public Shared Function MammalsHandler() As Mammals  
        Return Nothing  
    End Function  
    Public Shared Function DogsHandler() As Dogs  
        Return Nothing  
    End Function  
    Sub Test()  
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler  
        ' Covariance enables this assignment.  
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler  
    End Sub  
End Class  
```  
  
## <a name="example-2-contravariance"></a><span data-ttu-id="c4ee4-111">Exemplo 2: contravariância</span><span class="sxs-lookup"><span data-stu-id="c4ee4-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="c4ee4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4ee4-112">Description</span></span>  
 <span data-ttu-id="c4ee4-113">Este exemplo demonstra como delegados podem ser usados com métodos que têm parâmetros de um tipo que são tipos base do tipo de parâmetro de assinatura do delegado.</span><span class="sxs-lookup"><span data-stu-id="c4ee4-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="c4ee4-114">Com contravariância, você pode usar um manipulador de eventos em vez de manipuladores separados.</span><span class="sxs-lookup"><span data-stu-id="c4ee4-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="c4ee4-115">Por exemplo, você pode criar um manipulador de eventos que aceita um `EventArgs` parâmetro de entrada e usá-la com um `Button.MouseClick` eventos que envia uma `MouseEventArgs` tipo como um parâmetro e também com um `TextBox.KeyDown` eventos que envia um `KeyEventArgs` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c4ee4-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c4ee4-116">Código</span><span class="sxs-lookup"><span data-stu-id="c4ee4-116">Code</span></span>  
  
```vb  
' Event hander that accepts a parameter of the EventArgs type.  
Private Sub MultiHandler(ByVal sender As Object,  
                         ByVal e As System.EventArgs)  
    Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Form1_Load(ByVal sender As System.Object,  
    ByVal e As System.EventArgs) Handles MyBase.Load  
  
    ' You can use a method that has an EventArgs parameter,  
    ' although the event expects the KeyEventArgs parameter.  
    AddHandler Button1.KeyDown, AddressOf MultiHandler  
  
    ' You can use the same method   
    ' for the event that expects the MouseEventArgs parameter.  
    AddHandler Button1.MouseClick, AddressOf MultiHandler  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4ee4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4ee4-117">See Also</span></span>  
 <span data-ttu-id="c4ee4-118">[Variação em delegações (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) </span><span class="sxs-lookup"><span data-stu-id="c4ee4-118">[Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) </span></span>  
<span data-ttu-id="c4ee4-119"> [Usando variação para delegações Func e Action genérica (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="c4ee4-119"> [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span></span>
