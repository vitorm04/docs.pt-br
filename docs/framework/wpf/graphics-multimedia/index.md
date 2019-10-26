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
ms.openlocfilehash: 150b742c2195c07abf2b2823871627b0ba827580
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919986"
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="bef8a-102">Gráficos e multimídia</span><span class="sxs-lookup"><span data-stu-id="bef8a-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="bef8a-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece suporte para multimídia, gráficos vetoriais, animação e composição de conteúdo, facilitando para os desenvolvedores a criação de conteúdo e interfaces de usuário interessantes.</span><span class="sxs-lookup"><span data-stu-id="bef8a-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="bef8a-104">Usando o Visual Studio, você pode criar gráficos vetoriais ou animações complexas e integrar mídia em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bef8a-104">Using Visual Studio, you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="bef8a-105">Este tópico apresenta os recursos de gráficos, animação e mídia de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], que permitem que você adicione gráficos, efeitos de transição, som e vídeo a seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bef8a-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="bef8a-106">Não é recomendável usar tipos do WPF em um serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="bef8a-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="bef8a-107">Se você tentar usar tipos do WPF em um serviço Windows, será possível que o serviço não funcione conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="bef8a-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="bef8a-108">Novidades sobre gráficos e multimídia no WPF 4</span><span class="sxs-lookup"><span data-stu-id="bef8a-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="bef8a-109">Várias alterações foram feitas com relação aos gráficos e animações.</span><span class="sxs-lookup"><span data-stu-id="bef8a-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="bef8a-110">Arredondamento de layout</span><span class="sxs-lookup"><span data-stu-id="bef8a-110">Layout Rounding</span></span>

  <span data-ttu-id="bef8a-111">Quando a borda de um objeto está no meio de um dispositivo de pixel, o sistema de gráficos independente de DPI pode criar artefatos de renderização, como bordas desfocadas ou semitransparentes.</span><span class="sxs-lookup"><span data-stu-id="bef8a-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="bef8a-112">Versões anteriores do WPF incluíam o ajuste de pixels para ajudar a lidar com esse caso.</span><span class="sxs-lookup"><span data-stu-id="bef8a-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="bef8a-113">O Silverlight 2 introduziu o arredondamento de layout, que é outra maneira de mover elementos para que as bordas fiquem nos limites de pixels inteiros.</span><span class="sxs-lookup"><span data-stu-id="bef8a-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="bef8a-114">O WPF agora dá suporte ao arredondamento de layout com a propriedade anexada <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> em <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="bef8a-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="bef8a-115">Composição em cache</span><span class="sxs-lookup"><span data-stu-id="bef8a-115">Cached Composition</span></span>

  <span data-ttu-id="bef8a-116">Usando as novas classes <xref:System.Windows.Media.BitmapCache> e <xref:System.Windows.Media.BitmapCacheBrush>, você pode armazenar em cache uma parte complexa da árvore visual como um bitmap e melhorar muito o tempo de renderização.</span><span class="sxs-lookup"><span data-stu-id="bef8a-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="bef8a-117">O bitmap permanece responsivo a entradas do usuário, como cliques do mouse e você pode pintá-lo em outros elementos, como faria com qualquer pincel.</span><span class="sxs-lookup"><span data-stu-id="bef8a-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="bef8a-118">Suporte para o Sombreador de Pixel 3</span><span class="sxs-lookup"><span data-stu-id="bef8a-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="bef8a-119">O WPF 4 se baseia no suporte a <xref:System.Windows.Media.Effects.ShaderEffect> introduzido no WPF 3,5 SP1, permitindo que os aplicativos gravem efeitos usando o sombreador de pixel (PS) versão 3,0.</span><span class="sxs-lookup"><span data-stu-id="bef8a-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="bef8a-120">O modelo de sombreador PS 3.0 é mais sofisticado do que o PS 2.0, o que permite ainda mais efeitos em hardware com suporte.</span><span class="sxs-lookup"><span data-stu-id="bef8a-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="bef8a-121">Funções de easing</span><span class="sxs-lookup"><span data-stu-id="bef8a-121">Easing Functions</span></span>

  <span data-ttu-id="bef8a-122">Você pode aprimorar animações com funções de easing, que fornecem controle adicional sobre o comportamento das animações.</span><span class="sxs-lookup"><span data-stu-id="bef8a-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="bef8a-123">Por exemplo, você pode aplicar um <xref:System.Windows.Media.Animation.ElasticEase> a uma animação para dar uma animação ao comportamento de uma porta.</span><span class="sxs-lookup"><span data-stu-id="bef8a-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="bef8a-124">Para obter mais informações, consulte os tipos de atenuação no namespace <xref:System.Windows.Media.Animation>.</span><span class="sxs-lookup"><span data-stu-id="bef8a-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="bef8a-125">Gráficos e renderização</span><span class="sxs-lookup"><span data-stu-id="bef8a-125">Graphics and Rendering</span></span>

<span data-ttu-id="bef8a-126">O WPF inclui suporte para gráficos 2D de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="bef8a-126">WPF includes support for high quality 2-D graphics.</span></span> <span data-ttu-id="bef8a-127">A funcionalidade inclui pincéis, geometrias, imagens, formas e transformações.</span><span class="sxs-lookup"><span data-stu-id="bef8a-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="bef8a-128">Para obter mais informações, consulte [Gráficos](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="bef8a-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="bef8a-129">A renderização de elementos gráficos baseia-se na classe <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="bef8a-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="bef8a-130">A estrutura de objetos visuais na tela é descrita pela árvore visual.</span><span class="sxs-lookup"><span data-stu-id="bef8a-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="bef8a-131">Para obter mais informações, consulte [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bef8a-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2-d-shapes"></a><span data-ttu-id="bef8a-132">Formas 2D</span><span class="sxs-lookup"><span data-stu-id="bef8a-132">2-D Shapes</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="bef8a-133">fornece uma biblioteca de formas 2D e desenhadas com vetores comumente usadas, como retângulos e elipses, que a ilustração a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="bef8a-133">provides a library of commonly used, vector-drawn 2-D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Diagrama mostrando reticências e retângulos.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="bef8a-135">Essas formas [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] intrínsecas não são apenas formas: elas são elementos programáveis que implementam muitos dos recursos que você espera da maioria dos controles comuns, que incluem a entrada de mouse e teclado.</span><span class="sxs-lookup"><span data-stu-id="bef8a-135">These intrinsic [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="bef8a-136">O exemplo a seguir mostra como manipular o evento <xref:System.Windows.UIElement.MouseUp> gerado clicando em um elemento <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="bef8a-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="bef8a-137">A ilustração a seguir mostra a saída para a marcação [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anterior e code-behind.</span><span class="sxs-lookup"><span data-stu-id="bef8a-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![Uma caixa de mensagem dizendo "você clicou na elipse!"](./media/index/messagebox-text-output.png)

<span data-ttu-id="bef8a-139">Para obter mais informações, consulte [Visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bef8a-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="bef8a-140">Para ver um exemplo introdutório, consulte [Amostra de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="bef8a-140">For an introductory sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>

### <a name="2-d-geometries"></a><span data-ttu-id="bef8a-141">Geometrias 2D</span><span class="sxs-lookup"><span data-stu-id="bef8a-141">2-D Geometries</span></span>

<span data-ttu-id="bef8a-142">Quando as formas 2D que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece não são suficientes, você pode usar o suporte a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para geometrias e caminhos para criar o seu próprio.</span><span class="sxs-lookup"><span data-stu-id="bef8a-142">When the 2-D shapes that [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides are not sufficient, you can use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] support for geometries and paths to create your own.</span></span> <span data-ttu-id="bef8a-143">A ilustração a seguir mostra como você pode usar geometrias para criar formas, como um pincel de desenho e cortar outros elementos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bef8a-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elements.</span></span>

![Captura de tela mostrando como você pode usar geometrias para criar formas.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="bef8a-145">Para obter mais informações, consulte [Visão geral de geometria](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bef8a-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="bef8a-146">Para ver um exemplo introdutório, consulte [Amostra de geometrias](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="bef8a-146">For an introductory sample, see [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>

### <a name="2-d-effects"></a><span data-ttu-id="bef8a-147">Efeitos 2D</span><span class="sxs-lookup"><span data-stu-id="bef8a-147">2-D Effects</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="bef8a-148">fornece uma biblioteca de classes 2D que você pode usar para criar uma variedade de efeitos.</span><span class="sxs-lookup"><span data-stu-id="bef8a-148">provides a library of 2-D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="bef8a-149">A capacidade de renderização de 2D do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece a capacidade de pintar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos que têm gradientes, bitmaps, desenhos e vídeos; e para manipulá-los usando rotação, dimensionamento e distorção.</span><span class="sxs-lookup"><span data-stu-id="bef8a-149">The 2-D rendering capability of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="bef8a-150">A ilustração a seguir fornece um exemplo dos muitos efeitos que você pode obter usando pincéis [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bef8a-150">The following illustration gives an example of the many effects you can achieve by using [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] brushes.</span></span>

![Ilustração mostrando os diferentes pincéis do WPF e elementos de pintura.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="bef8a-152">Para obter mais informações, consulte [Visão geral de pincéis do WPF](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bef8a-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="bef8a-153">Para ver um exemplo introdutório, consulte [Amostra de pincéis](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="bef8a-153">For an introductory sample, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>

<a name="rendering"></a>

## <a name="3-d-rendering"></a><span data-ttu-id="bef8a-154">Renderização 3D</span><span class="sxs-lookup"><span data-stu-id="bef8a-154">3-D Rendering</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="bef8a-155">fornece um conjunto de recursos de renderização 3D que se integram ao suporte de gráficos 2D no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para que você possa criar layouts, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]e visualização de dados mais empolgantes.</span><span class="sxs-lookup"><span data-stu-id="bef8a-155">provides a set of 3-D rendering capabilities that integrate with 2-D graphics support in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="bef8a-156">Em uma extremidade do espectro, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permite que você processe imagens 2D nas superfícies de formas 3D, que a ilustração a seguir demonstra.</span><span class="sxs-lookup"><span data-stu-id="bef8a-156">At one end of the spectrum, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to render 2-D images onto the surfaces of 3-D shapes, which the following illustration demonstrates.</span></span>

![Captura de tela de um exemplo mostrando formas 3D com texturas diferentes.](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="bef8a-158">Para obter mais informações, consulte [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bef8a-158">For more information, see [3-D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="bef8a-159">Para ver um exemplo introdutório, consulte [Amostra de sólidos em 3D](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="bef8a-159">For an introductory sample, see [3-D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="bef8a-160">Animação</span><span class="sxs-lookup"><span data-stu-id="bef8a-160">Animation</span></span>

<span data-ttu-id="bef8a-161">Use a animação para fazer controles e elementos crescerem, tremerem, rodarem e esmaecerem, e para criar transições de página interessantes e muito mais.</span><span class="sxs-lookup"><span data-stu-id="bef8a-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="bef8a-162">Como o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permite que você anime a maioria das propriedades, você pode não só animar a maioria dos objetos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], mas também pode usar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para animar os objetos personalizados que você cria.</span><span class="sxs-lookup"><span data-stu-id="bef8a-162">Because [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to animate most properties, not only can you animate most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objects, you can also use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to animate custom objects that you create.</span></span>

![Captura de tela de um cubo animado.](./media/index/animate-custom-objects.png)

<span data-ttu-id="bef8a-164">Para obter mais informações, consulte [Visão geral de animação](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bef8a-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="bef8a-165">Para obter um exemplo introdutório, consulte [Galeria de exemplos de animação](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="bef8a-165">For an introductory sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="bef8a-166">Mídia</span><span class="sxs-lookup"><span data-stu-id="bef8a-166">Media</span></span>

<span data-ttu-id="bef8a-167">Imagens, vídeo e áudio são formas de mídia avançadas que transmitem informações experiências do usuário.</span><span class="sxs-lookup"><span data-stu-id="bef8a-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="bef8a-168">Imagens</span><span class="sxs-lookup"><span data-stu-id="bef8a-168">Images</span></span>

<span data-ttu-id="bef8a-169">Imagens, que incluem ícones, planos de fundo e até mesmo partes de animações, são uma parte principal da maioria dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bef8a-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="bef8a-170">Como você precisa usar imagens com frequência, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] expõe a capacidade de trabalhar com elas de diversas formas.</span><span class="sxs-lookup"><span data-stu-id="bef8a-170">Because you frequently need to use images, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="bef8a-171">A ilustração a seguir mostra apenas uma dessas formas.</span><span class="sxs-lookup"><span data-stu-id="bef8a-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="bef8a-172">![Captura de tela de exemplo de estilo](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="bef8a-172">![Styling sample screenshot](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="bef8a-173">Para obter mais informações, consulte [Visão geral de geração de imagens](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bef8a-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="bef8a-174">Áudio e vídeo</span><span class="sxs-lookup"><span data-stu-id="bef8a-174">Video and Audio</span></span>

<span data-ttu-id="bef8a-175">Um recurso principal das funcionalidades gráficas do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é dar suporte nativo para trabalhar com multimídia, o que inclui vídeo e áudio.</span><span class="sxs-lookup"><span data-stu-id="bef8a-175">A core feature of the graphics capabilities of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="bef8a-176">O exemplo a seguir mostra como inserir um player de mídia em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bef8a-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="bef8a-177"><xref:System.Windows.Controls.MediaElement> é capaz de reproduzir vídeo e áudio e é extensível o suficiente para permitir a fácil criação de UIs personalizadas.</span><span class="sxs-lookup"><span data-stu-id="bef8a-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="bef8a-178">Para obter mais informações, consulte [Visão geral de multimídia](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bef8a-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bef8a-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bef8a-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="bef8a-180">Elementos gráficos e geração de imagens 2D</span><span class="sxs-lookup"><span data-stu-id="bef8a-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="bef8a-181">Visão geral de formas e desenho básico no WPF</span><span class="sxs-lookup"><span data-stu-id="bef8a-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="bef8a-182">Visão geral da pintura com cores sólidas e gradientes</span><span class="sxs-lookup"><span data-stu-id="bef8a-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="bef8a-183">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="bef8a-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="bef8a-184">Tópicos explicativos de animação e tempo</span><span class="sxs-lookup"><span data-stu-id="bef8a-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="bef8a-185">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="bef8a-185">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="bef8a-186">Visão geral de multimídia</span><span class="sxs-lookup"><span data-stu-id="bef8a-186">Multimedia Overview</span></span>](multimedia-overview.md)
