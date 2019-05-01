---
title: Visão geral da pintura com cores sólidas e gradientes
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- painting with gradients [WPF]
- gradients [WPF], painting with
- brushes [WPF], painting with solid colors
- brushes [WPF], painting with gradients
- painting with solid colors [WPF]
ms.assetid: f5b182f3-c5c7-4cbe-9f2f-65e690d08255
ms.openlocfilehash: 7945660f40e44596fe36a6b9d53223a0e264a064
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009383"
---
# <a name="painting-with-solid-colors-and-gradients-overview"></a>Visão geral da pintura com cores sólidas e gradientes
Este tópico descreve como usar <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.LinearGradientBrush>, e <xref:System.Windows.Media.RadialGradientBrush> objetos para pintar com cores sólidas, gradientes lineares e gradientes radiais.  

<a name="solidcolor"></a>   
## <a name="painting-an-area-with-a-solid-color"></a>Pintar uma área com uma cor sólida  
 Uma das operações mais comuns em qualquer plataforma é pintar uma área com uma sólida <xref:System.Windows.Media.Color>. Para realizar essa tarefa, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece o <xref:System.Windows.Media.SolidColorBrush> classe. As seções a seguir descrevem as diferentes maneiras de pintar com um <xref:System.Windows.Media.SolidColorBrush>.  
  
<a name="solidcolorinxaml"></a>   
### <a name="using-a-solidcolorbrush-in-xaml"></a>Usando um SolidColorBrush em "XAML"  
 Para pintar uma área com uma cor sólida em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use uma das opções a seguir.  
  
- Selecione um pincel de cor sólida predefinida pelo nome.  Por exemplo, você pode definir um botão <xref:System.Windows.Controls.Control.Background%2A> "Vermelho" ou "MediumBlue".  Para obter uma lista das outras predefinidas pincéis de cores sólidas, consulte as propriedades estáticas do <xref:System.Windows.Media.Brushes> classe. Confira o exemplo abaixo.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]  
  
- Escolha uma cor da paleta de cores de 32 bits, especificando as quantidades de vermelho, verde e azul para combinar em uma única cor sólida.  O formato para especificar uma cor da paleta de 32 bits é "*#rrggbb*", em que *rr* é um número hexadecimal de dois dígitos que especifica a quantidade relativa de vermelho, *gg* especifica a quantidade de verde e *bb* especifica a quantidade de azul.  Além disso, a cor pode ser especificada como "#*aarrggbb*" em que *aa* especifica o valor *alfa*, ou a transparência, da cor. Essa abordagem permite que você crie cores parcialmente transparentes.  No exemplo a seguir, o <xref:System.Windows.Controls.Control.Background%2A> de um <xref:System.Windows.Controls.Button> é definido como vermelho totalmente opaco usando notação hexadecimal.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]  
  
- Usar a sintaxe de marca de propriedade para descrever um <xref:System.Windows.Media.SolidColorBrush>. Essa sintaxe é mais detalhada, mas permite que você especifique configurações adicionais, como a opacidade do pincel. No exemplo a seguir, o <xref:System.Windows.Controls.Control.Background%2A> propriedades de dois <xref:System.Windows.Controls.Button> elementos serão definidos como vermelho totalmente opaco. A primeira cor do pincel é descrita usando um nome de cor predefinido. A segunda cor do pincel é descrita usando notação hexadecimal.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]  
  
<a name="solidcolorsincode"></a>   
### <a name="painting-with-a-solidcolorbrush-in-code"></a>Pintando com um SolidColorBrush no código  
 Para pintar uma área com uma cor sólida no código, use uma das opções a seguir.  
  
- Use um dos pincéis predefinidos fornecidos pelo <xref:System.Windows.Media.Brushes> classe. No exemplo a seguir, o <xref:System.Windows.Controls.Control.Background%2A> de um <xref:System.Windows.Controls.Button> é definido como <xref:System.Windows.Media.Brushes.Red%2A>.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]  
  
- Criar uma <xref:System.Windows.Media.SolidColorBrush> e defina sua <xref:System.Windows.Media.SolidColorBrush.Color%2A> propriedade usando um <xref:System.Windows.Media.Color> estrutura. Você pode usar uma cor predefinida na <xref:System.Windows.Media.Colors> classe, ou você pode criar um <xref:System.Windows.Media.Color> usando o estático <xref:System.Windows.Media.Color.FromArgb%2A> método.  
  
     O exemplo a seguir mostra como definir a <xref:System.Windows.Media.SolidColorBrush.Color%2A> propriedade de um <xref:System.Windows.Media.SolidColorBrush> usando uma cor predefinida.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]  
  
 Estático <xref:System.Windows.Media.Color.FromArgb%2A> permite que você especifique os valores da cor alfa, vermelho, verde e azul. O intervalo típico para cada um desses valores é de 0 a 255. Por exemplo, um valor alfa igual a 0 indica que uma cor é completamente transparente, enquanto um valor de 255 indica que a cor é completamente opaca. Da mesma forma, um valor de vermelho igual a 0 indica que uma cor não contém nenhum vermelho, enquanto um valor de 255 indica que uma cor tem a quantidade máxima possível de vermelho.  No exemplo a seguir, a cor do pincel é descrita especificando valores alfa, vermelho, verde e azul.  
  
 [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]  
  
 Para outras maneiras de especificar a cor, consulte o <xref:System.Windows.Media.Color> tópico de referência.  
  
<a name="gradient"></a>   
## <a name="painting-an-area-with-a-gradient"></a>Pintando uma área com um gradiente  
 Um pincel de gradiente pinta uma área com várias cores que se mesclam ao longo de um eixo. Você pode usá-los para criar impressões de luz e sombra, dando uma aparência tridimensional aos seus controles. Você também pode usá-los para simular vidro, cromado, água e outras superfícies suaves.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece dois tipos de pincéis de gradiente: <xref:System.Windows.Media.LinearGradientBrush> e <xref:System.Windows.Media.RadialGradientBrush>.  
  
<a name="lineargradientbrush"></a>   
## <a name="linear-gradients"></a>Gradientes lineares  
 Um <xref:System.Windows.Media.LinearGradientBrush> pinta uma área com um gradiente definido ao longo de uma linha, o *eixo do gradiente*.  Especificar as cores de gradiente e suas localizações ao longo do eixo do gradiente usando <xref:System.Windows.Media.GradientStop> objetos.  Você também pode modificar o eixo do gradiente, o que permite criar gradientes horizontais e verticais e inverter a direção do gradiente. O eixo de gradiente é descrito na próxima seção. Por padrão, é criado um gradiente diagonal.  
  
 O exemplo a seguir mostra o código que cria um gradiente linear com quatro cores.  
  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Esse código produz o gradiente a seguir:  
  
 ![Um gradiente linear diagonal](./media/wcpsdk-graphicsmm-diaglgradient-nolabel.jpg "wcpsdk_graphicsmm_diaglgradient_nolabel")  
  
 **Observação:** Os exemplos de gradiente neste tópico usam o sistema de coordenadas padrão para definir pontos de início e pontos de extremidade. O sistema de coordenadas padrão é relativo a uma caixa delimitadora: 0 indica 0 por cento da caixa delimitadora e 1 indica 100 por cento da caixa delimitadora. Você pode alterar esse sistema de coordenadas definindo a <xref:System.Windows.Media.GradientBrush.MappingMode%2A> propriedade para o valor <xref:System.Windows.Media.BrushMappingMode.Absolute>. Um sistema de coordenadas absoluto não é relativo a uma caixa delimitadora. Os valores são interpretados diretamente no espaço local.  
  
 O <xref:System.Windows.Media.GradientStop> é o bloco de construção básico de um pincel de gradiente.  Uma parada de gradiente Especifica um <xref:System.Windows.Media.GradientStop.Color%2A> em um <xref:System.Windows.Media.GradientStop.Offset%2A> ao longo do eixo de gradiente.  
  
- A parada de gradiente <xref:System.Windows.Media.GradientStop.Color%2A> propriedade especifica a cor da marca de gradiente. Você pode definir a cor usando uma cor predefinida (fornecida pelo <xref:System.Windows.Media.Colors> classe) ou especificando valores de ScRGB ou ARGB. Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode usar a notação hexadecimal para descrever uma cor. Para obter mais informações, consulte o <xref:System.Windows.Media.Color> estrutura.  
  
- A parada de gradiente <xref:System.Windows.Media.GradientStop.Offset%2A> propriedade especifica a posição da cor da parada de gradiente no eixo do gradiente. O deslocamento é um <xref:System.Double> que varia de 0 a 1. Quanto mais próximo de 0 for o valor de deslocamento da marca de gradiente, mais próxima a cor estará do início do gradiente. Quanto mais próximo de 1 for o valor de deslocamento da marca do gradiente, mais próxima a cor estará do final do gradiente.  
  
 A cor de cada ponto entre as marcas de gradiente é interpolada linearmente como uma combinação da cor especificada pelas duas marcas de gradiente delimitadoras. A ilustração a seguir realça as marcas de gradiente do exemplo anterior. Os círculos marcam a posição das marcas de gradiente e uma linha tracejada mostra o eixo do gradiente.  
  
 ![Marcas de gradiente em um gradiente linear](./media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk_graphicsmm_4gradientstops")  
  
 A primeira marca de gradiente especifica a cor amarela em um deslocamento de `0.0`.  A segunda marca de gradiente especifica a cor vermelha em um deslocamento de `0.25`.  Os pontos entre essas duas marcas mudam gradualmente de amarelo para vermelho conforme você move da esquerda para a direita ao longo do eixo do gradiente.  A terceira marca de gradiente especifica a cor azul em um deslocamento de `0.75`.  Os pontos entre a segunda e a terceira marca de gradiente mudam gradualmente de vermelho para azul. A quarta marca de gradiente especifica a cor verde-limão em um deslocamento de `1.0`. Os pontos entre a terceira e a quarta marca de gradiente mudam gradualmente de azul para verde-limão.  
  
<a name="gradientaxis"></a>   
### <a name="the-gradient-axis"></a>O eixo do gradiente  
 Conforme mencionado anteriormente, as marcas de gradiente de um pincel de gradiente linear são posicionadas ao longo de uma linha, o eixo do gradiente. Você pode alterar a orientação e o tamanho da linha usando o pincel <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> e <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> propriedades. Manipulando o pincel <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> e <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, você pode criar horizontal e gradientes verticais, inverter a direção do gradiente, condensar o espalhamento do gradiente e muito mais.  
  
 Por padrão, o pincel de gradiente linear <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> e <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> são relativas à área que está sendo pintada. O ponto (0,0) representa o canto superior esquerdo da área que está sendo pintada e (1,1) representa o canto inferior direito da área que está sendo pintada. O padrão <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> de um <xref:System.Windows.Media.LinearGradientBrush> é (0,0) e seu padrão <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> é (1,1), que cria um gradiente diagonal começando no canto superior esquerdo e estendendo-se para o canto inferior direito da área que está sendo pintada. A ilustração a seguir mostra o eixo do gradiente de um pincel de gradiente linear com o padrão <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> e <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>.  
  
 ![Eixo do gradiente de um gradiente linear diagonal](./media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk_graphicsmm_diagonalgradientaxis")  
  
 O exemplo a seguir mostra como criar um horizontal gradiente, especificando o pincel <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> e <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>. Observe que as paradas de gradiente são as mesmas nos exemplos anteriores; simplesmente alterando a <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> e <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, o gradiente foi alterado de diagonal para horizontal.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 A ilustração a seguir mostra o gradiente que é criado. O eixo do gradiente é marcado com uma linha tracejada e as marcas de gradiente são marcadas com círculos.  
  
 ![Eixo do gradiente de um gradiente linear horizontal](./media/wcpsdk-graphicsmm-horizontalgradient.jpg "wcpsdk_graphicsmm_horizontalgradient")  
  
 O exemplo a seguir mostra como criar um gradiente vertical.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 A ilustração a seguir mostra o gradiente que é criado. O eixo do gradiente é marcado com uma linha tracejada e as marcas de gradiente são marcadas com círculos.  
  
 ![Eixo do gradiente para um gradiente vertical](./media/wcpsdk-graphicsmm-verticalgradient.jpg "wcpsdk_graphicsmm_verticalgradient")  
  
<a name="radialgradients"></a>   
## <a name="radial-gradients"></a>Gradientes radiais  
 Como uma <xref:System.Windows.Media.LinearGradientBrush>, um <xref:System.Windows.Media.RadialGradientBrush> pinta uma área com cores que se mesclam ao longo do eixo. Os exemplos anteriores mostraram como o eixo de um pincel de gradiente linear é uma linha reta. O eixo de um pincel de gradiente radial é definido por um círculo e suas cores "irradiam" para fora de sua origem.  
  
 No exemplo a seguir, um pincel de gradiente radial é usado para pintar o interior de um retângulo.  
  
 [!code-xaml[GradientBrushExamples_snip#RadialGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]  
  
 A ilustração a seguir mostra o gradiente criado no exemplo anterior. As marcas de gradiente do pincel foram realçadas. Observe que, embora os resultados sejam diferentes, as marcas de gradiente neste exemplo são idênticas às marcas de gradiente nos exemplos anteriores de pincel de gradiente linear.  
  
 ![Marcas de gradiente em um gradiente radial](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
 O <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> Especifica o ponto inicial de eixo do gradiente do pincel de gradiente radial. O eixo do gradiente irradia da origem do gradiente para o círculo do gradiente. Círculo de gradiente do pincel é definido por seu <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, e <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> propriedades.  
  
 A ilustração a seguir mostra vários gradientes radiais com diferentes <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>, <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, e <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> configurações.  
  
 ![Configurações de RadialGradientBrush](./media/wcpsdk-graphicsmm-originscirclesandradii.gif "wcpsdk_graphicsmm_originscirclesandradii")  
RadialGradientBrushes com diferentes configurações de GradientOrigin, Center, RadiusX e RadiusY.  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-transparent-or-partially-transparent-gradient-stops"></a>Especificando marcas de gradiente transparentes ou parcialmente transparentes  
 Como paradas de gradiente não fornecem uma propriedade de opacidade, você deve especificar o canal alfa das cores usando [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] notação hexadecimal na marcação ou usar o <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> método para criar marcas de gradiente que sejam transparentes ou parcialmente transparentes. As seções a seguir explicam como criar marcas de gradiente parcialmente transparentes em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e no código.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>Especificando a opacidade das cores em "XAML"  
 Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você usa a notação hexadecimal [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] para especificar a opacidade das cores individuais. A notação hexadecimal [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] usa a seguinte sintaxe:  
  
 `#` **aa** *rrggbb*  
  
 O *aa* na linha anterior representa um valor hexadecimal de dois dígitos usado para especificar a opacidade da cor. O *rr*, o *gg* e o *bb* representam um valor hexadecimal de dois dígitos usado para especificar a quantidade de vermelho, verde e azul na cor. Cada dígito hexadecimal pode ter um valor de 0 a 9 ou de A a F. 0 é o menor valor. F é o maior valor. Um valor alfa de 00 especifica uma cor que é completamente transparente, enquanto um valor alfa de FF cria uma cor que é totalmente opaca.  No exemplo a seguir, a notação [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] hexadecimal é usada para especificar duas cores. A primeira é parcialmente transparente (tem um valor alfa de x20), enquanto a segundo é completamente opaca.  
  
 [!code-xaml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]  
  
<a name="fromscrgbsyntax"></a>   
### <a name="specifying-color-opacity-in-code"></a>Especificando a opacidade das cores no código  
 Ao usar o código, estático <xref:System.Windows.Media.Color.FromArgb%2A> método permite que você especifique um valor alfa ao criar uma cor. O método utiliza quatro parâmetros do tipo <xref:System.Byte>. O primeiro parâmetro especifica o canal alfa da cor e os outros três parâmetros especificam os valores de vermelho, verde e azul da cor. Cada valor deve estar entre 0 e 255, inclusivo. Um valor alfa de 0 especifica que a cor é completamente transparente, enquanto um valor alfa de 255 especifica que a cor é completamente opaca. No exemplo a seguir, o <xref:System.Windows.Media.Color.FromArgb%2A> método é usado para produzir duas cores. A primeira cor é parcialmente transparente (tem um valor alfa de 32), enquanto a segunda é completamente opaca.  
  
 [!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]  
  
 Como alternativa, você pode usar o <xref:System.Windows.Media.Color.FromScRgb%2A> método, que permite que você use valores ScRGB para criar uma cor.  
  
<a name="otherbrushes"></a>   
## <a name="painting-with-images-drawings-visuals-and-patterns"></a>Pintando com imagens, desenhos, elementos visuais e padrões  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, e <xref:System.Windows.Media.VisualBrush> classes permitem pintar uma área com imagens, desenhos ou visuais. Para obter informações sobre como pintar com imagens, desenhos e padrões, consulte [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Visão geral da transformação de pincel](brush-transformation-overview.md)
- [Camadas de renderização de gráficos](../advanced/graphics-rendering-tiers.md)
