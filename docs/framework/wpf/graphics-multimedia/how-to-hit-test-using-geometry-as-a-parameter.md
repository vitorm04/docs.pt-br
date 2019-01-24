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
ms.openlocfilehash: d52f8da891ecdf632952c441f94aab4c0b56da7f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564247"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>Como: Teste de clique usando geometria como um parâmetro
Este exemplo mostra como executar um teste de clique em um objeto visual usando um <xref:System.Windows.Media.Geometry> como um teste de clique parâmetro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como configurar um teste de clique usando <xref:System.Windows.Media.GeometryHitTestParameters> para o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> método. O <xref:System.Windows.Point> valor que é passado para o `OnMouseDown` método é usado para criar um <xref:System.Windows.Media.Geometry> objeto para expandir o intervalo do teste de clique.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 O <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> propriedade de <xref:System.Windows.Media.GeometryHitTestResult> fornece informações sobre os resultados de um teste de clique que usa um <xref:System.Windows.Media.Geometry> como um teste de clique parâmetro. A ilustração a seguir mostra a relação entre a geometria de teste de clique (o círculo azul) e o conteúdo renderizado do objeto visual de destino (o quadrado vermelho).  
  
 ![Diagrama de IntersectionDetail usado no teste de hit](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")  
Interseção entre geometria do teste de clique e o objeto visual de destino  
  
 O exemplo a seguir mostra como implementar um retorno de chamada de teste de clique quando um <xref:System.Windows.Media.Geometry> é usado como um parâmetro de teste de clique. O `result` parâmetro é convertido em um <xref:System.Windows.Media.GeometryHitTestResult> para recuperar o valor da <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> propriedade. O valor da propriedade permite que você determine se o <xref:System.Windows.Media.Geometry> parâmetro de teste de clique é contido total ou parcialmente dentro do conteúdo renderizado do destino do teste de clique. Nesse caso, o código de exemplo só está acrescentando resultados do teste de clique à lista de visuais que estão completamente contidos dentro do limite de destino.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  O <xref:System.Windows.Media.HitTestResult> retorno de chamada não deve ser chamado quando o detalhe da interseção for <xref:System.Windows.Media.IntersectionDetail.Empty>.  
  
## <a name="see-also"></a>Consulte também
- [Teste de clique na camada visual](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
- [Teste de clique de geometria em um visual](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)
