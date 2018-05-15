---
title: Como substituir o método OnRender do painel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
ms.openlocfilehash: e591bc195d3b0ba58002bda42ddb3e9ed35d312e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-override-the-panel-onrender-method"></a><span data-ttu-id="6a492-102">Como substituir o método OnRender do painel</span><span class="sxs-lookup"><span data-stu-id="6a492-102">How to: Override the Panel OnRender Method</span></span>
<span data-ttu-id="6a492-103">Este exemplo mostra como substituir o <xref:System.Windows.Controls.Panel.OnRender%2A> método <xref:System.Windows.Controls.Panel> para adicionar efeitos gráficos personalizados a um elemento de layout.</span><span class="sxs-lookup"><span data-stu-id="6a492-103">This example shows how to override the <xref:System.Windows.Controls.Panel.OnRender%2A> method of <xref:System.Windows.Controls.Panel> in order to add custom graphical effects to a layout element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a492-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6a492-104">Example</span></span>  
 <span data-ttu-id="6a492-105">Use o <xref:System.Windows.Controls.Panel.OnRender%2A> método para adicionar efeitos gráficos a um elemento de painel renderizado.</span><span class="sxs-lookup"><span data-stu-id="6a492-105">Use the <xref:System.Windows.Controls.Panel.OnRender%2A> method in order to add graphical effects to a rendered panel element.</span></span> <span data-ttu-id="6a492-106">Por exemplo, você pode usar esse método para adicionar efeitos de plano de fundo ou borda personalizada.</span><span class="sxs-lookup"><span data-stu-id="6a492-106">For example, you can use this method to add custom border or background effects.</span></span> <span data-ttu-id="6a492-107">Um <xref:System.Windows.Media.DrawingContext> objeto é passado como um argumento, que fornece métodos para desenhar formas, texto, imagens ou vídeos.</span><span class="sxs-lookup"><span data-stu-id="6a492-107">A <xref:System.Windows.Media.DrawingContext> object is passed as an argument, which provides methods for drawing shapes, text, images, or videos.</span></span> <span data-ttu-id="6a492-108">Como resultado, esse método é útil para a personalização de um objeto de painel.</span><span class="sxs-lookup"><span data-stu-id="6a492-108">As a result, this method is useful for customization of a panel object.</span></span>  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6a492-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a492-109">See Also</span></span>  
 <xref:System.Windows.Controls.Panel>  
 [<span data-ttu-id="6a492-110">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="6a492-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="6a492-111">Exemplo de painel Radial personalizado</span><span class="sxs-lookup"><span data-stu-id="6a492-111">Custom Radial Panel Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159982)  
 [<span data-ttu-id="6a492-112">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="6a492-112">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
