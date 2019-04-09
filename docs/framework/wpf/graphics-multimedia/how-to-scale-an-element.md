---
title: 'Como: Dimensionar um elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 607b3a11085f746503c1b82552f1740b49d9ef5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131697"
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="72c0e-102">Como: Dimensionar um elemento</span><span class="sxs-lookup"><span data-stu-id="72c0e-102">How to: Scale an Element</span></span>
<span data-ttu-id="72c0e-103">Este exemplo mostra como usar um <xref:System.Windows.Media.ScaleTransform> para dimensionar um elemento.</span><span class="sxs-lookup"><span data-stu-id="72c0e-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="72c0e-104">Use o <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> e <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriedades para redimensionar o elemento pelo fator especificado.</span><span class="sxs-lookup"><span data-stu-id="72c0e-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="72c0e-105">Por exemplo, um <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> valor de 1,5 alonga o elemento em 150% de sua largura original.</span><span class="sxs-lookup"><span data-stu-id="72c0e-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="72c0e-106">Um <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> valor de 0,5 reduz a altura de um elemento em 50%.</span><span class="sxs-lookup"><span data-stu-id="72c0e-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="72c0e-107">Use o <xref:System.Windows.Media.ScaleTransform.CenterX%2A> e <xref:System.Windows.Media.ScaleTransform.CenterY%2A> propriedades para especificar o ponto que é o centro da operação de escala.</span><span class="sxs-lookup"><span data-stu-id="72c0e-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="72c0e-108">Por padrão, um <xref:System.Windows.Media.ScaleTransform> é centralizado no ponto (0,0), que corresponde ao canto superior esquerdo do retângulo.</span><span class="sxs-lookup"><span data-stu-id="72c0e-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="72c0e-109">Isso tem o efeito de mover o elemento e também de fazê-lo parecer maior, pois quando você aplica um <xref:System.Windows.Media.Transform>, você alterar o espaço de coordenadas no qual o objeto reside.</span><span class="sxs-lookup"><span data-stu-id="72c0e-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="72c0e-110">O exemplo a seguir usa uma <xref:System.Windows.Media.ScaleTransform> para dobrar o tamanho de um 50 por 50 <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="72c0e-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="72c0e-111">O <xref:System.Windows.Media.ScaleTransform> tem um valor de 0 (o padrão) para ambos <xref:System.Windows.Media.ScaleTransform.CenterX%2A> e <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span><span class="sxs-lookup"><span data-stu-id="72c0e-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72c0e-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c0e-112">Example</span></span>  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="72c0e-113">Normalmente, você definir <xref:System.Windows.Media.ScaleTransform.CenterX%2A> e <xref:System.Windows.Media.ScaleTransform.CenterY%2A> para o centro do objeto que é escalado: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).</span><span class="sxs-lookup"><span data-stu-id="72c0e-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="72c0e-114">O exemplo a seguir mostra outro <xref:System.Windows.Shapes.Rectangle> que é duplicado em tamanho; no entanto, isso <xref:System.Windows.Media.ScaleTransform> tem um valor de 25 para ambos <xref:System.Windows.Media.ScaleTransform.CenterX%2A> e <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, que corresponde ao centro do retângulo.</span><span class="sxs-lookup"><span data-stu-id="72c0e-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="72c0e-115">A ilustração a seguir mostra a diferença entre os dois <xref:System.Windows.Media.ScaleTransform> operações.</span><span class="sxs-lookup"><span data-stu-id="72c0e-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="72c0e-116">A linha pontilhada mostra o tamanho e a posição do retângulo antes do dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="72c0e-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="72c0e-117">![escalas de x 2 com diferentes pontos centrais](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="72c0e-117">![2x scales with different center points](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="72c0e-118">Duas operações ScaleTransform com valores idênticos de ScaleX e ScaleY, mas com diferentes centros</span><span class="sxs-lookup"><span data-stu-id="72c0e-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="72c0e-119">Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="72c0e-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72c0e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72c0e-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="72c0e-121">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="72c0e-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="72c0e-122">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="72c0e-122">How-to Topics</span></span>](transformations-how-to-topics.md)
