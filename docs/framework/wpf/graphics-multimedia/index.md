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
ms.openlocfilehash: 58ee58577b9ff71112103abb4d33c8b85d3c806f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786062"
---
# <a name="graphics-and-multimedia"></a>Gráficos e multimídia

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece suporte para multimídia, gráficos vetoriais, animação e composição de conteúdo, tornando mais fácil para os desenvolvedores criem interfaces de usuário interessantes e de conteúdo. Usando [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], você pode criar gráficos vetoriais ou animações complexas e integrar mídias em seus aplicativos.

Este tópico apresenta os recursos de gráficos, animação e mídia de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], que permitem que você adicione gráficos, efeitos de transição, som e vídeo a seus aplicativos.

> [!NOTE]
> Não é recomendável usar tipos do WPF em um serviço Windows. Se você tentar usar tipos do WPF em um serviço Windows, será possível que o serviço não funcione conforme o esperado.

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Novidades sobre gráficos e multimídia no WPF 4

Várias alterações foram feitas com relação aos gráficos e animações.

- Arredondamento de layout

  Quando a borda de um objeto está no meio de um dispositivo de pixel, o sistema de gráficos independente de DPI pode criar artefatos de renderização, como bordas desfocadas ou semitransparentes. Versões anteriores do WPF incluíam o ajuste de pixels para ajudar a lidar com esse caso. O Silverlight 2 introduziu o arredondamento de layout, que é outra maneira de mover elementos para que as bordas fiquem nos limites de pixels inteiros. Agora o WPF dá suporte ao arredondamento de layout com o <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> propriedade anexada em <xref:System.Windows.FrameworkElement>.

- Composição em cache

  Ao usar os novos <xref:System.Windows.Media.BitmapCache> e <xref:System.Windows.Media.BitmapCacheBrush> classes, você pode armazenar em cache uma parte complexa da árvore visual como um bitmap e aprimorar o tempo de renderização. O bitmap permanece responsivo a entradas do usuário, como cliques do mouse e você pode pintá-lo em outros elementos, como faria com qualquer pincel.

- Suporte para o Sombreador de Pixel 3

  O WPF 4 se baseia na parte superior do <xref:System.Windows.Media.Effects.ShaderEffect> suporte introduzido no WPF 3.5 SP1, permitindo que os aplicativos gravem efeitos usando Pixel Shader (PS) versão 3.0. O modelo de sombreador PS 3.0 é mais sofisticado do que o PS 2.0, o que permite ainda mais efeitos em hardware com suporte.

- Funções de easing

  Você pode aprimorar animações com funções de easing, que fornecem controle adicional sobre o comportamento das animações. Por exemplo, você pode aplicar um <xref:System.Windows.Media.Animation.ElasticEase> a uma animação para dar a ela um comportamento semelhante. Para obter mais informações, consulte os tipos de easing a <xref:System.Windows.Media.Animation> namespace.

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>Gráficos e renderização

O WPF inclui suporte para gráficos 2D de alta qualidade. A funcionalidade inclui pincéis, geometrias, imagens, formas e transformações. Para obter mais informações, consulte [Gráficos](graphics.md). A renderização de elementos gráficos se baseia o <xref:System.Windows.Media.Visual> classe. A estrutura de objetos visuais na tela é descrita pela árvore visual. Para obter mais informações, consulte [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md).

### <a name="2-d-shapes"></a>Formas 2D

O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece uma biblioteca de formas [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] vetoriais usadas com frequência, como retângulos e elipses, que são mostradas na ilustração a seguir.

![Diagrama mostrando elipses e retângulos.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

Essas formas [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] intrínsecas não são apenas formas: elas são elementos programáveis que implementam muitos dos recursos que você espera da maioria dos controles comuns, que incluem a entrada de mouse e teclado. O exemplo a seguir mostra como lidar com o <xref:System.Windows.UIElement.MouseUp> evento gerado ao clicar em um <xref:System.Windows.Shapes.Ellipse> elemento.

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

![Uma caixa de mensagem dizendo "You clicked elipse!"](./media/index/messagebox-text-output.png)

Para obter mais informações, consulte [Visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md). Para ver um exemplo introdutório, consulte [Amostra de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).

### <a name="2-d-geometries"></a>Geometrias 2D

Quando as formas [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] que o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece não forem suficientes, você pode usar o suporte a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para geometrias e caminhos para criar as suas próprias formas. A ilustração a seguir mostra como você pode usar geometrias para criar formas, como um pincel de desenho e cortar outros elementos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].

![Captura de tela mostrando como você pode usar geometrias para criar formas.](./media/index/use-geometries-create-shapes.png)

Para obter mais informações, consulte [Visão geral de geometria](geometry-overview.md). Para ver um exemplo introdutório, consulte [Amostra de geometrias](https://go.microsoft.com/fwlink/?LinkID=159989).

### <a name="2-d-effects"></a>Efeitos 2D

O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece uma biblioteca de classes [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] que você pode usar para criar uma variedade de efeitos. A capacidade de renderização [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece a capacidade de pintar elementos [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que têm gradientes, bitmaps, desenhos e vídeos; e de manipulá-los por meio de rotação, dimensionamento e inclinação. A ilustração a seguir fornece um exemplo dos muitos efeitos que você pode obter usando pincéis [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].

![Ilustração mostrando os elementos de pintura e diferentes pincéis do WPF.](./media/index/brushes-paint-elements.png)

Para obter mais informações, consulte [Visão geral de pincéis do WPF](wpf-brushes-overview.md). Para ver um exemplo introdutório, consulte [Amostra de pincéis](https://go.microsoft.com/fwlink/?LinkID=159973).

<a name="rendering"></a>

## <a name="3-d-rendering"></a>Renderização 3D

O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece um conjunto de recursos de renderização [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] que se integram com o suporte a gráficos [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para que você crie um layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] e visualização de dados mais interessante. Em uma extremidade do espectro, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permite que você renderize imagens [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] nas superfícies de formas [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)], o que a ilustração a seguir demonstra.

![Captura de tela de um exemplo que mostra as formas 3D com texturas diferentes.](./media/index/visual-three-dimensional-shape.png)

Para obter mais informações, consulte [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md). Para ver um exemplo introdutório, consulte [Amostra de sólidos em 3D](https://go.microsoft.com/fwlink/?LinkID=159964).

<a name="animation"></a>

## <a name="animation"></a>Animação

Use a animação para fazer controles e elementos crescerem, tremerem, rodarem e esmaecerem, e para criar transições de página interessantes e muito mais. Como o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permite que você anime a maioria das propriedades, você pode não só animar a maioria dos objetos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], mas também pode usar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para animar os objetos personalizados que você cria.

![Captura de tela de um cubo animado.](./media/index/animate-custom-objects.png)

Para obter mais informações, consulte [Visão geral de animação](animation-overview.md). Para obter um exemplo introdutório, consulte [Galeria de exemplos de animação](https://go.microsoft.com/fwlink/?LinkID=159969).

<a name="media"></a>

## <a name="media"></a>Mídia

Imagens, vídeo e áudio são formas de mídia avançadas que transmitem informações experiências do usuário.

### <a name="images"></a>Imagens

Imagens, que incluem ícones, planos de fundo e até mesmo partes de animações, são uma parte principal da maioria dos aplicativos. Como você precisa usar imagens com frequência, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] expõe a capacidade de trabalhar com elas de diversas formas. A ilustração a seguir mostra apenas uma dessas formas.

![Captura de tela de exemplo de definição de estilo](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

Para obter mais informações, consulte [Visão geral de geração de imagens](imaging-overview.md).

### <a name="video-and-audio"></a>Áudio e vídeo

Um recurso principal das funcionalidades gráficas do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é dar suporte nativo para trabalhar com multimídia, o que inclui vídeo e áudio. O exemplo a seguir mostra como inserir um player de mídia em um aplicativo.

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement> é capaz de executar áudio e vídeo e é extensível o suficiente para permitir a fácil criação de custom [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].

Para obter mais informações, consulte [Visão geral de multimídia](multimedia-overview.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md)
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Tópicos explicativos de animação e tempo](animation-and-timing-how-to-topics.md)
- [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md)
- [Visão geral de multimídia](multimedia-overview.md)
