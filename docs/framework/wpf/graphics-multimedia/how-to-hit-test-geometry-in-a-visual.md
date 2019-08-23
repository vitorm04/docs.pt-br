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
# <a name="how-to-hit-test-geometry-in-a-visual"></a>Como: Teste de clique de geometria em um visual
Este exemplo mostra como executar um teste de clique em um objeto visual que é composto por um ou mais <xref:System.Windows.Media.Geometry> objetos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como recuperar o <xref:System.Windows.Media.DrawingGroup> de um objeto visual que usa o <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> método. Um teste de clique é então executado no conteúdo renderizado de cada desenho no <xref:System.Windows.Media.DrawingGroup> para determinar qual geometria foi atingida.  
  
> [!NOTE]
> Na maioria dos casos, você usaria o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> método para determinar se um ponto cruza qualquer conteúdo renderizado de um Visual.  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 O <xref:System.Windows.Media.Geometry.FillContains%2A> método é um método sobrecarregado que permite que você clique em teste usando <xref:System.Windows.Point> um ou <xref:System.Windows.Media.Geometry>. Se uma geometria for traçada, o traço poderá se estender para fora dos limites de preenchimento. Nesse caso, talvez você queira chamar <xref:System.Windows.Media.Geometry.StrokeContains%2A> além de. <xref:System.Windows.Media.Geometry.FillContains%2A>  
  
 Você também pode fornecer um <xref:System.Windows.Media.ToleranceType> que é usado para fins de achatamento de Bézier.  
  
> [!NOTE]
> Este exemplo não considera quaisquer transformações ou distorções que possam ser aplicadas à geometria. Além disso, este exemplo não funcionará com um controle com estilo, pois não tem desenhos diretamente associados a ele.  
  
## <a name="see-also"></a>Consulte também

- [Teste de clique na camada visual](hit-testing-in-the-visual-layer.md)
- [Teste de clique usando geometria como um parâmetro](how-to-hit-test-using-geometry-as-a-parameter.md)
