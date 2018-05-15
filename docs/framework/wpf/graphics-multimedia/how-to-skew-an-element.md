---
title: Como distorcer um elemento
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 8bd860a71253a55cb3148426dbb61cbd3477e95e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="10807-102">Como distorcer um elemento</span><span class="sxs-lookup"><span data-stu-id="10807-102">How to: Skew an Element</span></span>
<span data-ttu-id="10807-103">Este exemplo mostra como usar um <xref:System.Windows.Media.SkewTransform> para inclinar um elemento.</span><span class="sxs-lookup"><span data-stu-id="10807-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="10807-104">Uma distorção, também conhecida como cisalhamento, é uma transformação que alonga o espaço de coordenadas de uma maneira não uniforme.</span><span class="sxs-lookup"><span data-stu-id="10807-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="10807-105">Um uso típico de um <xref:System.Windows.Media.SkewTransform> é para simular [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] profundidade em [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objetos.</span><span class="sxs-lookup"><span data-stu-id="10807-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] depth in [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objects.</span></span>  
  
 <span data-ttu-id="10807-106">Use o <xref:System.Windows.Media.SkewTransform.CenterX%2A> e <xref:System.Windows.Media.SkewTransform.CenterY%2A> propriedades para especificar o centro do ponto do <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="10807-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="10807-107">Use o <xref:System.Windows.Media.SkewTransform.AngleX%2A> e <xref:System.Windows.Media.SkewTransform.AngleY%2A> propriedades para especificar o ângulo de inclinação dos eixos x e y e para inclinar o sistema de coordenadas atual ao longo desses eixos.</span><span class="sxs-lookup"><span data-stu-id="10807-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="10807-108">Para prever o efeito de uma transformação de distorção, considere que <xref:System.Windows.Media.SkewTransform.AngleX%2A> inclina valores do eixo x relativo ao sistema de coordenadas original.</span><span class="sxs-lookup"><span data-stu-id="10807-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="10807-109">Portanto, para um <xref:System.Windows.Media.SkewTransform.AngleX%2A> de 30, o eixo y gira 30 graus pela origem e inclina os valores de x-em 30 graus a partir dessa origem.</span><span class="sxs-lookup"><span data-stu-id="10807-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="10807-110">Da mesma forma, um <xref:System.Windows.Media.SkewTransform.AngleY%2A> de 30 inclina os valores de y da forma em 30 graus a partir da origem.</span><span class="sxs-lookup"><span data-stu-id="10807-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="10807-111">Observe que este não é o mesmo efeito que mover o sistema de coordenadas em 30 graus em x ou y.</span><span class="sxs-lookup"><span data-stu-id="10807-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="10807-112">O exemplo a seguir aplica uma distorção horizontal de 45 graus para um <xref:System.Windows.Shapes.Rectangle> de um ponto central de (0,0).</span><span class="sxs-lookup"><span data-stu-id="10807-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10807-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10807-113">Example</span></span>  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="10807-114">O exemplo a seguir aplica uma distorção horizontal de 45 graus para um <xref:System.Windows.Shapes.Rectangle> de um ponto central (25,25).</span><span class="sxs-lookup"><span data-stu-id="10807-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="10807-115">O exemplo a seguir aplica uma inclinação vertical de 45 graus para um <xref:System.Windows.Shapes.Rectangle> de um ponto central (25,25).</span><span class="sxs-lookup"><span data-stu-id="10807-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="10807-116">A ilustração a seguir mostra as diferentes distorções usadas neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="10807-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="10807-117">![Exemplos de SkewTransform](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="10807-117">![SkewTransform examples](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="10807-118">Três exemplos ilustrativos de SkewTransform</span><span class="sxs-lookup"><span data-stu-id="10807-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="10807-119">Para obter o exemplo completo, consulte [Amostras de Transformação 2D](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="10807-119">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10807-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10807-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [<span data-ttu-id="10807-121">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="10807-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="10807-122">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="10807-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
