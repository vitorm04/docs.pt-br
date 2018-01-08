---
title: "Como implementar acessadores de eventos personalizados (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c27becec6b5d298c31198fe9470a65baa32e32bf
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="0edca-102">Como implementar acessadores de eventos personalizados (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="0edca-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="0edca-103">Um evento é um tipo especial de delegado multicast que só pode ser invocado de dentro da classe que ela está declarado.</span><span class="sxs-lookup"><span data-stu-id="0edca-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="0edca-104">O código cliente assina o evento ao fornecer uma referência a um método que deve ser invocado quando o evento for disparado.</span><span class="sxs-lookup"><span data-stu-id="0edca-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="0edca-105">Esses métodos são adicionados à lista de invocação do delegado por meio de acessadores de evento, que se assemelham aos acessadores de propriedade, com a exceção de que os acessadores de eventos são nomeados `add` e `remove`.</span><span class="sxs-lookup"><span data-stu-id="0edca-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="0edca-106">Na maioria dos casos, não é necessário fornecer acessadores de eventos personalizados.</span><span class="sxs-lookup"><span data-stu-id="0edca-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="0edca-107">Quando nenhum acessador de evento personalizado for fornecido no código, o compilador o adicionará automaticamente.</span><span class="sxs-lookup"><span data-stu-id="0edca-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="0edca-108">No entanto, em alguns casos será necessário fornecer um comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="0edca-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="0edca-109">Um caso desse tipo é mostrado no tópico [Como Implementar Eventos de Interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="0edca-109">One such case is shown in the topic [How to:  Implement Interface Events](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0edca-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0edca-110">Example</span></span>  
 <span data-ttu-id="0edca-111">O exemplo a seguir mostra como implementar os acessadores de eventos personalizados adicionar e remover.</span><span class="sxs-lookup"><span data-stu-id="0edca-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="0edca-112">Embora seja possível substituir qualquer código dentro dos acessadores, é recomendável que você bloqueie o evento antes de adicionar ou remover um novo método de manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="0edca-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
```csharp
event EventHandler IDrawingObject.OnDraw  
{  
    add  
    {  
        lock (PreDrawEvent)  
        {  
            PreDrawEvent += value;  
        }  
    }  
    remove  
    {  
        lock (PreDrawEvent)  
        {  
            PreDrawEvent -= value;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0edca-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0edca-113">See Also</span></span>  
 [<span data-ttu-id="0edca-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="0edca-114">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="0edca-115">event</span><span class="sxs-lookup"><span data-stu-id="0edca-115">event</span></span>](../../../csharp/language-reference/keywords/event.md)