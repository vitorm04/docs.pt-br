---
title: Como fazer teste de clique da geometria em um visual
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a990a43853e375c1c97f88dc6792932ad64c8d37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a><span data-ttu-id="407fb-102">Como fazer teste de clique da geometria em um visual</span><span class="sxs-lookup"><span data-stu-id="407fb-102">How to: Hit Test Geometry in a Visual</span></span>
<span data-ttu-id="407fb-103">Este exemplo mostra como executar um teste de clique em um objeto visual que é composto de um ou mais <xref:System.Windows.Media.Geometry> objetos.</span><span class="sxs-lookup"><span data-stu-id="407fb-103">This example shows how to perform a hit test on a visual object that is composed of one or more <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="407fb-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="407fb-104">Example</span></span>  
 <span data-ttu-id="407fb-105">O exemplo a seguir mostra como recuperar o <xref:System.Windows.Media.DrawingGroup> de um objeto visual que utiliza o <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> método.</span><span class="sxs-lookup"><span data-stu-id="407fb-105">The following example shows how to retrieve the <xref:System.Windows.Media.DrawingGroup> from a visual object that uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method.</span></span> <span data-ttu-id="407fb-106">Um teste de clique, em seguida, é executado no conteúdo renderizado de cada desenho no <xref:System.Windows.Media.DrawingGroup> para determinar qual geometria foi atingida.</span><span class="sxs-lookup"><span data-stu-id="407fb-106">A hit test is then performed on the rendered content of each drawing in the <xref:System.Windows.Media.DrawingGroup> to determine which geometry was hit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="407fb-107">Na maioria dos casos, você usaria o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> método para determinar se um ponto intercepta qualquer conteúdo renderizado de um visual.</span><span class="sxs-lookup"><span data-stu-id="407fb-107">In most cases, you would use the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to determine whether a point intersects any of the rendered content of a visual.</span></span>  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <span data-ttu-id="407fb-108">O <xref:System.Windows.Media.Geometry.FillContains%2A> método é um método sobrecarregado que permite que você teste usando um especificado <xref:System.Windows.Point> ou <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="407fb-108">The <xref:System.Windows.Media.Geometry.FillContains%2A> method is an overloaded method that allows you to hit test by using a specified <xref:System.Windows.Point> or <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="407fb-109">Se uma geometria for traçada, o traço poderá se estender para fora dos limites de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="407fb-109">If a geometry is stroked, the stroke can extend outside the fill bounds.</span></span> <span data-ttu-id="407fb-110">Nesse caso, convém chamar <xref:System.Windows.Media.Geometry.StrokeContains%2A> além <xref:System.Windows.Media.Geometry.FillContains%2A>.</span><span class="sxs-lookup"><span data-stu-id="407fb-110">In which case, you may want to call <xref:System.Windows.Media.Geometry.StrokeContains%2A> in addition to <xref:System.Windows.Media.Geometry.FillContains%2A>.</span></span>  
  
 <span data-ttu-id="407fb-111">Você também pode fornecer um <xref:System.Windows.Media.ToleranceType> que é usado para fins de Bézier.</span><span class="sxs-lookup"><span data-stu-id="407fb-111">You can also provide a <xref:System.Windows.Media.ToleranceType> that is used for the purposes of Bezier flattening.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="407fb-112">Este exemplo não considera quaisquer transformações ou distorções que possam ser aplicadas à geometria.</span><span class="sxs-lookup"><span data-stu-id="407fb-112">This sample does not take into account any transforms or clipping that may be applied to the geometry.</span></span> <span data-ttu-id="407fb-113">Além disso, este exemplo não funcionará com um controle com estilo, pois não tem desenhos diretamente associados a ele.</span><span class="sxs-lookup"><span data-stu-id="407fb-113">In addition, this sample will not work with a styled control, since it does not have any drawings directly associated with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="407fb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="407fb-114">See Also</span></span>  
 [<span data-ttu-id="407fb-115">Teste de clique na camada visual</span><span class="sxs-lookup"><span data-stu-id="407fb-115">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="407fb-116">Teste de clique usando geometria como um parâmetro</span><span class="sxs-lookup"><span data-stu-id="407fb-116">Hit Test Using Geometry as a Parameter</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)
