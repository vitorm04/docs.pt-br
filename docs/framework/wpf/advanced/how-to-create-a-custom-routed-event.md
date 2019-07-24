---
title: 'Como: Criar um evento roteado personalizado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: cbfb88af4e35e3f090248982bb14d6b7a3a03cef
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401472"
---
# <a name="how-to-create-a-custom-routed-event"></a><span data-ttu-id="d0ce2-102">Como: Criar um evento roteado personalizado</span><span class="sxs-lookup"><span data-stu-id="d0ce2-102">How to: Create a Custom Routed Event</span></span>
<span data-ttu-id="d0ce2-103">Para que seu evento personalizado dê suporte ao roteamento de eventos, você precisa <xref:System.Windows.RoutedEvent> registrar um <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> usando o método.</span><span class="sxs-lookup"><span data-stu-id="d0ce2-103">For your custom event to support event routing, you need to register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="d0ce2-104">Este exemplo demonstra as noções básicas da criação de um evento roteado personalizado.</span><span class="sxs-lookup"><span data-stu-id="d0ce2-104">This example demonstrates the basics of creating a custom routed event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0ce2-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0ce2-105">Example</span></span>  
 <span data-ttu-id="d0ce2-106">Conforme mostrado no exemplo a seguir, primeiro você registra um <xref:System.Windows.RoutedEvent> usando o <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> método.</span><span class="sxs-lookup"><span data-stu-id="d0ce2-106">As shown in the following example, you first register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="d0ce2-107">Por convenção, o <xref:System.Windows.RoutedEvent> nome do campo estático deve terminar com o ***evento***de sufixo.</span><span class="sxs-lookup"><span data-stu-id="d0ce2-107">By convention, the <xref:System.Windows.RoutedEvent> static field name should end with the suffix ***Event***.</span></span> <span data-ttu-id="d0ce2-108">Neste exemplo, o nome do evento é `Tap` e a estratégia de roteamento do evento é. <xref:System.Windows.RoutingStrategy.Bubble></span><span class="sxs-lookup"><span data-stu-id="d0ce2-108">In this example, the name of the event is `Tap` and the routing strategy of the event is <xref:System.Windows.RoutingStrategy.Bubble>.</span></span> <span data-ttu-id="d0ce2-109">Após a chamada de registro, você pode fornecer aos acessadores de eventos de adição e remoção Common Language Runtime (CLR) para o evento.</span><span class="sxs-lookup"><span data-stu-id="d0ce2-109">After the registration call, you can provide add-and-remove common language runtime (CLR) event accessors for the event.</span></span>  
  
 <span data-ttu-id="d0ce2-110">Observe que, embora o evento seja gerado por meio do método virtual `OnTap` nesse exemplo específico, a maneira como você gera seu evento ou como ele responde às mudanças depende das suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="d0ce2-110">Note that even though the event is raised through the `OnTap` virtual method in this particular example, how you raise your event or how your event responds to changes depends on your needs.</span></span>  
  
 <span data-ttu-id="d0ce2-111">Observe também que esse exemplo basicamente implementa uma subclasse inteira de <xref:System.Windows.Controls.Button>; essa subclasse é criada como um assembly separado e, em seguida, instanciada como uma classe personalizada em uma página separada. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0ce2-111">Note also that this example basically implements an entire subclass of <xref:System.Windows.Controls.Button>; that subclass is built as a separate assembly and then instantiated as a custom class on a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="d0ce2-112">Isso serve é para ilustrar o conceito que controles de subclasse podem ser inseridos em árvores compostas por outros controles e que nessa situação, eventos personalizados nesses controles têm exatamente os mesmos recursos de roteamento de eventos que qualquer elemento [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nativo.</span><span class="sxs-lookup"><span data-stu-id="d0ce2-112">This is to illustrate the concept that subclassed controls can be inserted into trees composed of other controls, and that in this situation, custom events on these controls have the very same event routing capabilities as any native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] element does.</span></span>  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 <span data-ttu-id="d0ce2-113">Os eventos de túnel são criados da mesma forma, mas <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> com definido <xref:System.Windows.RoutingStrategy.Tunnel> como na chamada de registro.</span><span class="sxs-lookup"><span data-stu-id="d0ce2-113">Tunneling events are created the same way, but with <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> set to <xref:System.Windows.RoutingStrategy.Tunnel> in the registration call.</span></span> <span data-ttu-id="d0ce2-114">Por convenção, eventos de túnel em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são prefixados com a palavra “Visualização”.</span><span class="sxs-lookup"><span data-stu-id="d0ce2-114">By convention, tunneling events in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] are prefixed with the word "Preview".</span></span>  
  
 <span data-ttu-id="d0ce2-115">Para ver um exemplo de como eventos de propagação funcionam, consulte [Manipular um evento roteado](how-to-handle-a-routed-event.md).</span><span class="sxs-lookup"><span data-stu-id="d0ce2-115">To see an example of how bubbling events work, see [Handle a Routed Event](how-to-handle-a-routed-event.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ce2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0ce2-116">See also</span></span>

- [<span data-ttu-id="d0ce2-117">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="d0ce2-117">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="d0ce2-118">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="d0ce2-118">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="d0ce2-119">Visão geral da criação de controle</span><span class="sxs-lookup"><span data-stu-id="d0ce2-119">Control Authoring Overview</span></span>](../controls/control-authoring-overview.md)
