---
title: Como dimensionar um elemento
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 34d954f68747be9eedc0ef71634e0c18b411d260
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112044"
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="2e636-102">Como dimensionar um elemento</span><span class="sxs-lookup"><span data-stu-id="2e636-102">How to: Scale an Element</span></span>
<span data-ttu-id="2e636-103">Este exemplo mostra como <xref:System.Windows.Media.ScaleTransform> usar um para escalar um elemento.</span><span class="sxs-lookup"><span data-stu-id="2e636-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="2e636-104">Use <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> as <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriedades e para redimensionar o elemento pelo fator especificado.</span><span class="sxs-lookup"><span data-stu-id="2e636-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="2e636-105">Por exemplo, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> um valor de 1,5 estende o elemento a 150% de sua largura original.</span><span class="sxs-lookup"><span data-stu-id="2e636-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="2e636-106">Um <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> valor de 0,5 reduz a altura de um elemento em 50%.</span><span class="sxs-lookup"><span data-stu-id="2e636-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="2e636-107">Use <xref:System.Windows.Media.ScaleTransform.CenterX%2A> as <xref:System.Windows.Media.ScaleTransform.CenterY%2A> propriedades e para especificar o ponto que é o centro da operação de escala.</span><span class="sxs-lookup"><span data-stu-id="2e636-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="2e636-108">Por padrão, <xref:System.Windows.Media.ScaleTransform> a é centrado no ponto (0,0), que corresponde ao canto superior esquerdo do retângulo.</span><span class="sxs-lookup"><span data-stu-id="2e636-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="2e636-109">Isso tem o efeito de mover o elemento e também de <xref:System.Windows.Media.Transform>fazê-lo parecer maior, porque quando você aplica um , você altera o espaço de coordenadas em que o objeto reside.</span><span class="sxs-lookup"><span data-stu-id="2e636-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="2e636-110">O exemplo a <xref:System.Windows.Media.ScaleTransform> seguir usa um para dobrar o <xref:System.Windows.Shapes.Rectangle>tamanho de um 50 por 50 .</span><span class="sxs-lookup"><span data-stu-id="2e636-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="2e636-111">O <xref:System.Windows.Media.ScaleTransform> tem um valor de 0 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> (o padrão) para ambos e <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e636-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e636-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e636-112">Example</span></span>  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="2e636-113">Normalmente, você <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A> define e para o centro do<xref:System.Windows.FrameworkElement.Width%2A>objeto que <xref:System.Windows.FrameworkElement.Height%2A>é dimensionado: ( /2, /2).</span><span class="sxs-lookup"><span data-stu-id="2e636-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="2e636-114">O exemplo a <xref:System.Windows.Shapes.Rectangle> seguir mostra outro que é dobrado em tamanho; no entanto, este <xref:System.Windows.Media.ScaleTransform> tem um <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>valor de 25 para ambos e , que corresponde ao centro do retângulo.</span><span class="sxs-lookup"><span data-stu-id="2e636-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="2e636-115">A ilustração a seguir <xref:System.Windows.Media.ScaleTransform> mostra a diferença entre as duas operações.</span><span class="sxs-lookup"><span data-stu-id="2e636-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="2e636-116">A linha pontilhada mostra o tamanho e a posição do retângulo antes do dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="2e636-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="2e636-117">![Ajustes de escala de duas vezes com pontos centrais diferentes](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="2e636-117">![2x scales with different center points](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="2e636-118">Duas operações ScaleTransform com valores idênticos de ScaleX e ScaleY, mas com diferentes centros</span><span class="sxs-lookup"><span data-stu-id="2e636-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="2e636-119">Para obter a amostra completa, consulte [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="2e636-119">For the complete sample, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e636-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="2e636-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="2e636-121">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="2e636-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="2e636-122">Tópicos de como fazer</span><span class="sxs-lookup"><span data-stu-id="2e636-122">How-to Topics</span></span>](transformations-how-to-topics.md)
