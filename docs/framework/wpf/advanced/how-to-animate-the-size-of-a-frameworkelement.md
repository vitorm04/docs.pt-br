---
title: Como animar o tamanho de um FrameworkElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf31fa1a10748c3c2f6d239d041c72c57a148e1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a><span data-ttu-id="82ee8-102">Como animar o tamanho de um FrameworkElement</span><span class="sxs-lookup"><span data-stu-id="82ee8-102">How to: Animate the Size of a FrameworkElement</span></span>
<span data-ttu-id="82ee8-103">Para animar o tamanho de um <xref:System.Windows.FrameworkElement>, é possível animar ou seu <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades ou use uma imagem <xref:System.Windows.Media.ScaleTransform>.</span><span class="sxs-lookup"><span data-stu-id="82ee8-103">To animate the size of a <xref:System.Windows.FrameworkElement>, you can either animate its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties or use an animated <xref:System.Windows.Media.ScaleTransform>.</span></span>  
  
 <span data-ttu-id="82ee8-104">No exemplo a seguir anima o tamanho de dois botões usando estas duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="82ee8-104">In the following example animates the size of two buttons using these two approaches.</span></span> <span data-ttu-id="82ee8-105">Um botão é redimensionado pela animação seu <xref:System.Windows.FrameworkElement.Width%2A> propriedade e outro é redimensionado pela animação um <xref:System.Windows.Media.ScaleTransform> aplicadas ao seu <xref:System.Windows.UIElement.RenderTransform%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="82ee8-105">One button is resized by animating its <xref:System.Windows.FrameworkElement.Width%2A> property and another is resized by animating a <xref:System.Windows.Media.ScaleTransform> applied to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span> <span data-ttu-id="82ee8-106">Cada botão contém algum texto.</span><span class="sxs-lookup"><span data-stu-id="82ee8-106">Each button contains some text.</span></span> <span data-ttu-id="82ee8-107">Inicialmente, o texto parece o mesmo em ambos os botões, mas como os botões são redimensionados, o texto no segundo botão fica distorcido.</span><span class="sxs-lookup"><span data-stu-id="82ee8-107">Initially, the text appears the same in both buttons, but as the buttons are resized, the text in the second button becomes distorted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82ee8-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82ee8-108">Example</span></span>  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 <span data-ttu-id="82ee8-109">Quando você transforma um elemento, o elemento inteiro e seu conteúdo serão transformados.</span><span class="sxs-lookup"><span data-stu-id="82ee8-109">When you transform an element, the entire element and its contents are transformed.</span></span> <span data-ttu-id="82ee8-110">Quando você altera diretamente o tamanho de um elemento, como no caso do primeiro botão, o conteúdo do elemento não será redimensionado, a menos que seu tamanho e posição dependam do tamanho de seu elemento pai.</span><span class="sxs-lookup"><span data-stu-id="82ee8-110">When you directly alter the size of an element, as in the case of the first button, the element's contents are not resized unless their size and position depend on the size of their parent element.</span></span>  
  
 <span data-ttu-id="82ee8-111">O tamanho de um elemento de animação, aplicando uma transformação animada a sua <xref:System.Windows.UIElement.RenderTransform%2A> propriedade fornece melhor desempenho do que a animação seu <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> diretamente, porque o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade não aciona uma passagem de layout.</span><span class="sxs-lookup"><span data-stu-id="82ee8-111">Animating the size of an element by applying an animated transform to its <xref:System.Windows.UIElement.RenderTransform%2A> property provides better performance than animated its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> directly, because the <xref:System.Windows.UIElement.RenderTransform%2A> property does not trigger a layout pass.</span></span>  
  
 <span data-ttu-id="82ee8-112">Para obter mais informações sobre animação de propriedades, consulte [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="82ee8-112">For more information about animating properties, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="82ee8-113">Para obter mais informações sobre transformações, consulte a [Visão geral das transformações](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="82ee8-113">For more information about transforms, see the [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>
