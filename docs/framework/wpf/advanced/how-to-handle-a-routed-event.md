---
title: Como identificar um evento roteado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c491ff4e231d932b3714d2d059b52bad2502368c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-a-routed-event"></a><span data-ttu-id="638cb-102">Como identificar um evento roteado</span><span class="sxs-lookup"><span data-stu-id="638cb-102">How to: Handle a Routed Event</span></span>
<span data-ttu-id="638cb-103">Este exemplo mostra como os eventos de propagação funcionam e como escrever um manipulador que pode processar os dados de eventos roteados.</span><span class="sxs-lookup"><span data-stu-id="638cb-103">This example shows how bubbling events work and how to write a handler that can process the routed event data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="638cb-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="638cb-104">Example</span></span>  
 <span data-ttu-id="638cb-105">Em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], os elementos são organizados em uma estrutura de árvore de elementos.</span><span class="sxs-lookup"><span data-stu-id="638cb-105">In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elements are arranged in an element tree structure.</span></span> <span data-ttu-id="638cb-106">O elemento pai pode participar da manipulação de eventos que são inicialmente gerados por elementos filho na árvore de elementos.</span><span class="sxs-lookup"><span data-stu-id="638cb-106">The parent element can participate in the handling of events that are initially raised by child elements in the element tree.</span></span> <span data-ttu-id="638cb-107">Isso é possibilitado pelo roteamento de eventos.</span><span class="sxs-lookup"><span data-stu-id="638cb-107">This is possible because of event routing.</span></span>  
  
 <span data-ttu-id="638cb-108">Eventos roteados geralmente seguem uma das duas estratégias de roteamento, propagação ou túnel.</span><span class="sxs-lookup"><span data-stu-id="638cb-108">Routed events typically follow one of two routing strategies, bubbling or tunneling.</span></span> <span data-ttu-id="638cb-109">Este exemplo enfoca o evento e usa a <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> eventos para mostrar como roteamento funciona.</span><span class="sxs-lookup"><span data-stu-id="638cb-109">This example focuses on the bubbling event and uses the <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> event to show how routing works.</span></span>  
  
 <span data-ttu-id="638cb-110">O exemplo a seguir cria dois <xref:System.Windows.Controls.Button> controla e usa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributo sintaxe para anexar um manipulador de eventos a um elemento pai comum, que neste exemplo é <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="638cb-110">The following example creates two <xref:System.Windows.Controls.Button> controls and uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax to attach an event handler to a common parent element, which in this example is <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="638cb-111">Em vez de anexar manipuladores de eventos individuais para cada <xref:System.Windows.Controls.Button> elemento filho, o exemplo usa a sintaxe para anexar o manipulador de eventos para o <xref:System.Windows.Controls.StackPanel> elemento pai.</span><span class="sxs-lookup"><span data-stu-id="638cb-111">Instead of attaching individual event handlers for each <xref:System.Windows.Controls.Button> child element, the example uses attribute syntax to attach the event handler to the <xref:System.Windows.Controls.StackPanel> parent element.</span></span> <span data-ttu-id="638cb-112">Esse padrão de manipulação de eventos mostra como usar o roteamento de eventos como uma técnica para reduzir o número de elementos aos quais um manipulador está anexado.</span><span class="sxs-lookup"><span data-stu-id="638cb-112">This event-handling pattern shows how to use event routing as a technique for reducing the number of elements where a handler is attached.</span></span> <span data-ttu-id="638cb-113">Todos os eventos de bolha para cada <xref:System.Windows.Controls.Button> rota por meio do elemento pai.</span><span class="sxs-lookup"><span data-stu-id="638cb-113">All the bubbling events for each <xref:System.Windows.Controls.Button> route through the parent element.</span></span>  
  
 <span data-ttu-id="638cb-114">Observe que no pai <xref:System.Windows.Controls.StackPanel> elemento, o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> nome do evento especificado como o atributo é parcialmente qualificado ao nomear a <xref:System.Windows.Controls.Button> classe.</span><span class="sxs-lookup"><span data-stu-id="638cb-114">Note that on the parent <xref:System.Windows.Controls.StackPanel> element, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event name specified as the attribute is partially qualified by naming the <xref:System.Windows.Controls.Button> class.</span></span> <span data-ttu-id="638cb-115">O <xref:System.Windows.Controls.Button> classe é um <xref:System.Windows.Controls.Primitives.ButtonBase> derivado da classe que tem o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento na sua lista de membros.</span><span class="sxs-lookup"><span data-stu-id="638cb-115">The <xref:System.Windows.Controls.Button> class is a <xref:System.Windows.Controls.Primitives.ButtonBase> derived class that has the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in its members listing.</span></span> <span data-ttu-id="638cb-116">Essa técnica parcial de qualificação para anexar um manipulador de eventos será necessária se o evento que está sendo manipulado não existir nos membros de listagem do elemento ao qual o manipulador de eventos roteados está conectado.</span><span class="sxs-lookup"><span data-stu-id="638cb-116">This partial qualification technique for attaching an event handler is necessary if the event that is being handled does not exist in the members listing of the element where the routed event handler is attached.</span></span>  
  
 [!code-xaml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 <span data-ttu-id="638cb-117">A exemplo a seguir trata o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.</span><span class="sxs-lookup"><span data-stu-id="638cb-117">The following example handles the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  <span data-ttu-id="638cb-118">O exemplo informa qual elemento manipula o evento e qual elemento gera o evento.</span><span class="sxs-lookup"><span data-stu-id="638cb-118">The example reports which element handles the event and which element raises the event.</span></span> <span data-ttu-id="638cb-119">O manipulador de eventos é executado quando o usuário clica em um dos botões.</span><span class="sxs-lookup"><span data-stu-id="638cb-119">The event handler is executed when the user clicks either button.</span></span>  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="638cb-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="638cb-120">See Also</span></span>  
 <xref:System.Windows.RoutedEvent>  
 [<span data-ttu-id="638cb-121">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="638cb-121">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="638cb-122">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="638cb-122">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="638cb-123">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="638cb-123">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)  
 [<span data-ttu-id="638cb-124">Sintaxe XAML em detalhes</span><span class="sxs-lookup"><span data-stu-id="638cb-124">XAML Syntax In Detail</span></span>](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
