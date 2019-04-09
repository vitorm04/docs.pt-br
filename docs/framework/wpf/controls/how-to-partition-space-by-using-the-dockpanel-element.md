---
title: 'Como: Particionar espaço usando o elemento DockPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
ms.openlocfilehash: ab51270644bf370944ebc933c765b40c528681c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158880"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="e2fbe-102">Como: Particionar espaço usando o elemento DockPanel</span><span class="sxs-lookup"><span data-stu-id="e2fbe-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="e2fbe-103">O exemplo a seguir cria um simples [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework usando um <xref:System.Windows.Controls.DockPanel> elemento.</span><span class="sxs-lookup"><span data-stu-id="e2fbe-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="e2fbe-104">O <xref:System.Windows.Controls.DockPanel> particiona o espaço disponível para seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="e2fbe-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2fbe-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2fbe-105">Example</span></span>  
 <span data-ttu-id="e2fbe-106">Este exemplo usa o <xref:System.Windows.Controls.DockPanel.Dock%2A> propriedade, que é uma propriedade anexada, para encaixar dois idênticos <xref:System.Windows.Controls.Border> elementos no <xref:System.Windows.Controls.Dock.Top> do espaço particionado.</span><span class="sxs-lookup"><span data-stu-id="e2fbe-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="e2fbe-107">Um terceiro <xref:System.Windows.Controls.Border> elemento é encaixado a <xref:System.Windows.Controls.Dock.Left>, com sua largura definida para 200 pixels.</span><span class="sxs-lookup"><span data-stu-id="e2fbe-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="e2fbe-108">Um quarto <xref:System.Windows.Controls.Border> é encaixado a <xref:System.Windows.Controls.Dock.Bottom> da tela.</span><span class="sxs-lookup"><span data-stu-id="e2fbe-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="e2fbe-109">A última <xref:System.Windows.Controls.Border> elemento preenche automaticamente o espaço restante.</span><span class="sxs-lookup"><span data-stu-id="e2fbe-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  <span data-ttu-id="e2fbe-110">Por padrão, o último filho de um <xref:System.Windows.Controls.DockPanel> elemento preenche o espaço não alocado restante.</span><span class="sxs-lookup"><span data-stu-id="e2fbe-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="e2fbe-111">Se você não quiser esse comportamento, defina `LastChildFill="False"`.</span><span class="sxs-lookup"><span data-stu-id="e2fbe-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="e2fbe-112">O aplicativo compilado produz uma nova interface do usuário que se parece com isso.</span><span class="sxs-lookup"><span data-stu-id="e2fbe-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="e2fbe-113">![Um cenário de DockPanel típico.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="e2fbe-113">![A typical DockPanel scenario.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2fbe-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2fbe-114">See also</span></span>

- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="e2fbe-115">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="e2fbe-115">Panels Overview</span></span>](panels-overview.md)
