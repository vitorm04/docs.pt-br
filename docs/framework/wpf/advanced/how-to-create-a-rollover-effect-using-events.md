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
ms.openlocfilehash: 806056397200fa5c567e83227499ba721544f523
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005184"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="20ad7-102">Como: Criar um efeito de sobreposição usando eventos</span><span class="sxs-lookup"><span data-stu-id="20ad7-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="20ad7-103">Este exemplo mostra como alterar a cor de um elemento conforme o ponteiro do mouse entra e sai da área ocupada pelo elemento.</span><span class="sxs-lookup"><span data-stu-id="20ad7-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="20ad7-104">Este exemplo consiste em um arquivo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="20ad7-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20ad7-105">Este exemplo demonstra como usar eventos, mas a maneira recomendada para atingir esse mesmo efeito é usar um <xref:System.Windows.Trigger> em um estilo.</span><span class="sxs-lookup"><span data-stu-id="20ad7-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="20ad7-106">Para obter mais informações, consulte [Estilo e modelagem](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="20ad7-106">For more information, see [Styling and Templating](../controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="20ad7-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="20ad7-107">Example</span></span>  
 <span data-ttu-id="20ad7-108">O XAML a seguir cria a interface do usuário, que consiste em <xref:System.Windows.Controls.Border> em um <xref:System.Windows.Controls.TextBlock> e anexa os manipuladores de eventos <xref:System.Windows.Input.Mouse.MouseEnter> e <xref:System.Windows.UIElement.MouseLeave> ao <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="20ad7-108">The following XAML creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="20ad7-109">O seguinte código por trás cria os manipuladores de eventos <xref:System.Windows.UIElement.MouseEnter> e <xref:System.Windows.UIElement.MouseLeave>.</span><span class="sxs-lookup"><span data-stu-id="20ad7-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="20ad7-110">Quando o ponteiro do mouse entra no <xref:System.Windows.Controls.Border>, o plano de fundo do <xref:System.Windows.Controls.Border> é alterado para vermelho.</span><span class="sxs-lookup"><span data-stu-id="20ad7-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="20ad7-111">Quando o ponteiro do mouse sai do <xref:System.Windows.Controls.Border>, o plano de fundo do <xref:System.Windows.Controls.Border> é alterado de volta para branco.</span><span class="sxs-lookup"><span data-stu-id="20ad7-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
