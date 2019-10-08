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
ms.openlocfilehash: 5c59dc5f2f8f26fac69933f9ef641a3a51306619
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004829"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="e25d7-102">Como: Alterar a cor de um elemento usando eventos de foco</span><span class="sxs-lookup"><span data-stu-id="e25d7-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="e25d7-103">Este exemplo mostra como alterar a cor de um elemento quando ele é ganho e perde o foco usando os eventos <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="e25d7-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="e25d7-104">Este exemplo consiste em um arquivo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="e25d7-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e25d7-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e25d7-105">Example</span></span>  
 <span data-ttu-id="e25d7-106">O XAML a seguir cria a interface do usuário, que consiste em dois objetos <xref:System.Windows.Controls.Button> e anexa manipuladores de eventos para os eventos <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus> aos objetos <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="e25d7-106">The following XAML creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="e25d7-107">O seguinte código por trás cria os manipuladores de eventos <xref:System.Windows.UIElement.GotFocus> e <xref:System.Windows.UIElement.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="e25d7-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="e25d7-108">Quando o <xref:System.Windows.Controls.Button> ganha o foco do teclado, o <xref:System.Windows.Controls.Control.Background%2A> do <xref:System.Windows.Controls.Button> é alterado para vermelho.</span><span class="sxs-lookup"><span data-stu-id="e25d7-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="e25d7-109">Quando o <xref:System.Windows.Controls.Button> perde o foco do teclado, o <xref:System.Windows.Controls.Control.Background%2A> do <xref:System.Windows.Controls.Button> é alterado de volta para branco.</span><span class="sxs-lookup"><span data-stu-id="e25d7-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="e25d7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e25d7-110">See also</span></span>

- [<span data-ttu-id="e25d7-111">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="e25d7-111">Input Overview</span></span>](input-overview.md)
