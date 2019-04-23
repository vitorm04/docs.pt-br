---
title: 'Como: Inverter um UIElement horizontal ou verticalmente'
ms.date: 03/30/2017
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
ms.openlocfilehash: 6b3da322493d17e4f8e36a35b9a0e40fdc9dc685
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215515"
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a><span data-ttu-id="8ca1d-102">Como: Inverter um UIElement horizontal ou verticalmente</span><span class="sxs-lookup"><span data-stu-id="8ca1d-102">How to: Flip a UIElement Horizontally or Vertically</span></span>
<span data-ttu-id="8ca1d-103">Este exemplo mostra como usar um <xref:System.Windows.Media.ScaleTransform> inverter um <xref:System.Windows.UIElement> horizontal ou verticalmente.</span><span class="sxs-lookup"><span data-stu-id="8ca1d-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to flip a <xref:System.Windows.UIElement> horizontally or vertically.</span></span> <span data-ttu-id="8ca1d-104">Neste exemplo, uma <xref:System.Windows.Controls.Button> controle (um tipo de <xref:System.Windows.UIElement>) é invertido aplicando um <xref:System.Windows.Media.ScaleTransform> ao seu <xref:System.Windows.UIElement.RenderTransform%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8ca1d-104">In this example, a <xref:System.Windows.Controls.Button> control (a type of <xref:System.Windows.UIElement>) is flipped by applying a <xref:System.Windows.Media.ScaleTransform> to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ca1d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ca1d-105">Example</span></span>  
 <span data-ttu-id="8ca1d-106">A ilustração a seguir mostra o botão a ser invertido.</span><span class="sxs-lookup"><span data-stu-id="8ca1d-106">The following illustration shows the button to flip.</span></span>  
  
 <span data-ttu-id="8ca1d-107">![Um botão sem transformação](./media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span><span class="sxs-lookup"><span data-stu-id="8ca1d-107">![A button with no transform](./media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span></span>  
<span data-ttu-id="8ca1d-108">O UIElement a ser invertido</span><span class="sxs-lookup"><span data-stu-id="8ca1d-108">The UIElement to flip</span></span>  
  
 <span data-ttu-id="8ca1d-109">O exemplo a seguir mostra o código que cria o botão.</span><span class="sxs-lookup"><span data-stu-id="8ca1d-109">The following shows the code that creates the button.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a><span data-ttu-id="8ca1d-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ca1d-110">Example</span></span>  
 <span data-ttu-id="8ca1d-111">Para inverter o botão horizontalmente, crie uma <xref:System.Windows.Media.ScaleTransform> e defina seu <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> propriedade como -1.</span><span class="sxs-lookup"><span data-stu-id="8ca1d-111">To flip the button horizontally, create a <xref:System.Windows.Media.ScaleTransform> and set its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property to -1.</span></span> <span data-ttu-id="8ca1d-112">Aplicar a <xref:System.Windows.Media.ScaleTransform> do botão <xref:System.Windows.UIElement.RenderTransform%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8ca1d-112">Apply the <xref:System.Windows.Media.ScaleTransform> to the button's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 <span data-ttu-id="8ca1d-113">![Um botão invertido horizontalmente sobre &#40;0,0&#41;](./media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span><span class="sxs-lookup"><span data-stu-id="8ca1d-113">![A button flipped horizontally about &#40;0,0&#41;](./media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span></span>  
<span data-ttu-id="8ca1d-114">O botão após a aplicação de ScaleTransform</span><span class="sxs-lookup"><span data-stu-id="8ca1d-114">The button after applying the ScaleTransform</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ca1d-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ca1d-115">Example</span></span>  
 <span data-ttu-id="8ca1d-116">Como você pode ver na ilustração anterior, o botão foi invertido, mas também foi movido.</span><span class="sxs-lookup"><span data-stu-id="8ca1d-116">As you can see from the previous illustration, the button was flipped, but it was also moved.</span></span> <span data-ttu-id="8ca1d-117">Isso ocorre porque o botão foi invertido no seu canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="8ca1d-117">That's because the button was flipped from its top left corner.</span></span> <span data-ttu-id="8ca1d-118">Para inverter o botão no lugar, você deseja aplicar o <xref:System.Windows.Media.ScaleTransform> ao seu centro, não a seu canto.</span><span class="sxs-lookup"><span data-stu-id="8ca1d-118">To flip the button in place, you want to apply the <xref:System.Windows.Media.ScaleTransform> to its center, not its corner.</span></span> <span data-ttu-id="8ca1d-119">Uma maneira fácil de aplicar a <xref:System.Windows.Media.ScaleTransform> aos botões center é definir o botão <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade como 0,5, 0,5.</span><span class="sxs-lookup"><span data-stu-id="8ca1d-119">An easy way to apply the <xref:System.Windows.Media.ScaleTransform> to the buttons center is to set the button's <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to 0.5, 0.5.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 <span data-ttu-id="8ca1d-120">![Um botão invertido horizontalmente sobre seu centro](./media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="8ca1d-120">![A button flipped horizontally about its center](./media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span></span>  
<span data-ttu-id="8ca1d-121">O botão com um RenderTransformOrigin de 0,5, 0,5</span><span class="sxs-lookup"><span data-stu-id="8ca1d-121">The button with a RenderTransformOrigin of 0.5, 0.5</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ca1d-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ca1d-122">Example</span></span>  
 <span data-ttu-id="8ca1d-123">Para Inverter verticalmente o botão, defina a <xref:System.Windows.Media.ScaleTransform> do objeto <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriedade em vez de seu <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8ca1d-123">To flip the button vertically, set the <xref:System.Windows.Media.ScaleTransform> object's <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> property instead of its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 <span data-ttu-id="8ca1d-124">![Um botão invertido verticalmente sobre seu centro](./media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="8ca1d-124">![A button flipped vertically about its center](./media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span></span>  
<span data-ttu-id="8ca1d-125">O botão invertido verticalmente</span><span class="sxs-lookup"><span data-stu-id="8ca1d-125">The vertically flipped button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca1d-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ca1d-126">See also</span></span>

- [<span data-ttu-id="8ca1d-127">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="8ca1d-127">Transforms Overview</span></span>](../graphics-multimedia/transforms-overview.md)
