---
title: "Eventos (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f714bded446e62ac6165d691d2404249275178e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="05a16-102">Eventos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="05a16-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="05a16-103">Eventos permitem que uma [classe](../../../csharp/language-reference/keywords/class.md) ou objeto notifique outras classes ou objetos quando algo interessante ocorre.</span><span class="sxs-lookup"><span data-stu-id="05a16-103">Events enable a [class](../../../csharp/language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="05a16-104">A classe que envia (ou *aciona*) o evento é chamada de *editor* e as classes que recebem (ou *manipulam*) os eventos são chamadas *assinantes*.</span><span class="sxs-lookup"><span data-stu-id="05a16-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="05a16-105">Em um aplicativo Windows Forms em C# ou Web típico, você assina eventos acionados pelos controles, como botões e caixas de listagem.</span><span class="sxs-lookup"><span data-stu-id="05a16-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="05a16-106">Você pode usar o IDE [!INCLUDE[csprcs](~/includes/csprcs-md.md)] (ambiente de desenvolvimento integrado) para procurar os eventos que um controle publica e selecionar aqueles que você deseja manipular.</span><span class="sxs-lookup"><span data-stu-id="05a16-106">You can use the [!INCLUDE[csprcs](~/includes/csprcs-md.md)] integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="05a16-107">O IDE adiciona automaticamente um método de manipulador de eventos vazio e o código para assinar o evento.</span><span class="sxs-lookup"><span data-stu-id="05a16-107">The IDE automatically adds an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="05a16-108">Para obter mais informações, consulte [Como realizar e cancelar a assinatura de eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="05a16-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="05a16-109">Visão geral sobre eventos</span><span class="sxs-lookup"><span data-stu-id="05a16-109">Events Overview</span></span>  
 <span data-ttu-id="05a16-110">Os eventos têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="05a16-110">Events have the following properties:</span></span>  
  
-   <span data-ttu-id="05a16-111">O editor determina quando um evento é acionado. Os assinantes determinam a ação que é executada em resposta ao evento.</span><span class="sxs-lookup"><span data-stu-id="05a16-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
-   <span data-ttu-id="05a16-112">Um evento pode ter vários assinantes.</span><span class="sxs-lookup"><span data-stu-id="05a16-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="05a16-113">Um assinante pode manipular vários eventos de vários publicadores.</span><span class="sxs-lookup"><span data-stu-id="05a16-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
-   <span data-ttu-id="05a16-114">Eventos que não têm assinantes nunca são acionados.</span><span class="sxs-lookup"><span data-stu-id="05a16-114">Events that have no subscribers are never raised.</span></span>  
  
-   <span data-ttu-id="05a16-115">Normalmente, os eventos são usados para sinalizar ações do usuário, como cliques de botão ou seleções de menu em interfaces gráficas do usuário.</span><span class="sxs-lookup"><span data-stu-id="05a16-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
-   <span data-ttu-id="05a16-116">Quando um evento tem vários assinantes, os manipuladores de eventos são invocados sincronicamente quando um evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="05a16-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="05a16-117">Para invocar eventos de forma assíncrona, consulte [Chamando métodos síncronos assincronamente](https://msdn.microsoft.com/library/2e08f6yc).</span><span class="sxs-lookup"><span data-stu-id="05a16-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](https://msdn.microsoft.com/library/2e08f6yc).</span></span>  
  
-   <span data-ttu-id="05a16-118">Na biblioteca de classes do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], os eventos são baseados no delegado <xref:System.EventHandler> e na classe base <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="05a16-118">In the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="05a16-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="05a16-119">Related Sections</span></span>  
 <span data-ttu-id="05a16-120">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="05a16-120">For more information, see:</span></span>  
  
-   [<span data-ttu-id="05a16-121">Como realizar e cancelar a assinatura de eventos</span><span class="sxs-lookup"><span data-stu-id="05a16-121">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [<span data-ttu-id="05a16-122">Como publicar eventos em conformidade com as diretrizes do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="05a16-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [<span data-ttu-id="05a16-123">Como acionar eventos de classe base em classes derivadas</span><span class="sxs-lookup"><span data-stu-id="05a16-123">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [<span data-ttu-id="05a16-124">Como implementar eventos de interface</span><span class="sxs-lookup"><span data-stu-id="05a16-124">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="05a16-125">Sincronização de Thread </span><span class="sxs-lookup"><span data-stu-id="05a16-125">Thread Synchronization</span></span>](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [<span data-ttu-id="05a16-126">Como usar um dicionário para armazenar instâncias de eventos</span><span class="sxs-lookup"><span data-stu-id="05a16-126">How to: Use a Dictionary to Store Event Instances</span></span>](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [<span data-ttu-id="05a16-127">Como implementar acessadores de eventos personalizados</span><span class="sxs-lookup"><span data-stu-id="05a16-127">How to: Implement Custom Event Accessors</span></span>](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="05a16-128">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="05a16-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="05a16-129">Capítulos do Livro em Destaque</span><span class="sxs-lookup"><span data-stu-id="05a16-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="05a16-130">[Expressões lambda, eventos e delegados](http://go.microsoft.com/fwlink/?LinkId=195395) em [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span><span class="sxs-lookup"><span data-stu-id="05a16-130">[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span></span>  
  
 <span data-ttu-id="05a16-131">[Delegados e eventos](http://go.microsoft.com/fwlink/?LinkId=195418) em [Learning C# 3.0: Master the fundamentals of C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)</span><span class="sxs-lookup"><span data-stu-id="05a16-131">[Delegates and Events](http://go.microsoft.com/fwlink/?LinkId=195418) in [Learning C# 3.0: Master the fundamentals of C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05a16-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05a16-132">See Also</span></span>  
 <xref:System.EventHandler>  
 [<span data-ttu-id="05a16-133">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="05a16-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="05a16-134">Delegados</span><span class="sxs-lookup"><span data-stu-id="05a16-134">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="05a16-135">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05a16-135">Creating Event Handlers in Windows Forms</span></span>](https://msdn.microsoft.com/library/dacysss4.aspx)  
 [<span data-ttu-id="05a16-136">Programação multi-threaded com o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="05a16-136">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](https://msdn.microsoft.com/library/hkasytyf)
