---
title: Como obter ou definir um valor de encaixe
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
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ca4d7e753282a7c1d2236a70535e10d5109cd3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-or-set-a-dock-value"></a><span data-ttu-id="d6dfb-102">Como obter ou definir um valor de encaixe</span><span class="sxs-lookup"><span data-stu-id="d6dfb-102">How to: Get or Set a Dock Value</span></span>
<span data-ttu-id="d6dfb-103">O exemplo a seguir mostra como atribuir um <xref:System.Windows.Controls.Dock> valor para um objeto.</span><span class="sxs-lookup"><span data-stu-id="d6dfb-103">The following example shows how to assign a <xref:System.Windows.Controls.Dock> value for an object.</span></span> <span data-ttu-id="d6dfb-104">O exemplo usa o <xref:System.Windows.Controls.DockPanel.GetDock%2A> e <xref:System.Windows.Controls.DockPanel.SetDock%2A> métodos de <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="d6dfb-104">The example uses the <xref:System.Windows.Controls.DockPanel.GetDock%2A> and <xref:System.Windows.Controls.DockPanel.SetDock%2A> methods of <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6dfb-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6dfb-105">Example</span></span>  
 <span data-ttu-id="d6dfb-106">O exemplo cria uma instância do <xref:System.Windows.Controls.TextBlock> elemento, `txt1`e atribui um <xref:System.Windows.Controls.Dock> valor `Top` usando o <xref:System.Windows.Controls.DockPanel.SetDock%2A> método <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="d6dfb-106">The example creates an instance of the <xref:System.Windows.Controls.TextBlock> element, `txt1`, and assigns a <xref:System.Windows.Controls.Dock> value of `Top` by using the <xref:System.Windows.Controls.DockPanel.SetDock%2A> method of <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="d6dfb-107">Ele, em seguida, anexa o valor do <xref:System.Windows.Controls.Dock> propriedade para o <xref:System.Windows.Controls.TextBlock.Text%2A> do <xref:System.Windows.Controls.TextBlock> elemento usando o <xref:System.Windows.Controls.DockPanel.GetDock%2A> método.</span><span class="sxs-lookup"><span data-stu-id="d6dfb-107">It then appends the value of the <xref:System.Windows.Controls.Dock> property to the <xref:System.Windows.Controls.TextBlock.Text%2A> of the <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.DockPanel.GetDock%2A> method.</span></span> <span data-ttu-id="d6dfb-108">Finalmente, o exemplo adiciona o <xref:System.Windows.Controls.TextBlock> elemento pai <xref:System.Windows.Controls.DockPanel>, `dp1`.</span><span class="sxs-lookup"><span data-stu-id="d6dfb-108">Finally, the example adds the <xref:System.Windows.Controls.TextBlock> element to the parent <xref:System.Windows.Controls.DockPanel>, `dp1`.</span></span>  
  
 [!code-csharp[DockPanelSetDock#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d6dfb-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6dfb-109">See Also</span></span>  
 <xref:System.Windows.Controls.DockPanel>  
 <xref:System.Windows.Controls.DockPanel.GetDock%2A>  
 <xref:System.Windows.Controls.DockPanel.SetDock%2A>  
 [<span data-ttu-id="d6dfb-110">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="d6dfb-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
