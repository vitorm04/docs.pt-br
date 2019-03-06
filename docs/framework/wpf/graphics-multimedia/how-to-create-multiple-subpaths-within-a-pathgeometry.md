---
title: 'Como: Criar vários subcaminhos dentro de um PathGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 0b57d0441c1aa9d5972af1f1c6b989aacba7f87f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353356"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a>Como: Criar vários subcaminhos dentro de um PathGeometry
Este exemplo mostra como criar vários subcaminhos em um <xref:System.Windows.Media.PathGeometry>. Para criar vários subcaminhos, você cria um <xref:System.Windows.Media.PathFigure> para cada subcaminho.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria dois subcaminhos, cada um de um triângulo.  
  
 [!code-xaml[GeometrySample#38](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 O exemplo a seguir mostra como criar vários subcaminhos usando um <xref:System.Windows.Shapes.Path> e [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sintaxe de atributo. Cada `M` cria um novo subcaminho para que o exemplo cria dois subcaminhos que cada Desenha um triângulo.  
  
 [!code-xaml[GeometrySample#58](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 (Observe que essa sintaxe de atributo na verdade cria um <xref:System.Windows.Media.StreamGeometry>, uma versão leve de um <xref:System.Windows.Media.PathGeometry>. Para obter mais informações, consulte o [sintaxe de marcação de caminho](path-markup-syntax.md) página.)  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de geometria](geometry-overview.md)
