---
title: 'Como: Transformar a escala de um modelo 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3D objects
- 3D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: be41a0e10929912c1b54bf7140d743d9453199bf
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111979"
---
# <a name="how-to-transform-the-scale-of-a-3d-model"></a>Como: Transformar a escala de um modelo 3D
Este exemplo mostra como dimensionar um objeto 3D. Para dimensionar um objeto <xref:System.Windows.Media.Media3D.ScaleTransform3D>3D, use um . As <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>propriedades <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> e propriedades redimensionam o elemento pelo fator especificado. Por exemplo, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> um valor de 1,5 estende um objeto a 150% de sua largura original. Um <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> valor de 0,5 reduz a altura de um objeto em 50%. O código abaixo <xref:System.Windows.Media.Media3D.ScaleTransform3D> mostra usando um <xref:System.Windows.Media.Media3D.GeometryModel3D>como a transformação para um .  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra toda a amostra.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>Confira também

- [Animar traduções 3D](how-to-animate-3-d-translations.md)
- [Criar uma cena 3D](how-to-create-a-3-d-scene.md)
- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
