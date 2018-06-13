---
title: Como inverter um UIElement horizontal ou verticalmente
ms.date: 03/30/2017
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
ms.openlocfilehash: 89dcf668f1fe361480dabdab227a35ea40c344a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544389"
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a><span data-ttu-id="5e379-102">Como inverter um UIElement horizontal ou verticalmente</span><span class="sxs-lookup"><span data-stu-id="5e379-102">How to: Flip a UIElement Horizontally or Vertically</span></span>
<span data-ttu-id="5e379-103">Este exemplo mostra como usar um <xref:System.Windows.Media.ScaleTransform> para inverter uma <xref:System.Windows.UIElement> horizontal ou verticalmente.</span><span class="sxs-lookup"><span data-stu-id="5e379-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to flip a <xref:System.Windows.UIElement> horizontally or vertically.</span></span> <span data-ttu-id="5e379-104">Neste exemplo, um <xref:System.Windows.Controls.Button> controle (um tipo de <xref:System.Windows.UIElement>) é invertido aplicando uma <xref:System.Windows.Media.ScaleTransform> para sua <xref:System.Windows.UIElement.RenderTransform%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5e379-104">In this example, a <xref:System.Windows.Controls.Button> control (a type of <xref:System.Windows.UIElement>) is flipped by applying a <xref:System.Windows.Media.ScaleTransform> to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e379-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e379-105">Example</span></span>  
 <span data-ttu-id="5e379-106">A ilustração a seguir mostra o botão a ser invertido.</span><span class="sxs-lookup"><span data-stu-id="5e379-106">The following illustration shows the button to flip.</span></span>  
  
 <span data-ttu-id="5e379-107">![Um botão sem transformação](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span><span class="sxs-lookup"><span data-stu-id="5e379-107">![A button with no transform](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span></span>  
<span data-ttu-id="5e379-108">O UIElement a ser invertido</span><span class="sxs-lookup"><span data-stu-id="5e379-108">The UIElement to flip</span></span>  
  
 <span data-ttu-id="5e379-109">O exemplo a seguir mostra o código que cria o botão.</span><span class="sxs-lookup"><span data-stu-id="5e379-109">The following shows the code that creates the button.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a><span data-ttu-id="5e379-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e379-110">Example</span></span>  
 <span data-ttu-id="5e379-111">Para inverter o botão horizontalmente, crie uma <xref:System.Windows.Media.ScaleTransform> e defina seu <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> propriedade como -1.</span><span class="sxs-lookup"><span data-stu-id="5e379-111">To flip the button horizontally, create a <xref:System.Windows.Media.ScaleTransform> and set its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property to -1.</span></span> <span data-ttu-id="5e379-112">Aplicar o <xref:System.Windows.Media.ScaleTransform> para o botão <xref:System.Windows.UIElement.RenderTransform%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5e379-112">Apply the <xref:System.Windows.Media.ScaleTransform> to the button's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 <span data-ttu-id="5e379-113">![Um botão invertido horizontalmente sobre &#40;0,0&#41;](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span><span class="sxs-lookup"><span data-stu-id="5e379-113">![A button flipped horizontally about &#40;0,0&#41;](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span></span>  
<span data-ttu-id="5e379-114">O botão após a aplicação de ScaleTransform</span><span class="sxs-lookup"><span data-stu-id="5e379-114">The button after applying the ScaleTransform</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e379-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e379-115">Example</span></span>  
 <span data-ttu-id="5e379-116">Como você pode ver na ilustração anterior, o botão foi invertido, mas também foi movido.</span><span class="sxs-lookup"><span data-stu-id="5e379-116">As you can see from the previous illustration, the button was flipped, but it was also moved.</span></span> <span data-ttu-id="5e379-117">Isso ocorre porque o botão foi invertido no seu canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="5e379-117">That's because the button was flipped from its top left corner.</span></span> <span data-ttu-id="5e379-118">Para inverter o botão no lugar, você deseja aplicar o <xref:System.Windows.Media.ScaleTransform> a seu centro, não a seu canto.</span><span class="sxs-lookup"><span data-stu-id="5e379-118">To flip the button in place, you want to apply the <xref:System.Windows.Media.ScaleTransform> to its center, not its corner.</span></span> <span data-ttu-id="5e379-119">Uma maneira fácil de aplicar o <xref:System.Windows.Media.ScaleTransform> aos botões center é definido no botão <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade como 0,5, 0,5.</span><span class="sxs-lookup"><span data-stu-id="5e379-119">An easy way to apply the <xref:System.Windows.Media.ScaleTransform> to the buttons center is to set the button's <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to 0.5, 0.5.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 <span data-ttu-id="5e379-120">![Um botão invertido horizontalmente sobre seu centro](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="5e379-120">![A button flipped horizontally about its center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span></span>  
<span data-ttu-id="5e379-121">O botão com um RenderTransformOrigin de 0,5, 0,5</span><span class="sxs-lookup"><span data-stu-id="5e379-121">The button with a RenderTransformOrigin of 0.5, 0.5</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e379-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e379-122">Example</span></span>  
 <span data-ttu-id="5e379-123">Para Inverter verticalmente o botão, defina a <xref:System.Windows.Media.ScaleTransform> do objeto <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriedade em vez de seu <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5e379-123">To flip the button vertically, set the <xref:System.Windows.Media.ScaleTransform> object's <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> property instead of its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 <span data-ttu-id="5e379-124">![Um botão invertido verticalmente sobre seu centro](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="5e379-124">![A button flipped vertically about its center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span></span>  
<span data-ttu-id="5e379-125">O botão invertido verticalmente</span><span class="sxs-lookup"><span data-stu-id="5e379-125">The vertically flipped button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e379-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e379-126">See Also</span></span>  
 [<span data-ttu-id="5e379-127">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="5e379-127">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
