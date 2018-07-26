---
title: Como implementar eventos de interface (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 7437868bffa0f317ad29ed6c920ae007c602defa
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874875"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="f1a07-102">Como implementar eventos de interface (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f1a07-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="f1a07-103">Um [interface](../../../csharp/language-reference/keywords/interface.md) pode declarar uma [evento](../../../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="f1a07-103">An [interface](../../../csharp/language-reference/keywords/interface.md) can declare an [event](../../../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="f1a07-104">O exemplo a seguir mostra como implementar eventos de interface em uma classe.</span><span class="sxs-lookup"><span data-stu-id="f1a07-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="f1a07-105">Basicamente, as regras são as mesmas aplicadas à implementação de qualquer método ou propriedade de interface.</span><span class="sxs-lookup"><span data-stu-id="f1a07-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="f1a07-106">Implementar eventos de interface em uma classe</span><span class="sxs-lookup"><span data-stu-id="f1a07-106">To implement interface events in a class</span></span>  
  
<span data-ttu-id="f1a07-107">Declare o evento na classe e, em seguida, invoque-o nas áreas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="f1a07-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
```csharp
namespace ImplementInterfaceEvents  
{  
    public interface IDrawingObject  
    {  
        event EventHandler ShapeChanged;  
    }  
    public class MyEventArgs : EventArgs   
    {  
        // class members  
    }  
    public class Shape : IDrawingObject  
    {  
        public event EventHandler ShapeChanged;  
        void ChangeShape()  
        {  
            // Do something here before the event…  

            OnShapeChanged(new MyEventArgs(/*arguments*/));  

            // or do something here after the event.   
        }  
        protected virtual void OnShapeChanged(MyEventArgs e)  
        {  
            ShapeChanged?.Invoke(this, e);  
        }  
    }  

}  
```  
  
## <a name="example"></a><span data-ttu-id="f1a07-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1a07-108">Example</span></span>  
<span data-ttu-id="f1a07-109">O exemplo a seguir mostra como lidar com a situação menos comum, na qual a classe herda de duas ou mais interfaces e cada interface tem um evento com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="f1a07-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="f1a07-110">Nessa situação, é necessário fornecer uma implementação explícita da interface para pelo menos um dos eventos.</span><span class="sxs-lookup"><span data-stu-id="f1a07-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="f1a07-111">Ao gravar uma implementação explícita da interface de um evento, também é necessário gravar os acessadores de evento `add` e `remove`.</span><span class="sxs-lookup"><span data-stu-id="f1a07-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="f1a07-112">Normalmente, eles são fornecidos pelo compilador, mas nesse caso o compilador não pode fornecê-los.</span><span class="sxs-lookup"><span data-stu-id="f1a07-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="f1a07-113">Ao fornecer acessadores próprios, é possível especificar se os dois eventos são representados pelo mesmo evento na classe ou por eventos diferentes.</span><span class="sxs-lookup"><span data-stu-id="f1a07-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="f1a07-114">Por exemplo, se os eventos forem gerados em horários diferentes, de acordo com as especificações da interface, será possível associar cada evento a uma implementação separada na classe.</span><span class="sxs-lookup"><span data-stu-id="f1a07-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="f1a07-115">No exemplo a seguir, os assinantes determinam qual evento `OnDraw` receberão ao converter a referência de forma para um `IShape` ou um `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="f1a07-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[WrapTwoInterfaceEvents](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs#everything)]
  
## <a name="see-also"></a><span data-ttu-id="f1a07-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1a07-116">See Also</span></span>  
 [<span data-ttu-id="f1a07-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f1a07-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f1a07-118">Eventos</span><span class="sxs-lookup"><span data-stu-id="f1a07-118">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="f1a07-119">Delegados</span><span class="sxs-lookup"><span data-stu-id="f1a07-119">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="f1a07-120">Implementação de interface explícita</span><span class="sxs-lookup"><span data-stu-id="f1a07-120">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 [<span data-ttu-id="f1a07-121">Como acionar eventos de classe base em classes derivadas</span><span class="sxs-lookup"><span data-stu-id="f1a07-121">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
