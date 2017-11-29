---
title: Como aplicar um desenho a um modelo 3D
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a44607498c6870a598122f41bf2b7ddc5968c61d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Como aplicar um desenho a um modelo 3D
Este exemplo mostra como usar um <xref:System.Windows.Media.DrawingBrush> como o <xref:System.Windows.Media.Media3D.Material> aplicado a um [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelo.  
  
 O código a seguir define uma <xref:System.Windows.Media.DrawingGroup> como o conteúdo de um <xref:System.Windows.Media.DrawingBrush>.  O <xref:System.Windows.Media.DrawingBrush> é definido como o <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> propriedade do <xref:System.Windows.Media.Media3D.DiffuseMaterial> aplicado a um [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plano.  
  
 **Observação:** geralmente é desejável para definir objetos complexos e valores, como o desenho abaixo como recursos que podem ser reutilizados e simplificam seu código. Consulte [recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) para obter mais informações.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o exemplo completo.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Criar uma cena 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Visão geral dos objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Visão geral de elementos gráficos 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
