---
title: "Como criar um efeito de sobreposição usando eventos"
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
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fc65c9342cc86d4ceebd65e91c05cc1bea464e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="f8a77-102">Como criar um efeito de sobreposição usando eventos</span><span class="sxs-lookup"><span data-stu-id="f8a77-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="f8a77-103">Este exemplo mostra como alterar a cor de um elemento quando o ponteiro do mouse entra e sai da área ocupada pelo elemento.</span><span class="sxs-lookup"><span data-stu-id="f8a77-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="f8a77-104">Este exemplo consiste em um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de arquivo e um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="f8a77-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8a77-105">Este exemplo demonstra como usar eventos, mas a maneira recomendada para atingir o mesmo efeito é usar um <xref:System.Windows.Trigger> em um estilo.</span><span class="sxs-lookup"><span data-stu-id="f8a77-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="f8a77-106">Para obter mais informações, consulte [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="f8a77-106">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8a77-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f8a77-107">Example</span></span>  
 <span data-ttu-id="f8a77-108">O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria a interface do usuário, que consiste em <xref:System.Windows.Controls.Border> em torno de um <xref:System.Windows.Controls.TextBlock>e anexa o <xref:System.Windows.Input.Mouse.MouseEnter> e <xref:System.Windows.UIElement.MouseLeave> manipuladores de eventos para o <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="f8a77-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="f8a77-109">O código a seguir cria o <xref:System.Windows.UIElement.MouseEnter> e <xref:System.Windows.UIElement.MouseLeave> manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="f8a77-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="f8a77-110">Quando o ponteiro do mouse entra o <xref:System.Windows.Controls.Border>, plano de fundo do <xref:System.Windows.Controls.Border> muda para vermelho.</span><span class="sxs-lookup"><span data-stu-id="f8a77-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="f8a77-111">Quando o ponteiro do mouse deixa o <xref:System.Windows.Controls.Border>, plano de fundo do <xref:System.Windows.Controls.Border> é alterada para branco.</span><span class="sxs-lookup"><span data-stu-id="f8a77-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
