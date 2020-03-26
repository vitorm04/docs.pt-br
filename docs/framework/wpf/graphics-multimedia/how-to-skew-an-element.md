---
title: Como distorcer um elemento
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 10b00044c1c518641281e2e72cdb5a68474b5170
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112018"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="cf055-102">Como distorcer um elemento</span><span class="sxs-lookup"><span data-stu-id="cf055-102">How to: Skew an Element</span></span>
<span data-ttu-id="cf055-103">Este exemplo mostra como <xref:System.Windows.Media.SkewTransform> usar um para distorcer um elemento.</span><span class="sxs-lookup"><span data-stu-id="cf055-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="cf055-104">Uma distorção, também conhecida como cisalhamento, é uma transformação que alonga o espaço de coordenadas de uma maneira não uniforme.</span><span class="sxs-lookup"><span data-stu-id="cf055-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="cf055-105">Um uso típico <xref:System.Windows.Media.SkewTransform> de a é para simular profundidade 3D em objetos 2D.</span><span class="sxs-lookup"><span data-stu-id="cf055-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating 3D depth in 2D objects.</span></span>  
  
 <span data-ttu-id="cf055-106">Use <xref:System.Windows.Media.SkewTransform.CenterX%2A> as <xref:System.Windows.Media.SkewTransform.CenterY%2A> propriedades e para especificar o ponto central do <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="cf055-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="cf055-107">Use <xref:System.Windows.Media.SkewTransform.AngleX%2A> as <xref:System.Windows.Media.SkewTransform.AngleY%2A> propriedades e para especificar o ângulo de inclinação do eixo x e do eixo y, e para distorcer o sistema de coordenadas atual ao longo desses eixos.</span><span class="sxs-lookup"><span data-stu-id="cf055-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="cf055-108">Para prever o efeito de uma <xref:System.Windows.Media.SkewTransform.AngleX%2A> transformação de distorção, considere que distorce os valores do eixo x em relação ao sistema de coordenadas original.</span><span class="sxs-lookup"><span data-stu-id="cf055-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="cf055-109">Portanto, para <xref:System.Windows.Media.SkewTransform.AngleX%2A> um de 30, o eixo y gira 30 graus através da origem e distorce os valores em x- por 30 graus a partir dessa origem.</span><span class="sxs-lookup"><span data-stu-id="cf055-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="cf055-110">Da mesma <xref:System.Windows.Media.SkewTransform.AngleY%2A> forma, um de 30 distorce os valores y da forma em 30 graus da origem.</span><span class="sxs-lookup"><span data-stu-id="cf055-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="cf055-111">Observe que este não é o mesmo efeito que mover o sistema de coordenadas em 30 graus em x ou y.</span><span class="sxs-lookup"><span data-stu-id="cf055-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="cf055-112">O exemplo a seguir aplica uma inclinação horizontal <xref:System.Windows.Shapes.Rectangle> de 45 graus a a a de um ponto central de (0,0).</span><span class="sxs-lookup"><span data-stu-id="cf055-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf055-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf055-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="cf055-114">O exemplo a seguir aplica uma inclinação horizontal <xref:System.Windows.Shapes.Rectangle> de 45 graus a a a de um ponto central de (25,25).</span><span class="sxs-lookup"><span data-stu-id="cf055-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="cf055-115">O exemplo a seguir aplica uma inclinação vertical <xref:System.Windows.Shapes.Rectangle> de 45 graus a a a de um ponto central de (25,25).</span><span class="sxs-lookup"><span data-stu-id="cf055-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="cf055-116">A ilustração a seguir mostra as diferentes distorções usadas neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="cf055-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="cf055-117">![Exemplos SkewTransform](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="cf055-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="cf055-118">Três exemplos ilustrativos de SkewTransform</span><span class="sxs-lookup"><span data-stu-id="cf055-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="cf055-119">Para obter a amostra completa, consulte [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="cf055-119">For the complete sample, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf055-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="cf055-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="cf055-121">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="cf055-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="cf055-122">Tópicos de como fazer</span><span class="sxs-lookup"><span data-stu-id="cf055-122">How-to Topics</span></span>](transformations-how-to-topics.md)
