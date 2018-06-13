---
title: Como aplicar material à frente e ao verso de um objeto 3D
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 0ccf0aa045886f0731cd22ecdc8e14fa6af55fd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559726"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a>Como aplicar material à frente e ao verso de um objeto 3D
O exemplo a seguir mostra como aplicar um <xref:System.Windows.Media.Media3D.Material> de objeto para a frente e verso um 3D e animar o objeto para mostrar ambos os lados do objeto. O <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> propriedade de um <xref:System.Windows.Media.Media3D.GeometryModel3D> é usado para aplicar um vermelho <xref:System.Windows.Media.Brush> para o lado frontal do objeto e o <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> propriedade do <xref:System.Windows.Media.Media3D.GeometryModel3D> é usado para aplicar um azul <xref:System.Windows.Media.Brush> a parte traseira do objeto. O código a seguir mostra o aplicativo de materiais para o objeto:  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o exemplo completo.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 [Criar uma cena 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Visão geral de elementos gráficos 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Animar propriedades de material em uma cena 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [Aplicar material emissivo a um objeto 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
