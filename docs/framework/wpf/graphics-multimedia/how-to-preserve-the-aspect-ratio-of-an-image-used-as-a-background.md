---
title: Como preservar a taxa de proporção de uma imagem usada como um plano de fundo
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: b467fcd353994faef19b5a997e03d6582789eac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186025"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>Como preservar a taxa de proporção de uma imagem usada como um plano de fundo
Este exemplo mostra como <xref:System.Windows.Media.TileBrush.Stretch%2A> usar <xref:System.Windows.Media.ImageBrush> a propriedade de um para preservar a proporção da imagem.  
  
 Por padrão, quando <xref:System.Windows.Media.ImageBrush> você usa um para pintar uma área, seu conteúdo se estende para preencher completamente a área de saída. Quando a área de saída e a imagem têm proporções diferentes, a imagem é distorcida pelo ajuste.  
  
 Para preservar <xref:System.Windows.Media.ImageBrush> a proporção de sua <xref:System.Windows.Media.TileBrush.Stretch%2A> imagem, <xref:System.Windows.Media.Stretch.Uniform> <xref:System.Windows.Media.Stretch.UniformToFill>defina a propriedade para ou .  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Media.ImageBrush> seguir usa dois objetos para pintar dois retângulos. Cada retângulo tem 300 por 150 pixels, e cada um contém uma imagem de 300 por 300 pixels. A <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade do primeiro pincel <xref:System.Windows.Media.Stretch.Uniform>está <xref:System.Windows.Media.TileBrush.Stretch%2A> definida para , e <xref:System.Windows.Media.Stretch.UniformToFill>a propriedade do segundo pincel é definida como .  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 A ilustração a seguir mostra a saída <xref:System.Windows.Media.TileBrush.Stretch%2A> do <xref:System.Windows.Media.Stretch.Uniform>primeiro pincel, que tem uma configuração de .  
  
 ![Pincel de imagem com alongamento uniforme](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 A próxima ilustração mostra a saída do <xref:System.Windows.Media.TileBrush.Stretch%2A> segundo <xref:System.Windows.Media.Stretch.UniformToFill>pincel, que tem uma configuração de .  
  
 ![Pincel de imagem com alongamento uniformepara preenchimento](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 Observe que <xref:System.Windows.Media.TileBrush.Stretch%2A> a propriedade se comporta <xref:System.Windows.Media.TileBrush> de forma idêntica <xref:System.Windows.Media.DrawingBrush> para <xref:System.Windows.Media.VisualBrush>os outros objetos, ou seja, para e . Para obter <xref:System.Windows.Media.ImageBrush> mais informações <xref:System.Windows.Media.TileBrush> sobre e os outros objetos, consulte [Pintura com Imagens, Desenhos e Visuais](painting-with-images-drawings-and-visuals.md).  
  
 Observe também que, <xref:System.Windows.Media.TileBrush.Stretch%2A> embora a propriedade <xref:System.Windows.Media.TileBrush> pareça especificar como o conteúdo se estende <xref:System.Windows.Media.TileBrush> para se adequar à sua área de saída, ele realmente especifica como o conteúdo se estende para preencher seu bloco base. Para obter mais informações, consulte <xref:System.Windows.Media.TileBrush>.  
  
 Este exemplo de código é parte de um <xref:System.Windows.Media.ImageBrush> exemplo maior que é fornecido para a classe. Para obter a amostra completa, consulte [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.TileBrush>
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
