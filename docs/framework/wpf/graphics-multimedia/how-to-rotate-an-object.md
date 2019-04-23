---
title: 'Como: Girar um objeto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: d1c4700a5dc8f6ed99043552999d8f014116da8f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189626"
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="98832-102">Como: Girar um objeto</span><span class="sxs-lookup"><span data-stu-id="98832-102">How to: Rotate an Object</span></span>
<span data-ttu-id="98832-103">Este exemplo mostra como girar um objeto.</span><span class="sxs-lookup"><span data-stu-id="98832-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="98832-104">O exemplo cria primeiro um <xref:System.Windows.Media.RotateTransform> e, em seguida, especifica sua <xref:System.Windows.Media.RotateTransform.Angle%2A> em graus.</span><span class="sxs-lookup"><span data-stu-id="98832-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="98832-105">O exemplo a seguir gira um <xref:System.Windows.Shapes.Polyline> 45 graus sobre seu canto superior esquerdo do objeto.</span><span class="sxs-lookup"><span data-stu-id="98832-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98832-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98832-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="98832-107">O <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriedades do <xref:System.Windows.Media.RotateTransform> especificar o ponto sobre o qual o objeto é girado.</span><span class="sxs-lookup"><span data-stu-id="98832-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="98832-108">Esse ponto central é expresso no espaço coordenado do elemento que é transformado.</span><span class="sxs-lookup"><span data-stu-id="98832-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="98832-109">Por padrão, a rotação é aplicada a (0,0), que é o canto superior esquerdo do objeto a ser transformado.</span><span class="sxs-lookup"><span data-stu-id="98832-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="98832-110">O próximo exemplo gira um <xref:System.Windows.Shapes.Polyline> 45 graus no sentido horário em torno do ponto (25,50) do objeto.</span><span class="sxs-lookup"><span data-stu-id="98832-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="98832-111">A ilustração a seguir mostra os resultados da aplicação de um <xref:System.Windows.Media.Transform> aos dois objetos.</span><span class="sxs-lookup"><span data-stu-id="98832-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="98832-112">![rotações de 45 graus com diferentes pontos centrais](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="98832-112">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="98832-113">Dois objetos que giram 45 graus de diferentes centros de rotação</span><span class="sxs-lookup"><span data-stu-id="98832-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="98832-114">O <xref:System.Windows.Shapes.Polyline> nos exemplos anteriores é um <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="98832-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="98832-115">Quando você aplica um <xref:System.Windows.Media.Transform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade de uma <xref:System.Windows.UIElement>, você pode usar os <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade para especificar uma origem para cada <xref:System.Windows.Media.Transform> aplicáveis ao elemento.</span><span class="sxs-lookup"><span data-stu-id="98832-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="98832-116">Porque o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade usa coordenadas relativas, você pode aplicar uma transformação ao centro do elemento, mesmo se você não souber seu tamanho.</span><span class="sxs-lookup"><span data-stu-id="98832-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="98832-117">Para obter mais informações e para obter um exemplo, consulte [especificar a origem de uma transformação usando valores relativos](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span><span class="sxs-lookup"><span data-stu-id="98832-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="98832-118">Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="98832-118">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98832-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98832-119">See also</span></span>

- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="98832-120">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="98832-120">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="98832-121">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="98832-121">How-to Topics</span></span>](transformations-how-to-topics.md)
