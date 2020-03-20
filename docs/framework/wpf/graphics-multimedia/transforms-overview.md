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
ms.openlocfilehash: 49fb0109e1d7db065f7e241955f30cb038699020
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187463"
---
# <a name="transforms-overview"></a>Visão geral de transformações
Este tópico descreve como usar as <xref:System.Windows.Media.Transform> classes 2D para girar, dimensionar, mover (traduzir) e distorcer <xref:System.Windows.FrameworkElement> objetos.  

<a name="whatIsATransformSection"></a>
## <a name="what-is-a-transform"></a>O que é uma transformação?  
 A <xref:System.Windows.Media.Transform> define como mapear, ou transformar, pontos de um espaço de coordenadas para outro espaço de coordenadas. Este mapeamento é descrito <xref:System.Windows.Media.Matrix>por uma transformação, que é uma <xref:System.Double> coleção de três linhas com três colunas de valores.  
  
> [!NOTE]
> O Windows Presentation Foundation (WPF) usa matrizes principais de linha. Vetores são expressos em vetores de linha, não vetores de coluna.  
  
 A tabela a seguir mostra a estrutura de uma matriz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="a-2-d-transformation-matrix"></a>A matriz de transformação 2D  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Padrão: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Padrão: 0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Padrão: 0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Padrão: 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Padrão: 0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Padrão: 0.0|1.0|  
  
 Manipulando valores de matriz, você pode girar, dimensionar, inclinar e mover (transladar) um objeto. Por exemplo, se você alterar o valor na primeira <xref:System.Windows.Media.Matrix.OffsetX%2A> coluna da terceira linha (o valor) para 100, você poderá usá-lo para mover um objeto de 100 unidades ao longo do eixo x. Se você alterar o valor na segunda coluna da segunda linha para 3, poderá usá-lo para alongar um objeto para três vezes sua altura atual. Se você alterar os valores, mova objeto 100 unidades no eixo e alongue sua altura por um fator de 3. Como o Windows Presentation Foundation (WPF) só suporta transformações afim, os valores na coluna direita são sempre 0, 0, 1.  
  
 Embora o Windows Presentation Foundation (WPF) permita manipular diretamente <xref:System.Windows.Media.Transform> os valores da matriz, ele também fornece várias classes que permitem transformar um objeto sem saber como a estrutura de matriz subjacente é configurada. Por exemplo, <xref:System.Windows.Media.ScaleTransform> a classe permite que você <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> dimensione um objeto definindo suas propriedades, em vez de manipular uma matriz de transformação. Da mesma <xref:System.Windows.Media.RotateTransform> forma, a classe permite que <xref:System.Windows.Media.RotateTransform.Angle%2A> você gire um objeto apenas definindo sua propriedade.  
  
<a name="transformClassesSection"></a>
## <a name="transform-classes"></a>Classes de transformação  
 O Windows Presentation Foundation (WPF) <xref:System.Windows.Media.Transform> fornece as seguintes classes 2D para operações comuns de transformação:  
  
|Classe|Descrição|Exemplo|Ilustração|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Gira um elemento pelo <xref:System.Windows.Media.RotateTransform.Angle%2A>especificado .|[Girar um objeto](how-to-rotate-an-object.md)|![Ilustração rotativa](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Dimensiona um elemento pelos <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> valores especificados e.|[Dimensionar um elemento](how-to-scale-an-element.md)|![Ilustração em escala](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Distorce um elemento pelos valores especificados <xref:System.Windows.Media.SkewTransform.AngleX%2A> e. <xref:System.Windows.Media.SkewTransform.AngleY%2A>|[Inclinar um elemento](how-to-skew-an-element.md)|![Ilustração de distorção](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Move (traduz) um elemento pelos <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform.Y%2A> valores especificados e.|[Converter um elemento](how-to-translate-an-element.md)|![Traduzir ilustração](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Para criar transformações mais complexas, o Windows Presentation Foundation (WPF) fornece as seguintes duas classes:  
  
|Classe|Descrição|Exemplo|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Agrupa <xref:System.Windows.Media.TransformGroup> vários objetos <xref:System.Windows.Media.Transform> em um único que você pode aplicar para transformar propriedades.|[Aplicar várias transformações a um objeto](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Cria transformações personalizadas que não <xref:System.Windows.Media.Transform> são fornecidas pelas outras classes. Quando você <xref:System.Windows.Media.MatrixTransform>usa um, você manipula uma Matrix diretamente.|[Usar um MatrixTransform para criar transformações personalizadas](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 O Windows Presentation Foundation (WPF) também fornece transformações 3D. Para obter mais informações, consulte a classe <xref:System.Windows.Media.Media3D.Transform3D>.  
  
<a name="transformationproperties"></a>
## <a name="common-transformation-properties"></a>Propriedades de transformação comum  
 Uma maneira de transformar um objeto <xref:System.Windows.Media.Transform> é declarar o tipo apropriado e aplicá-lo à propriedade de transformação do objeto. Diferentes tipos de objetos têm diferentes tipos de propriedades de transformação. A tabela a seguir lista vários tipos comumente usados do Windows Presentation Foundation (WPF) e suas propriedades de transformação.  
  
|Type|Propriedades de transformação|  
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
 Quando você transformar um objeto, você não apenas transforma o objeto, você transforma o espaço de coordenadas no qual o objeto existe. Por padrão, uma transformação é centralizada na origem do sistema de coordenadas do objeto alvo: (0,0). A única <xref:System.Windows.Media.TranslateTransform>exceção é: a <xref:System.Windows.Media.TranslateTransform> não tem propriedades centrais para definir porque o efeito de tradução é o mesmo, independentemente de onde está centrado.  
  
 O exemplo a <xref:System.Windows.Media.RotateTransform> seguir <xref:System.Windows.Shapes.Rectangle> usa um para <xref:System.Windows.FrameworkElement>girar um elemento, um tipo de , por 45 graus sobre seu centro padrão, (0, 0). A ilustração a seguir mostra o efeito da rotação.  
  
 ![Um FrameworkElement girado 45 graus ao redor (0,0)](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Um elemento retângulo rotacionado em 45 graus em torno do ponto (0,0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Por padrão, o elemento rotaciona sobre seu canto superior esquerdo, (0, 0). As <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.ScaleTransform>classes <xref:System.Windows.Media.SkewTransform> e as classes fornecem propriedades CenterX e CenterY que permitem especificar o ponto em que a transformação é aplicada.  
  
 O próximo exemplo <xref:System.Windows.Media.RotateTransform> também usa <xref:System.Windows.Shapes.Rectangle> um para girar um elemento em 45 graus; no entanto, <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> desta vez as propriedades <xref:System.Windows.Media.RotateTransform> e propriedades são definidas de modo que o tem um centro de (25, 25). A ilustração a seguir mostra o efeito da rotação.  
  
 ![Uma geometria girado 45 graus em (25, 25)](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Um elemento retângulo rotacionado em 45 graus em torno do ponto (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>
## <a name="transforming-a-frameworkelement"></a>Transformando um FrameworkElement  
 Para aplicar transformações <xref:System.Windows.FrameworkElement>a <xref:System.Windows.Media.Transform> um , criar um e aplicá-lo a uma das duas propriedades que a <xref:System.Windows.FrameworkElement> classe fornece:  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A>– Uma transformação que é aplicada antes do layout passar. Depois que a transformação é aplicada, o sistema de layout processa o tamanho transformado e a posição do elemento.  
  
- <xref:System.Windows.UIElement.RenderTransform%2A>– Uma transformação que modifica a aparência do elemento, mas é aplicada após a passagem de layout ser concluída. Ao usar <xref:System.Windows.UIElement.RenderTransform%2A> a propriedade <xref:System.Windows.FrameworkElement.LayoutTransform%2A> em vez da propriedade, você pode obter benefícios de desempenho.  
  
 Qual propriedade você deve usar? Devido aos benefícios de desempenho que <xref:System.Windows.UIElement.RenderTransform%2A> ele proporciona, use a <xref:System.Windows.Media.Transform> propriedade sempre que possível, especialmente quando você usa objetos animados. Use <xref:System.Windows.FrameworkElement.LayoutTransform%2A> a propriedade ao dimensionar, girar ou distorcer e você precisa que o pai do elemento se ajuste ao tamanho transformado do elemento. Observe que, quando são <xref:System.Windows.FrameworkElement.LayoutTransform%2A> usados <xref:System.Windows.Media.TranslateTransform> com a propriedade, os objetos parecem não ter efeito sobre os elementos. Isso ocorre porque o sistema de layout retorna o elemento transladado à sua posição original como parte do processamento.  
  
 Para obter informações adicionais sobre layout em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consulte a visão geral do [Layout](../advanced/layout.md).  
  
<a name="exampleRotateAnElement45degSection"></a>
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Exemplo: Rotacionar um FrameworkElement em 45 graus  
 O exemplo a <xref:System.Windows.Media.RotateTransform> seguir usa um para girar um botão no sentido horário em 45 graus. O botão está <xref:System.Windows.Controls.StackPanel> contido em um que tem dois outros botões.  
  
 Por padrão, <xref:System.Windows.Media.RotateTransform> um gira em volta do ponto (0, 0). Porque o exemplo não especifica um valor de centro, o botão gira sobre o ponto (0, 0), que é seu canto superior esquerdo. O <xref:System.Windows.Media.RotateTransform> é aplicado <xref:System.Windows.UIElement.RenderTransform%2A> à propriedade. A ilustração a seguir mostra o resultado da transformação.  
  
 ![Um botão transformado com RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Rotação horária em 45 graus no canto superior esquerdo  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 O próximo exemplo <xref:System.Windows.Media.RotateTransform> também usa um para girar um botão de <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 45 graus no sentido horário, mas também define o botão para (0,5, 0,5). O valor <xref:System.Windows.UIElement.RenderTransformOrigin%2A> da propriedade é relativo ao tamanho do botão. Como resultado, a rotação é aplicada ao centro do botão, em vez de seu canto superior esquerdo. A ilustração a seguir mostra o resultado da transformação.  
  
 ![Um botão transformado sobre seu centro](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Rotação em sentido horário em 45 graus em torno do centro  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 O exemplo a <xref:System.Windows.FrameworkElement.LayoutTransform%2A> seguir usa <xref:System.Windows.UIElement.RenderTransform%2A> a propriedade em vez da propriedade para girar o botão.  Isso faz com que a transformação afete o layout do botão, que dispara uma passagem completa pelo sistema de layout. Como resultado, o botão é rotacionado e então reposicionado porque seu tamanho foi alterado. A ilustração a seguir mostra o resultado da transformação.  
  
 ![Um botão transformado usando LayoutTransform](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
LayoutTransform utilizado para rotacionar o botão  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>
## <a name="animating-transformations"></a>Animando transformações  
 Porque herdam <xref:System.Windows.Media.Animation.Animatable> da <xref:System.Windows.Media.Transform> classe, as aulas podem ser animadas. Para animar <xref:System.Windows.Media.Transform>um , aplique uma animação de um tipo compatível à propriedade que você deseja animar.  
  
 O exemplo a <xref:System.Windows.Media.Animation.Storyboard> seguir <xref:System.Windows.Media.Animation.DoubleAnimation> usa <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Controls.Button> e a com um para fazer um giro no lugar quando ele é clicado.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms). Para mais informações sobre animações, consulte [Visão Geral de Animação](animation-overview.md).  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Recursos congeláveis  
 Por herdar da <xref:System.Windows.Freezable> classe, <xref:System.Windows.Media.Transform> a classe fornece <xref:System.Windows.Media.Transform> várias características especiais: os objetos podem ser declarados como [recursos,](../../../desktop-wpf/fundamentals/xaml-resources-define.md)compartilhados entre vários objetos, feitos somente de leitura para melhorar o desempenho, clonados e tornados seguros para threads. Para obter mais informações sobre os <xref:System.Windows.Freezable> diferentes recursos fornecidos pelos objetos, consulte a visão geral dos [objetos acongelamento](../advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [Tópicos de como fazer](transformations-how-to-topics.md)
- [Exemplo de transformações 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
