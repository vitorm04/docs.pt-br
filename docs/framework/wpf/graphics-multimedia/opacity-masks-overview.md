---
title: Visão geral de máscaras da opacidade
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 680d7441301b425c088d549f9e0e0d2b976cc69f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566227"
---
# <a name="opacity-masks-overview"></a>Visão geral de máscaras da opacidade
As máscaras de opacidade permitem que você torne partes de um elemento ou visual transparentes ou parcialmente transparentes. Para criar uma máscara de opacidade, você aplica um <xref:System.Windows.Media.Brush> para o <xref:System.Windows.UIElement.OpacityMask%2A> propriedade de um elemento ou <xref:System.Windows.Media.Visual>.  O pincel é mapeado para o elemento ou visual, e o valor de opacidade de cada pixel do pincel é usado para determinar a opacidade resultante de cada pixel correspondente do elemento ou visual.  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Esta visão geral assume que você esteja familiarizado com <xref:System.Windows.Media.Brush> objetos. Para uma introdução ao uso de pincéis, consulte [Visão geral sobre a pintura com cores sólidas e gradientes](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Para obter informações sobre <xref:System.Windows.Media.ImageBrush> e <xref:System.Windows.Media.DrawingBrush>, consulte [pintura com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>Criando efeitos visuais com máscaras de opacidade  
 Uma máscara de opacidade funciona pelo mapeamento de seu conteúdo para o elemento ou visual. O canal alfa de cada um dos pixels do pincel é usado para determinar a opacidade resultante de elemento ou pixels correspondentes do visual. A cor real do pincel será ignorada. Se uma determinada parte do pincel for transparente, a parte correspondente do elemento ou visual se tornará transparente. Se uma determinada parte do pincel for opaca, a opacidade da parte correspondente do elemento ou visual permanecerá inalterada. A opacidade especificada pela máscara de opacidade é combinada com quaisquer configurações de opacidade presentes no elemento ou visual. Por exemplo, se um elemento é 25 por cento opaco e uma máscara de opacidade é aplicada e faz a transição do completamente opaco para o totalmente transparente, o resultado é um elemento que faz a transição de 25 por cento de opacidade para totalmente transparente.  
  
> [!NOTE]
>  Embora os exemplos nesta visão geral demonstram o uso de máscaras opacidade em elementos de imagem, uma máscara de opacidade pode ser aplicada a qualquer elemento ou <xref:System.Windows.Media.Visual>, incluindo painéis e controles.  
  
 As máscaras de opacidade são usadas para criar efeitos visuais interessantes, como criar imagens ou botões que somem do modo de exibição, adicionar texturas a elementos ou combinar gradientes para produzir superfícies tipo vidro. A ilustração a seguir demonstra o uso de uma máscara de opacidade. Uma tela de fundo quadriculada é usada para mostrar as partes transparentes da máscara.  
  
 ![O objeto com uma máscara de opacidade LinearGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Exemplo de máscara de opacidade  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>Criando uma máscara de opacidade  
 Para criar uma máscara de opacidade, você cria um <xref:System.Windows.Media.Brush> e aplicá-lo para o <xref:System.Windows.UIElement.OpacityMask%2A> propriedade de um elemento ou visual. Você pode usar qualquer tipo de <xref:System.Windows.Media.Brush> como uma máscara de opacidade.  
  
-   <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Usado para um elemento ou visual esmaecer.  
  
     A imagem a seguir mostra um <xref:System.Windows.Media.LinearGradientBrush> usado como uma máscara de opacidade.  
  
     ![Um objeto com uma máscara de opacidade LinearGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
Exemplo de máscara de opacidade LinearGradientBrush  
  
-   <xref:System.Windows.Media.ImageBrush>: Usado para criar textura e efeitos de borda suave ou interrompidos.  
  
     A imagem a seguir mostra um <xref:System.Windows.Media.ImageBrush> usado como uma máscara de opacidade.  
  
     ![Objeto que tem uma máscara de opacidade ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
Exemplo de máscara de opacidade LinearGradientBrush  
  
-   <xref:System.Windows.Media.DrawingBrush>: Usado para criar máscaras de opacidade complexas de padrões de formas, imagens e gradientes.  
  
     A imagem a seguir mostra um <xref:System.Windows.Media.DrawingBrush> usado como uma máscara de opacidade.  
  
     ![O objeto com uma máscara de opacidade DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
Exemplo de máscara de opacidade DrawingBrush  
  
 Pincéis de gradiente (<xref:System.Windows.Media.LinearGradientBrush> e <xref:System.Windows.Media.RadialGradientBrush>) são especialmente adequados para uso como uma máscara de opacidade. Porque um <xref:System.Windows.Media.SolidColorBrush> preenche uma área com uma cor uniforme, façam opacidade ruins mascara; usando um <xref:System.Windows.Media.SolidColorBrush> é equivalente à definição do elemento ou do visual <xref:System.Windows.UIElement.OpacityMask%2A> propriedade.  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>Usando um gradiente como uma máscara de opacidade  
 Para criar um preenchimento de gradiente, você deve especificar duas ou mais marcas de gradiente. Cada marca de gradiente descreve uma cor e uma posição (consulte [Visão geral da pintura com cores sólidas e gradientes](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) para obter mais informações sobre como criar e usar gradientes). O processo é o mesmo que usar um gradiente como uma máscara de opacidade, exceto que, em vez de combinar cores, o gradiente da máscara de opacidade combina os valores do canal alfa. Portanto, a cor real do conteúdo do gradiente não importa, apenas o canal alfa, ou a opacidade, de cada cor é importante. Confira o exemplo abaixo.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Especificando marcas de gradiente para uma máscara de opacidade  
 No exemplo anterior, a cor definida pelo sistema <xref:System.Windows.Media.Colors.Black%2A> é usado como a cor inicial do gradiente. Como todas as cores no <xref:System.Windows.Media.Colors> classe, exceto <xref:System.Windows.Media.Colors.Transparent%2A>, são totalmente opacas, eles podem ser usados para definir uma cor inicial para uma máscara de opacidade com gradiente.  
  
 Para obter controle adicional sobre os valores alfa ao definir uma máscara de opacidade, você pode especificar o canal alfa das cores usando [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] notação hexadecimal em marcação ou o <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> método.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>Especificando a opacidade das cores em "XAML"  
 Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você usa a notação hexadecimal [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] para especificar a opacidade das cores individuais. A notação hexadecimal [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] usa a seguinte sintaxe:  
  
 `#` **aa** *rrggbb*  
  
 O *aa* na linha anterior representa um valor hexadecimal de dois dígitos usado para especificar a opacidade da cor. O *rr*, o *gg* e o *bb* representam um valor hexadecimal de dois dígitos usado para especificar a quantidade de vermelho, verde e azul na cor. Cada dígito hexadecimal pode ter um valor de 0 a 9 ou de A a F. 0 é o menor valor. F é o maior valor. Um valor alfa de 00 especifica uma cor que é completamente transparente, enquanto um valor alfa de FF cria uma cor que é totalmente opaca.  No exemplo a seguir, a notação [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] hexadecimal é usada para especificar duas cores. A primeira é totalmente opaca, enquanto a segunda é completamente transparente.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>Usando uma imagem como uma máscara de opacidade  
 As imagens também podem ser usadas como uma máscara de opacidade. O código a seguir mostra um exemplo. Uma tela de fundo quadriculada é usada para mostrar as partes transparentes da máscara.  
  
 ![Um objeto com uma máscara de opacidade ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Exemplo de máscara de opacidade  
  
 Para usar uma imagem como uma máscara de opacidade, use um <xref:System.Windows.Media.ImageBrush> para conter a imagem. Ao criar uma imagem a ser usada como uma máscara de opacidade, salve a imagem em um formato que dá suporte a vários níveis de transparência, como [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]. O exemplo a seguir mostra o código usado para criar a ilustração anterior.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Usando uma imagem lado a lado como uma máscara de opacidade  
 No exemplo a seguir, a mesma imagem é usada com outro <xref:System.Windows.Media.ImageBrush>, mas os recursos do lado a lado do pincel são usados para produzir os blocos do quadrado imagem 50 pixels.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Criando uma máscara de opacidade de um desenho  
 Os desenhos podem ser usados uma máscara de opacidade. As formas contidas dentro do desenho podem ser preenchidas com gradientes, cores sólidas, imagens ou até mesmo outros desenhos. A imagem a seguir mostra um exemplo de um desenho usado como uma máscara de opacidade. Uma tela de fundo quadriculada é usada para mostrar as partes transparentes da máscara.  
  
 ![Um objeto com uma máscara de opacidade DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
Exemplo de máscara de opacidade DrawingBrush  
  
 Para usar um desenho como uma máscara de opacidade, use um <xref:System.Windows.Media.DrawingBrush> para conter o desenho. O exemplo a seguir mostra o código usado para criar a ilustração anterior:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Usando um desenho lado a lado como uma máscara de opacidade  
 Como o <xref:System.Windows.Media.ImageBrush>, o <xref:System.Windows.Media.DrawingBrush> podem ser feitas para o desenho lado a lado. No exemplo a seguir, um pincel de desenho é usado para criar uma máscara de opacidade lado a lado.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Consulte também  
 [Pintando com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Visão geral da pintura com cores sólidas e gradientes](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
