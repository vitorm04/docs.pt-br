---
title: 'Como: Aplicar um desenho a um modelo 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: a20b89a7359fc85d9790ac02dd2b173452df8c22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125028"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Como: Aplicar um desenho a um modelo 3D
Este exemplo mostra como usar um <xref:System.Windows.Media.DrawingBrush> como o <xref:System.Windows.Media.Media3D.Material> aplicados a um [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelo.  
  
 O código a seguir define uma <xref:System.Windows.Media.DrawingGroup> como o conteúdo de um <xref:System.Windows.Media.DrawingBrush>.  O <xref:System.Windows.Media.DrawingBrush> é definido como o <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> propriedade da <xref:System.Windows.Media.Media3D.DiffuseMaterial> aplicado a um [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plano.  
  
 **Observação:** Muitas vezes é desejável para definir objetos complexos e valores, como o desenho abaixo como recursos que podem ser reutilizados e simplificam seu código. Ver [recursos XAML](../advanced/xaml-resources.md) para obter mais informações.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o exemplo completo.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também

- [Recursos XAML](../advanced/xaml-resources.md)
- [Criar uma cena 3D](how-to-create-a-3-d-scene.md)
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)
- [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md)
