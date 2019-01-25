---
title: 'Como: Pintar uma área com uma imagem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 8c855a81b1bf7cccb59fe22fb2a2056f18ccae72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580727"
---
# <a name="how-to-paint-an-area-with-an-image"></a>Como: Pintar uma área com uma imagem
Este exemplo mostra como usar o <xref:System.Windows.Media.ImageBrush> classe pintar uma área com uma imagem. Uma <xref:System.Windows.Media.ImageBrush> exibe uma única imagem, que é especificada pelo seu <xref:System.Windows.Media.ImageBrush.ImageSource%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir pinta a <xref:System.Windows.Controls.Control.Background%2A> de um botão usando um <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 Por padrão, um <xref:System.Windows.Media.ImageBrush> alonga a imagem para preencher completamente a área que você está pintando. No exemplo anterior, a imagem é esticada para preencher o botão, possivelmente distorcendo a imagem. Você pode controlar esse comportamento, definindo a <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade de <xref:System.Windows.Media.TileBrush> à <xref:System.Windows.Media.Stretch.Uniform> ou <xref:System.Windows.Media.Stretch.UniformToFill>, que faz com que o pincel preserve a taxa de proporção da imagem.  
  
 Se você definir a <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedades de um <xref:System.Windows.Media.ImageBrush>, você pode criar um padrão de repetição. O exemplo a seguir pinta um botão usando um padrão que é criado por meio de uma imagem.  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 Para obter mais informações sobre o <xref:System.Windows.Media.ImageBrush> classe, consulte [pintando com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Este exemplo de código é parte de um exemplo maior fornecido para o <xref:System.Windows.Media.ImageBrush> classe. Para o exemplo completo, consulte [exemplo de ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Consulte também
- [Pintando com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
