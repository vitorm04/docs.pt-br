---
title: 'Como: Inclinar um elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 47f671f493e7b379c36f9bf4b50ec9d185d10b8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61804047"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="dbc51-102">Como: Inclinar um elemento</span><span class="sxs-lookup"><span data-stu-id="dbc51-102">How to: Skew an Element</span></span>
<span data-ttu-id="dbc51-103">Este exemplo mostra como usar um <xref:System.Windows.Media.SkewTransform> para inclinar um elemento.</span><span class="sxs-lookup"><span data-stu-id="dbc51-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="dbc51-104">Uma distorção, também conhecida como cisalhamento, é uma transformação que alonga o espaço de coordenadas de uma maneira não uniforme.</span><span class="sxs-lookup"><span data-stu-id="dbc51-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="dbc51-105">Um uso típico de um <xref:System.Windows.Media.SkewTransform> é para simular [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] profundidade em [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objetos.</span><span class="sxs-lookup"><span data-stu-id="dbc51-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] depth in [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objects.</span></span>  
  
 <span data-ttu-id="dbc51-106">Use o <xref:System.Windows.Media.SkewTransform.CenterX%2A> e <xref:System.Windows.Media.SkewTransform.CenterY%2A> as propriedades para especificar o centro do ponto do <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="dbc51-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="dbc51-107">Use o <xref:System.Windows.Media.SkewTransform.AngleX%2A> e <xref:System.Windows.Media.SkewTransform.AngleY%2A> propriedades para especificar o ângulo de inclinação do eixo x e eixo y e para distorcer o sistema de coordenadas atual ao longo desses eixos.</span><span class="sxs-lookup"><span data-stu-id="dbc51-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="dbc51-108">Para prever o efeito de uma transformação de distorção, considere que <xref:System.Windows.Media.SkewTransform.AngleX%2A> distorce os valores do eixo x em relação ao sistema de coordenadas original.</span><span class="sxs-lookup"><span data-stu-id="dbc51-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="dbc51-109">Portanto, para um <xref:System.Windows.Media.SkewTransform.AngleX%2A> de 30, o eixo y gira 30 graus pela origem e distorce os valores em x-em 30 graus a partir dessa origem.</span><span class="sxs-lookup"><span data-stu-id="dbc51-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="dbc51-110">Da mesma forma, um <xref:System.Windows.Media.SkewTransform.AngleY%2A> de 30 distorce os valores y da forma em 30 graus da origem.</span><span class="sxs-lookup"><span data-stu-id="dbc51-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="dbc51-111">Observe que este não é o mesmo efeito que mover o sistema de coordenadas em 30 graus em x ou y.</span><span class="sxs-lookup"><span data-stu-id="dbc51-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="dbc51-112">O exemplo a seguir aplica uma distorção horizontal de 45 graus para um <xref:System.Windows.Shapes.Rectangle> de um ponto central (0,0).</span><span class="sxs-lookup"><span data-stu-id="dbc51-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbc51-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dbc51-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="dbc51-114">O exemplo a seguir aplica uma distorção horizontal de 45 graus para um <xref:System.Windows.Shapes.Rectangle> de um ponto central (25,25).</span><span class="sxs-lookup"><span data-stu-id="dbc51-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="dbc51-115">O exemplo a seguir aplica uma distorção vertical de 45 graus para um <xref:System.Windows.Shapes.Rectangle> de um ponto central (25,25).</span><span class="sxs-lookup"><span data-stu-id="dbc51-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="dbc51-116">A ilustração a seguir mostra as diferentes distorções usadas neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="dbc51-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="dbc51-117">![Exemplos SkewTransform](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="dbc51-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="dbc51-118">Três exemplos ilustrativos de SkewTransform</span><span class="sxs-lookup"><span data-stu-id="dbc51-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="dbc51-119">Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="dbc51-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc51-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbc51-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="dbc51-121">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="dbc51-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="dbc51-122">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="dbc51-122">How-to Topics</span></span>](transformations-how-to-topics.md)
