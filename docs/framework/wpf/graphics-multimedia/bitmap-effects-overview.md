---
title: Visão geral dos efeitos de bitmap
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: f2fa42d5d63cad6a71efd259416dad3416bf2d72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935297"
---
# <a name="bitmap-effects-overview"></a>Visão geral dos efeitos de bitmap
Os efeitos de bitmap permitem que designers e desenvolvedores apliquem efeitos visuais ao conteúdo do Windows Presentation Foundation renderizado (WPF). Por exemplo, efeitos de bitmap permitem que você aplique facilmente <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> um efeito ou um efeito de desfoque a uma imagem ou a um botão.  
  
> [!IMPORTANT]
> No .NET Framework 4 ou posterior, a <xref:System.Windows.Media.Effects.BitmapEffect> classe é obsoleta. Se você tentar usar a <xref:System.Windows.Media.Effects.BitmapEffect> classe, receberá uma exceção obsoleta. A alternativa não obsoleta para a <xref:System.Windows.Media.Effects.BitmapEffect> classe é a <xref:System.Windows.Media.Effects.Effect> classe. Na maioria das situações, <xref:System.Windows.Media.Effects.Effect> a classe é significativamente mais rápida.  

<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>Efeitos de bitmap do WPF  
 Os efeitos de<xref:System.Windows.Media.Effects.BitmapEffect> bitmap (objeto) são operações de processamento de pixel simples. Um efeito de bitmap usa <xref:System.Windows.Media.Imaging.BitmapSource> um como entrada e produz um novo <xref:System.Windows.Media.Imaging.BitmapSource> depois de aplicar o efeito, como um desfoque ou sombra. Cada efeito <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> de bitmap expõe propriedades que podem controlar as propriedades de filtragem, como <xref:System.Windows.Media.Effects.BlurBitmapEffect>de.  
  
 Como um caso especial, no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], os efeitos podem ser definidos como propriedades em <xref:System.Windows.Media.Visual> objetos dinâmicos, como <xref:System.Windows.Controls.Button> um <xref:System.Windows.Controls.TextBox>ou. O processamento de pixel é aplicado e renderizado no tempo de execução. Nesse caso, no momento da renderização, um <xref:System.Windows.Media.Visual> é automaticamente convertido em seu <xref:System.Windows.Media.Imaging.BitmapSource> equivalente e é alimentado como entrada para o <xref:System.Windows.Media.Effects.BitmapEffect>. A saída substitui o <xref:System.Windows.Media.Visual> comportamento de renderização padrão do objeto. É por isso <xref:System.Windows.Media.Effects.BitmapEffect> que os objetos forçam os visuais a serem renderizados apenas em software, ou seja, sem aceleração de hardware em visuais quando efeitos são aplicados.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>simula um objeto que aparece fora do foco.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>Cria um halo de cor em todo o perímetro de um objeto.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>Cria uma sombra por trás de um objeto.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>Cria um bisel que gera a superfície de uma imagem de acordo com uma curva especificada.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect>Cria um mapeamento de relevo <xref:System.Windows.Media.Visual> de um para dar a impressão de profundidade e textura de uma fonte de luz artificial.  
  
> [!NOTE]
> Os efeitos de bitmap [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] são renderizados em um modo de software. Qualquer objeto que aplique um efeito também será renderizado em software. A maior redução de desempenho acontece ao usar efeitos de Bitmap em visuais grandes ou ao animar propriedades de um efeito de Bitmap. Isso é não quer dizer que você não deva usar efeitos de Bitmap desta forma, mas deve ter cuidado e testar totalmente para garantir que os usuários tenham a experiência esperada.  
  
> [!NOTE]
> Os efeitos de bitmap [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] não têm suporte para execução em confiança parcial. Um aplicativo deve ter permissões de confiança total para usar efeitos de bitmap.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Como aplicar um efeito  
 <xref:System.Windows.Media.Effects.BitmapEffect>é uma propriedade em <xref:System.Windows.Media.Visual>. Portanto, aplicar efeitos a visuais, como <xref:System.Windows.Controls.Button>um, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>ou <xref:System.Windows.UIElement>, é tão fácil quanto definir uma propriedade. <xref:System.Windows.UIElement.BitmapEffect%2A>pode ser definido como um único <xref:System.Windows.Media.Effects.BitmapEffect> objeto ou vários efeitos podem ser encadeados usando o <xref:System.Windows.Media.Effects.BitmapEffectGroup> objeto.  
  
 O exemplo a seguir demonstra como aplicar um <xref:System.Windows.Media.Effects.BitmapEffect> no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 O exemplo a seguir demonstra como aplicar um <xref:System.Windows.Media.Effects.BitmapEffect> código no.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> Quando um <xref:System.Windows.Media.Effects.BitmapEffect> é aplicado a um contêiner de layout, <xref:System.Windows.Controls.DockPanel> como ou <xref:System.Windows.Controls.Canvas>, o efeito é aplicado à árvore visual do elemento ou Visual, incluindo todos os seus elementos filho.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Criando efeitos personalizados  
 O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] também fornece interfaces não gerenciadas para criar efeitos personalizados que podem ser usados em aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gerenciados. Para material de referência adicional para a criação de efeitos de bitmap personalizados, consulte a documentação [Unmanaged WPF Bitmap Effect](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) (Efeito de bitmap WPF não gerenciado).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Efeito de bitmap do WPF não gerenciado](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Visão geral da geração de imagens](imaging-overview.md)
- [Segurança](../security-wpf.md)
- [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md)
- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
