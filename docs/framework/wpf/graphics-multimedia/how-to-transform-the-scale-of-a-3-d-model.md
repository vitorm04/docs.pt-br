---
title: 'Como: Transformar a escala de um modelo 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: afe18cea95be945313ef78a690c58950a3fff9b0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378776"
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a>Como: Transformar a escala de um modelo 3D
Este exemplo mostra como dimensionar um objeto 3D. Para dimensionar um objeto 3D, usar um <xref:System.Windows.Media.Media3D.ScaleTransform3D>. O <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, e <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> propriedades redimensionar o elemento pelo fator especificado. Por exemplo, um <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> valor de 1,5 alonga um objeto em 150% de sua largura original. Um <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> valor de 0,5 reduz a altura de um objeto em 50%. O código a seguir mostra o uso uma <xref:System.Windows.Media.Media3D.ScaleTransform3D> como a transformação para um <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o exemplo completo.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também
- [Animar translações 3D](how-to-animate-3-d-translations.md)
- [Criar uma cena 3D](how-to-create-a-3-d-scene.md)
- [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md)
