---
title: Como girar um objeto
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: 02d8144c28b7a4e54fb86fea5abb694cf7af34af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185961"
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="9809a-102">Como girar um objeto</span><span class="sxs-lookup"><span data-stu-id="9809a-102">How to: Rotate an Object</span></span>
<span data-ttu-id="9809a-103">Este exemplo mostra como girar um objeto.</span><span class="sxs-lookup"><span data-stu-id="9809a-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="9809a-104">O exemplo primeiro <xref:System.Windows.Media.RotateTransform> cria a <xref:System.Windows.Media.RotateTransform.Angle%2A> e, em seguida, especifica seu em graus.</span><span class="sxs-lookup"><span data-stu-id="9809a-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="9809a-105">O exemplo a <xref:System.Windows.Shapes.Polyline> seguir gira um objeto de 45 graus sobre seu canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="9809a-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9809a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9809a-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="9809a-107">As <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriedades do <xref:System.Windows.Media.RotateTransform> especificar o ponto sobre o qual o objeto é girado.</span><span class="sxs-lookup"><span data-stu-id="9809a-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="9809a-108">Esse ponto central é expresso no espaço coordenado do elemento que é transformado.</span><span class="sxs-lookup"><span data-stu-id="9809a-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="9809a-109">Por padrão, a rotação é aplicada a (0,0), que é o canto superior esquerdo do objeto a ser transformado.</span><span class="sxs-lookup"><span data-stu-id="9809a-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="9809a-110">O próximo exemplo <xref:System.Windows.Shapes.Polyline> gira um objeto no sentido horário 45 graus sobre o ponto (25,50).</span><span class="sxs-lookup"><span data-stu-id="9809a-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="9809a-111">A ilustração a seguir mostra <xref:System.Windows.Media.Transform> os resultados da aplicação de um aos dois objetos.</span><span class="sxs-lookup"><span data-stu-id="9809a-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="9809a-112">![Rotações de 45 graus com pontos centrais diferentes](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="9809a-112">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="9809a-113">Dois objetos que giram 45 graus de diferentes centros de rotação</span><span class="sxs-lookup"><span data-stu-id="9809a-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="9809a-114">Os <xref:System.Windows.Shapes.Polyline> exemplos anteriores são <xref:System.Windows.UIElement>um .</span><span class="sxs-lookup"><span data-stu-id="9809a-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="9809a-115">Quando você <xref:System.Windows.Media.Transform> aplica <xref:System.Windows.UIElement.RenderTransform%2A> um à <xref:System.Windows.UIElement>propriedade de <xref:System.Windows.UIElement.RenderTransformOrigin%2A> um , você pode <xref:System.Windows.Media.Transform> usar a propriedade para especificar uma origem para cada que você aplica ao elemento.</span><span class="sxs-lookup"><span data-stu-id="9809a-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="9809a-116">Como <xref:System.Windows.UIElement.RenderTransformOrigin%2A> a propriedade usa coordenadas relativas, você pode aplicar uma transformação ao centro do elemento mesmo que você não saiba o seu tamanho.</span><span class="sxs-lookup"><span data-stu-id="9809a-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="9809a-117">Para obter mais informações e por exemplo, consulte [Especificar a Origem de uma Transformação usando valores relativos](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span><span class="sxs-lookup"><span data-stu-id="9809a-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="9809a-118">Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="9809a-118">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9809a-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="9809a-119">See also</span></span>

- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="9809a-120">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="9809a-120">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="9809a-121">Tópicos de como fazer</span><span class="sxs-lookup"><span data-stu-id="9809a-121">How-to Topics</span></span>](transformations-how-to-topics.md)
