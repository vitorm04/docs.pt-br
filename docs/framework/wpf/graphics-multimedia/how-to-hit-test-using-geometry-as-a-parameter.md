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
ms.openlocfilehash: 8bed7784b00f49178c9a87def74b62f7ce620ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923402"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>Como: Teste de clique usando geometria como um parâmetro
Este exemplo mostra como executar um teste de clique em um objeto visual usando um <xref:System.Windows.Media.Geometry> como um parâmetro de teste de clique.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como configurar um teste de clique usando <xref:System.Windows.Media.GeometryHitTestParameters> para o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> método. O <xref:System.Windows.Point> valor que é passado para o `OnMouseDown` método é usado para criar um <xref:System.Windows.Media.Geometry> objeto a fim de expandir o intervalo do teste de clique.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 A <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> propriedade de <xref:System.Windows.Media.GeometryHitTestResult> fornece informações sobre os resultados de um teste de clique que usa <xref:System.Windows.Media.Geometry> um como um parâmetro de teste de clique. A ilustração a seguir mostra a relação entre a geometria de teste de clique (o círculo azul) e o conteúdo renderizado do objeto visual de destino (o quadrado vermelho).  
  
 ![Diagrama que mostra o IntersectionDetail usado em testes de clique.](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 O exemplo a seguir mostra como implementar um retorno de chamada de teste <xref:System.Windows.Media.Geometry> de clique quando um é usado como um parâmetro de teste de clique. O `result` parâmetro é convertido <xref:System.Windows.Media.GeometryHitTestResult> em a para <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> recuperar o valor da propriedade. O valor da propriedade permite que você determine se <xref:System.Windows.Media.Geometry> o parâmetro de teste de clique está completo ou parcialmente contido no conteúdo renderizado do destino do teste de clique. Nesse caso, o código de exemplo só está acrescentando resultados do teste de clique à lista de visuais que estão completamente contidos dentro do limite de destino.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
> O <xref:System.Windows.Media.HitTestResult> retorno de chamada não deve ser chamado quando o detalhe da <xref:System.Windows.Media.IntersectionDetail.Empty>interseção é.  
  
## <a name="see-also"></a>Consulte também

- [Teste de clique na camada visual](hit-testing-in-the-visual-layer.md)
- [Teste de clique de geometria em um visual](how-to-hit-test-geometry-in-a-visual.md)
