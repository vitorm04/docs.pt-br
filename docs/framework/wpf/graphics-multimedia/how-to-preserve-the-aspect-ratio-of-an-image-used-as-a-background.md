---
title: Como preservar a taxa de proporção de uma imagem usada como um plano de fundo
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: 906033b43ba657acc873f12a00000189db6796ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562710"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>Como preservar a taxa de proporção de uma imagem usada como um plano de fundo
Este exemplo mostra como usar o <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade de um <xref:System.Windows.Media.ImageBrush> para preservar a taxa de proporção da imagem.  
  
 Por padrão, quando você usa um <xref:System.Windows.Media.ImageBrush> para pintar uma área, seu conteúdo é alongado para preencher completamente a área de saída. Quando a área de saída e a imagem têm proporções diferentes, a imagem é distorcida pelo ajuste.  
  
 Para fazer um <xref:System.Windows.Media.ImageBrush> preservar a proporção de sua imagem, defina o <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade <xref:System.Windows.Media.Stretch.Uniform> ou <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa duas <xref:System.Windows.Media.ImageBrush> objetos para pintar dois retângulos. Cada retângulo tem 300 por 150 pixels, e cada um contém uma imagem de 300 por 300 pixels. O <xref:System.Windows.Media.TileBrush.Stretch%2A> do primeiro pincel é definida como <xref:System.Windows.Media.Stretch.Uniform>e o <xref:System.Windows.Media.TileBrush.Stretch%2A> do segundo pincel é definida como <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 A ilustração a seguir mostra a saída do primeiro pincel, que tem um <xref:System.Windows.Media.TileBrush.Stretch%2A> de <xref:System.Windows.Media.Stretch.Uniform>.  
  
 ![ImageBrush com alongamento uniforme](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 A ilustração a seguir mostra a saída do segundo pincel, que tem um <xref:System.Windows.Media.TileBrush.Stretch%2A> de <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 ![ImageBrush com alongamento UniformToFill](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 Observe que o <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade se comporta de forma idêntica para os outros <xref:System.Windows.Media.TileBrush> objetos, ou seja, para <xref:System.Windows.Media.DrawingBrush> e <xref:System.Windows.Media.VisualBrush>. Para obter mais informações sobre <xref:System.Windows.Media.ImageBrush> e outros <xref:System.Windows.Media.TileBrush> objetos, consulte [pintura com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Observe também que, embora o <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade aparece para especificar como o <xref:System.Windows.Media.TileBrush> conteúdo ajusta-se para sua área de saída, ela na verdade especifica como o <xref:System.Windows.Media.TileBrush> conteúdo expande para preencher seu tile base. Para obter mais informações, consulte <xref:System.Windows.Media.TileBrush>.  
  
 Este exemplo de código é parte de um exemplo maior fornecido para a <xref:System.Windows.Media.ImageBrush> classe. Para o exemplo completo, consulte [ImageBrush exemplo](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.TileBrush>  
 [Pintando com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
