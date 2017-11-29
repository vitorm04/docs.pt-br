---
title: "Usando variação em delegações (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb8512945fa7aefa9afce4f4f1f8e0200dc3e2b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="a3c9a-102">Usando variação em delegações (C#)</span><span class="sxs-lookup"><span data-stu-id="a3c9a-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="a3c9a-103">Quando você atribui um método a um delegado, a *covariância* e a *contravariância* fornece flexibilidade para corresponder um tipo de delegado a uma assinatura de método.</span><span class="sxs-lookup"><span data-stu-id="a3c9a-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="a3c9a-104">A covariância permite que um método tenha o tipo de retorno mais derivado do que o definido no delegado.</span><span class="sxs-lookup"><span data-stu-id="a3c9a-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="a3c9a-105">A contravariância permite que um método que tem tipos de parâmetro menos derivados do que no tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="a3c9a-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="a3c9a-106">Exemplo 1: covariância</span><span class="sxs-lookup"><span data-stu-id="a3c9a-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="a3c9a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3c9a-107">Description</span></span>  
 <span data-ttu-id="a3c9a-108">Este exemplo demonstra como delegados podem ser usados com métodos que têm tipos de retorno que são derivados do tipo de retorno na assinatura do delegado.</span><span class="sxs-lookup"><span data-stu-id="a3c9a-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="a3c9a-109">O tipo de dados retornado por `DogsHandler` é do tipo `Dogs`, que deriva do tipo `Mammals` definido no delegado.</span><span class="sxs-lookup"><span data-stu-id="a3c9a-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a3c9a-110">Código</span><span class="sxs-lookup"><span data-stu-id="a3c9a-110">Code</span></span>  
  
```csharp  
class Mammals{}  
class Dogs : Mammals{}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a><span data-ttu-id="a3c9a-111">Exemplo 2: contravariância</span><span class="sxs-lookup"><span data-stu-id="a3c9a-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="a3c9a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3c9a-112">Description</span></span>  
 <span data-ttu-id="a3c9a-113">Este exemplo demonstra como delegados podem ser usados com métodos que têm parâmetros de um tipo que são tipos base do tipo de parâmetro de assinatura do delegado.</span><span class="sxs-lookup"><span data-stu-id="a3c9a-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="a3c9a-114">Com a contravariância, você pode usar um manipulador de eventos em vez de manipuladores separados.</span><span class="sxs-lookup"><span data-stu-id="a3c9a-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="a3c9a-115">Por exemplo, você pode criar um manipulador de eventos que aceita um parâmetro de entrada `EventArgs` e usá-lo com um evento `Button.MouseClick` que envia um tipo `MouseEventArgs` como um parâmetro e também com um evento `TextBox.KeyDown` que envia um parâmetro `KeyEventArgs`.</span><span class="sxs-lookup"><span data-stu-id="a3c9a-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a3c9a-116">Código</span><span class="sxs-lookup"><span data-stu-id="a3c9a-116">Code</span></span>  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method   
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3c9a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3c9a-117">See Also</span></span>  
 [<span data-ttu-id="a3c9a-118">Variação em delegados (C#)</span><span class="sxs-lookup"><span data-stu-id="a3c9a-118">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [<span data-ttu-id="a3c9a-119">Usando variação para delegados genéricos Func e Action (C#)</span><span class="sxs-lookup"><span data-stu-id="a3c9a-119">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
