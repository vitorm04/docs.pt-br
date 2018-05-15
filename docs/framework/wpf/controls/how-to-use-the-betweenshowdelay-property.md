---
title: Como usar a propriedade BetweenShowDelay
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: 7d48fb859ec6d37abd2490bc718d58cbdaa67f13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-betweenshowdelay-property"></a><span data-ttu-id="c05c2-102">Como usar a propriedade BetweenShowDelay</span><span class="sxs-lookup"><span data-stu-id="c05c2-102">How to: Use the BetweenShowDelay Property</span></span>
<span data-ttu-id="c05c2-103">Este exemplo mostra como usar o <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriedade de tempo para que apareçam dicas de ferramentas rapidamente — com pouco ou nenhum atraso — quando um usuário move o ponteiro do mouse de uma dica de ferramenta diretamente para outra.</span><span class="sxs-lookup"><span data-stu-id="c05c2-103">This example shows how to use the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> time property so that tooltips appear quickly—with little or no delay—when a user moves the mouse pointer from one tooltip directly to another.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c05c2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c05c2-104">Example</span></span>  
 <span data-ttu-id="c05c2-105">No exemplo a seguir, o <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> propriedade é definida como um segundo (1000 milissegundos) e o <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> é definido como dois segundos (2000 milissegundos) para as dicas de ferramentas de ambos <xref:System.Windows.Shapes.Ellipse> controles.</span><span class="sxs-lookup"><span data-stu-id="c05c2-105">In the following example, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> property is set to one second (1000 milliseconds) and the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> is set to two seconds (2000 milliseconds) for the tooltips of both <xref:System.Windows.Shapes.Ellipse> controls.</span></span> <span data-ttu-id="c05c2-106">Se você exibir a dica de ferramentas para uma das elipses e mover o ponteiro do mouse para outra elipse dentro de dois segundos e pausar nela, a dica de ferramenta da segunda elipse será exibida imediatamente.</span><span class="sxs-lookup"><span data-stu-id="c05c2-106">If you display the tooltip for one of the ellipses and then move the mouse pointer to another ellipse within two seconds and pause on it, the tooltip of the second ellipse displays immediately.</span></span>  
  
 <span data-ttu-id="c05c2-107">Em qualquer um dos cenários a seguir, o <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> se aplica, que faz com que a dica de ferramenta para a segunda elipse espere um segundo antes que ele apareça:</span><span class="sxs-lookup"><span data-stu-id="c05c2-107">In either of the following scenarios, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> applies, which causes the tooltip for the second ellipse to wait one second before it appears:</span></span>  
  
-   <span data-ttu-id="c05c2-108">Se o tempo levado para mover para o segundo botão for maior do que dois segundos.</span><span class="sxs-lookup"><span data-stu-id="c05c2-108">If the time it takes to move to the second button is more than two seconds.</span></span>  
  
-   <span data-ttu-id="c05c2-109">Se a dica de ferramenta não estiver visível no início do intervalo de tempo para a primeira elipse.</span><span class="sxs-lookup"><span data-stu-id="c05c2-109">If the tooltip is not visible at the beginning of the time interval for the first ellipse.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="c05c2-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c05c2-110">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="c05c2-111">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="c05c2-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="c05c2-112">Visão geral de ToolTip</span><span class="sxs-lookup"><span data-stu-id="c05c2-112">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)
