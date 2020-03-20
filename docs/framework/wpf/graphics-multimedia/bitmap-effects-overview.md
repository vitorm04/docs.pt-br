---
title: Visão geral dos efeitos de bitmap
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 4a5e73f21d4ce4988f56c139d13038dca902b5b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187003"
---
# <a name="bitmap-effects-overview"></a>Visão geral dos efeitos de bitmap
Os efeitos do Bitmap permitem que designers e desenvolvedores apliquem efeitos visuais ao conteúdo renderizado da Windows Presentation Foundation (WPF). Por exemplo, os efeitos do bitmap permitem aplicar facilmente um <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> efeito ou um efeito de desfoque em uma imagem ou um botão.  
  
> [!IMPORTANT]
> No Quadro .NET 4 ou <xref:System.Windows.Media.Effects.BitmapEffect> posterior, a classe está obsoleta. Se você tentar <xref:System.Windows.Media.Effects.BitmapEffect> usar a classe, você terá uma exceção obsoleta. A alternativa não obsoleta para a <xref:System.Windows.Media.Effects.BitmapEffect> classe é a <xref:System.Windows.Media.Effects.Effect> classe. Na maioria das <xref:System.Windows.Media.Effects.Effect> situações, a classe é significativamente mais rápida.  

<a name="wpf_effects"></a>
## <a name="wpf-bitmap-effects"></a>Efeitos de bitmap do WPF  
 Os efeitos<xref:System.Windows.Media.Effects.BitmapEffect> do Bitmap (objeto) são operações simples de processamento de pixels. Um efeito bitmap <xref:System.Windows.Media.Imaging.BitmapSource> toma uma entrada e <xref:System.Windows.Media.Imaging.BitmapSource> produz um novo após a aplicação do efeito, como um borrão ou sombra projetada. Cada efeito bitmap expõe propriedades que podem controlar <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> as <xref:System.Windows.Media.Effects.BlurBitmapEffect>propriedades de filtragem, como de .  
  
 Como um caso [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]especial, em , efeitos <xref:System.Windows.Media.Visual> podem ser definidos como propriedades em objetos vivos, como a <xref:System.Windows.Controls.Button> ou <xref:System.Windows.Controls.TextBox>. O processamento de pixel é aplicado e renderizado no tempo de execução. Neste caso, no momento da <xref:System.Windows.Media.Visual> renderização, um é <xref:System.Windows.Media.Imaging.BitmapSource> automaticamente convertido para o <xref:System.Windows.Media.Effects.BitmapEffect>seu equivalente e é alimentado como entrada para o . A saída substitui <xref:System.Windows.Media.Visual> o comportamento de renderização padrão do objeto. É por <xref:System.Windows.Media.Effects.BitmapEffect> isso que os objetos forçam o visual a renderizar em software apenas sem aceleração de hardware no visual quando os efeitos são aplicados.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>simula um objeto que aparece fora de foco.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>cria uma auréola de cor ao redor do perímetro de um objeto.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>cria uma sombra atrás de um objeto.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>cria um bisel que eleva a superfície de uma imagem de acordo com uma curva especificada.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect>cria um mapeamento <xref:System.Windows.Media.Visual> de colisão de a para dar a impressão de profundidade e textura a partir de uma fonte de luz artificial.  
  
> [!NOTE]
> Os efeitos do bitmap WPF são renderizados no modo de software. Qualquer objeto que aplique um efeito também será renderizado em software. A maior redução de desempenho acontece ao usar efeitos de Bitmap em visuais grandes ou ao animar propriedades de um efeito de Bitmap. Isso é não quer dizer que você não deva usar efeitos de Bitmap desta forma, mas deve ter cuidado e testar totalmente para garantir que os usuários tenham a experiência esperada.  
  
> [!NOTE]
> Os efeitos do bitmap WPF não suportam a execução parcial da confiança. Um aplicativo deve ter permissões de confiança total para usar efeitos de bitmap.  
  
<a name="applyeffects"></a>
## <a name="how-to-apply-an-effect"></a>Como aplicar um efeito  
 <xref:System.Windows.Media.Effects.BitmapEffect>é uma <xref:System.Windows.Media.Visual>propriedade em . Portanto, aplicar efeitos ao Visual, <xref:System.Windows.Controls.Button>como <xref:System.Windows.Controls.Image> <xref:System.Windows.Media.DrawingVisual>um <xref:System.Windows.UIElement>, ou , ou , é tão fácil quanto definir uma propriedade. <xref:System.Windows.UIElement.BitmapEffect%2A>pode ser definido <xref:System.Windows.Media.Effects.BitmapEffect> como um único objeto ou múltiplos efeitos podem ser acorrentados usando o <xref:System.Windows.Media.Effects.BitmapEffectGroup> objeto.  
  
 O exemplo a seguir <xref:System.Windows.Media.Effects.BitmapEffect> demonstra [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]como aplicar uma in .  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 O exemplo a seguir <xref:System.Windows.Media.Effects.BitmapEffect> demonstra como aplicar um código em código.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> Quando <xref:System.Windows.Media.Effects.BitmapEffect> a é aplicado a um <xref:System.Windows.Controls.DockPanel> recipiente <xref:System.Windows.Controls.Canvas>de layout, como ou , o efeito é aplicado à árvore visual do elemento ou visual, incluindo todos os seus elementos infantis.  
  
<a name="customeffects"></a>
## <a name="creating-custom-effects"></a>Criando efeitos personalizados  
 O WPF também fornece interfaces não gerenciadas para criar efeitos personalizados que podem ser usados em aplicativos WPF gerenciados. Para material de referência adicional para a criação de efeitos de bitmap personalizados, consulte a documentação [Unmanaged WPF Bitmap Effect](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) (Efeito de bitmap WPF não gerenciado).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Efeito de Bitmap WPF não gerenciado](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Visão geral da geração de imagens](imaging-overview.md)
- [Segurança](../security-wpf.md)
- [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md)
- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
