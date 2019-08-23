---
title: 'Como: Criar um efeito de sobreposição usando eventos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 3996a3b9bb976dd5f2e5b675de3894bbaba7d9d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960382"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="933d9-102">Como: Criar um efeito de sobreposição usando eventos</span><span class="sxs-lookup"><span data-stu-id="933d9-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="933d9-103">Este exemplo mostra como alterar a cor de um elemento conforme o ponteiro do mouse entra e sai da área ocupada pelo elemento.</span><span class="sxs-lookup"><span data-stu-id="933d9-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="933d9-104">Este exemplo consiste em um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo e um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="933d9-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="933d9-105">Este exemplo demonstra como usar eventos, mas a maneira recomendada para atingir esse mesmo efeito é usar um <xref:System.Windows.Trigger> em um estilo.</span><span class="sxs-lookup"><span data-stu-id="933d9-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="933d9-106">Para obter mais informações, consulte [Estilo e modelagem](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="933d9-106">For more information, see [Styling and Templating](../controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="933d9-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="933d9-107">Example</span></span>  
 <span data-ttu-id="933d9-108">O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria a interface do usuário, que <xref:System.Windows.Controls.Border> consiste em um <xref:System.Windows.Controls.TextBlock>e anexa os manipuladores <xref:System.Windows.Input.Mouse.MouseEnter> de <xref:System.Windows.UIElement.MouseLeave> eventos e ao <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="933d9-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="933d9-109">O code-behind a seguir <xref:System.Windows.UIElement.MouseEnter> cria <xref:System.Windows.UIElement.MouseLeave> os manipuladores de eventos e.</span><span class="sxs-lookup"><span data-stu-id="933d9-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="933d9-110">Quando o ponteiro do mouse entra <xref:System.Windows.Controls.Border>no, o plano <xref:System.Windows.Controls.Border> de fundo do é alterado para vermelho.</span><span class="sxs-lookup"><span data-stu-id="933d9-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="933d9-111">Quando o ponteiro do mouse sai <xref:System.Windows.Controls.Border>do, o plano <xref:System.Windows.Controls.Border> de fundo do é alterado de volta para branco.</span><span class="sxs-lookup"><span data-stu-id="933d9-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
