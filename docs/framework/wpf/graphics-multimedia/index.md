---
title: Gráficos e multimídia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: 8636afcc5b63b71dc729812a7f3eb4945ba49494
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112031"
---
# <a name="graphics-and-multimedia"></a>Gráficos e multimídia

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece suporte para multimídia, gráficos vetoriais, animação e composição de conteúdo, tornando mais fácil para os desenvolvedores criar interfaces do usuário e conteúdo interessantes. Usando o Visual Studio, você pode criar gráficos vetoriais ou animações complexas e integrar mídia em seus aplicativos.

Este tópico apresenta os recursos de gráficos, animação e mídia de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], que permitem que você adicione gráficos, efeitos de transição, som e vídeo a seus aplicativos.

> [!NOTE]
> Não é recomendável usar tipos do WPF em um serviço Windows. Se você tentar usar tipos do WPF em um serviço Windows, será possível que o serviço não funcione conforme o esperado.

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Novidades sobre gráficos e multimídia no WPF 4

Várias alterações foram feitas com relação aos gráficos e animações.

- Arredondamento de layout

  Quando a borda de um objeto está no meio de um dispositivo de pixel, o sistema de gráficos independente de DPI pode criar artefatos de renderização, como bordas desfocadas ou semitransparentes. Versões anteriores do WPF incluíam o ajuste de pixels para ajudar a lidar com esse caso. O Silverlight 2 introduziu o arredondamento de layout, que é outra maneira de mover elementos para que as bordas fiquem nos limites de pixels inteiros. O WPF agora suporta arredondamento de layout com a <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> propriedade anexada em <xref:System.Windows.FrameworkElement>.

- Composição em cache

  Usando as <xref:System.Windows.Media.BitmapCache> novas <xref:System.Windows.Media.BitmapCacheBrush> e classes, você pode armazenar uma parte complexa da árvore visual como um bitmap e melhorar muito o tempo de renderização. O bitmap permanece responsivo a entradas do usuário, como cliques do mouse e você pode pintá-lo em outros elementos, como faria com qualquer pincel.

- Suporte para o Sombreador de Pixel 3

  O WPF 4 se <xref:System.Windows.Media.Effects.ShaderEffect> baseia em cima do suporte introduzido no WPF 3.5 SP1, permitindo que os aplicativos escrevam efeitos usando a versão 3.0 do Pixel Shader (PS). O modelo de sombreador PS 3.0 é mais sofisticado do que o PS 2.0, o que permite ainda mais efeitos em hardware com suporte.

- Funções de easing

  Você pode aprimorar animações com funções de easing, que fornecem controle adicional sobre o comportamento das animações. Por exemplo, você <xref:System.Windows.Media.Animation.ElasticEase> pode aplicar um a uma animação para dar à animação um comportamento elástico. Para obter mais informações, consulte <xref:System.Windows.Media.Animation> os tipos de facilitação no namespace.

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>Gráficos e renderização

O WPF inclui suporte para gráficos 2D de alta qualidade. A funcionalidade inclui pincéis, geometrias, imagens, formas e transformações. Para obter mais informações, consulte [Gráficos](graphics.md). A renderização de elementos <xref:System.Windows.Media.Visual> gráficos é baseada na classe. A estrutura de objetos visuais na tela é descrita pela árvore visual. Para obter mais informações, consulte [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md).

### <a name="2d-shapes"></a>Formas 2D

O WPF fornece uma biblioteca de formas 2D comumente usadas e com vetores, como retângulos e elipses, que a ilustração a seguir mostra.

![Diagrama mostrando elipses e retângulos.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

Essas formas intrínsecas do WPF não são apenas formas: são elementos programáveis que implementam muitos dos recursos que você espera dos controles mais comuns, que incluem entrada de teclado e mouse. O exemplo a seguir <xref:System.Windows.UIElement.MouseUp> mostra como lidar com <xref:System.Windows.Shapes.Ellipse> o evento levantado clicando em um elemento.

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="Window1" >
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />
</Window>
```

```csharp
public partial class Window1  : Window
{
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)
    {
        MessageBox.Show("You clicked the ellipse!");
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)
        MessageBox.Show("You clicked the ellipse!")
    End Sub
End Class
```

A ilustração a seguir mostra a saída para a marcação [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anterior e code-behind.

![Uma caixa de mensagem dizendo "Você clicou na elipse!"](./media/index/messagebox-text-output.png)

Para obter mais informações, consulte [Visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md). Para ver um exemplo introdutório, consulte [Amostra de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).

### <a name="2d-geometries"></a>Geometrias 2D

Quando as formas 2D que o WPF fornece não são suficientes, você pode usar o suporte do WPF para geometrias e caminhos para criar o seu próprio. A ilustração a seguir mostra como você pode usar geometrias para criar formas, como um pincel de desenho, e para cortar outros elementos wpf.

![Captura de tela mostrando como você pode usar geometrias para criar formas.](./media/index/use-geometries-create-shapes.png)

Para obter mais informações, consulte [Geometry Overview](geometry-overview.md). Para ver um exemplo introdutório, consulte [Amostra de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).

### <a name="2d-effects"></a>Efeitos 2D

O WPF fornece uma biblioteca de classes 2D que você pode usar para criar uma variedade de efeitos. A capacidade de renderização 2D do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] WPF fornece a capacidade de pintar elementos que têm gradientes, bitmaps, desenhos e vídeos; e manipulá-los usando rotação, escala e distorção. A ilustração a seguir dá um exemplo dos muitos efeitos que você pode obter usando pincéis WPF.

![Ilustração mostrando os diferentes pincéis wpf e elementos de pintura.](./media/index/brushes-paint-elements.png)

Para obter mais informações, consulte [Visão geral do WPF Brushes](wpf-brushes-overview.md). Para ver um exemplo introdutório, consulte [Amostra de pincéis](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).

<a name="rendering"></a>

## <a name="3d-rendering"></a>Renderização 3D

O WPF fornece um conjunto de recursos de renderização 3D que se integram com [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]suporte gráfico 2D no WPF para que você crie layout mais emocionante e visualização de dados. Em uma extremidade do espectro, o WPF permite que você produza imagens 2D nas superfícies de formas 3D, o que a ilustração a seguir demonstra.

![Captura de tela de uma amostra mostrando formas 3D com diferentes texturas.](./media/index/visual-three-dimensional-shape.png)

Para obter mais informações, consulte [visão geral de gráficos 3D](3-d-graphics-overview.md). Para obter uma amostra introdutória, consulte [3D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).

<a name="animation"></a>

## <a name="animation"></a>Animação

Use a animação para fazer controles e elementos crescerem, tremerem, rodarem e esmaecerem, e para criar transições de página interessantes e muito mais. Como o WPF permite que você anime a maioria das propriedades, não só você pode animar a maioria dos objetos WPF, você também pode usar o WPF para animar objetos personalizados que você cria.

![Captura de tela de um cubo animado.](./media/index/animate-custom-objects.png)

Para obter mais informações, consulte [Visão geral da animação](animation-overview.md). Para obter um exemplo introdutório, consulte [Galeria de exemplos de animação](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).

<a name="media"></a>

## <a name="media"></a>Mídia

Imagens, vídeo e áudio são formas de mídia avançadas que transmitem informações experiências do usuário.

### <a name="images"></a>Imagens

Imagens, que incluem ícones, planos de fundo e até mesmo partes de animações, são uma parte principal da maioria dos aplicativos. Como você frequentemente precisa usar imagens, o WPF expõe a capacidade de trabalhar com elas de várias maneiras. A ilustração a seguir mostra apenas uma dessas formas.

![Captura de tela de amostra de estilo](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

Para obter mais informações, consulte [Visão geral de imagens](imaging-overview.md).

### <a name="video-and-audio"></a>Áudio e vídeo

Uma característica central dos recursos gráficos do WPF é fornecer suporte nativo para trabalhar com multimídia, que inclui vídeo e áudio. O exemplo a seguir mostra como inserir um player de mídia em um aplicativo.

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement>é capaz de reproduzir tanto vídeo quanto áudio, e é extensível o suficiente para permitir a fácil criação de UIs personalizadas.

Para obter mais informações, consulte [Visão geral de multimídia](multimedia-overview.md).

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Visão geral de formas e desenhos básicos no WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md)
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Tópicos explicativos de animação e tempo](animation-and-timing-how-to-topics.md)
- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
- [Visão geral de multimídia](multimedia-overview.md)
