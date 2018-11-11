---
title: Eventos (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 8923bb4263c6857e7c2e194851befdc48f33a89e
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50743934"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="f0d3d-102">Eventos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f0d3d-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="f0d3d-103">Eventos permitem que uma [classe](../../../csharp/language-reference/keywords/class.md) ou objeto notifique outras classes ou objetos quando algo interessante ocorre.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-103">Events enable a [class](../../../csharp/language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="f0d3d-104">A classe que envia (ou *aciona*) o evento é chamada de *editor* e as classes que recebem (ou *manipulam*) os eventos são chamadas *assinantes*.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="f0d3d-105">Em um aplicativo Windows Forms em C# ou Web típico, você assina eventos acionados pelos controles, como botões e caixas de listagem.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="f0d3d-106">Você pode usar o IDE (ambiente de desenvolvimento integrado) do Visual C# para procurar os eventos que um controle publica e selecionar aqueles que você deseja manipular.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="f0d3d-107">O IDE adiciona automaticamente um método de manipulador de eventos vazio e o código para assinar o evento.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-107">The IDE automatically adds an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="f0d3d-108">Para obter mais informações, consulte [Como realizar e cancelar a assinatura de eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="f0d3d-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="f0d3d-109">Visão geral sobre eventos</span><span class="sxs-lookup"><span data-stu-id="f0d3d-109">Events Overview</span></span>  
 <span data-ttu-id="f0d3d-110">Os eventos têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="f0d3d-110">Events have the following properties:</span></span>  
  
-   <span data-ttu-id="f0d3d-111">O editor determina quando um evento é acionado. Os assinantes determinam a ação que é executada em resposta ao evento.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
-   <span data-ttu-id="f0d3d-112">Um evento pode ter vários assinantes.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="f0d3d-113">Um assinante pode manipular vários eventos de vários publicadores.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
-   <span data-ttu-id="f0d3d-114">Eventos que não têm assinantes nunca são acionados.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-114">Events that have no subscribers are never raised.</span></span>  
  
-   <span data-ttu-id="f0d3d-115">Normalmente, os eventos são usados para sinalizar ações do usuário, como cliques de botão ou seleções de menu em interfaces gráficas do usuário.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
-   <span data-ttu-id="f0d3d-116">Quando um evento tem vários assinantes, os manipuladores de eventos são invocados sincronicamente quando um evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="f0d3d-117">Para invocar eventos de forma assíncrona, consulte [Chamando métodos síncronos assincronamente](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="f0d3d-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
-   <span data-ttu-id="f0d3d-118">Na biblioteca de classes do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], os eventos são baseados no delegado <xref:System.EventHandler> e na classe base <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-118">In the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f0d3d-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="f0d3d-119">Related Sections</span></span>  
 <span data-ttu-id="f0d3d-120">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="f0d3d-120">For more information, see:</span></span>  
  
-   [<span data-ttu-id="f0d3d-121">Como realizar e cancelar a assinatura de eventos</span><span class="sxs-lookup"><span data-stu-id="f0d3d-121">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [<span data-ttu-id="f0d3d-122">Como publicar eventos em conformidade com as diretrizes do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f0d3d-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [<span data-ttu-id="f0d3d-123">Como acionar eventos de classe base em classes derivadas</span><span class="sxs-lookup"><span data-stu-id="f0d3d-123">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [<span data-ttu-id="f0d3d-124">Como implementar eventos de interface</span><span class="sxs-lookup"><span data-stu-id="f0d3d-124">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="f0d3d-125">Como usar um dicionário para armazenar instâncias de eventos</span><span class="sxs-lookup"><span data-stu-id="f0d3d-125">How to: Use a Dictionary to Store Event Instances</span></span>](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [<span data-ttu-id="f0d3d-126">Como implementar acessadores de eventos personalizados</span><span class="sxs-lookup"><span data-stu-id="f0d3d-126">How to: Implement Custom Event Accessors</span></span>](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="f0d3d-127">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f0d3d-127">C# Language Specification</span></span>  

<span data-ttu-id="f0d3d-128">Para obter mais informações, veja [Eventos](~/_csharplang/spec/classes.md#events) na [Especificação da linguagem C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f0d3d-128">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="f0d3d-129">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-129">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="f0d3d-130">Capítulos do Livro em Destaque</span><span class="sxs-lookup"><span data-stu-id="f0d3d-130">Featured Book Chapters</span></span>  
 <span data-ttu-id="f0d3d-131">[Expressões lambda, eventos e delegados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) em [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="f0d3d-131">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="f0d3d-132">[Delegados e eventos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) em [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="f0d3d-132">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d3d-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="f0d3d-133">See Also</span></span>

- <xref:System.EventHandler>  
- [<span data-ttu-id="f0d3d-134">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f0d3d-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f0d3d-135">Delegados</span><span class="sxs-lookup"><span data-stu-id="f0d3d-135">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
- [<span data-ttu-id="f0d3d-136">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f0d3d-136">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
