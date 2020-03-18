---
title: Como implementar eventos de interface - C# Guia de Programação
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 8c0d221ef1272a43e2682ef2af3fa37d2d12d35e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167473"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="34e7c-102">Como implementar eventos de interface (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="34e7c-102">How to implement interface events (C# Programming Guide)</span></span>
<span data-ttu-id="34e7c-103">Um [interface](../../language-reference/keywords/interface.md) pode declarar uma [evento](../../language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="34e7c-103">An [interface](../../language-reference/keywords/interface.md) can declare an [event](../../language-reference/keywords/event.md).</span></span> <span data-ttu-id="34e7c-104">O exemplo a seguir mostra como implementar eventos de interface em uma classe.</span><span class="sxs-lookup"><span data-stu-id="34e7c-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="34e7c-105">Basicamente, as regras são as mesmas aplicadas à implementação de qualquer método ou propriedade de interface.</span><span class="sxs-lookup"><span data-stu-id="34e7c-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="34e7c-106">Implementar eventos de interface em uma classe</span><span class="sxs-lookup"><span data-stu-id="34e7c-106">To implement interface events in a class</span></span>  
  
<span data-ttu-id="34e7c-107">Declare o evento na classe e, em seguida, invoque-o nas áreas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="34e7c-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="34e7c-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34e7c-108">Example</span></span>  
<span data-ttu-id="34e7c-109">O exemplo a seguir mostra como lidar com a situação menos comum, na qual a classe herda de duas ou mais interfaces e cada interface tem um evento com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="34e7c-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="34e7c-110">Nessa situação, é necessário fornecer uma implementação explícita da interface para pelo menos um dos eventos.</span><span class="sxs-lookup"><span data-stu-id="34e7c-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="34e7c-111">Ao gravar uma implementação explícita da interface de um evento, também é necessário gravar os acessadores de evento `add` e `remove`.</span><span class="sxs-lookup"><span data-stu-id="34e7c-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="34e7c-112">Normalmente, eles são fornecidos pelo compilador, mas nesse caso o compilador não pode fornecê-los.</span><span class="sxs-lookup"><span data-stu-id="34e7c-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="34e7c-113">Ao fornecer acessadores próprios, é possível especificar se os dois eventos são representados pelo mesmo evento na classe ou por eventos diferentes.</span><span class="sxs-lookup"><span data-stu-id="34e7c-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="34e7c-114">Por exemplo, se os eventos forem gerados em horários diferentes, de acordo com as especificações da interface, será possível associar cada evento a uma implementação separada na classe.</span><span class="sxs-lookup"><span data-stu-id="34e7c-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="34e7c-115">No exemplo a seguir, os assinantes determinam qual evento `OnDraw` receberão ao converter a referência de forma para um `IShape` ou um `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="34e7c-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a><span data-ttu-id="34e7c-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="34e7c-116">See also</span></span>

- [<span data-ttu-id="34e7c-117">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="34e7c-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="34e7c-118">Eventos</span><span class="sxs-lookup"><span data-stu-id="34e7c-118">Events</span></span>](./index.md)
- [<span data-ttu-id="34e7c-119">Delega</span><span class="sxs-lookup"><span data-stu-id="34e7c-119">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="34e7c-120">Implementação explícita da interface</span><span class="sxs-lookup"><span data-stu-id="34e7c-120">Explicit Interface Implementation</span></span>](../interfaces/explicit-interface-implementation.md)
- [<span data-ttu-id="34e7c-121">Como acionar eventos de classe base em classes derivadas</span><span class="sxs-lookup"><span data-stu-id="34e7c-121">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)
