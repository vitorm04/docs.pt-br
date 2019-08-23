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
ms.openlocfilehash: d22a808ce3ab95e3b351408bf4cc372a335da553
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960194"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="2abea-102">Como: Particionar espaço usando o elemento DockPanel</span><span class="sxs-lookup"><span data-stu-id="2abea-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="2abea-103">O exemplo a seguir cria uma [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] estrutura simples usando <xref:System.Windows.Controls.DockPanel> um elemento.</span><span class="sxs-lookup"><span data-stu-id="2abea-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="2abea-104">O <xref:System.Windows.Controls.DockPanel> espaço disponível de partições para seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="2abea-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2abea-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2abea-105">Example</span></span>  
 <span data-ttu-id="2abea-106">Este exemplo usa a <xref:System.Windows.Controls.DockPanel.Dock%2A> Propriedade, que é uma propriedade anexada, para encaixar dois elementos <xref:System.Windows.Controls.Dock.Top> idênticos <xref:System.Windows.Controls.Border> no do espaço particionado.</span><span class="sxs-lookup"><span data-stu-id="2abea-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="2abea-107">Um terceiro <xref:System.Windows.Controls.Border> elemento é encaixado <xref:System.Windows.Controls.Dock.Left>no, com sua largura definida como 200 pixels.</span><span class="sxs-lookup"><span data-stu-id="2abea-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="2abea-108">Um quarto <xref:System.Windows.Controls.Border> é encaixado no <xref:System.Windows.Controls.Dock.Bottom> da tela.</span><span class="sxs-lookup"><span data-stu-id="2abea-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="2abea-109">O último <xref:System.Windows.Controls.Border> elemento preenche automaticamente o espaço restante.</span><span class="sxs-lookup"><span data-stu-id="2abea-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
> <span data-ttu-id="2abea-110">Por padrão, o último filho de um <xref:System.Windows.Controls.DockPanel> elemento preenche o espaço não alocado restante.</span><span class="sxs-lookup"><span data-stu-id="2abea-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="2abea-111">Se você não quiser esse comportamento, defina `LastChildFill="False"`.</span><span class="sxs-lookup"><span data-stu-id="2abea-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="2abea-112">O aplicativo compilado produz uma nova interface do usuário parecida com esta.</span><span class="sxs-lookup"><span data-stu-id="2abea-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="2abea-113">![Um cenário de DockPanel típico.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="2abea-113">![A typical DockPanel scenario.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2abea-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2abea-114">See also</span></span>

- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="2abea-115">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="2abea-115">Panels Overview</span></span>](panels-overview.md)
