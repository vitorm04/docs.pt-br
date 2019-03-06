---
title: 'Como: Animar translações 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 0290beac5a92a955b39d0b8fcc24705346c2964a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351912"
---
# <a name="how-to-animate-3-d-translations"></a>Como: Animar translações 3D
Este tópico demonstra como animar uma transformação de conversão definida em um [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelo.  
  
 O código a seguir mostra o aplicativo de um <xref:System.Windows.Media.Media3D.TranslateTransform3D> do objeto para o <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> propriedade de um <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 O <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> propriedade deste <xref:System.Windows.Media.Media3D.TranslateTransform3D> objeto é animado usando o código a seguir.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o exemplo completo.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral da animação](animation-overview.md)
- [Criar uma cena 3D](how-to-create-a-3-d-scene.md)
- [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md)
- [Visão geral de transformações](transforms-overview.md)
