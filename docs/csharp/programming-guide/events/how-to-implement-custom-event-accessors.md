---
title: 'Como: implementar acessadores de eventos personalizados – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 8cb6f6f22282ef72f040431e525f1129b46e8c26
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200358"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="40af5-102">Como: implementar acessadores de eventos personalizados (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="40af5-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="40af5-103">Um evento é um tipo especial de delegado multicast que só pode ser invocado de dentro da classe que ela está declarado.</span><span class="sxs-lookup"><span data-stu-id="40af5-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="40af5-104">O código cliente assina o evento ao fornecer uma referência a um método que deve ser invocado quando o evento for disparado.</span><span class="sxs-lookup"><span data-stu-id="40af5-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="40af5-105">Esses métodos são adicionados à lista de invocação do delegado por meio de acessadores de evento, que se assemelham aos acessadores de propriedade, com a exceção de que os acessadores de eventos são nomeados `add` e `remove`.</span><span class="sxs-lookup"><span data-stu-id="40af5-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="40af5-106">Na maioria dos casos, não é necessário fornecer acessadores de eventos personalizados.</span><span class="sxs-lookup"><span data-stu-id="40af5-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="40af5-107">Quando nenhum acessador de evento personalizado for fornecido no código, o compilador o adicionará automaticamente.</span><span class="sxs-lookup"><span data-stu-id="40af5-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="40af5-108">No entanto, em alguns casos será necessário fornecer um comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="40af5-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="40af5-109">Um caso desse tipo é mostrado no tópico [Como  implementar eventos de interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="40af5-109">One such case is shown in the topic [How to:  Implement Interface Events](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40af5-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="40af5-110">Example</span></span>  
 <span data-ttu-id="40af5-111">O exemplo a seguir mostra como implementar os acessadores de eventos personalizados adicionar e remover.</span><span class="sxs-lookup"><span data-stu-id="40af5-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="40af5-112">Embora seja possível substituir qualquer código dentro dos acessadores, é recomendável que você bloqueie o evento antes de adicionar ou remover um novo método de manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="40af5-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="40af5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40af5-113">See also</span></span>

- [<span data-ttu-id="40af5-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="40af5-114">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="40af5-115">event</span><span class="sxs-lookup"><span data-stu-id="40af5-115">event</span></span>](../../../csharp/language-reference/keywords/event.md)
