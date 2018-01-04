---
title: Como alterar a cor de um elemento usando eventos de foco
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
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8b0e3f1b0a3287be89aba6e26f0621525c458a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="94ae0-102">Como alterar a cor de um elemento usando eventos de foco</span><span class="sxs-lookup"><span data-stu-id="94ae0-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="94ae0-103">Este exemplo mostra como alterar a cor de um elemento quando ele recebe e perde o foco usando o <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus> eventos.</span><span class="sxs-lookup"><span data-stu-id="94ae0-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="94ae0-104">Este exemplo consiste em um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de arquivo e um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="94ae0-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94ae0-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94ae0-105">Example</span></span>  
 <span data-ttu-id="94ae0-106">O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria a interface do usuário, que consiste em dois <xref:System.Windows.Controls.Button> objetos e anexa os manipuladores de eventos para o <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus> eventos para o <xref:System.Windows.Controls.Button> objetos.</span><span class="sxs-lookup"><span data-stu-id="94ae0-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="94ae0-107">O código a seguir cria o <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus> manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="94ae0-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="94ae0-108">Quando o <xref:System.Windows.Controls.Button> ganha o foco, teclado do <xref:System.Windows.Controls.Control.Background%2A> do <xref:System.Windows.Controls.Button> muda para vermelho.</span><span class="sxs-lookup"><span data-stu-id="94ae0-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="94ae0-109">Quando o <xref:System.Windows.Controls.Button> perde o foco do teclado, o <xref:System.Windows.Controls.Control.Background%2A> do <xref:System.Windows.Controls.Button> é alterada para branco.</span><span class="sxs-lookup"><span data-stu-id="94ae0-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="94ae0-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94ae0-110">See Also</span></span>  
 [<span data-ttu-id="94ae0-111">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="94ae0-111">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
