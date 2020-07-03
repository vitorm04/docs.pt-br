---
title: Gráficos e multimídia
description: Descubra os recursos de mídia do Windows Presentation Foundation (WPF). Adicione elementos gráficos, efeitos de transição, som e vídeo aos seus aplicativos.
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
ms.openlocfilehash: ba52e78564484f7714ab0035a5e1861766b72bbf
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853683"
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="e2c08-104">Gráficos e multimídia</span><span class="sxs-lookup"><span data-stu-id="e2c08-104">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="e2c08-105">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece suporte para multimídia, gráficos vetoriais, animação e composição de conteúdo, tornando mais fácil para os desenvolvedores criar interfaces do usuário e conteúdo interessantes.</span><span class="sxs-lookup"><span data-stu-id="e2c08-105">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="e2c08-106">Usando o Visual Studio, você pode criar gráficos vetoriais ou animações complexas e integrar mídia em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e2c08-106">Using Visual Studio, you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="e2c08-107">Este tópico apresenta os recursos de gráficos, animação e mídia de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], que permitem que você adicione gráficos, efeitos de transição, som e vídeo a seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e2c08-107">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="e2c08-108">Não é recomendável usar tipos do WPF em um serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="e2c08-108">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="e2c08-109">Se você tentar usar tipos do WPF em um serviço Windows, será possível que o serviço não funcione conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="e2c08-109">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="e2c08-110">Novidades sobre gráficos e multimídia no WPF 4</span><span class="sxs-lookup"><span data-stu-id="e2c08-110">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="e2c08-111">Várias alterações foram feitas com relação aos gráficos e animações.</span><span class="sxs-lookup"><span data-stu-id="e2c08-111">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="e2c08-112">Arredondamento de layout</span><span class="sxs-lookup"><span data-stu-id="e2c08-112">Layout Rounding</span></span>

  <span data-ttu-id="e2c08-113">Quando a borda de um objeto está no meio de um dispositivo de pixel, o sistema de gráficos independente de DPI pode criar artefatos de renderização, como bordas desfocadas ou semitransparentes.</span><span class="sxs-lookup"><span data-stu-id="e2c08-113">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="e2c08-114">Versões anteriores do WPF incluíam o ajuste de pixels para ajudar a lidar com esse caso.</span><span class="sxs-lookup"><span data-stu-id="e2c08-114">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="e2c08-115">O Silverlight 2 introduziu o arredondamento de layout, que é outra maneira de mover elementos para que as bordas fiquem nos limites de pixels inteiros.</span><span class="sxs-lookup"><span data-stu-id="e2c08-115">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="e2c08-116">O WPF agora dá suporte ao arredondamento de layout com a <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> Propriedade anexada em <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="e2c08-116">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="e2c08-117">Composição em cache</span><span class="sxs-lookup"><span data-stu-id="e2c08-117">Cached Composition</span></span>

  <span data-ttu-id="e2c08-118">Usando as novas <xref:System.Windows.Media.BitmapCache> classes e <xref:System.Windows.Media.BitmapCacheBrush> , você pode armazenar em cache uma parte complexa da árvore visual como um bitmap e melhorar muito o tempo de renderização.</span><span class="sxs-lookup"><span data-stu-id="e2c08-118">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="e2c08-119">O bitmap permanece responsivo a entradas do usuário, como cliques do mouse e você pode pintá-lo em outros elementos, como faria com qualquer pincel.</span><span class="sxs-lookup"><span data-stu-id="e2c08-119">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="e2c08-120">Suporte para o Sombreador de Pixel 3</span><span class="sxs-lookup"><span data-stu-id="e2c08-120">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="e2c08-121">O WPF 4 se baseia no <xref:System.Windows.Media.Effects.ShaderEffect> suporte introduzido no WPF 3,5 SP1, permitindo que os aplicativos gravem efeitos usando o sombreador de pixel (PS) versão 3,0.</span><span class="sxs-lookup"><span data-stu-id="e2c08-121">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="e2c08-122">O modelo de sombreador PS 3.0 é mais sofisticado do que o PS 2.0, o que permite ainda mais efeitos em hardware com suporte.</span><span class="sxs-lookup"><span data-stu-id="e2c08-122">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="e2c08-123">Funções de easing</span><span class="sxs-lookup"><span data-stu-id="e2c08-123">Easing Functions</span></span>

  <span data-ttu-id="e2c08-124">Você pode aprimorar animações com funções de easing, que fornecem controle adicional sobre o comportamento das animações.</span><span class="sxs-lookup"><span data-stu-id="e2c08-124">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="e2c08-125">Por exemplo, você pode aplicar um <xref:System.Windows.Media.Animation.ElasticEase> a uma animação para dar à animação um comportamento de porta.</span><span class="sxs-lookup"><span data-stu-id="e2c08-125">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="e2c08-126">Para obter mais informações, consulte os tipos de atenuação no <xref:System.Windows.Media.Animation> namespace.</span><span class="sxs-lookup"><span data-stu-id="e2c08-126">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="e2c08-127">Gráficos e renderização</span><span class="sxs-lookup"><span data-stu-id="e2c08-127">Graphics and Rendering</span></span>

<span data-ttu-id="e2c08-128">O WPF inclui suporte para gráficos 2D de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="e2c08-128">WPF includes support for high quality 2D graphics.</span></span> <span data-ttu-id="e2c08-129">A funcionalidade inclui pincéis, geometrias, imagens, formas e transformações.</span><span class="sxs-lookup"><span data-stu-id="e2c08-129">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="e2c08-130">Para obter mais informações, consulte [Gráficos](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="e2c08-130">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="e2c08-131">A renderização de elementos gráficos baseia-se na <xref:System.Windows.Media.Visual> classe.</span><span class="sxs-lookup"><span data-stu-id="e2c08-131">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="e2c08-132">A estrutura de objetos visuais na tela é descrita pela árvore visual.</span><span class="sxs-lookup"><span data-stu-id="e2c08-132">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="e2c08-133">Para obter mais informações, consulte [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e2c08-133">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="e2c08-134">Formas 2D</span><span class="sxs-lookup"><span data-stu-id="e2c08-134">2D Shapes</span></span>

<span data-ttu-id="e2c08-135">O WPF fornece uma biblioteca de formas 2D com desenho de vetores comumente usadas, como retângulos e elipses, que a ilustração a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="e2c08-135">WPF provides a library of commonly used, vector-drawn 2D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Diagrama mostrando reticências e retângulos.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="e2c08-137">Essas formas intrínsecas do WPF não são apenas formas: são elementos programáveis que implementam muitos dos recursos que você espera dos controles mais comuns, que incluem entrada de teclado e mouse.</span><span class="sxs-lookup"><span data-stu-id="e2c08-137">These intrinsic WPF shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="e2c08-138">O exemplo a seguir mostra como lidar com o <xref:System.Windows.UIElement.MouseUp> evento gerado clicando em um <xref:System.Windows.Shapes.Ellipse> elemento.</span><span class="sxs-lookup"><span data-stu-id="e2c08-138">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="e2c08-139">A ilustração a seguir mostra a saída para a marcação [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anterior e code-behind.</span><span class="sxs-lookup"><span data-stu-id="e2c08-139">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![Uma caixa de mensagem dizendo "você clicou na elipse!"](./media/index/messagebox-text-output.png)

<span data-ttu-id="e2c08-141">Para obter mais informações, consulte [Visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e2c08-141">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="e2c08-142">Para ver um exemplo introdutório, consulte [Amostra de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="e2c08-142">For an introductory sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="e2c08-143">Geometrias 2D</span><span class="sxs-lookup"><span data-stu-id="e2c08-143">2D Geometries</span></span>

<span data-ttu-id="e2c08-144">Quando as formas 2D que o WPF fornece não forem suficientes, você poderá usar o suporte do WPF para geometrias e caminhos para criar o seu próprio.</span><span class="sxs-lookup"><span data-stu-id="e2c08-144">When the 2D shapes that WPF provides are not sufficient, you can use WPF support for geometries and paths to create your own.</span></span> <span data-ttu-id="e2c08-145">A ilustração a seguir mostra como você pode usar geometrias para criar formas, como um pincel de desenho e para recortar outros elementos do WPF.</span><span class="sxs-lookup"><span data-stu-id="e2c08-145">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other WPF elements.</span></span>

![Captura de tela mostrando como você pode usar geometrias para criar formas.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="e2c08-147">Para obter mais informações, consulte [visão geral da geometria](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e2c08-147">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="e2c08-148">Para ver um exemplo introdutório, consulte [Amostra de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="e2c08-148">For an introductory sample, see [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="e2c08-149">Efeitos 2D</span><span class="sxs-lookup"><span data-stu-id="e2c08-149">2D Effects</span></span>

<span data-ttu-id="e2c08-150">O WPF fornece uma biblioteca de classes 2D que você pode usar para criar uma variedade de efeitos.</span><span class="sxs-lookup"><span data-stu-id="e2c08-150">WPF provides a library of 2D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="e2c08-151">A capacidade de renderização 2D do WPF fornece a capacidade de pintar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos que têm gradientes, bitmaps, desenhos e vídeos; e manipulá-los usando rotação, dimensionamento e inclinação.</span><span class="sxs-lookup"><span data-stu-id="e2c08-151">The 2D rendering capability of WPF provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="e2c08-152">A ilustração a seguir fornece um exemplo dos muitos efeitos que você pode obter usando os pincéis do WPF.</span><span class="sxs-lookup"><span data-stu-id="e2c08-152">The following illustration gives an example of the many effects you can achieve by using WPF brushes.</span></span>

![Ilustração mostrando os diferentes pincéis do WPF e elementos de pintura.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="e2c08-154">Para obter mais informações, consulte [visão geral de pincéis do WPF](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e2c08-154">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="e2c08-155">Para ver um exemplo introdutório, consulte [Amostra de pincéis](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="e2c08-155">For an introductory sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>

<a name="rendering"></a>

## <a name="3d-rendering"></a><span data-ttu-id="e2c08-156">Renderização 3D</span><span class="sxs-lookup"><span data-stu-id="e2c08-156">3D Rendering</span></span>

<span data-ttu-id="e2c08-157">O WPF fornece um conjunto de recursos de renderização 3D que se integram ao suporte a gráficos 2D no WPF para que você possa criar layouts e visualização de dados mais empolgantes [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e2c08-157">WPF provides a set of 3D rendering capabilities that integrate with 2D graphics support in WPF in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="e2c08-158">Em uma extremidade do espectro, o WPF permite renderizar imagens 2D nas superfícies de formas 3D, que a ilustração a seguir demonstra.</span><span class="sxs-lookup"><span data-stu-id="e2c08-158">At one end of the spectrum, WPF enables you to render 2D images onto the surfaces of 3D shapes, which the following illustration demonstrates.</span></span>

![Captura de tela de um exemplo mostrando formas 3D com texturas diferentes.](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="e2c08-160">Para obter mais informações, consulte [visão geral de gráficos 3D](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e2c08-160">For more information, see [3D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="e2c08-161">Para obter um exemplo introdutório, consulte [exemplo de sólidos 3D](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="e2c08-161">For an introductory sample, see [3D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="e2c08-162">Animação</span><span class="sxs-lookup"><span data-stu-id="e2c08-162">Animation</span></span>

<span data-ttu-id="e2c08-163">Use a animação para fazer controles e elementos crescerem, tremerem, rodarem e esmaecerem, e para criar transições de página interessantes e muito mais.</span><span class="sxs-lookup"><span data-stu-id="e2c08-163">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="e2c08-164">Como o WPF permite que você anime a maioria das propriedades, não só é possível animar a maioria dos objetos do WPF, você também pode usar o WPF para animar objetos personalizados criados por você.</span><span class="sxs-lookup"><span data-stu-id="e2c08-164">Because WPF enables you to animate most properties, not only can you animate most WPF objects, you can also use WPF to animate custom objects that you create.</span></span>

![Captura de tela de um cubo animado.](./media/index/animate-custom-objects.png)

<span data-ttu-id="e2c08-166">Para obter mais informações, consulte [visão geral da animação](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e2c08-166">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="e2c08-167">Para obter um exemplo introdutório, consulte [Galeria de exemplos de animação](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="e2c08-167">For an introductory sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="e2c08-168">Mídia</span><span class="sxs-lookup"><span data-stu-id="e2c08-168">Media</span></span>

<span data-ttu-id="e2c08-169">Imagens, vídeo e áudio são formas de mídia avançadas que transmitem informações experiências do usuário.</span><span class="sxs-lookup"><span data-stu-id="e2c08-169">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="e2c08-170">Imagens</span><span class="sxs-lookup"><span data-stu-id="e2c08-170">Images</span></span>

<span data-ttu-id="e2c08-171">Imagens, que incluem ícones, planos de fundo e até mesmo partes de animações, são uma parte principal da maioria dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e2c08-171">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="e2c08-172">Como você geralmente precisa usar imagens, o WPF expõe a capacidade de trabalhar com elas de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="e2c08-172">Because you frequently need to use images, WPF exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="e2c08-173">A ilustração a seguir mostra apenas uma dessas formas.</span><span class="sxs-lookup"><span data-stu-id="e2c08-173">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="e2c08-174">![Captura de tela de exemplo de estilo](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="e2c08-174">![Styling sample screenshot](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="e2c08-175">Para obter mais informações, consulte [visão geral da geração de imagens](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e2c08-175">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="e2c08-176">Áudio e vídeo</span><span class="sxs-lookup"><span data-stu-id="e2c08-176">Video and Audio</span></span>

<span data-ttu-id="e2c08-177">Um recurso fundamental dos recursos gráficos do WPF é fornecer suporte nativo para trabalhar com multimídia, que inclui vídeo e áudio.</span><span class="sxs-lookup"><span data-stu-id="e2c08-177">A core feature of the graphics capabilities of WPF is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="e2c08-178">O exemplo a seguir mostra como inserir um player de mídia em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e2c08-178">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="e2c08-179"><xref:System.Windows.Controls.MediaElement>é capaz de reproduzir vídeo e áudio e é extensível o suficiente para permitir a criação fácil de interfaces do cliente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="e2c08-179"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="e2c08-180">Para obter mais informações, consulte [Visão geral de multimídia](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e2c08-180">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2c08-181">Confira também</span><span class="sxs-lookup"><span data-stu-id="e2c08-181">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="e2c08-182">Elementos gráficos e geração de imagens 2D</span><span class="sxs-lookup"><span data-stu-id="e2c08-182">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="e2c08-183">Visão geral de formas e desenho básico no WPF</span><span class="sxs-lookup"><span data-stu-id="e2c08-183">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="e2c08-184">Visão geral da pintura com cores sólidas e gradientes</span><span class="sxs-lookup"><span data-stu-id="e2c08-184">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="e2c08-185">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="e2c08-185">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="e2c08-186">Tópicos explicativos de animação e tempo</span><span class="sxs-lookup"><span data-stu-id="e2c08-186">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="e2c08-187">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="e2c08-187">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="e2c08-188">Visão geral de multimídia</span><span class="sxs-lookup"><span data-stu-id="e2c08-188">Multimedia Overview</span></span>](multimedia-overview.md)
