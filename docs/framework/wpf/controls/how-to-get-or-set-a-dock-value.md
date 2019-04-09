---
title: 'Como: Obter ou definir um valor de encaixe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
ms.openlocfilehash: fb6c8a7d62aa09a6e1d82cb4079d1425a7f39f8c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160726"
---
# <a name="how-to-get-or-set-a-dock-value"></a><span data-ttu-id="3dd38-102">Como: Obter ou definir um valor de encaixe</span><span class="sxs-lookup"><span data-stu-id="3dd38-102">How to: Get or Set a Dock Value</span></span>
<span data-ttu-id="3dd38-103">O exemplo a seguir mostra como atribuir um <xref:System.Windows.Controls.Dock> valor para um objeto.</span><span class="sxs-lookup"><span data-stu-id="3dd38-103">The following example shows how to assign a <xref:System.Windows.Controls.Dock> value for an object.</span></span> <span data-ttu-id="3dd38-104">O exemplo usa o <xref:System.Windows.Controls.DockPanel.GetDock%2A> e <xref:System.Windows.Controls.DockPanel.SetDock%2A> métodos de <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="3dd38-104">The example uses the <xref:System.Windows.Controls.DockPanel.GetDock%2A> and <xref:System.Windows.Controls.DockPanel.SetDock%2A> methods of <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dd38-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3dd38-105">Example</span></span>  
 <span data-ttu-id="3dd38-106">O exemplo cria uma instância das <xref:System.Windows.Controls.TextBlock> elemento, `txt1`e atribui uma <xref:System.Windows.Controls.Dock> valor de `Top` usando o <xref:System.Windows.Controls.DockPanel.SetDock%2A> método de <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="3dd38-106">The example creates an instance of the <xref:System.Windows.Controls.TextBlock> element, `txt1`, and assigns a <xref:System.Windows.Controls.Dock> value of `Top` by using the <xref:System.Windows.Controls.DockPanel.SetDock%2A> method of <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="3dd38-107">Ele, em seguida, anexa o valor da <xref:System.Windows.Controls.Dock> propriedade para o <xref:System.Windows.Controls.TextBlock.Text%2A> da <xref:System.Windows.Controls.TextBlock> elemento usando o <xref:System.Windows.Controls.DockPanel.GetDock%2A> método.</span><span class="sxs-lookup"><span data-stu-id="3dd38-107">It then appends the value of the <xref:System.Windows.Controls.Dock> property to the <xref:System.Windows.Controls.TextBlock.Text%2A> of the <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.DockPanel.GetDock%2A> method.</span></span> <span data-ttu-id="3dd38-108">Por fim, o exemplo adiciona o <xref:System.Windows.Controls.TextBlock> elemento para o pai <xref:System.Windows.Controls.DockPanel>, `dp1`.</span><span class="sxs-lookup"><span data-stu-id="3dd38-108">Finally, the example adds the <xref:System.Windows.Controls.TextBlock> element to the parent <xref:System.Windows.Controls.DockPanel>, `dp1`.</span></span>  
  
 [!code-csharp[DockPanelSetDock#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3dd38-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3dd38-109">See also</span></span>

- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.DockPanel.GetDock%2A>
- <xref:System.Windows.Controls.DockPanel.SetDock%2A>
- [<span data-ttu-id="3dd38-110">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="3dd38-110">Panels Overview</span></span>](panels-overview.md)
