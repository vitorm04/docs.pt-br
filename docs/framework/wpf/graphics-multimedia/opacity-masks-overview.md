---
title: Visão geral de máscaras da opacidade
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 76ec595b1d2cc732e1c8bc2dc2ca6def904bf94c
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545347"
---
# <a name="opacity-masks-overview"></a>Visão geral de máscaras da opacidade
As máscaras de opacidade permitem que você torne partes de um elemento ou visual transparentes ou parcialmente transparentes. Para criar uma máscara de opacidade, você aplica <xref:System.Windows.Media.Brush> uma <xref:System.Windows.UIElement.OpacityMask%2A> à propriedade de um elemento ou <xref:System.Windows.Media.Visual>.  O pincel é mapeado para o elemento ou visual, e o valor de opacidade de cada pixel do pincel é usado para determinar a opacidade resultante de cada pixel correspondente do elemento ou visual.  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Esta visão geral pressupõe que você esteja familiarizado <xref:System.Windows.Media.Brush> com objetos. Para uma introdução ao uso de pincéis, consulte [Visão geral sobre a pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md). Para obter informações <xref:System.Windows.Media.ImageBrush> sobre <xref:System.Windows.Media.DrawingBrush>o e o, consulte [pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>Criando efeitos visuais com máscaras de opacidade  
 Uma máscara de opacidade funciona pelo mapeamento de seu conteúdo para o elemento ou visual. O canal alfa de cada um dos pixels do pincel é usado para determinar a opacidade resultante de elemento ou pixels correspondentes do visual. A cor real do pincel será ignorada. Se uma determinada parte do pincel for transparente, a parte correspondente do elemento ou visual se tornará transparente. Se uma determinada parte do pincel for opaca, a opacidade da parte correspondente do elemento ou visual permanecerá inalterada. A opacidade especificada pela máscara de opacidade é combinada com quaisquer configurações de opacidade presentes no elemento ou visual. Por exemplo, se um elemento é 25 por cento opaco e uma máscara de opacidade é aplicada e faz a transição do completamente opaco para o totalmente transparente, o resultado é um elemento que faz a transição de 25 por cento de opacidade para totalmente transparente.  
  
> [!NOTE]
>  Embora os exemplos nesta visão geral demonstrem o uso de máscaras de opacidade em elementos Image, uma máscara de opacidade pode ser aplicada a <xref:System.Windows.Media.Visual>qualquer elemento ou, incluindo painéis e controles.  
  
 As máscaras de opacidade são usadas para criar efeitos visuais interessantes, como criar imagens ou botões que somem do modo de exibição, adicionar texturas a elementos ou combinar gradientes para produzir superfícies tipo vidro. A ilustração a seguir demonstra o uso de uma máscara de opacidade. Uma tela de fundo quadriculada é usada para mostrar as partes transparentes da máscara.  
  
 ![Objeto com uma máscara de opacidade LinearGradientBrush](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Exemplo de máscara de opacidade  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>Criando uma máscara de opacidade  
 Para criar uma máscara de opacidade, você cria <xref:System.Windows.Media.Brush> uma e a aplica <xref:System.Windows.UIElement.OpacityMask%2A> à propriedade de um elemento ou Visual. Você pode usar qualquer tipo de <xref:System.Windows.Media.Brush> uma máscara de opacidade.  
  
- <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Usado para fazer com que um elemento ou Visual apareça na exibição.  
  
     A imagem a seguir mostra <xref:System.Windows.Media.LinearGradientBrush> um usado como uma máscara de opacidade.  
  
     ![Um objeto com uma máscara de opacidade LinearGradientBrush](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
Exemplo de máscara de opacidade LinearGradientBrush  
  
- <xref:System.Windows.Media.ImageBrush>: Usado para criar textura e efeitos de borda suave ou rasgado.  
  
     A imagem a seguir mostra <xref:System.Windows.Media.ImageBrush> um usado como uma máscara de opacidade.  
  
     ![Objeto que tem uma máscara de opacidade ImageBrush](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
Exemplo de máscara de opacidade LinearGradientBrush  
  
- <xref:System.Windows.Media.DrawingBrush>: Usado para criar máscaras de opacidade complexas de padrões de formas, imagens e gradientes.  
  
     A imagem a seguir mostra <xref:System.Windows.Media.DrawingBrush> um usado como uma máscara de opacidade.  
  
     ![Objeto com uma máscara de opacidade DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
Exemplo de máscara de opacidade DrawingBrush  
  
 Os pincéis de gradiente <xref:System.Windows.Media.RadialGradientBrush>(<xref:System.Windows.Media.LinearGradientBrush> e) são especialmente adequados para uso como uma máscara de opacidade. Como um <xref:System.Windows.Media.SolidColorBrush> preenche uma área com uma cor uniforme, elas fazem máscaras de opacidade ruins; usar <xref:System.Windows.Media.SolidColorBrush> um é equivalente a definir a <xref:System.Windows.UIElement.OpacityMask%2A> Propriedade do elemento ou do Visual.  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>Usando um gradiente como uma máscara de opacidade  
 Para criar um preenchimento de gradiente, você deve especificar duas ou mais marcas de gradiente. Cada marca de gradiente descreve uma cor e uma posição (consulte [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md) para obter mais informações sobre como criar e usar gradientes). O processo é o mesmo que usar um gradiente como uma máscara de opacidade, exceto que, em vez de combinar cores, o gradiente da máscara de opacidade combina os valores do canal alfa. Portanto, a cor real do conteúdo do gradiente não importa, apenas o canal alfa, ou a opacidade, de cada cor é importante. Confira o exemplo abaixo.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Especificando marcas de gradiente para uma máscara de opacidade  
 No exemplo anterior, a cor <xref:System.Windows.Media.Colors.Black%2A> definida pelo sistema é usada como a cor inicial do gradiente. Como todas as cores na <xref:System.Windows.Media.Colors> classe, exceto <xref:System.Windows.Media.Colors.Transparent%2A>, são totalmente opacas, elas podem ser usadas para simplesmente definir uma cor inicial para uma máscara de opacidade de gradiente.  
  
 Para obter controle adicional sobre valores Alfa ao definir uma máscara de opacidade, você pode especificar o canal alfa de cores usando a notação hexadecimal ARGB na <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> marcação ou usando o método.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>Especificando a opacidade das cores em "XAML"  
 No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você usa a notação hexadecimal ARGB para especificar a opacidade de cores individuais. A notação hexadecimal ARGB usa a seguinte sintaxe:  
  
 `#` **aa** *rrggbb*  
  
 O *aa* na linha anterior representa um valor hexadecimal de dois dígitos usado para especificar a opacidade da cor. O *rr*, o *gg* e o *bb* representam um valor hexadecimal de dois dígitos usado para especificar a quantidade de vermelho, verde e azul na cor. Cada dígito hexadecimal pode ter um valor de 0 a 9 ou de A a F. 0 é o menor valor. F é o maior valor. Um valor alfa de 00 especifica uma cor que é completamente transparente, enquanto um valor alfa de FF cria uma cor que é totalmente opaca.  No exemplo a seguir, a notação ARGB do hexadecimal é usada para especificar duas cores. A primeira é totalmente opaca, enquanto a segunda é completamente transparente.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>Usando uma imagem como uma máscara de opacidade  
 As imagens também podem ser usadas como uma máscara de opacidade. O código a seguir mostra um exemplo. Uma tela de fundo quadriculada é usada para mostrar as partes transparentes da máscara.  
  
 ![Um objeto com uma máscara de opacidade ImageBrush](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Exemplo de máscara de opacidade  
  
 Para usar uma imagem como uma máscara de opacidade, use <xref:System.Windows.Media.ImageBrush> uma para conter a imagem. Ao criar uma imagem a ser usada como uma máscara de opacidade, salve a imagem em um formato que dê suporte a vários níveis de transparência, como PNG (Portable Network Graphics). O exemplo a seguir mostra o código usado para criar a ilustração anterior.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Usando uma imagem lado a lado como uma máscara de opacidade  
 No exemplo a seguir, a mesma imagem é usada com outra <xref:System.Windows.Media.ImageBrush>, mas os recursos de divisão do pincel são usados para produzir blocos do quadrado de imagem 50 pixels.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Criando uma máscara de opacidade de um desenho  
 Os desenhos podem ser usados uma máscara de opacidade. As formas contidas dentro do desenho podem ser preenchidas com gradientes, cores sólidas, imagens ou até mesmo outros desenhos. A imagem a seguir mostra um exemplo de um desenho usado como uma máscara de opacidade. Uma tela de fundo quadriculada é usada para mostrar as partes transparentes da máscara.  
  
 ![Um objeto com uma máscara de opacidade DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
Exemplo de máscara de opacidade DrawingBrush  
  
 Para usar um desenho como uma máscara de opacidade, use <xref:System.Windows.Media.DrawingBrush> um para conter o desenho. O exemplo a seguir mostra o código usado para criar a ilustração anterior:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Usando um desenho lado a lado como uma máscara de opacidade  
 Como o <xref:System.Windows.Media.ImageBrush>, o <xref:System.Windows.Media.DrawingBrush> pode ser feito para dividir seu desenho. No exemplo a seguir, um pincel de desenho é usado para criar uma máscara de opacidade lado a lado.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Consulte também

- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md)
