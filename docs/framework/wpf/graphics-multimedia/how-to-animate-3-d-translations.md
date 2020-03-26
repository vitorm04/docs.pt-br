---
title: 'Como: Animar traduções 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations
- 3D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 7d4fff9c74663bd220ad5d15a983bcb639621afd
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112252"
---
# <a name="how-to-animate-3d-translations"></a>Como: Animar traduções 3D
Este tópico demonstra como animar uma transformação de tradução definida em um modelo 3D.  
  
 O código abaixo mostra <xref:System.Windows.Media.Media3D.TranslateTransform3D> a aplicação <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> de <xref:System.Windows.Media.Media3D.GeometryModel3D>um objeto à propriedade de um .  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 A <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> propriedade <xref:System.Windows.Media.Media3D.TranslateTransform3D> deste objeto é animada usando o código abaixo.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra toda a amostra.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
- [Criar uma cena 3D](how-to-create-a-3-d-scene.md)
- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
- [Visão geral de transformações](transforms-overview.md)
