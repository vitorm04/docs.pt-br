---
title: Como escolher entre StackPanel e DockPanel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
ms.openlocfilehash: bdf4b38e67a7856136224368e86609c135e5ad6f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976436"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a><span data-ttu-id="473b0-102">Como escolher entre StackPanel e DockPanel</span><span class="sxs-lookup"><span data-stu-id="473b0-102">How to: Choose Between StackPanel and DockPanel</span></span>
<span data-ttu-id="473b0-103">Este exemplo mostra como escolher entre usar um <xref:System.Windows.Controls.StackPanel> ou um <xref:System.Windows.Controls.DockPanel> quando você empilha o conteúdo em uma <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="473b0-103">This example shows how to choose between using a <xref:System.Windows.Controls.StackPanel> or a <xref:System.Windows.Controls.DockPanel> when you stack content in a <xref:System.Windows.Controls.Panel>.</span></span>

## <a name="example"></a><span data-ttu-id="473b0-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="473b0-104">Example</span></span>
 <span data-ttu-id="473b0-105">Embora você possa usar <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.StackPanel> para empilhar elementos filho, os dois controles nem sempre produzem os mesmos resultados.</span><span class="sxs-lookup"><span data-stu-id="473b0-105">Although you can use either <xref:System.Windows.Controls.DockPanel> or <xref:System.Windows.Controls.StackPanel> to stack child elements, the two controls do not always produce the same results.</span></span> <span data-ttu-id="473b0-106">Por exemplo, a ordem em que você coloca elementos filho pode afetar o tamanho dos elementos filho em um <xref:System.Windows.Controls.DockPanel>, mas não em um <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="473b0-106">For example, the order that you place child elements can affect the size of child elements in a <xref:System.Windows.Controls.DockPanel> but not in a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="473b0-107">Esse comportamento diferente ocorre porque <xref:System.Windows.Controls.StackPanel> medidas na direção do empilhamento em [Double. PositiveInfinity](xref:System.Double.PositiveInfinity); no entanto, <xref:System.Windows.Controls.DockPanel> mede apenas o tamanho disponível.</span><span class="sxs-lookup"><span data-stu-id="473b0-107">This different behavior occurs because <xref:System.Windows.Controls.StackPanel> measures in the direction of stacking at [Double.PositiveInfinity](xref:System.Double.PositiveInfinity); however, <xref:System.Windows.Controls.DockPanel> measures only the available size.</span></span>

 <span data-ttu-id="473b0-108">O exemplo a seguir demonstra essa diferença importante entre <xref:System.Windows.Controls.DockPanel> e <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="473b0-108">The following example demonstrates this key difference between <xref:System.Windows.Controls.DockPanel> and <xref:System.Windows.Controls.StackPanel>.</span></span>

 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="473b0-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="473b0-109">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="473b0-110">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="473b0-110">Panels Overview</span></span>](panels-overview.md)
