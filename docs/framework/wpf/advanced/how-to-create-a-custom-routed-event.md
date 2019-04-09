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
ms.openlocfilehash: a3850875c8ca747f8709b55f8fe721d25be24304
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091467"
---
# <a name="how-to-create-a-custom-routed-event"></a><span data-ttu-id="2c677-102">Como: Criar um evento roteado personalizado</span><span class="sxs-lookup"><span data-stu-id="2c677-102">How to: Create a Custom Routed Event</span></span>
<span data-ttu-id="2c677-103">Para o evento personalizado dar suporte ao roteamento de eventos, você precisa registrar um <xref:System.Windows.RoutedEvent> usando o <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> método.</span><span class="sxs-lookup"><span data-stu-id="2c677-103">For your custom event to support event routing, you need to register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="2c677-104">Este exemplo demonstra as noções básicas da criação de um evento roteado personalizado.</span><span class="sxs-lookup"><span data-stu-id="2c677-104">This example demonstrates the basics of creating a custom routed event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c677-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c677-105">Example</span></span>  
 <span data-ttu-id="2c677-106">Como mostrado no exemplo a seguir, você primeiro registra um <xref:System.Windows.RoutedEvent> usando o <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> método.</span><span class="sxs-lookup"><span data-stu-id="2c677-106">As shown in the following example, you first register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="2c677-107">Por convenção, o <xref:System.Windows.RoutedEvent> nome do campo estático deve terminar com o sufixo ***evento***.</span><span class="sxs-lookup"><span data-stu-id="2c677-107">By convention, the <xref:System.Windows.RoutedEvent> static field name should end with the suffix ***Event***.</span></span> <span data-ttu-id="2c677-108">Neste exemplo, o nome do evento é `Tap` e a estratégia de roteamento do evento é <xref:System.Windows.RoutingStrategy.Bubble>.</span><span class="sxs-lookup"><span data-stu-id="2c677-108">In this example, the name of the event is `Tap` and the routing strategy of the event is <xref:System.Windows.RoutingStrategy.Bubble>.</span></span> <span data-ttu-id="2c677-109">Após a chamada de registro, você pode fornecer acessadores de evento de adição e remoção [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] para o evento.</span><span class="sxs-lookup"><span data-stu-id="2c677-109">After the registration call, you can provide add-and-remove [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event accessors for the event.</span></span>  
  
 <span data-ttu-id="2c677-110">Observe que, embora o evento seja gerado por meio do método virtual `OnTap` nesse exemplo específico, a maneira como você gera seu evento ou como ele responde às mudanças depende das suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="2c677-110">Note that even though the event is raised through the `OnTap` virtual method in this particular example, how you raise your event or how your event responds to changes depends on your needs.</span></span>  
  
 <span data-ttu-id="2c677-111">Observe também que esse exemplo basicamente implementa uma subclasse inteira de <xref:System.Windows.Controls.Button>; essa subclasse é criada como um assembly separado e, em seguida, instanciado como uma classe personalizada em um diferente [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] página.</span><span class="sxs-lookup"><span data-stu-id="2c677-111">Note also that this example basically implements an entire subclass of <xref:System.Windows.Controls.Button>; that subclass is built as a separate assembly and then instantiated as a custom class on a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="2c677-112">Isso serve é para ilustrar o conceito que controles de subclasse podem ser inseridos em árvores compostas por outros controles e que nessa situação, eventos personalizados nesses controles têm exatamente os mesmos recursos de roteamento de eventos que qualquer elemento [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nativo.</span><span class="sxs-lookup"><span data-stu-id="2c677-112">This is to illustrate the concept that subclassed controls can be inserted into trees composed of other controls, and that in this situation, custom events on these controls have the very same event routing capabilities as any native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] element does.</span></span>  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 <span data-ttu-id="2c677-113">Eventos por túnel são criados da mesma maneira, mas com <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> definido como <xref:System.Windows.RoutingStrategy.Tunnel> na chamada de registro.</span><span class="sxs-lookup"><span data-stu-id="2c677-113">Tunneling events are created the same way, but with <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> set to <xref:System.Windows.RoutingStrategy.Tunnel> in the registration call.</span></span> <span data-ttu-id="2c677-114">Por convenção, eventos de túnel em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são prefixados com a palavra “Visualização”.</span><span class="sxs-lookup"><span data-stu-id="2c677-114">By convention, tunneling events in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] are prefixed with the word "Preview".</span></span>  
  
 <span data-ttu-id="2c677-115">Para ver um exemplo de como eventos de propagação funcionam, consulte [Manipular um evento roteado](how-to-handle-a-routed-event.md).</span><span class="sxs-lookup"><span data-stu-id="2c677-115">To see an example of how bubbling events work, see [Handle a Routed Event](how-to-handle-a-routed-event.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c677-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c677-116">See also</span></span>

- [<span data-ttu-id="2c677-117">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="2c677-117">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="2c677-118">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="2c677-118">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="2c677-119">Visão geral da criação de controle</span><span class="sxs-lookup"><span data-stu-id="2c677-119">Control Authoring Overview</span></span>](../controls/control-authoring-overview.md)
