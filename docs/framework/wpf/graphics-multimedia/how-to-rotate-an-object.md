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
ms.openlocfilehash: 7eb562d81bdd8c9187672b31ed08ed6ac27da41c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="21481-102">Como girar um objeto</span><span class="sxs-lookup"><span data-stu-id="21481-102">How to: Rotate an Object</span></span>
<span data-ttu-id="21481-103">Este exemplo mostra como girar um objeto.</span><span class="sxs-lookup"><span data-stu-id="21481-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="21481-104">O exemplo cria primeiro um <xref:System.Windows.Media.RotateTransform> e, em seguida, especifica sua <xref:System.Windows.Media.RotateTransform.Angle%2A> em graus.</span><span class="sxs-lookup"><span data-stu-id="21481-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="21481-105">O exemplo a seguir gira um <xref:System.Windows.Shapes.Polyline> 45 graus sobre seu canto superior esquerdo do objeto.</span><span class="sxs-lookup"><span data-stu-id="21481-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21481-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="21481-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="21481-107">O <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriedades do <xref:System.Windows.Media.RotateTransform> especificar o ponto sobre o qual o objeto for girado.</span><span class="sxs-lookup"><span data-stu-id="21481-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="21481-108">Esse ponto central é expresso no espaço coordenado do elemento que é transformado.</span><span class="sxs-lookup"><span data-stu-id="21481-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="21481-109">Por padrão, a rotação é aplicada a (0,0), que é o canto superior esquerdo do objeto a ser transformado.</span><span class="sxs-lookup"><span data-stu-id="21481-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="21481-110">O exemplo a seguir gira um <xref:System.Windows.Shapes.Polyline> 45 graus no sentido horário em torno do ponto (25,50) do objeto.</span><span class="sxs-lookup"><span data-stu-id="21481-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="21481-111">A ilustração a seguir mostra os resultados da aplicação de um <xref:System.Windows.Media.Transform> para os dois objetos.</span><span class="sxs-lookup"><span data-stu-id="21481-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="21481-112">![rotações de 45 graus com diferentes pontos centrais](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="21481-112">![45 degree rotations with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="21481-113">Dois objetos que giram 45 graus de diferentes centros de rotação</span><span class="sxs-lookup"><span data-stu-id="21481-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="21481-114">O <xref:System.Windows.Shapes.Polyline> nos exemplos anteriores é um <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="21481-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="21481-115">Quando você aplica um <xref:System.Windows.Media.Transform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade de um <xref:System.Windows.UIElement>, você pode usar o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade para especificar uma origem para cada <xref:System.Windows.Media.Transform> aplicáveis ao elemento.</span><span class="sxs-lookup"><span data-stu-id="21481-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="21481-116">Porque o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade usa coordenadas relativas, você pode aplicar uma transformação para o centro do elemento, mesmo se você não souber seu tamanho.</span><span class="sxs-lookup"><span data-stu-id="21481-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="21481-117">Para obter mais informações e para obter um exemplo, consulte [especificar a origem de uma transformação por valores relativos usando](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span><span class="sxs-lookup"><span data-stu-id="21481-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="21481-118">Para obter o exemplo completo, consulte [Amostras de Transformação 2D](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="21481-118">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21481-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21481-119">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="21481-120">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="21481-120">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="21481-121">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="21481-121">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
