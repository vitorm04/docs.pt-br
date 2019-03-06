---
title: 'Como: Teste de clique usando geometria como um parâmetro'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 15a33d05cb3ca4fd40f04170bd1756e466631275
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366355"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a><span data-ttu-id="e14a4-102">Como: Teste de clique usando geometria como um parâmetro</span><span class="sxs-lookup"><span data-stu-id="e14a4-102">How to: Hit Test Using Geometry as a Parameter</span></span>
<span data-ttu-id="e14a4-103">Este exemplo mostra como executar um teste de clique em um objeto visual usando um <xref:System.Windows.Media.Geometry> como um teste de clique parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e14a4-103">This example shows how to perform a hit test on a visual object using a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e14a4-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e14a4-104">Example</span></span>  
 <span data-ttu-id="e14a4-105">O exemplo a seguir mostra como configurar um teste de clique usando <xref:System.Windows.Media.GeometryHitTestParameters> para o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e14a4-105">The following example shows how to set up a hit test using <xref:System.Windows.Media.GeometryHitTestParameters> for the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="e14a4-106">O <xref:System.Windows.Point> valor que é passado para o `OnMouseDown` método é usado para criar um <xref:System.Windows.Media.Geometry> objeto para expandir o intervalo do teste de clique.</span><span class="sxs-lookup"><span data-stu-id="e14a4-106">The <xref:System.Windows.Point> value that is passed to the `OnMouseDown` method is used to create a <xref:System.Windows.Media.Geometry> object in order to expand the range of the hit test.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <span data-ttu-id="e14a4-107">O <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> propriedade de <xref:System.Windows.Media.GeometryHitTestResult> fornece informações sobre os resultados de um teste de clique que usa um <xref:System.Windows.Media.Geometry> como um teste de clique parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e14a4-107">The <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property of <xref:System.Windows.Media.GeometryHitTestResult> provides information about the results of a hit test that uses a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span> <span data-ttu-id="e14a4-108">A ilustração a seguir mostra a relação entre a geometria de teste de clique (o círculo azul) e o conteúdo renderizado do objeto visual de destino (o quadrado vermelho).</span><span class="sxs-lookup"><span data-stu-id="e14a4-108">The following illustration shows the relationship between the hit test geometry (the blue circle) and the rendered content of the target visual object (the red square).</span></span>  
  
 <span data-ttu-id="e14a4-109">![Diagrama de IntersectionDetail usado no teste de hit](./media/intersectiondetail01.png "IntersectionDetail01")</span><span class="sxs-lookup"><span data-stu-id="e14a4-109">![Diagram of IntersectionDetail used in hit testing](./media/intersectiondetail01.png "IntersectionDetail01")</span></span>  
<span data-ttu-id="e14a4-110">Interseção entre geometria do teste de clique e o objeto visual de destino</span><span class="sxs-lookup"><span data-stu-id="e14a4-110">Intersection between hit test geometry and target visual object</span></span>  
  
 <span data-ttu-id="e14a4-111">O exemplo a seguir mostra como implementar um retorno de chamada de teste de clique quando um <xref:System.Windows.Media.Geometry> é usado como um parâmetro de teste de clique.</span><span class="sxs-lookup"><span data-stu-id="e14a4-111">The following example shows how to implement a hit test callback when a <xref:System.Windows.Media.Geometry> is used as a hit test parameter.</span></span> <span data-ttu-id="e14a4-112">O `result` parâmetro é convertido em um <xref:System.Windows.Media.GeometryHitTestResult> para recuperar o valor da <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="e14a4-112">The `result` parameter is cast to a <xref:System.Windows.Media.GeometryHitTestResult> in order to retrieve the value of the <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property.</span></span> <span data-ttu-id="e14a4-113">O valor da propriedade permite que você determine se o <xref:System.Windows.Media.Geometry> parâmetro de teste de clique é contido total ou parcialmente dentro do conteúdo renderizado do destino do teste de clique.</span><span class="sxs-lookup"><span data-stu-id="e14a4-113">The property value allows you to determine if the <xref:System.Windows.Media.Geometry> hit test parameter is fully or partially contained within the rendered content of the hit test target.</span></span> <span data-ttu-id="e14a4-114">Nesse caso, o código de exemplo só está acrescentando resultados do teste de clique à lista de visuais que estão completamente contidos dentro do limite de destino.</span><span class="sxs-lookup"><span data-stu-id="e14a4-114">In this case, the sample code is only adding hit test results to the list for visuals that are fully contained within the target boundary.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <span data-ttu-id="e14a4-115">O <xref:System.Windows.Media.HitTestResult> retorno de chamada não deve ser chamado quando o detalhe da interseção for <xref:System.Windows.Media.IntersectionDetail.Empty>.</span><span class="sxs-lookup"><span data-stu-id="e14a4-115">The <xref:System.Windows.Media.HitTestResult> callback should not be called when the intersection detail is <xref:System.Windows.Media.IntersectionDetail.Empty>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e14a4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e14a4-116">See also</span></span>
- [<span data-ttu-id="e14a4-117">Teste de clique na camada visual</span><span class="sxs-lookup"><span data-stu-id="e14a4-117">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="e14a4-118">Teste de clique de geometria em um visual</span><span class="sxs-lookup"><span data-stu-id="e14a4-118">Hit Test Geometry in a Visual</span></span>](how-to-hit-test-geometry-in-a-visual.md)
