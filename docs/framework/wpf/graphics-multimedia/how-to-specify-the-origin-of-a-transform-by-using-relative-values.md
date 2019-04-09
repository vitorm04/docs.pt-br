---
title: 'Como: Especificar a origem de uma transformação usando valores relativos'
ms.date: 03/30/2017
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
ms.openlocfilehash: 48b3b0df8dab8516873495a996074eae57ffe00f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082952"
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a><span data-ttu-id="9e910-102">Como: Especificar a origem de uma transformação usando valores relativos</span><span class="sxs-lookup"><span data-stu-id="9e910-102">How to: Specify the Origin of a Transform by Using Relative Values</span></span>
<span data-ttu-id="9e910-103">Este exemplo mostra como usar valores relativos para especificar a origem de um <xref:System.Windows.UIElement.RenderTransform%2A> que é aplicado a um <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="9e910-103">This example shows how to use relative values to specify the origin of a <xref:System.Windows.UIElement.RenderTransform%2A> that is applied to a <xref:System.Windows.FrameworkElement>.</span></span>  
  
 <span data-ttu-id="9e910-104">Quando você girar, dimensionar ou distorcer um <xref:System.Windows.FrameworkElement> usando o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade, a configuração padrão se aplica a transformação ao canto superior esquerdo do elemento.</span><span class="sxs-lookup"><span data-stu-id="9e910-104">When you rotate, scale, or skew a <xref:System.Windows.FrameworkElement> by using the <xref:System.Windows.UIElement.RenderTransform%2A> property, the default setting applies the transform to the upper-left corner of the element.</span></span> <span data-ttu-id="9e910-105">Se você deseja girar, dimensionar ou distorcer no centro do elemento, compense definindo o centro da transformação para o centro do elemento.</span><span class="sxs-lookup"><span data-stu-id="9e910-105">If you want to rotate, scale, or skew from the center of the element, you can compensate by setting the center of the transform to the center of the element.</span></span> <span data-ttu-id="9e910-106">No entanto, essa solução requer que você saiba o tamanho do elemento.</span><span class="sxs-lookup"><span data-stu-id="9e910-106">However, that solution requires that you know the size of the element.</span></span> <span data-ttu-id="9e910-107">Uma maneira mais fácil de aplicar uma transformação para o Centro de um elemento é definir sua <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade para (0,5, 0,5), em vez de definir um valor central na própria transformação.</span><span class="sxs-lookup"><span data-stu-id="9e910-107">An easier way of applying a transform to the center of an element is to set its <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to (0.5, 0.5), instead of setting a center value on the transform itself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e910-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e910-108">Example</span></span>  
 <span data-ttu-id="9e910-109">O exemplo a seguir usa uma <xref:System.Windows.Media.RotateTransform> girar um <xref:System.Windows.Controls.Button> 45 graus no sentido horário.</span><span class="sxs-lookup"><span data-stu-id="9e910-109">The following example uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise.</span></span> <span data-ttu-id="9e910-110">Porque o exemplo não especifica um centro, o botão gira sobre o ponto (0, 0), que é seu canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="9e910-110">Because the example does not specify a center, the button rotates about the point (0, 0), which is its upper-left corner.</span></span> <span data-ttu-id="9e910-111">O <xref:System.Windows.Media.RotateTransform> é aplicada para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9e910-111">The <xref:System.Windows.Media.RotateTransform> is applied to the <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="9e910-112">A ilustração a seguir mostra o resultado da transformação do seguinte exemplo.</span><span class="sxs-lookup"><span data-stu-id="9e910-112">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="9e910-113">![Um botão transformado com RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span><span class="sxs-lookup"><span data-stu-id="9e910-113">![A button transformed using RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span></span>  
<span data-ttu-id="9e910-114">Uma rotação de 45 graus no sentido horário usando a propriedade RenderTransform</span><span class="sxs-lookup"><span data-stu-id="9e910-114">A 45 degree clockwise rotation by using the RenderTransform property</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 <span data-ttu-id="9e910-115">O exemplo a seguir também usa um <xref:System.Windows.Media.RotateTransform> girar uma <xref:System.Windows.Controls.Button> 45 graus no sentido horário; no entanto, este exemplo define o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> do botão para (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="9e910-115">The following example also uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise; however, this example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> of the button to (0.5, 0.5).</span></span> <span data-ttu-id="9e910-116">Como resultado, a rotação é aplicada ao centro do botão em vez de seu canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="9e910-116">As a result, the rotation is applied to the center of the button instead of to the upper-left corner.</span></span>  
  
 <span data-ttu-id="9e910-117">A ilustração a seguir mostra o resultado da transformação do seguinte exemplo.</span><span class="sxs-lookup"><span data-stu-id="9e910-117">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="9e910-118">![Um botão transformado sobre seu centro](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span><span class="sxs-lookup"><span data-stu-id="9e910-118">![A button transformed about its center](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span></span>  
<span data-ttu-id="9e910-119">Uma rotação de 45 graus usando a propriedade RenderTransform com um RenderTransformOrigin de (0,5, 0,5)</span><span class="sxs-lookup"><span data-stu-id="9e910-119">A 45 degree rotation by using the RenderTransform property with a RenderTransformOrigin of (0.5, 0.5)</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 <span data-ttu-id="9e910-120">Para obter mais informações sobre como transformar <xref:System.Windows.FrameworkElement> objetos, consulte a [visão geral de transformações](transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9e910-120">For more information about transforming <xref:System.Windows.FrameworkElement> objects, see the [Transforms Overview](transforms-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e910-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e910-121">See also</span></span>

- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="9e910-122">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="9e910-122">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="9e910-123">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="9e910-123">How-to Topics</span></span>](transformations-how-to-topics.md)
