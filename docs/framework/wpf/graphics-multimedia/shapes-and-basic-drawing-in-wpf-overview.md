---
title: Visão geral de formas e desenho básico
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
ms.openlocfilehash: dfdbf67d35cbb13e80d0c5184f165b0cc660e2ef
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731628"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Visão geral de formas e desenho básico no WPF
Este tópico fornece uma visão geral de como desenhar com <xref:System.Windows.Shapes.Shape> objetos. Um <xref:System.Windows.Shapes.Shape> é um tipo de <xref:System.Windows.UIElement> que permite desenhar uma forma na tela. Como são elementos da interface do usuário, <xref:System.Windows.Shapes.Shape> objetos podem ser usados dentro de elementos <xref:System.Windows.Controls.Panel> e da maioria dos controles.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferece várias camadas de acesso aos elementos gráficos e serviços de renderização. Na camada superior, <xref:System.Windows.Shapes.Shape> objetos são fáceis de usar e fornecem muitos recursos úteis, como o layout e a participação no sistema de eventos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="shapes"></a>   
## <a name="shape-objects"></a>Objetos de forma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece vários objetos de <xref:System.Windows.Shapes.Shape> prontos para uso.  Todos os objetos de forma herdam da classe <xref:System.Windows.Shapes.Shape>. Os objetos de forma disponíveis incluem <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>e <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Shapes.Shape> objetos compartilham as seguintes propriedades comuns.  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: descreve como o contorno da forma é pintado.  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: descreve a espessura do contorno da forma.  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: descreve como o interior da forma é pintado.  
  
- Propriedades de dados para especificar as coordenadas e vértices, medido em pixels independentes de dispositivo.  
  
 Como derivam de <xref:System.Windows.UIElement>, os objetos de forma podem ser usados dentro de painéis e da maioria dos controles. O painel de <xref:System.Windows.Controls.Canvas> é uma opção particularmente boa para a criação de desenhos complexos porque ele dá suporte ao posicionamento absoluto de seus objetos filho.  
  
 A classe <xref:System.Windows.Shapes.Line> permite desenhar uma linha entre dois pontos. O exemplo a seguir mostra várias maneiras para especificar as coordenadas de linha e propriedades de traço.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 A imagem a seguir mostra o <xref:System.Windows.Shapes.Line>renderizado.  
  
 ![Ilustração de linha](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Embora a classe <xref:System.Windows.Shapes.Line> forneça uma propriedade <xref:System.Windows.Shapes.Shape.Fill%2A>, defini-la não tem nenhum efeito porque uma <xref:System.Windows.Shapes.Line> não tem nenhuma área.  
  
 Outra forma comum é a <xref:System.Windows.Shapes.Ellipse>.  Crie um <xref:System.Windows.Shapes.Ellipse> definindo as propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> da forma. Para desenhar um círculo, especifique um <xref:System.Windows.Shapes.Ellipse> cujos valores <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> sejam iguais.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 A imagem a seguir mostra um exemplo de um <xref:System.Windows.Shapes.Ellipse>renderizado.  
  
 ![Ilustração da elipse](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>Usando caminhos e geometrias  
 A classe <xref:System.Windows.Shapes.Path> permite desenhar curvas e formas complexas. Essas curvas e formas são descritas usando objetos <xref:System.Windows.Media.Geometry>. Para usar uma <xref:System.Windows.Shapes.Path>, crie um <xref:System.Windows.Media.Geometry> e use-o para definir a propriedade <xref:System.Windows.Shapes.Path.Data%2A> do objeto de <xref:System.Windows.Shapes.Path>.  
  
 Há uma variedade de objetos <xref:System.Windows.Media.Geometry> para sua escolha. As classes <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>e <xref:System.Windows.Media.EllipseGeometry> descrevem formas relativamente simples. Para criar formas mais complexas ou criar curvas, use um <xref:System.Windows.Media.PathGeometry>.  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry e PathSegments  
 os objetos de <xref:System.Windows.Media.PathGeometry> são compostos de um ou mais objetos de <xref:System.Windows.Media.PathFigure>; cada <xref:System.Windows.Media.PathFigure> representa uma "figura" ou forma diferente. Cada <xref:System.Windows.Media.PathFigure> é composta de um ou mais objetos de <xref:System.Windows.Media.PathSegment>, cada um representando uma parte conectada da figura ou forma. Os tipos de segmento incluem o seguinte: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>e <xref:System.Windows.Media.ArcSegment>.  
  
 No exemplo a seguir, um <xref:System.Windows.Shapes.Path> é usado para desenhar uma curva de Bézier quadrática.  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 A imagem a seguir mostra a forma renderizada.  
  
 ![Ilustração de caminho](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Para obter mais informações sobre <xref:System.Windows.Media.PathGeometry> e outras classes de <xref:System.Windows.Media.Geometry>, consulte a [visão geral da geometria](geometry-overview.md).  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>Sintaxe XAML abreviada  
 Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você também pode usar uma sintaxe abreviada especial para descrever uma <xref:System.Windows.Shapes.Path>. No exemplo a seguir, a sintaxe abreviada é usada para desenhar uma forma complexa.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 A imagem a seguir mostra um <xref:System.Windows.Shapes.Path>renderizado.  
  
 ![Ilustração de caminho](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 A cadeia de caracteres do atributo <xref:System.Windows.Shapes.Path.Data%2A> começa com o comando "MoveTo", indicado por M, que estabelece um ponto de partida para o caminho no sistema de coordenadas do <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Shapes.Path> parâmetros de dados diferenciam maiúsculas de minúsculas. O M maiúsculo indica um local absoluto para o novo ponto atual. Um m minúsculo indicaria coordenadas relativas. O primeiro segmento é um início de curva de Bézier cúbico no (100,200) e terminando em (400,175), desenhado usando os dois controle pontos (100,25) e (400,350). Esse segmento é indicado pelo comando C na cadeia de caracteres do atributo <xref:System.Windows.Shapes.Path.Data%2A>. Novamente, o C maiúsculo indica um caminho absoluto; o c minúsculo indicaria um caminho relativo.  
  
 O segundo segmento começa com um comando absoluto horizontal "lineto" H, que especifica uma linha desenhada do ponto de extremidade do subcaminho anterior (400,175) para um novo ponto de extremidade (280,175). Como é um comando horizontal "lineto", o valor especificado é uma coordenada *x*.  
  
 Para obter a sintaxe de caminho completo, consulte a referência de <xref:System.Windows.Shapes.Path.Data%2A> e [criar uma forma usando um PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>Pintando formas  
 <xref:System.Windows.Media.Brush> objetos são usados para pintar <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.Fill%2A>de uma forma. No exemplo a seguir, o traço e o preenchimento de uma <xref:System.Windows.Shapes.Ellipse> são especificados. Observe que a entrada válida para propriedades de pincel pode ser uma palavra-chave ou o valor hexadecimal da cor. Para obter mais informações sobre palavras-chave de cores disponíveis, consulte Propriedades da classe <xref:System.Windows.Media.Colors> no namespace <xref:System.Windows.Media>.  
  
```xaml
<Canvas Background="LightGray">   
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
```  
  
 A imagem a seguir mostra o <xref:System.Windows.Shapes.Ellipse>renderizado.  
  
 ![Uma elipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Como alternativa, você pode usar a sintaxe do elemento Property para criar explicitamente um <xref:System.Windows.Media.SolidColorBrush> objeto para pintar a forma com uma cor sólida.  
  
```xaml
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"   
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 A ilustração a seguir mostra a forma renderizada.  
  
 ![Ilustração de SolidColorBrush](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Você também pode pintar um traço ou preenchimento da forma com gradientes, imagens, padrões e muito mais. Para obter mais informações, consulte a [visão geral sobre pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>Formas alongáveis  
 Todas as classes <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>e <xref:System.Windows.Shapes.Rectangle> têm uma propriedade <xref:System.Windows.Shapes.Shape.Stretch%2A>. Essa propriedade determina como o conteúdo de um <xref:System.Windows.Shapes.Shape> objeto (a forma a ser desenhada) é ampliado para preencher o espaço de layout do objeto de <xref:System.Windows.Shapes.Shape>. O espaço de layout de um objeto de <xref:System.Windows.Shapes.Shape> é a quantidade de espaço que o <xref:System.Windows.Shapes.Shape> é alocado pelo sistema de layout, devido a uma configuração explícita de <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> ou devido às suas configurações <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> e <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. Para obter informações adicionais sobre o layout em Windows Presentation Foundation, consulte Visão geral de [layout](../advanced/layout.md) .  
  
 A propriedade Stretch usa um dos seguintes valores:  
  
- <xref:System.Windows.Media.Stretch.None>: o conteúdo do objeto <xref:System.Windows.Shapes.Shape> não é alongado.  
  
- <xref:System.Windows.Media.Stretch.Fill>: o conteúdo do objeto <xref:System.Windows.Shapes.Shape> é ampliado para preencher seu espaço de layout.  A taxa de proporção não é preservada.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: o conteúdo do objeto <xref:System.Windows.Shapes.Shape> é alongado tanto quanto possível para preencher seu espaço de layout enquanto preserva sua taxa de proporção original.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: o conteúdo do objeto <xref:System.Windows.Shapes.Shape> é alongado para preencher completamente seu espaço de layout enquanto preserva sua taxa de proporção original.  
  
 Observe que, quando o conteúdo de um objeto de <xref:System.Windows.Shapes.Shape> é ampliado, a estrutura de tópicos do objeto <xref:System.Windows.Shapes.Shape> é pintada após o alongamento.  
  
 No exemplo a seguir, um <xref:System.Windows.Shapes.Polygon> é usado para desenhar um triângulo muito pequeno de (0, 0) para (0, 1) a (1, 1). O <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> do objeto de <xref:System.Windows.Shapes.Polygon> são definidos como 100 e sua propriedade Stretch é definida como Fill. Como resultado, o conteúdo do objeto <xref:System.Windows.Shapes.Polygon> (o triângulo) é ampliado para preencher o espaço maior.  
  
```xaml
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
```

```csharp
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
```

<a name="transforms"></a>   
## <a name="transforming-shapes"></a>transformando as formas  
 A classe <xref:System.Windows.Media.Transform> fornece os meios para transformar formas em um plano bidimensional.  Os diferentes tipos de transformação incluem rotação (<xref:System.Windows.Media.RotateTransform>), escala (<xref:System.Windows.Media.ScaleTransform>), distorção (<xref:System.Windows.Media.SkewTransform>) e translação (<xref:System.Windows.Media.TranslateTransform>).  
  
 Uma transformação comum a ser aplicada a uma forma é uma rotação.  Para girar uma forma, crie um <xref:System.Windows.Media.RotateTransform> e especifique sua <xref:System.Windows.Media.RotateTransform.Angle%2A>. Um <xref:System.Windows.Media.RotateTransform.Angle%2A> de 45 gira o elemento 45 graus no sentido horário; um ângulo de 90 gira o elemento 90 graus no sentido horário; e assim por diante. Defina as propriedades <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> se desejar controlar o ponto sobre o qual o elemento é girado. Esses valores de propriedade são expressos no espaço de coordenadas do elemento que está sendo transformado. <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> têm valores padrão de zero. Por fim, aplique o <xref:System.Windows.Media.RotateTransform> ao elemento. Se você não quiser que a transformação afete o layout, defina a propriedade <xref:System.Windows.UIElement.RenderTransform%2A> da forma.  
  
 No exemplo a seguir, um <xref:System.Windows.Media.RotateTransform> é usado para girar uma forma 45 graus sobre o canto superior esquerdo da forma (0, 0).  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 No próximo exemplo, outra forma é girada 45 graus, mas dessa vez é girada em torno do ponto (25,50).  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 A ilustração a seguir mostra os resultados da aplicação das duas transformações.  
  
 ![Rotações de 45 graus com pontos centrais diferentes](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 Nos exemplos anteriores, um única transformação foi aplicada a cada objeto de forma. Para aplicar várias transformações a uma forma (ou qualquer outro elemento de interface do usuário), use um <xref:System.Windows.Media.TransformGroup>.  
  
## <a name="see-also"></a>Consulte também

- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md)
- [Visão geral de geometria](geometry-overview.md)
- [Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Visão geral da animação](animation-overview.md)
