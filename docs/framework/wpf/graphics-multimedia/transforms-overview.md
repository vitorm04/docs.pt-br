---
title: Visão geral de transformações
ms.date: 03/30/2017
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2-D transform
- transform classes [WPF], 2-D
- 2-D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
ms.openlocfilehash: 4fd846502fd348222bc1da1c8746f037e9f237fe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554400"
---
# <a name="transforms-overview"></a>Visão geral de transformações
Este tópico descreve como usar o [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> classes para girar, redimensionar, mover (transladar) e distorcer <xref:System.Windows.FrameworkElement> objetos.  
  
  
<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>O que é uma transformação?  
 Um <xref:System.Windows.Media.Transform> define como mapear ou transformar pontos de um espaço de coordenadas para outro espaço de coordenadas. Esse mapeamento é descrito por uma transformação <xref:System.Windows.Media.Matrix>, que é uma coleção de três linhas com três colunas de <xref:System.Double> valores.  
  
> [!NOTE]
>  Windows Presentation Foundation (WPF) usa matrizes de linhas principais. Vetores são expressos em vetores de linha, não vetores de coluna.  
  
 A tabela a seguir mostra a estrutura de uma matriz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="a-2-d-transformation-matrix"></a>A matriz de transformação 2D  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Padrão: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Padrão: 0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Padrão: 0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Padrão: 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Padrão: 0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Padrão: 0.0|1.0|  
  
 Manipulando valores de matriz, você pode girar, dimensionar, inclinar e mover (transladar) um objeto. Por exemplo, se você alterar o valor na primeira coluna da terceira linha (o <xref:System.Windows.Media.Matrix.OffsetX%2A> valor) para 100, você pode usá-lo para mover um objeto 100 unidades no eixo. Se você alterar o valor na segunda coluna da segunda linha para 3, poderá usá-lo para alongar um objeto para três vezes sua altura atual. Se você alterar os valores, mova objeto 100 unidades no eixo e alongue sua altura por um fator de 3. Como o Windows Presentation Foundation (WPF) somente suporta transformações afins, os valores na coluna à direita são sempre 0, 0, 1.  
  
 Embora o Windows Presentation Foundation (WPF) permite que você manipule diretamente os valores da matriz, também fornece diversas <xref:System.Windows.Media.Transform> classes que permitem que você transformar um objeto sem conhecer como a estrutura da matriz subjacente é configurada. Por exemplo, o <xref:System.Windows.Media.ScaleTransform> classe permite que você dimensione um objeto, definindo seu <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> e <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriedades, em vez de manipular uma matriz de transformação. Da mesma forma, o <xref:System.Windows.Media.RotateTransform> classe permite girar um objeto apenas configurando seu <xref:System.Windows.Media.RotateTransform.Angle%2A> propriedade.  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Classes de transformação  
 Windows Presentation Foundation (WPF) fornece os seguintes [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> classes para operações de transformação comuns:  
  
|Classe|Descrição|Exemplo|Ilustração|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Gira um elemento especificado <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Girar um objeto](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object.md)|![Girar ilustração](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Redimensiona um elemento especificado <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> e <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> quantidades.|[Dimensionar um elemento](../../../../docs/framework/wpf/graphics-multimedia/how-to-scale-an-element.md)|![Dimensionar ilustração](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Inclina um elemento especificado <xref:System.Windows.Media.SkewTransform.AngleX%2A> e <xref:System.Windows.Media.SkewTransform.AngleY%2A> quantidades.|[Inclinar um elemento](../../../../docs/framework/wpf/graphics-multimedia/how-to-skew-an-element.md)|![Inclinar ilustração](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Move (converte) um elemento pelo especificado <xref:System.Windows.Media.TranslateTransform.X%2A> e <xref:System.Windows.Media.TranslateTransform.Y%2A> quantidades.|[Converter um elemento](../../../../docs/framework/wpf/graphics-multimedia/how-to-translate-an-element.md)|![Converte Ilustração](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Para criar transformações mais complexas, o Windows Presentation Foundation (WPF) fornece as seguintes classes:  
  
|Classe|Descrição|Exemplo|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Agrupa vários <xref:System.Windows.Media.TransformGroup> objetos em um único <xref:System.Windows.Media.Transform> que, em seguida, você pode aplicar propriedades de transformação.|[Aplicar várias transformações a um objeto](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Cria transformações personalizadas que não são fornecidas por outros <xref:System.Windows.Media.Transform> classes. Quando você usa um <xref:System.Windows.Media.MatrixTransform>, você manipula a matriz diretamente.|[Usar um MatrixTransform para criar transformações personalizadas](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) também fornece [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] transformações. Para obter mais informações, consulte a classe <xref:System.Windows.Media.Media3D.Transform3D>.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Propriedades de transformação comum  
 Uma forma de transformar um objeto é declarar apropriado <xref:System.Windows.Media.Transform> digite e aplicá-la à propriedade de transformação do objeto. Diferentes tipos de objetos têm diferentes tipos de propriedades de transformação. A tabela a seguir lista vários tipos mais comuns do Windows Presentation Foundation (WPF) e suas propriedades de transformação.  
  
|Tipo|Propriedades de transformação|  
|----------|-------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## <a name="transformations-and-coordinate-systems"></a>Sistemas de coordenadas e transformações  
 Quando você transformar um objeto, você não apenas transforma o objeto, você transforma o espaço de coordenadas no qual o objeto existe. Por padrão, uma transformação é centralizada na origem do sistema de coordenadas do objeto alvo: (0,0). A única exceção é <xref:System.Windows.Media.TranslateTransform>; um <xref:System.Windows.Media.TranslateTransform> não tem nenhuma propriedade do centro para definir porque o efeito de translação é o mesmo, independentemente de onde esteja centrado.  
  
 O exemplo a seguir usa uma <xref:System.Windows.Media.RotateTransform> girar uma <xref:System.Windows.Shapes.Rectangle> elemento, um tipo de <xref:System.Windows.FrameworkElement>, em 45 graus sobre seu centro padrão, (0, 0). A ilustração a seguir mostra o efeito da rotação.  
  
 ![Um FrameworkElement girado 45 graus em torno de &#40;0,0&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Um elemento retângulo rotacionado em 45 graus em torno do ponto (0,0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Por padrão, o elemento rotaciona sobre seu canto superior esquerdo, (0, 0). O <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform>, e <xref:System.Windows.Media.SkewTransform> classes fornecem propriedades CenterX e CenterY que lhe permitem especificar o ponto em que a transformação é aplicada.  
  
 O próximo exemplo também usa um <xref:System.Windows.Media.RotateTransform> girar um <xref:System.Windows.Shapes.Rectangle> elemento 45 graus; no entanto, desta vez o <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> são definidas para que o <xref:System.Windows.Media.RotateTransform> tenha um centro de (25, 25). A ilustração a seguir mostra o efeito da rotação.  
  
 ![Uma geometria girado 45 graus em torno de &#40;25, 25&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Um elemento retângulo rotacionado em 45 graus em torno do ponto (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>Transformando um FrameworkElement  
 Para aplicar transformações a um <xref:System.Windows.FrameworkElement>, crie um <xref:System.Windows.Media.Transform> e aplicá-la a uma das duas propriedades que o <xref:System.Windows.FrameworkElement> classe fornece:  
  
-   <xref:System.Windows.FrameworkElement.LayoutTransform%2A> – Uma transformação que é aplicada antes da passagem do layout. Depois que a transformação é aplicada, o sistema de layout processa o tamanho transformado e a posição do elemento.  
  
-   <xref:System.Windows.UIElement.RenderTransform%2A> – Uma transformação que modifica a aparência do elemento mas é aplicada após a passagem de layout é concluída. Usando o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade em vez do <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriedade, você pode obter benefícios de desempenho.  
  
 Qual propriedade você deve usar? Devido aos benefícios de desempenho que ele oferece, use o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade sempre que possível, especialmente quando você usa animada <xref:System.Windows.Media.Transform> objetos. Use o <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriedade quando a colocação em escala, girar ou inclinar e você precisa do pai do elemento para ajustar o tamanho transformado do elemento. Observe que, quando eles são usados com o <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriedade, <xref:System.Windows.Media.TranslateTransform> objetos parecem não ter nenhum efeito nos elementos. Isso ocorre porque o sistema de layout retorna o elemento transladado à sua posição original como parte do processamento.  
  
 Para obter informações adicionais sobre layout em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consulte a visão geral do [Layout](../../../../docs/framework/wpf/advanced/layout.md).  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Exemplo: Rotacionar um FrameworkElement em 45 graus  
 O exemplo a seguir usa um <xref:System.Windows.Media.RotateTransform> para girar o botão em 45 graus. O botão está contido em um <xref:System.Windows.Controls.StackPanel> que tem outros dois botões.  
  
 Por padrão, um <xref:System.Windows.Media.RotateTransform> gira sobre o ponto (0, 0). Porque o exemplo não especifica um valor de centro, o botão gira sobre o ponto (0, 0), que é seu canto superior esquerdo. O <xref:System.Windows.Media.RotateTransform> é aplicada para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade. A ilustração a seguir mostra o resultado da transformação.  
  
 ![Um botão transformado com RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Rotação horária em 45 graus no canto superior esquerdo  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 O próximo exemplo também usa um <xref:System.Windows.Media.RotateTransform> girar um botão em 45 graus no sentido horário, mas ele também define o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> do botão para (0,5, 0,5). O valor da <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade é relativo ao tamanho do botão. Como resultado, a rotação é aplicada ao centro do botão, em vez de seu canto superior esquerdo. A ilustração a seguir mostra o resultado da transformação.  
  
 ![Um botão transformado sobre seu centro](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Rotação em sentido horário em 45 graus em torno do centro  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 O exemplo a seguir usa o <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriedade em vez do <xref:System.Windows.UIElement.RenderTransform%2A> propriedade para rotacionar o botão.  Isso faz com que a transformação afete o layout do botão, que dispara uma passagem completa pelo sistema de layout. Como resultado, o botão é rotacionado e então reposicionado porque seu tamanho foi alterado. A ilustração a seguir mostra o resultado da transformação.  
  
 ![Um botão transformado usando LayoutTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
LayoutTransform utilizado para rotacionar o botão  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Animando transformações  
 Porque eles herdam a <xref:System.Windows.Media.Animation.Animatable> classe, o <xref:System.Windows.Media.Transform> classes podem ser animadas. Para animar um <xref:System.Windows.Media.Transform>, aplicar uma animação de um tipo compatível à propriedade que você deseja animar.  
  
 O exemplo a seguir usa uma <xref:System.Windows.Media.Animation.Storyboard> e uma <xref:System.Windows.Media.Animation.DoubleAnimation> com um <xref:System.Windows.Media.RotateTransform> para fazer um <xref:System.Windows.Controls.Button> rotação em vigor quando ele for clicado.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://go.microsoft.com/fwlink/?LinkID=158252). Para mais informações sobre animações, consulte [Visão Geral de Animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Recursos congeláveis  
 Porque ele herda do <xref:System.Windows.Freezable> classe, o <xref:System.Windows.Media.Transform> classe fornece várias funcionalidades especiais: <xref:System.Windows.Media.Transform> objetos podem ser declarados como [recursos](../../../../docs/framework/wpf/advanced/xaml-resources.md), compartilhados entre vários objetos, somente leitura para melhorar desempenho, clonados e transformados em thread-safe. Para obter mais informações sobre os diferentes recursos que são fornecidos pelo <xref:System.Windows.Freezable> objetos, consulte a [visão geral de objetos congeláveis](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Matrix>  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Exemplo de transformações 2D](https://go.microsoft.com/fwlink/?LinkID=158252)
