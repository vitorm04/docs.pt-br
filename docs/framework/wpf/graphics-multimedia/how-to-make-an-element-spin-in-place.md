---
title: Como criar um giro do elemento in-loco
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a1b515822391de08ec8ed8ff0ff1f0086874dc02
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112070"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="b6932-102">Como criar um giro do elemento in-loco</span><span class="sxs-lookup"><span data-stu-id="b6932-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="b6932-103">Este exemplo mostra como fazer um <xref:System.Windows.Media.RotateTransform> elemento <xref:System.Windows.Media.Animation.DoubleAnimation>girar usando a e a .</span><span class="sxs-lookup"><span data-stu-id="b6932-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="b6932-104">O exemplo a <xref:System.Windows.Media.RotateTransform> seguir <xref:System.Windows.UIElement.RenderTransform%2A> aplica-se à propriedade do elemento.</span><span class="sxs-lookup"><span data-stu-id="b6932-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="b6932-105">O exemplo <xref:System.Windows.Media.Animation.DoubleAnimation> usa um <xref:System.Windows.Media.RotateTransform.Angle%2A> para <xref:System.Windows.Media.RotateTransform>animar o do .</span><span class="sxs-lookup"><span data-stu-id="b6932-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="b6932-106">Para fazer o elemento girar no <xref:System.Windows.UIElement.RenderTransformOrigin%2A> lugar, o exemplo define a propriedade do elemento ao ponto (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="b6932-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6932-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6932-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="b6932-108">Para a amostra completa, que inclui mais exemplos de transformação, consulte [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="b6932-108">For the complete sample, which includes more transformation examples, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6932-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="b6932-109">See also</span></span>

- [<span data-ttu-id="b6932-110">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="b6932-110">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="b6932-111">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="b6932-111">Transforms Overview</span></span>](transforms-overview.md)
