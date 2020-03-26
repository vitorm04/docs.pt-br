---
title: 'Como: Aplicar material na frente e atrás de um objeto 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 5c24879d97e7857fb07fcef4a9ba8efa901e4a39
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112135"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3d-object"></a>Como: Aplicar material na frente e atrás de um objeto 3D
O exemplo a seguir <xref:System.Windows.Media.Media3D.Material> mostra como aplicar um na frente e atrás de um objeto 3D e animar o objeto para mostrar ambos os lados do objeto. A <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> propriedade <xref:System.Windows.Media.Media3D.GeometryModel3D> de a é <xref:System.Windows.Media.Brush> usada para aplicar um vermelho <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> na <xref:System.Windows.Media.Media3D.GeometryModel3D> parte frontal do <xref:System.Windows.Media.Brush> objeto e a propriedade do é usada para aplicar um azul na parte traseira do objeto. O código abaixo mostra a aplicação dos materiais ao objeto:  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra toda a amostra.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Confira também

- [Criar uma cena 3D](how-to-create-a-3-d-scene.md)
- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
- [Propriedades de material animado em uma cena 3D](how-to-animate-material-properties-in-a-3-d-scene.md)
- [Aplique material emissivo a um objeto 3D](how-to-apply-emissive-material-to-a-3-d-object.md)
