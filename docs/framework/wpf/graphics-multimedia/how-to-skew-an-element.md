---
title: Como distorcer um elemento
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 370ac28b07427345b52822133b5414b45d4462eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187656"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="d352a-102">Como distorcer um elemento</span><span class="sxs-lookup"><span data-stu-id="d352a-102">How to: Skew an Element</span></span>
<span data-ttu-id="d352a-103">Este exemplo mostra como <xref:System.Windows.Media.SkewTransform> usar um para distorcer um elemento.</span><span class="sxs-lookup"><span data-stu-id="d352a-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="d352a-104">Uma distorção, também conhecida como cisalhamento, é uma transformação que alonga o espaço de coordenadas de uma maneira não uniforme.</span><span class="sxs-lookup"><span data-stu-id="d352a-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="d352a-105">Um uso típico <xref:System.Windows.Media.SkewTransform> de a é para simular profundidade 3D em objetos 2D.</span><span class="sxs-lookup"><span data-stu-id="d352a-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating 3-D depth in 2-D objects.</span></span>  
  
 <span data-ttu-id="d352a-106">Use <xref:System.Windows.Media.SkewTransform.CenterX%2A> as <xref:System.Windows.Media.SkewTransform.CenterY%2A> propriedades e para especificar o ponto central do <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="d352a-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="d352a-107">Use <xref:System.Windows.Media.SkewTransform.AngleX%2A> as <xref:System.Windows.Media.SkewTransform.AngleY%2A> propriedades e para especificar o ângulo de inclinação do eixo x e do eixo y, e para distorcer o sistema de coordenadas atual ao longo desses eixos.</span><span class="sxs-lookup"><span data-stu-id="d352a-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="d352a-108">Para prever o efeito de uma <xref:System.Windows.Media.SkewTransform.AngleX%2A> transformação de distorção, considere que distorce os valores do eixo x em relação ao sistema de coordenadas original.</span><span class="sxs-lookup"><span data-stu-id="d352a-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="d352a-109">Portanto, para <xref:System.Windows.Media.SkewTransform.AngleX%2A> um de 30, o eixo y gira 30 graus através da origem e distorce os valores em x- por 30 graus a partir dessa origem.</span><span class="sxs-lookup"><span data-stu-id="d352a-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="d352a-110">Da mesma <xref:System.Windows.Media.SkewTransform.AngleY%2A> forma, um de 30 distorce os valores y da forma em 30 graus da origem.</span><span class="sxs-lookup"><span data-stu-id="d352a-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="d352a-111">Observe que este não é o mesmo efeito que mover o sistema de coordenadas em 30 graus em x ou y.</span><span class="sxs-lookup"><span data-stu-id="d352a-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="d352a-112">O exemplo a seguir aplica uma inclinação horizontal <xref:System.Windows.Shapes.Rectangle> de 45 graus a a a de um ponto central de (0,0).</span><span class="sxs-lookup"><span data-stu-id="d352a-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d352a-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d352a-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="d352a-114">O exemplo a seguir aplica uma inclinação horizontal <xref:System.Windows.Shapes.Rectangle> de 45 graus a a a de um ponto central de (25,25).</span><span class="sxs-lookup"><span data-stu-id="d352a-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="d352a-115">O exemplo a seguir aplica uma inclinação vertical <xref:System.Windows.Shapes.Rectangle> de 45 graus a a a de um ponto central de (25,25).</span><span class="sxs-lookup"><span data-stu-id="d352a-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="d352a-116">A ilustração a seguir mostra as diferentes distorções usadas neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="d352a-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="d352a-117">![Exemplos SkewTransform](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="d352a-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="d352a-118">Três exemplos ilustrativos de SkewTransform</span><span class="sxs-lookup"><span data-stu-id="d352a-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="d352a-119">Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="d352a-119">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d352a-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="d352a-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="d352a-121">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="d352a-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="d352a-122">Tópicos de como fazer</span><span class="sxs-lookup"><span data-stu-id="d352a-122">How-to Topics</span></span>](transformations-how-to-topics.md)
