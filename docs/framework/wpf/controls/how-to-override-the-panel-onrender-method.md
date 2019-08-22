---
title: 'Como: Substituir o método OnRender do painel'
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
ms.openlocfilehash: 23c3353e130585ed83726816a467ca73f6aa9152
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666709"
---
# <a name="how-to-override-the-panel-onrender-method"></a><span data-ttu-id="2d53a-102">Como: Substituir o método OnRender do painel</span><span class="sxs-lookup"><span data-stu-id="2d53a-102">How to: Override the Panel OnRender Method</span></span>
<span data-ttu-id="2d53a-103">Este exemplo mostra como substituir o <xref:System.Windows.Controls.Panel.OnRender%2A> método de para adicionar efeitos gráficos personalizados a um elemento de <xref:System.Windows.Controls.Panel> layout.</span><span class="sxs-lookup"><span data-stu-id="2d53a-103">This example shows how to override the <xref:System.Windows.Controls.Panel.OnRender%2A> method of <xref:System.Windows.Controls.Panel> in order to add custom graphical effects to a layout element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d53a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2d53a-104">Example</span></span>  
 <span data-ttu-id="2d53a-105">Use o <xref:System.Windows.Controls.Panel.OnRender%2A> método para adicionar efeitos gráficos a um elemento do painel renderizado.</span><span class="sxs-lookup"><span data-stu-id="2d53a-105">Use the <xref:System.Windows.Controls.Panel.OnRender%2A> method in order to add graphical effects to a rendered panel element.</span></span> <span data-ttu-id="2d53a-106">Por exemplo, você pode usar esse método para adicionar efeitos de borda ou de plano de fundo personalizados.</span><span class="sxs-lookup"><span data-stu-id="2d53a-106">For example, you can use this method to add custom border or background effects.</span></span> <span data-ttu-id="2d53a-107">Um <xref:System.Windows.Media.DrawingContext> objeto é passado como um argumento, que fornece métodos para desenhar formas, texto, imagens ou vídeos.</span><span class="sxs-lookup"><span data-stu-id="2d53a-107">A <xref:System.Windows.Media.DrawingContext> object is passed as an argument, which provides methods for drawing shapes, text, images, or videos.</span></span> <span data-ttu-id="2d53a-108">Como resultado, esse método é útil para a personalização de um objeto de painel.</span><span class="sxs-lookup"><span data-stu-id="2d53a-108">As a result, this method is useful for customization of a panel object.</span></span>  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2d53a-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d53a-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="2d53a-110">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="2d53a-110">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="2d53a-111">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="2d53a-111">How-to Topics</span></span>](panel-how-to-topics.md)
