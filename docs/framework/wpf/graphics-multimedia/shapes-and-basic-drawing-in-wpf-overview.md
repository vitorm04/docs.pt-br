---
title: Formas e visão geral do desenho básico
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
ms.openlocfilehash: 44104bec478f1fbb10acc0e591af43ea95fecdc5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141322"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Visão geral de formas e desenho básico no WPF
Este tópico dá uma visão geral <xref:System.Windows.Shapes.Shape> de como desenhar com objetos. A <xref:System.Windows.Shapes.Shape> é um <xref:System.Windows.UIElement> tipo de que permite desenhar uma forma para a tela. Por serem elementos <xref:System.Windows.Shapes.Shape> de IU, <xref:System.Windows.Controls.Panel> os objetos podem ser usados dentro de elementos e a maioria dos controles.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferece várias camadas de acesso aos elementos gráficos e serviços de renderização. Na camada superior, <xref:System.Windows.Shapes.Shape> os objetos são fáceis de usar e [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornecem muitos recursos úteis, como layout e participação no sistema de eventos.  

<a name="shapes"></a>
## <a name="shape-objects"></a>Objetos de forma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornece uma série de objetos prontos para uso. <xref:System.Windows.Shapes.Shape>  Todos os objetos <xref:System.Windows.Shapes.Shape> de forma herdam da classe. Os objetos <xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Shapes.Line>de <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>forma <xref:System.Windows.Shapes.Polyline>disponíveis <xref:System.Windows.Shapes.Rectangle>incluem, , , , , e . <xref:System.Windows.Shapes.Shape>objetos compartilham as seguintes propriedades comuns.  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: Descreve como o contorno da forma é pintado.  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Descreve a espessura do contorno da forma.  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: Descreve como o interior da forma é pintado.  
  
- Propriedades de dados para especificar as coordenadas e vértices, medido em pixels independentes de dispositivo.  
  
 Por derivarem de objetos de <xref:System.Windows.UIElement>forma, podem ser usados dentro de painéis e a maioria dos controles. O <xref:System.Windows.Controls.Canvas> painel é uma escolha particularmente boa para criar desenhos complexos porque suporta o posicionamento absoluto de seus objetos infantis.  
  
 A <xref:System.Windows.Shapes.Line> classe permite que você desenhe uma linha entre dois pontos. O exemplo a seguir mostra várias maneiras para especificar as coordenadas de linha e propriedades de traço.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 A imagem a seguir <xref:System.Windows.Shapes.Line>mostra a renderização .  
  
 ![Ilustração da linha](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Embora <xref:System.Windows.Shapes.Line> a classe <xref:System.Windows.Shapes.Shape.Fill%2A> forneça uma propriedade, defini-la não tem efeito porque a não <xref:System.Windows.Shapes.Line> tem área.  
  
 Outra forma comum é a <xref:System.Windows.Shapes.Ellipse>.  Crie <xref:System.Windows.Shapes.Ellipse> um definindo a <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> forma e as propriedades. Para desenhar um círculo, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> especifique um <xref:System.Windows.Shapes.Ellipse> cujos valores são iguais.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 A imagem a seguir mostra <xref:System.Windows.Shapes.Ellipse>um exemplo de uma renderização .  
  
 ![Ilustração de elipse](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a>Usando caminhos e geometrias  
 A <xref:System.Windows.Shapes.Path> classe permite desenhar curvas e formas complexas. Essas curvas e formas <xref:System.Windows.Media.Geometry> são descritas usando objetos. Para usar <xref:System.Windows.Shapes.Path>um , <xref:System.Windows.Media.Geometry> você cria um <xref:System.Windows.Shapes.Path> e <xref:System.Windows.Shapes.Path.Data%2A> usa-o para definir a propriedade do objeto.  
  
 Há uma variedade <xref:System.Windows.Media.Geometry> de objetos para escolher. As <xref:System.Windows.Media.LineGeometry> <xref:System.Windows.Media.RectangleGeometry>classes <xref:System.Windows.Media.EllipseGeometry> descrevem formas relativamente simples. Para criar formas mais complexas ou <xref:System.Windows.Media.PathGeometry>criar curvas, use um .  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry e PathSegments  
 <xref:System.Windows.Media.PathGeometry>objetos são compostos <xref:System.Windows.Media.PathFigure> por um ou mais objetos; cada <xref:System.Windows.Media.PathFigure> um representa uma "figura" ou forma diferente. Cada <xref:System.Windows.Media.PathFigure> um é composto por <xref:System.Windows.Media.PathSegment> um ou mais objetos, cada um representando uma parte conectada da figura ou forma. Os tipos de <xref:System.Windows.Media.LineSegment>segmento <xref:System.Windows.Media.BezierSegment>incluem: , e <xref:System.Windows.Media.ArcSegment>.  
  
 No exemplo a <xref:System.Windows.Shapes.Path> seguir, a é usado para desenhar uma curva quadrática de Bezier.  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 A imagem a seguir mostra a forma renderizada.  
  
 ![Ilustração do caminho](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Para obter <xref:System.Windows.Media.PathGeometry> mais informações <xref:System.Windows.Media.Geometry> sobre e as outras classes, consulte a [visão geral da geometria](geometry-overview.md).  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a>Sintaxe XAML abreviada  
 Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você também pode usar uma sintaxe <xref:System.Windows.Shapes.Path>abreviada especial para descrever um . No exemplo a seguir, a sintaxe abreviada é usada para desenhar uma forma complexa.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 A imagem a seguir <xref:System.Windows.Shapes.Path>mostra uma renderização .  
  
 ![Ilustração do caminho](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 A <xref:System.Windows.Shapes.Path.Data%2A> seqüência de atributos começa com o comando "moveto", indicado por M, <xref:System.Windows.Controls.Canvas>que estabelece um ponto de partida para o caminho no sistema de coordenadas do . <xref:System.Windows.Shapes.Path>os parâmetros de dados são sensíveis a maiúsculas e minúsculas. A capital M indica uma localização absoluta para o novo ponto atual. Um m minúsculo indicaria coordenadas relativas. O primeiro segmento é um início de curva de Bézier cúbico no (100,200) e terminando em (400,175), desenhado usando os dois controle pontos (100,25) e (400,350). Este segmento é indicado pelo comando <xref:System.Windows.Shapes.Path.Data%2A> C na seqüência de atributos. Novamente, o C maiúsculo indica um caminho absoluto; o c minúsculo indicaria um caminho relativo.  
  
 O segundo segmento começa com um comando absoluto horizontal "lineto" H, que especifica uma linha desenhada do ponto de extremidade do subcaminho anterior (400,175) para um novo ponto de extremidade (280,175). Por ser um comando horizontal "lineto", o valor especificado é uma coordenada *x.*  
  
 Para obter a sintaxe <xref:System.Windows.Shapes.Path.Data%2A> completa do caminho, consulte a referência e [crie uma forma usando uma geometria de caminho](how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a>Pintando formas  
 <xref:System.Windows.Media.Brush>objetos são usados para <xref:System.Windows.Shapes.Shape.Stroke%2A> <xref:System.Windows.Shapes.Shape.Fill%2A>pintar uma forma e . No exemplo a seguir, o <xref:System.Windows.Shapes.Ellipse> traçado e o preenchimento de um são especificados. Observe que a entrada válida para propriedades de pincel pode ser uma palavra-chave ou o valor hexadecimal da cor. Para obter mais informações sobre palavras-chave <xref:System.Windows.Media.Colors> coloridas <xref:System.Windows.Media> disponíveis, consulte as propriedades da classe no namespace.  
  
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
  
 A imagem a seguir <xref:System.Windows.Shapes.Ellipse>mostra a renderização .  
  
 ![Uma elipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternativamente, você pode usar a sintaxe <xref:System.Windows.Media.SolidColorBrush> do elemento de propriedade para criar explicitamente um objeto para pintar a forma com uma cor sólida.  
  
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
  
 ![Ilustração solidcolorbrush](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Você também pode pintar um traço ou preenchimento da forma com gradientes, imagens, padrões e muito mais. Para obter mais informações, consulte a [pintura com cores sólidas e visão geral dos gradientes](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a>Formas alongáveis  
 <xref:System.Windows.Shapes.Polyline> <xref:System.Windows.Shapes.Rectangle> Todas as <xref:System.Windows.Shapes.Shape.Stretch%2A> classes têm uma propriedade. <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon> Esta propriedade determina <xref:System.Windows.Shapes.Shape> como o conteúdo de um objeto (a forma <xref:System.Windows.Shapes.Shape> a ser desenhada) é estendido para preencher o espaço de layout do objeto. O <xref:System.Windows.Shapes.Shape> espaço de layout de um <xref:System.Windows.Shapes.Shape> objeto é a quantidade de espaço que <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> é alocado pelo <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> sistema de layout, por causa de uma configuração explícita ou por causa de suas configurações. Para obter informações adicionais sobre o layout na Windows Presentation Foundation, consulte visão geral [do layout.](../advanced/layout.md)  
  
 A propriedade Stretch usa um dos seguintes valores:  
  
- <xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> O conteúdo do objeto não está esticado.  
  
- <xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> O conteúdo do objeto é estendido para preencher seu espaço de layout.  A taxa de proporção não é preservada.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> O conteúdo do objeto é estendido o máximo possível para preencher seu espaço de layout, preservando sua proporção original.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> O conteúdo do objeto é estendido para preencher completamente seu espaço de layout, preservando sua proporção original.  
  
 Observe que, <xref:System.Windows.Shapes.Shape> quando o conteúdo de um <xref:System.Windows.Shapes.Shape> objeto é esticado, o contorno do objeto é pintado após o alongamento.  
  
 No exemplo a <xref:System.Windows.Shapes.Polygon> seguir, a é usado para desenhar um triângulo muito pequeno de (0,0) para (0,1) para (1,1). O <xref:System.Windows.Shapes.Polygon> objeto <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> são definidos como 100, e sua propriedade de estiramento está definida como Fill. Como resultado, <xref:System.Windows.Shapes.Polygon> o conteúdo do objeto (o triângulo) é esticado para preencher o espaço maior.  
  
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
 A <xref:System.Windows.Media.Transform> classe fornece os meios para transformar formas em um plano bidimensional.  Os diferentes tipos de<xref:System.Windows.Media.RotateTransform>transformação<xref:System.Windows.Media.ScaleTransform>incluem rotação<xref:System.Windows.Media.SkewTransform>( ),<xref:System.Windows.Media.TranslateTransform>escala ( ), distorção ( ) e tradução ( ).  
  
 Uma transformação comum a ser aplicada a uma forma é uma rotação.  Para girar uma forma, crie um <xref:System.Windows.Media.RotateTransform> e especifique sua <xref:System.Windows.Media.RotateTransform.Angle%2A>. Um <xref:System.Windows.Media.RotateTransform.Angle%2A> de 45 gira o elemento 45 graus no sentido horário; um ângulo de 90 gira o elemento 90 graus no sentido horário; e assim por diante. Defina <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> as propriedades e se você quiser controlar o ponto sobre o qual o elemento é girado. Esses valores de propriedade são expressos no espaço de coordenadas do elemento que está sendo transformado. <xref:System.Windows.Media.RotateTransform.CenterX%2A>e <xref:System.Windows.Media.RotateTransform.CenterY%2A> têm valores padrão de zero. Finalmente, aplique <xref:System.Windows.Media.RotateTransform> o elemento ao elemento. Se você não quiser que a transformação afete o layout, defina a propriedade da <xref:System.Windows.UIElement.RenderTransform%2A> forma.  
  
 No exemplo a <xref:System.Windows.Media.RotateTransform> seguir, a é usado para girar uma forma de 45 graus sobre o canto superior esquerdo da forma (0,0).  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 No próximo exemplo, outra forma é girada 45 graus, mas dessa vez é girada em torno do ponto (25,50).  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 A ilustração a seguir mostra os resultados da aplicação das duas transformações.  
  
 ![Rotações de 45 graus com pontos centrais diferentes](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 Nos exemplos anteriores, um única transformação foi aplicada a cada objeto de forma. Para aplicar várias transformações em uma forma (ou <xref:System.Windows.Media.TransformGroup>qualquer outro elemento de IA), use a .  
  
## <a name="see-also"></a>Confira também

- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md)
- [Visão geral de geometria](geometry-overview.md)
- [Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Visão geral da animação](animation-overview.md)
