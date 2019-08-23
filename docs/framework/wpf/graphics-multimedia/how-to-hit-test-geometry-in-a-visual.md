---
title: 'Como: Teste de clique de geometria em um visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 52b9b99b0af38d797e4a3c98dc0979211c930c1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923372"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a><span data-ttu-id="419d7-102">Como: Teste de clique de geometria em um visual</span><span class="sxs-lookup"><span data-stu-id="419d7-102">How to: Hit Test Geometry in a Visual</span></span>
<span data-ttu-id="419d7-103">Este exemplo mostra como executar um teste de clique em um objeto visual que é composto por um ou mais <xref:System.Windows.Media.Geometry> objetos.</span><span class="sxs-lookup"><span data-stu-id="419d7-103">This example shows how to perform a hit test on a visual object that is composed of one or more <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="419d7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="419d7-104">Example</span></span>  
 <span data-ttu-id="419d7-105">O exemplo a seguir mostra como recuperar o <xref:System.Windows.Media.DrawingGroup> de um objeto visual que usa o <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> método.</span><span class="sxs-lookup"><span data-stu-id="419d7-105">The following example shows how to retrieve the <xref:System.Windows.Media.DrawingGroup> from a visual object that uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method.</span></span> <span data-ttu-id="419d7-106">Um teste de clique é então executado no conteúdo renderizado de cada desenho no <xref:System.Windows.Media.DrawingGroup> para determinar qual geometria foi atingida.</span><span class="sxs-lookup"><span data-stu-id="419d7-106">A hit test is then performed on the rendered content of each drawing in the <xref:System.Windows.Media.DrawingGroup> to determine which geometry was hit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="419d7-107">Na maioria dos casos, você usaria o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> método para determinar se um ponto cruza qualquer conteúdo renderizado de um Visual.</span><span class="sxs-lookup"><span data-stu-id="419d7-107">In most cases, you would use the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to determine whether a point intersects any of the rendered content of a visual.</span></span>  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <span data-ttu-id="419d7-108">O <xref:System.Windows.Media.Geometry.FillContains%2A> método é um método sobrecarregado que permite que você clique em teste usando <xref:System.Windows.Point> um ou <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="419d7-108">The <xref:System.Windows.Media.Geometry.FillContains%2A> method is an overloaded method that allows you to hit test by using a specified <xref:System.Windows.Point> or <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="419d7-109">Se uma geometria for traçada, o traço poderá se estender para fora dos limites de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="419d7-109">If a geometry is stroked, the stroke can extend outside the fill bounds.</span></span> <span data-ttu-id="419d7-110">Nesse caso, talvez você queira chamar <xref:System.Windows.Media.Geometry.StrokeContains%2A> além de. <xref:System.Windows.Media.Geometry.FillContains%2A></span><span class="sxs-lookup"><span data-stu-id="419d7-110">In which case, you may want to call <xref:System.Windows.Media.Geometry.StrokeContains%2A> in addition to <xref:System.Windows.Media.Geometry.FillContains%2A>.</span></span>  
  
 <span data-ttu-id="419d7-111">Você também pode fornecer um <xref:System.Windows.Media.ToleranceType> que é usado para fins de achatamento de Bézier.</span><span class="sxs-lookup"><span data-stu-id="419d7-111">You can also provide a <xref:System.Windows.Media.ToleranceType> that is used for the purposes of Bezier flattening.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="419d7-112">Este exemplo não considera quaisquer transformações ou distorções que possam ser aplicadas à geometria.</span><span class="sxs-lookup"><span data-stu-id="419d7-112">This sample does not take into account any transforms or clipping that may be applied to the geometry.</span></span> <span data-ttu-id="419d7-113">Além disso, este exemplo não funcionará com um controle com estilo, pois não tem desenhos diretamente associados a ele.</span><span class="sxs-lookup"><span data-stu-id="419d7-113">In addition, this sample will not work with a styled control, since it does not have any drawings directly associated with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="419d7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="419d7-114">See also</span></span>

- [<span data-ttu-id="419d7-115">Teste de clique na camada visual</span><span class="sxs-lookup"><span data-stu-id="419d7-115">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="419d7-116">Teste de clique usando geometria como um parâmetro</span><span class="sxs-lookup"><span data-stu-id="419d7-116">Hit Test Using Geometry as a Parameter</span></span>](how-to-hit-test-using-geometry-as-a-parameter.md)
