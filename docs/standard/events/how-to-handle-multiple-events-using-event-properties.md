---
title: "Como manipular vários eventos usando propriedades de evento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET Framework]
- multiple events [.NET Framework]
- event handling [.NET Framework], with multiple events
- events [.NET Framework], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c16918e715a93de8fdf164e75ce7be81511b71b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="6cd3b-102">Como manipular vários eventos usando propriedades de evento</span><span class="sxs-lookup"><span data-stu-id="6cd3b-102">How to: Handle Multiple Events Using Event Properties</span></span>
<span data-ttu-id="6cd3b-103">Para usar as propriedades de evento, você define as propriedades de evento na classe que gera os eventos e, em seguida, definir os representantes para as propriedades de evento nas classes que tratam os eventos.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-103">To use event properties, you define the event properties in the class that raises the events, and then set the delegates for the event properties in classes that handle the events.</span></span> <span data-ttu-id="6cd3b-104">Para implementar várias propriedades de evento em uma classe, a classe deve armazenar internamente e manter o representante definido para cada evento.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-104">To implement multiple event properties in a class, the class must internally store and maintain the delegate defined for each event.</span></span> <span data-ttu-id="6cd3b-105">Uma abordagem típica é implementar uma coleção representante que é indexada por uma chave de evento.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-105">A typical approach is to implement a delegate collection that is indexed by an event key.</span></span>  
  
 <span data-ttu-id="6cd3b-106">Para armazenar os representantes para cada evento, você pode usar o <xref:System.ComponentModel.EventHandlerList> de classe ou implementar sua própria coleção.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-106">To store the delegates for each event, you can use the <xref:System.ComponentModel.EventHandlerList> class, or implement your own collection.</span></span> <span data-ttu-id="6cd3b-107">A classe de coleção deve fornecer métodos de configuração, acessando e recuperar o delegado do manipulador de eventos com base na chave de evento.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-107">The collection class must provide methods for setting, accessing, and retrieving the event handler delegate based on the event key.</span></span> <span data-ttu-id="6cd3b-108">Por exemplo, você pode usar um <xref:System.Collections.Hashtable> classe ou derivar uma classe personalizada do <xref:System.Collections.DictionaryBase> classe.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-108">For example, you could use a <xref:System.Collections.Hashtable> class, or derive a custom class from the <xref:System.Collections.DictionaryBase> class.</span></span> <span data-ttu-id="6cd3b-109">Os detalhes da implementação da coleção representante não precise ser exposto fora de sua classe.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-109">The implementation details of the delegate collection do not need to be exposed outside your class.</span></span>  
  
 <span data-ttu-id="6cd3b-110">Cada propriedade de evento dentro da classe define um método de acessador add e um método de acessador remove.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-110">Each event property within the class defines an add accessor method and a remove accessor method.</span></span> <span data-ttu-id="6cd3b-111">O acessador de adicionar uma propriedade de evento adiciona a instância representante de entrada à coleção representante.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-111">The add accessor for an event property adds the input delegate instance to the delegate collection.</span></span> <span data-ttu-id="6cd3b-112">O acessador de remover uma propriedade de evento remove a instância representante de entrada da coleção representante.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-112">The remove accessor for an event property removes the input delegate instance from the delegate collection.</span></span> <span data-ttu-id="6cd3b-113">Acessadores de propriedade de evento usam a chave predefinida para a propriedade de evento para adicionar e remover instâncias da coleção representante.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-113">The event property accessors use the predefined key for the event property to add and remove instances from the delegate collection.</span></span>  
  
### <a name="to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="6cd3b-114">Como manipular vários eventos usando propriedades de evento</span><span class="sxs-lookup"><span data-stu-id="6cd3b-114">To handle multiple events using event properties</span></span>  
  
1.  <span data-ttu-id="6cd3b-115">Defina uma coleção representante dentro da classe que gera os eventos.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-115">Define a delegate collection within the class that raises the events.</span></span>  
  
2.  <span data-ttu-id="6cd3b-116">Defina uma chave para cada evento.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-116">Define a key for each event.</span></span>  
  
3.  <span data-ttu-id="6cd3b-117">Defina as propriedades de evento na classe que gera os eventos.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-117">Define the event properties in the class that raises the events.</span></span>  
  
4.  <span data-ttu-id="6cd3b-118">Use a coleção de representante para implementar a adicionar e remover os métodos acessadores para as propriedades do evento.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-118">Use the delegate collection to implement the add and remove accessor methods for the event properties.</span></span>  
  
5.  <span data-ttu-id="6cd3b-119">Use as propriedades de evento público para adicionar e remover delegados de manipulador de eventos em classes que tratam os eventos.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-119">Use the public event properties to add and remove event handler delegates in the classes that handle the events.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cd3b-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6cd3b-120">Example</span></span>  
 <span data-ttu-id="6cd3b-121">O exemplo c# a seguir implementa as propriedades do evento `MouseDown` e `MouseUp`usando um <xref:System.ComponentModel.EventHandlerList> para armazenar representante cada evento.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-121">The following C# example implements the event properties `MouseDown` and `MouseUp`, using an <xref:System.ComponentModel.EventHandlerList> to store each event's delegate.</span></span> <span data-ttu-id="6cd3b-122">As palavras-chave das construções de propriedade de evento estão em negrito.</span><span class="sxs-lookup"><span data-stu-id="6cd3b-122">The keywords of the event property constructs are in bold type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cd3b-123">Não há suporte para propriedades de evento em [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6cd3b-123">Event properties are not supported in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)].</span></span>  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="6cd3b-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cd3b-124">See Also</span></span>  
 <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>  
 [<span data-ttu-id="6cd3b-125">Eventos</span><span class="sxs-lookup"><span data-stu-id="6cd3b-125">Events</span></span>](../../../docs/standard/events/index.md)  
 <xref:System.Web.UI.Control.Events%2A>  
 [<span data-ttu-id="6cd3b-126">Como declarar eventos personalizados para conservar memória</span><span class="sxs-lookup"><span data-stu-id="6cd3b-126">How to: Declare Custom Events To Conserve Memory</span></span>](~/docs/visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
