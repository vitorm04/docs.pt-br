---
title: Como pintar uma área com uma imagem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 92969778c04c6ac634a2964c402d6c3439b96b49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186052"
---
# <a name="how-to-paint-an-area-with-an-image"></a>Como pintar uma área com uma imagem
Este exemplo mostra como <xref:System.Windows.Media.ImageBrush> usar a classe para pintar uma área com uma imagem. Um <xref:System.Windows.Media.ImageBrush> exibe uma única imagem, que <xref:System.Windows.Media.ImageBrush.ImageSource%2A> é especificada por sua propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Controls.Control.Background%2A> seguir pinta o <xref:System.Windows.Media.ImageBrush>de um botão usando um .  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 Por padrão, <xref:System.Windows.Media.ImageBrush> um alonga sua imagem para preencher completamente a área que você está pintando. No exemplo anterior, a imagem é esticada para preencher o botão, possivelmente distorcendo a imagem. Você pode controlar esse <xref:System.Windows.Media.TileBrush.Stretch%2A> comportamento <xref:System.Windows.Media.TileBrush> definindo <xref:System.Windows.Media.Stretch.UniformToFill>a propriedade de ou <xref:System.Windows.Media.Stretch.Uniform> , o que faz com que o pincel preserve a proporção da imagem.  
  
 Se você <xref:System.Windows.Media.TileBrush.Viewport%2A> definir <xref:System.Windows.Media.TileBrush.TileMode%2A> as <xref:System.Windows.Media.ImageBrush>propriedades de um , você pode criar um padrão de repetição. O exemplo a seguir pinta um botão usando um padrão que é criado por meio de uma imagem.  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 Para obter mais <xref:System.Windows.Media.ImageBrush> informações sobre a classe, consulte [Pintura com Imagens, Desenhos e Visuais](painting-with-images-drawings-and-visuals.md).  
  
 Este exemplo de código é parte de um <xref:System.Windows.Media.ImageBrush> exemplo maior que é fornecido para a classe. Para obter a amostra completa, consulte [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).  
  
## <a name="see-also"></a>Confira também

- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
