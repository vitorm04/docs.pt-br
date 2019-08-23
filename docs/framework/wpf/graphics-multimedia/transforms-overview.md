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
ms.openlocfilehash: 89b781d3e5b88a66598a301a1d08cf7dfedd57a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962893"
---
# <a name="transforms-overview"></a>Visão geral de transformações
Este tópico descreve como usar as <xref:System.Windows.Media.Transform> classes 2D para girar, dimensionar, mover (traduzir) e distorcer <xref:System.Windows.FrameworkElement> objetos.  

<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>O que é uma transformação?  
 Um <xref:System.Windows.Media.Transform> define como mapear, ou transformar, pontos de um espaço de coordenadas para outro espaço de coordenadas. Esse mapeamento é descrito por uma transformação <xref:System.Windows.Media.Matrix>, que é uma coleção de três linhas com três colunas de <xref:System.Double> valores.  
  
> [!NOTE]
> Windows Presentation Foundation (WPF) usa matrizes de linha principal. Vetores são expressos em vetores de linha, não vetores de coluna.  
  
 A tabela a seguir mostra a estrutura de uma matriz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="a-2-d-transformation-matrix"></a>A matriz de transformação 2D  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Padrão: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Padrão: 0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Padrão: 0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Padrão: 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Padrão: 0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Padrão: 0.0|1.0|  
  
 Manipulando valores de matriz, você pode girar, dimensionar, inclinar e mover (transladar) um objeto. Por exemplo, se você alterar o valor na primeira coluna da terceira linha (o <xref:System.Windows.Media.Matrix.OffsetX%2A> valor) para 100, poderá usá-lo para mover um objeto 100 unidades ao longo do eixo x. Se você alterar o valor na segunda coluna da segunda linha para 3, poderá usá-lo para alongar um objeto para três vezes sua altura atual. Se você alterar os valores, mova objeto 100 unidades no eixo e alongue sua altura por um fator de 3. Como Windows Presentation Foundation (WPF) dá suporte apenas a transformações de afinidade, os valores na coluna direita são sempre 0, 0, 1.  
  
 Embora Windows Presentation Foundation (WPF) permita que você manipule diretamente os valores de matriz, ele também <xref:System.Windows.Media.Transform> fornece várias classes que permitem transformar um objeto sem saber como a estrutura de matriz subjacente é configurada. Por exemplo, a <xref:System.Windows.Media.ScaleTransform> classe permite que você dimensione um objeto definindo suas <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> propriedades <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> e, em vez de manipular uma matriz de transformação. Da mesma forma <xref:System.Windows.Media.RotateTransform> , a classe permite girar um objeto apenas definindo sua <xref:System.Windows.Media.RotateTransform.Angle%2A> propriedade.  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Classes de transformação  
 O Windows Presentation Foundation (WPF) fornece as seguintes <xref:System.Windows.Media.Transform> classes 2D para operações de transformação comuns:  
  
|Classe|Descrição|Exemplo|Ilustração|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Gira um elemento pelo especificado <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Girar um objeto](how-to-rotate-an-object.md)|![Girar ilustração](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Dimensiona um elemento de acordo com <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> as <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> quantidades especificadas e.|[Dimensionar um elemento](how-to-scale-an-element.md)|![Dimensionar ilustração](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Distorce um elemento de acordo com os <xref:System.Windows.Media.SkewTransform.AngleX%2A> valores <xref:System.Windows.Media.SkewTransform.AngleY%2A> e especificados.|[Inclinar um elemento](how-to-skew-an-element.md)|![Inclinar ilustração](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Move (traduz) um elemento de acordo com os <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform.Y%2A> valores especificados.|[Converter um elemento](how-to-translate-an-element.md)|![Converte Ilustração](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Para a criação de transformações mais complexas, Windows Presentation Foundation (WPF) fornece as duas classes a seguir:  
  
|Classe|Descrição|Exemplo|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Agrupa vários <xref:System.Windows.Media.TransformGroup> objetos em um único <xref:System.Windows.Media.Transform> que você pode aplicar às propriedades de transformação.|[Aplicar várias transformações a um objeto](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Cria transformações personalizadas que não são fornecidas pelas outras <xref:System.Windows.Media.Transform> classes. Ao usar um <xref:System.Windows.Media.MatrixTransform>, você manipula uma matriz diretamente.|[Usar um MatrixTransform para criar transformações personalizadas](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) também fornece transformações 3D. Para obter mais informações, consulte a classe <xref:System.Windows.Media.Media3D.Transform3D>.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Propriedades de transformação comum  
 Uma maneira de transformar um objeto é declarar o tipo apropriado <xref:System.Windows.Media.Transform> e aplicá-lo à propriedade de transformação do objeto. Diferentes tipos de objetos têm diferentes tipos de propriedades de transformação. A tabela a seguir lista vários tipos de Windows Presentation Foundation (WPF) usados com frequência e suas propriedades de transformação.  
  
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
 Quando você transformar um objeto, você não apenas transforma o objeto, você transforma o espaço de coordenadas no qual o objeto existe. Por padrão, uma transformação é centralizada na origem do sistema de coordenadas do objeto de destino: (0, 0). A única exceção é <xref:System.Windows.Media.TranslateTransform>: um <xref:System.Windows.Media.TranslateTransform> não tem propriedades de centro para definir porque o efeito de tradução é o mesmo, independentemente de onde ele está centralizado.  
  
 O exemplo a seguir usa <xref:System.Windows.Media.RotateTransform> um para girar <xref:System.Windows.Shapes.Rectangle> um elemento, um tipo <xref:System.Windows.FrameworkElement>de, por 45 graus sobre seu centro padrão, (0, 0). A ilustração a seguir mostra o efeito da rotação.  
  
 ![Um FrameworkElement girau 45 graus cerca &#40;de 0,&#41; 0](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Um elemento retângulo rotacionado em 45 graus em torno do ponto (0,0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Por padrão, o elemento rotaciona sobre seu canto superior esquerdo, (0, 0). As <xref:System.Windows.Media.RotateTransform>classes <xref:System.Windows.Media.ScaleTransform>, e<xref:System.Windows.Media.SkewTransform> fornecem as propriedades CenterX e CenterY que permitem especificar o ponto no qual a transformação é aplicada.  
  
 O exemplo a seguir também usa <xref:System.Windows.Media.RotateTransform> um para girar <xref:System.Windows.Shapes.Rectangle> um elemento por 45 graus; no entanto, <xref:System.Windows.Media.RotateTransform.CenterX%2A> desta <xref:System.Windows.Media.RotateTransform.CenterY%2A> vez, as propriedades e são <xref:System.Windows.Media.RotateTransform> definidas para que o tenha um centro de (25, 25). A ilustração a seguir mostra o efeito da rotação.  
  
 ![Uma geometria girada 45 graus cerca &#40;de 25,&#41; 25](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Um elemento retângulo rotacionado em 45 graus em torno do ponto (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>Transformando um FrameworkElement  
 Para aplicar transformações a um <xref:System.Windows.FrameworkElement>, crie um <xref:System.Windows.Media.Transform> e aplique-o a uma das duas propriedades que a <xref:System.Windows.FrameworkElement> classe fornece:  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A>– Uma transformação que é aplicada antes da passagem de layout. Depois que a transformação é aplicada, o sistema de layout processa o tamanho transformado e a posição do elemento.  
  
- <xref:System.Windows.UIElement.RenderTransform%2A>– Uma transformação que modifica a aparência do elemento, mas é aplicada após a conclusão da passagem de layout. Usando a <xref:System.Windows.UIElement.RenderTransform%2A> Propriedade em vez <xref:System.Windows.FrameworkElement.LayoutTransform%2A> da propriedade, você pode obter benefícios de desempenho.  
  
 Qual propriedade você deve usar? Devido aos benefícios de desempenho que ele fornece, use a <xref:System.Windows.UIElement.RenderTransform%2A> propriedade sempre que possível, especialmente quando você usa <xref:System.Windows.Media.Transform> objetos animados. Use a <xref:System.Windows.FrameworkElement.LayoutTransform%2A> Propriedade ao dimensionar, girar ou inclinar e você precisa que o pai do elemento seja ajustado para o tamanho transformado do elemento. Observe que, quando eles são usados com a <xref:System.Windows.FrameworkElement.LayoutTransform%2A> Propriedade, <xref:System.Windows.Media.TranslateTransform> os objetos parecem não ter nenhum efeito sobre os elementos. Isso ocorre porque o sistema de layout retorna o elemento transladado à sua posição original como parte do processamento.  
  
 Para obter informações adicionais sobre layout em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consulte a visão geral do [Layout](../advanced/layout.md).  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Exemplo: Girar um FrameworkElement 45 graus  
 O exemplo a seguir usa <xref:System.Windows.Media.RotateTransform> um para girar um botão no sentido horário por 45 graus. O botão está contido em um <xref:System.Windows.Controls.StackPanel> que tem dois outros botões.  
  
 Por padrão, um <xref:System.Windows.Media.RotateTransform> gira sobre o ponto (0, 0). Porque o exemplo não especifica um valor de centro, o botão gira sobre o ponto (0, 0), que é seu canto superior esquerdo. O <xref:System.Windows.Media.RotateTransform> é aplicado <xref:System.Windows.UIElement.RenderTransform%2A> à propriedade. A ilustração a seguir mostra o resultado da transformação.  
  
 ![Um botão transformado usando RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Rotação horária em 45 graus no canto superior esquerdo  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 O exemplo a seguir também usa <xref:System.Windows.Media.RotateTransform> um para girar um botão 45 graus no sentido horário, mas também <xref:System.Windows.UIElement.RenderTransformOrigin%2A> define o do botão para (0,5, 0,5). O valor da <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade é relativo ao tamanho do botão. Como resultado, a rotação é aplicada ao centro do botão, em vez de seu canto superior esquerdo. A ilustração a seguir mostra o resultado da transformação.  
  
 ![Um botão transformado sobre seu centro](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Rotação em sentido horário em 45 graus em torno do centro  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 O exemplo a seguir usa <xref:System.Windows.FrameworkElement.LayoutTransform%2A> a propriedade em vez <xref:System.Windows.UIElement.RenderTransform%2A> da propriedade para girar o botão.  Isso faz com que a transformação afete o layout do botão, que dispara uma passagem completa pelo sistema de layout. Como resultado, o botão é rotacionado e então reposicionado porque seu tamanho foi alterado. A ilustração a seguir mostra o resultado da transformação.  
  
 ![Um botão transformado usando LayoutTransform](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
LayoutTransform utilizado para rotacionar o botão  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Animando transformações  
 Como eles herdam da <xref:System.Windows.Media.Animation.Animatable> classe, as <xref:System.Windows.Media.Transform> classes podem ser animadas. Para animar <xref:System.Windows.Media.Transform>um, aplique uma animação de um tipo compatível à propriedade que você deseja animar.  
  
 O exemplo a seguir usa <xref:System.Windows.Media.Animation.Storyboard> um e <xref:System.Windows.Media.Animation.DoubleAnimation> um com <xref:System.Windows.Media.RotateTransform> um para fazer <xref:System.Windows.Controls.Button> uma rotação no local quando ele é clicado.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://go.microsoft.com/fwlink/?LinkID=158252). Para mais informações sobre animações, consulte [Visão Geral de Animação](animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Recursos congeláveis  
 Como ele é herdado <xref:System.Windows.Freezable> da classe, <xref:System.Windows.Media.Transform> a classe fornece vários recursos especiais <xref:System.Windows.Media.Transform> : os objetos podem ser declarados como [recursos](../advanced/xaml-resources.md), compartilhados entre vários objetos, feitos somente leitura para melhorar o desempenho, clonado e tornar thread-safe. Para obter mais informações sobre os diferentes recursos fornecidos por <xref:System.Windows.Freezable> objetos, consulte a [visão geral dos objetos Freezable](../advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [Tópicos de instruções](transformations-how-to-topics.md)
- [Exemplo de transformações 2D](https://go.microsoft.com/fwlink/?LinkID=158252)
