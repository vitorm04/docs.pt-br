---
title: Como animar um pop-up
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: 05b84eea7fe983340ebb8c5cdb20ff39eb2f0858
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553748"
---
# <a name="how-to-animate-a-popup"></a><span data-ttu-id="c36b7-102">Como animar um pop-up</span><span class="sxs-lookup"><span data-stu-id="c36b7-102">How to: Animate a Popup</span></span>
<span data-ttu-id="c36b7-103">Este exemplo mostra duas maneiras para animar uma <xref:System.Windows.Controls.Primitives.Popup> controle.</span><span class="sxs-lookup"><span data-stu-id="c36b7-103">This example shows two ways to animate a <xref:System.Windows.Controls.Primitives.Popup> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c36b7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c36b7-104">Example</span></span>  
 <span data-ttu-id="c36b7-105">O exemplo a seguir define o <xref:System.Windows.Controls.Primitives.PopupAnimation> propriedade com um valor de <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, que faz com que o <xref:System.Windows.Controls.Primitives.Popup> "deslize para dentro" quando ele for exibido.</span><span class="sxs-lookup"><span data-stu-id="c36b7-105">The following example sets the <xref:System.Windows.Controls.Primitives.PopupAnimation> property to a value of <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, which causes the <xref:System.Windows.Controls.Primitives.Popup> to "slide-in" when it appears.</span></span>  
  
 <span data-ttu-id="c36b7-106">Para girar o <xref:System.Windows.Controls.Primitives.Popup>, este exemplo atribui uma <xref:System.Windows.Media.RotateTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade o <xref:System.Windows.Controls.Canvas>, que é o elemento filho do <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="c36b7-106">In order to rotate the <xref:System.Windows.Controls.Primitives.Popup>, this example assigns a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property on the <xref:System.Windows.Controls.Canvas>, which is the child element of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  
  
 <span data-ttu-id="c36b7-107">Para que a transformação funcione corretamente, o exemplo deve definir a <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="c36b7-107">For the transform to work correctly, the example must set the <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> property to `true`.</span></span> <span data-ttu-id="c36b7-108">Além disso, o <xref:System.Windows.FrameworkElement.Margin%2A> no <xref:System.Windows.Controls.Canvas> conteúdo deve especificar espaço suficiente para o <xref:System.Windows.Controls.Primitives.Popup> para girar.</span><span class="sxs-lookup"><span data-stu-id="c36b7-108">In addition, the <xref:System.Windows.FrameworkElement.Margin%2A> on the <xref:System.Windows.Controls.Canvas> content must specify enough space for the <xref:System.Windows.Controls.Primitives.Popup> to rotate.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 <span data-ttu-id="c36b7-109">A exemplo a seguir mostra como um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento que ocorre quando um <xref:System.Windows.Controls.Button> é clicado, dispara o <xref:System.Windows.Media.Animation.Storyboard> que inicia a animação.</span><span class="sxs-lookup"><span data-stu-id="c36b7-109">The following example shows how a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which occurs when a <xref:System.Windows.Controls.Button> is clicked, triggers the <xref:System.Windows.Media.Animation.Storyboard> that starts the animation.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a><span data-ttu-id="c36b7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c36b7-110">See Also</span></span>  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Controls.Primitives.BulletDecorator>  
 <xref:System.Windows.Media.RotateTransform>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="c36b7-111">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="c36b7-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [<span data-ttu-id="c36b7-112">Visão geral do pop-up</span><span class="sxs-lookup"><span data-stu-id="c36b7-112">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)
