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
ms.openlocfilehash: 164eee7c10d9e388c6e6ee695af479ca2d6974b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958322"
---
# <a name="how-to-use-the-image-element"></a>Como: Usar o elemento de imagem
Este exemplo mostra como incluir imagens em um aplicativo usando o <xref:System.Windows.Controls.Image> elemento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como renderizar uma imagem de 200 pixels de largura. Neste exemplo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], a sintaxe de atributo e a de marca de propriedade são usadas para definir a imagem. Para obter mais informações sobre a sintaxe de atributo e a sintaxe de propriedade, consulte [Visão geral de propriedades de dependência](../advanced/dependency-properties-overview.md). Um <xref:System.Windows.Media.Imaging.BitmapImage> é usado para definir os dados de origem da imagem e é explicitamente definido para o exemplo de sintaxe de marca de propriedade. Além disso, o <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> <xref:System.Windows.Media.Imaging.BitmapImage> de é definido com <xref:System.Windows.FrameworkElement.Width%2A> a mesma <xref:System.Windows.Controls.Image>largura do do. Isso é feito para garantir que a quantidade mínima de memória seja usada ao renderizar a imagem.  
  
> [!NOTE]
> Em geral, se você quiser especificar o tamanho de uma imagem renderizada, especifique somente o <xref:System.Windows.FrameworkElement.Width%2A> ou o <xref:System.Windows.FrameworkElement.Height%2A> , mas não ambos. Se você especificar apenas um, a taxa de proporção da imagem será preservada. Caso contrário, a imagem pode parecer inesperadamente alongada ou distorcida. Para controlar o comportamento de alongamento da imagem, <xref:System.Windows.Controls.Image.Stretch%2A> use <xref:System.Windows.Controls.Image.StretchDirection%2A> as propriedades e.  
  
> [!NOTE]
> Quando você especifica o tamanho de uma imagem <xref:System.Windows.FrameworkElement.Width%2A> com ou <xref:System.Windows.FrameworkElement.Height%2A>, também deve definir um <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> ou <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> o mesmo tamanho respectivo.  
  
 A <xref:System.Windows.Controls.Image.Stretch%2A> propriedade determina como a origem da imagem é ampliada para preencher o elemento Image. Para obter mais informações, consulte a enumeração <xref:System.Windows.Media.Stretch>.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como renderizar uma imagem de 200 pixels de largura usando código.  
  
> [!NOTE]
> As <xref:System.Windows.Media.Imaging.BitmapImage> Propriedades de configuração devem ser feitas <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> dentro <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> de um bloco e.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da geração de imagens](../graphics-multimedia/imaging-overview.md)
