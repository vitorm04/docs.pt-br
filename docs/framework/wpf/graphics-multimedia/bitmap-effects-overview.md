---
title: '{1&gt;{2&gt;Visão geral de efeitos de bitmap&lt;2}&lt;1}'
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 4a5c304363efe7d0e9bd9e14ff916f8d852ab3a8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636010"
---
# <a name="bitmap-effects-overview"></a>{1&gt;{2&gt;Visão geral de efeitos de bitmap&lt;2}&lt;1}
Os efeitos de bitmap permitem que designers e desenvolvedores apliquem efeitos visuais ao conteúdo do Windows Presentation Foundation renderizado (WPF). Por exemplo, efeitos de bitmap permitem que você aplique facilmente um efeito de <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> ou um efeito de desfoque a uma imagem ou a um botão.  
  
> [!IMPORTANT]
> No .NET Framework 4 ou posterior, a classe <xref:System.Windows.Media.Effects.BitmapEffect> é obsoleta. Se você tentar usar a classe <xref:System.Windows.Media.Effects.BitmapEffect>, receberá uma exceção obsoleta. A alternativa não obsoleta para a classe <xref:System.Windows.Media.Effects.BitmapEffect> é a classe <xref:System.Windows.Media.Effects.Effect>. Na maioria das situações, a classe <xref:System.Windows.Media.Effects.Effect> é significativamente mais rápida.  

<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>Efeitos de bitmap do WPF  
 Os efeitos de bitmap (<xref:System.Windows.Media.Effects.BitmapEffect> objeto) são operações de processamento de pixel simples. Um efeito de bitmap usa uma <xref:System.Windows.Media.Imaging.BitmapSource> como uma entrada e produz um novo <xref:System.Windows.Media.Imaging.BitmapSource> depois de aplicar o efeito, como uma sombra desfoque ou "soltar". Cada efeito de bitmap expõe propriedades que podem controlar as propriedades de filtragem, como <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> de <xref:System.Windows.Media.Effects.BlurBitmapEffect>.  
  
 Como um caso especial, no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], os efeitos podem ser definidos como propriedades em objetos <xref:System.Windows.Media.Visual> ao vivo, como um <xref:System.Windows.Controls.Button> ou <xref:System.Windows.Controls.TextBox>. O processamento de pixel é aplicado e renderizado no tempo de execução. Nesse caso, no momento da renderização, um <xref:System.Windows.Media.Visual> é convertido automaticamente em seu <xref:System.Windows.Media.Imaging.BitmapSource> equivalente e é alimentado como entrada para o <xref:System.Windows.Media.Effects.BitmapEffect>. A saída substitui o comportamento de renderização padrão do objeto <xref:System.Windows.Media.Visual>. É por isso que <xref:System.Windows.Media.Effects.BitmapEffect> objetos forçam os visuais a serem renderizados somente em software, ou seja, sem aceleração de hardware em visuais quando efeitos são aplicados.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect> simula um objeto que aparece fora do foco.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> cria um halo de cor em todo o perímetro de um objeto.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> cria uma sombra por trás de um objeto.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect> cria um bisel que gera a superfície de uma imagem de acordo com uma curva especificada.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect> cria um mapeamento de relevo de uma <xref:System.Windows.Media.Visual> para dar a impressão de profundidade e textura de uma fonte de luz artificial.  
  
> [!NOTE]
> Os efeitos de bitmap do WPF são renderizados no modo de software. Qualquer objeto que aplique um efeito também será renderizado em software. A maior redução de desempenho acontece ao usar efeitos de Bitmap em visuais grandes ou ao animar propriedades de um efeito de Bitmap. Isso é não quer dizer que você não deva usar efeitos de Bitmap desta forma, mas deve ter cuidado e testar totalmente para garantir que os usuários tenham a experiência esperada.  
  
> [!NOTE]
> Os efeitos de bitmap do WPF não dão suporte à execução de confiança parcial. Um aplicativo deve ter permissões de confiança total para usar efeitos de bitmap.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Como aplicar um efeito  
 <xref:System.Windows.Media.Effects.BitmapEffect> é uma propriedade em <xref:System.Windows.Media.Visual>. Portanto, aplicar efeitos a visuais, como um <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>ou <xref:System.Windows.UIElement>, é tão fácil quanto definir uma propriedade. <xref:System.Windows.UIElement.BitmapEffect%2A> pode ser definido como um único objeto <xref:System.Windows.Media.Effects.BitmapEffect> ou vários efeitos podem ser encadeados usando o objeto <xref:System.Windows.Media.Effects.BitmapEffectGroup>.  
  
 O exemplo a seguir demonstra como aplicar um <xref:System.Windows.Media.Effects.BitmapEffect> no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 O exemplo a seguir demonstra como aplicar um <xref:System.Windows.Media.Effects.BitmapEffect> no código.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> Quando um <xref:System.Windows.Media.Effects.BitmapEffect> é aplicado a um contêiner de layout, como <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.Canvas>, o efeito é aplicado à árvore visual do elemento ou Visual, incluindo todos os seus elementos filho.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Criando efeitos personalizados  
 O WPF também fornece interfaces não gerenciadas para criar efeitos personalizados que podem ser usados em aplicativos WPF gerenciados. Para material de referência adicional para a criação de efeitos de bitmap personalizados, consulte a documentação [Unmanaged WPF Bitmap Effect](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) (Efeito de bitmap WPF não gerenciado).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Efeito de bitmap do WPF não gerenciado](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Visão geral da geração de imagens](imaging-overview.md)
- [Security](../security-wpf.md)
- [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md)
- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
