---
title: 'Como: Alterar a cor de um elemento usando eventos de foco'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: ad5ba8490f4b98512d539f5ae9c72b03333aca69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547008"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="2b598-102">Como: Alterar a cor de um elemento usando eventos de foco</span><span class="sxs-lookup"><span data-stu-id="2b598-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="2b598-103">Este exemplo mostra como alterar a cor de um elemento quando ele recebe e perde o foco usando o <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus> eventos.</span><span class="sxs-lookup"><span data-stu-id="2b598-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="2b598-104">Esse exemplo consiste em um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de arquivo e um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="2b598-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b598-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b598-105">Example</span></span>  
 <span data-ttu-id="2b598-106">O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria a interface de usuário, que consiste em dois <xref:System.Windows.Controls.Button> objetos e anexa os manipuladores de eventos para o <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus> eventos para o <xref:System.Windows.Controls.Button> objetos.</span><span class="sxs-lookup"><span data-stu-id="2b598-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="2b598-107">O código a seguir cria o <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus> manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="2b598-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="2b598-108">Quando o <xref:System.Windows.Controls.Button> ganhos de foco de teclado, o <xref:System.Windows.Controls.Control.Background%2A> da <xref:System.Windows.Controls.Button> muda para vermelho.</span><span class="sxs-lookup"><span data-stu-id="2b598-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="2b598-109">Quando o <xref:System.Windows.Controls.Button> perde o foco do teclado, o <xref:System.Windows.Controls.Control.Background%2A> da <xref:System.Windows.Controls.Button> é alterada de volta para branco.</span><span class="sxs-lookup"><span data-stu-id="2b598-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="2b598-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b598-110">See also</span></span>
- [<span data-ttu-id="2b598-111">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="2b598-111">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
