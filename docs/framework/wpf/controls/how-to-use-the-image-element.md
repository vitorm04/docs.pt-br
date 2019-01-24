---
title: 'Como: Usar o elemento de imagem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Image
- Image control [WPF]
- rendering images [WPF]
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
ms.openlocfilehash: d7aa2e0e9bd33dfcd68bd19b5084fa1666232a5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530795"
---
# <a name="how-to-use-the-image-element"></a>Como: Usar o elemento de imagem
Este exemplo mostra como incluir imagens em um aplicativo usando o <xref:System.Windows.Controls.Image> elemento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como renderizar uma imagem de 200 pixels de largura. Neste exemplo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], a sintaxe de atributo e a de marca de propriedade são usadas para definir a imagem. Para obter mais informações sobre a sintaxe de atributo e a sintaxe de propriedade, consulte [Visão geral de propriedades de dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Um <xref:System.Windows.Media.Imaging.BitmapImage> é usado para definir os dados de origem da imagem e é explicitamente definida para o exemplo de sintaxe de marca de propriedade. Além disso, o <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> do <xref:System.Windows.Media.Imaging.BitmapImage> é definido como a mesma largura que o <xref:System.Windows.FrameworkElement.Width%2A> da <xref:System.Windows.Controls.Image>. Isso é feito para garantir que a quantidade mínima de memória seja usada ao renderizar a imagem.  
  
> [!NOTE]
>  Em geral, se você quiser especificar o tamanho de uma imagem renderizada, especifique apenas o <xref:System.Windows.FrameworkElement.Width%2A> ou o <xref:System.Windows.FrameworkElement.Height%2A> , mas não ambos. Se você especificar apenas um, a taxa de proporção da imagem será preservada. Caso contrário, a imagem pode parecer inesperadamente alongada ou distorcida. Para controlar a imagem do comportamento de alongamento da, use o <xref:System.Windows.Controls.Image.Stretch%2A> e <xref:System.Windows.Controls.Image.StretchDirection%2A> propriedades.  
  
> [!NOTE]
>  Quando você especificar o tamanho de uma imagem com a <xref:System.Windows.FrameworkElement.Width%2A> ou <xref:System.Windows.FrameworkElement.Height%2A>, você deve também definir <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> ou <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> para o mesmo tamanho respectivo.  
  
 O <xref:System.Windows.Controls.Image.Stretch%2A> propriedade determina como a origem da imagem é esticada para preencher o elemento de imagem. Para obter mais informações, consulte a enumeração <xref:System.Windows.Media.Stretch>.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como renderizar uma imagem de 200 pixels de largura usando código.  
  
> [!NOTE]
>  Definindo <xref:System.Windows.Media.Imaging.BitmapImage> propriedades devem ser feitas dentro de um <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> e <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> bloco.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral da geração de imagens](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
