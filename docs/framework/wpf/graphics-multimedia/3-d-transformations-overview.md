---
title: Visão geral das transformações 3D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D transformations
- transformations [WPF], 3D
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
ms.openlocfilehash: 0efd6d247f23760c878c82cc92e99f1b83c1b9d2
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112343"
---
# <a name="3d-transformations-overview"></a>Visão geral das transformações 3D
Este tópico descreve como aplicar transformações em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] modelos 3D no sistema gráfico. As transformações permitem ao desenvolvedor reposicionar, redimensionar e reorientar modelos sem alterar os valores base que os definem.  

## <a name="3d-coordinate-space"></a>Espaço de Coordenadas 3D  
 O conteúdo gráfico [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D é encapsulado em um elemento, <xref:System.Windows.Controls.Viewport3D>que pode participar da estrutura de elementos bidimensionais. O sistema de elementos gráficos trata o Viewport3D como um elemento visual bidimensional da mesma forma que muitos outros no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. O Viewport3D funciona como uma janela (um visor) em uma cena tridimensional. Mais precisamente, é uma superfície na qual uma cena 3D é projetada.  Embora você possa usar viewport3D com outros objetos de desenho 2D no mesmo gráfico de cena, você não pode interpenetrar objetos 2D e 3D dentro de uma Viewport3D. Na discussão a seguir, o espaço de coordenadas descrito está contido pelo elemento Viewport3D.  
  
 O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sistema de coordenadas para gráficos 2D localiza a origem no canto superior esquerdo da superfície de renderização (tipicamente a tela). No sistema 2D, os valores positivos do eixo x prosseguem para os valores do eixo y certo e positivos procedem para baixo. No sistema de coordenadas 3D, no entanto, a origem está localizada no centro da tela, com valores positivos do eixo x seguindo para a direita, mas positivos valores do eixo y procedendo para cima, e valores positivos do eixo z procedendo para fora da origem, em direção o espectador.  
  
 ![Sistemas de coordenadas](./media/coordsystem-1.png "CoordSystem-1")  
Comparação do sistema de coordenadas  
  
 O espaço definido por esses eixos é o quadro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]estacionário de referência para objetos 3D em . Ao compilar modelos nesse espaço e criar luzes e câmeras para exibi-los, é útil distinguir esse quadro estacionário de referência, ou “espaço de mundo”, do quadro local da referência que você cria para cada modelo quando aplica transformações a ele. Lembre-se também de que objetos no espaço de mundo podem parecer totalmente diferentes ou até mesmo não serem visíveis, dependendo das configurações de câmera e de luz, mas a posição da câmera não altera o local dos objetos no espaço de mundo.  
  
## <a name="transforming-models"></a>Transformando modelos  
 Quando você cria modelos, eles têm uma localização específica na cena. Para mover esses modelos na cena, girá-los ou alterar seus tamanhos, não é prático alterar os vértices que definem os próprios modelos. Em vez disso, assim como em 2D, você aplica transformações em modelos.  
  
 Cada objeto modelo <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> tem uma propriedade com a qual você pode mover, reorientar ou redimensionar o modelo. Ao aplicar uma transformação, você efetivamente desloca todos os pontos do modelo por meio de qualquer vetor ou valor que é especificado pela transformação. Em outras palavras, você transformou o espaço de coordenadas no qual o modelo está definido (“espaço do modelo”), mas não alterou os valores que compõem a geometria do modelo no sistema de coordenadas de toda a cena (“espaço de mundo”).  
  
## <a name="translation-transformations"></a>Transformações de translação  
 Transformações 3D herdam <xref:System.Windows.Media.Media3D.Transform3D>da classe base abstrata; estes incluem as classes <xref:System.Windows.Media.Media3D.TranslateTransform3D> <xref:System.Windows.Media.Media3D.ScaleTransform3D>de <xref:System.Windows.Media.Media3D.RotateTransform3D>transformação afim, e . O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sistema 3D <xref:System.Windows.Media.Media3D.MatrixTransform3D> também fornece uma classe que permite especificar as mesmas transformações em operações de matriz mais concisas.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D>move todos os pontos do Model3D na direção do <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>vetor <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A> de deslocamento especificado com as propriedades e propriedades. Por exemplo, dado um vértice de um cubo em (2,2,2), um vetor de deslocamento de (0,1.6,1) moveria esse vértice (2,2,2) para (2,3.6,3). O vértice o cubo do ainda é (2,2,2) no espaço do modelo, mas agora esse espaço do modelo mudou sua relação com espaço de mundo para que (2,2,2) no espaço de modelo seja (2,3.6,3) no espaço de mundo.  
  
 ![Valor de translação](./media/transforms-translate.png "Transformações-Traduzir")  
Translação com deslocamento  
  
 Os exemplos de código a seguir mostram como aplicar uma translação.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Dimensionar transformações  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D>altera a escala do modelo por um vetor de escala especificado com referência a um ponto central. Especifique uma escala uniforme, que ajusta a escala do modelo com o mesmo valor nos eixos X, Y e Z, para alterar o tamanho do modelo proporcionalmente. Por exemplo, definir as <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>propriedades <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> da transformação para 0,5 metadedo do tamanho do modelo; definir as mesmas propriedades para 2 dobra sua escala em todos os três eixos.  
  
 ![ScaleTransform3D uniforme](./media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
Exemplo de ScaleVector  
  
 Ao especificar uma transformação de escala não uniforme (uma transformação de escala cujos valores X, Y e Z não são todos iguais), você pode fazer com um modelo se alongue ou contraia em uma ou duas dimensões sem afetar as outras. Por exemplo, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> configuração para <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> 1, para 2 e para 1 faria com que o modelo transformado dobrasse de altura, mas permaneceria inalterado ao longo dos eixos X e Z.  
  
 Por padrão, o ScaleTransform3D faz com que os vértices se expandam ou contraiam em relação à origem (0,0,0). No entanto, se o modelo que você deseja transformar não é desenhado em relação à origem, a colocação do modelo em escala com base na origem não ajustará a escala do modelo "in-loco". Em vez disso, quando os vértices do modelo forem multiplicados pelo vetor de escala, a operação de ajuste de escala terá o efeito de transladar o modelo, bem como de colocá-lo em escala.  
  
 ![Três cubos com a escala ajustada com o ponto central especificado](./media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Exemplo de centro de escala  
  
 Para dimensionar um modelo "no lugar", especifique o centro <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>do <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> modelo definindo as propriedades e propriedades do ScaleTransform3D. Isso garante que o sistema gráfico dimensione o espaço do modelo <xref:System.Windows.Media.Media3D.Point3D>e, em seguida, traduza-o para centralizar no especificado . Por outro lado, se você tiver criado o modelo sobre a origem e especificar um ponto central diferente, observe que o modelo será movido para longe da origem.  
  
## <a name="rotation-transformations"></a>Transformações de rotação  
 Você pode girar um modelo em 3D de várias maneiras diferentes. Uma típica transformação de rotação especifica um eixo e um ângulo de rotação em torno desse eixo. A <xref:System.Windows.Media.Media3D.RotateTransform3D> classe permite que <xref:System.Windows.Media.Media3D.Rotation3D> você <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> defina um com sua propriedade. Em seguida, você especifica <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> e <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> propriedades no <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>Rotation3D, neste caso um , para definir a transformação. Os exemplos a seguir giram um modelo por 60 graus em torno do eixo Y.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Nota:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D é um sistema destro, o que significa que um valor de ângulo positivo para uma rotação resulta em uma rotação no sentido anti-horário sobre o eixo.  
  
 As rotações de ângulo de eixo assumem a rotação <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A> <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>sobre <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> a origem se um valor não for especificado para , e propriedades em RotateTransform3D. Assim como na colocação em escala, é útil lembrar que a rotação transforma todo espaço de coordenadas do modelo. Se o modelo não tiver sido criado sobre a origem ou tiver sido movido anteriormente, a rotação poderá "girar" em relação à origem em vez de rotacionar no lugar.  
  
 ![Rotação com o novo ponto central](./media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Rotação com o novo centro especificado  
  
 Para girar o modelo "in-loco", especifique o centro real do modelo como o centro de rotação. Como a geometria normalmente é modelada em relação à origem, você geralmente poderá obter o resultado esperado de um conjunto de transformações primeiro dimensionando o modelo (colocando-o em escala), em seguida, configurando sua orientação (girando-o) e, finalmente, movendo-o para o local desejado (transladando-o).  
  
 ![Rotação de 60 graus nos eixos x&#45; e y&#45;](./media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Exemplo de rotação  
  
 As rotações eixo-ângulo funcionam bem para transformações estáticas e para algumas animações. No entanto, considere girar um modelo de cubo em 60 graus ao redor do eixo X e, em seguida, 45 graus em torno do eixo Z. Você pode descrever essa transformação como duas transformações afins discretas ou como uma matriz. No entanto, pode ser difícil animar suavemente uma rotação definida dessa maneira. Embora as posições inicial e final do modelo, calculadas por qualquer uma das abordagens, sejam as mesmas, as posições intermediárias assumidas pelo modelo são computacionalmente incertas. Os quatérnions representam uma maneira alternativa para calcular a interpolação entre o início e fim de uma rotação.  
  
 Um quatérnio representa um eixo no espaço 3D e uma rotação em torno do eixo em questão. Por exemplo, um quatérnion pode representar um eixo (1,1,2) e uma rotação de 50 graus. O poder dos quatérnions ao definir rotações é proveniente das duas operações que você pode realizar neles: composição e interpolação. A composição de dois quatérnions aplicados a uma geometria significa "girar a geometria ao redor do eixo 2 por rotação 2 e, em seguida, girá-la ao redor do eixo 1 por rotação 1". Ao usar a composição, você pode combinar as duas rotações na geometria para obter um único quatérnion que representa o resultado. Como a interpolação de quatérnions pode calcular um caminho suave e razoável de um eixo e de uma orientação à outra, é possível interpolar do quatérnion original para o composto para alcançar uma transição suave de um para outro, permitindo que você anime a transformação. Para modelos que você deseja animar, <xref:System.Windows.Media.Media3D.Quaternion> você pode especificar <xref:System.Windows.Media.Media3D.QuaternionRotation3D> um <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> destino para a rotação usando um para a propriedade.  
  
## <a name="using-transformation-collections"></a>Usando coleções de transformações  
 Ao criar uma cena, é comum aplicar mais de uma transformação a um modelo. Adicionar transformações <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> à coleção <xref:System.Windows.Media.Media3D.Transform3DGroup> da classe para transformarções em grupo convenientemente para aplicar a vários modelos na cena. Muitas vezes, é conveniente reutilizar uma transformação em vários grupos diferentes, da mesma maneira que você pode reutilizar um modelo, aplicando um conjunto diferente de transformações para cada instância. Observe que a ordem na qual as transformações são adicionadas à coleção é significativa: as transformações na coleção são aplicadas da primeira à última.  
  
## <a name="animating-transformations"></a>Animando transformações  
 A [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] implementação 3D participa do mesmo sistema de tempo e animação que os gráficos 2D. Ou seja, animar uma cena 3D, animar as propriedades de seus modelos. É possível animar propriedades de primitivas diretamente, mas é geralmente mais fácil animar transformações que alteram a posição ou a aparência de modelos. Como as transformações podem <xref:System.Windows.Media.Media3D.Model3DGroup> ser aplicadas a objetos, bem como modelos individuais, é possível aplicar um conjunto de animações aos filhos de um grupo Model3D e outro conjunto de animações a um grupo de objetos.  Para obter informações básicas sobre o sistema de animação e timing do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consulte [Visão geral de animação](animation-overview.md) e [Visão geral de storyboards](storyboards-overview.md).  
  
 Para animar um objeto no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], crie uma linha do tempo, defina uma animação (que é, na verdade, uma alteração em alguns valores da propriedade ao longo do tempo) e especifique a propriedade à qual aplicar a animação. Essa propriedade deve ser uma propriedade de um FrameworkElement. Como todos os objetos em uma cena 3D são filhos de Viewport3D, as propriedades direcionadas por qualquer animação que você deseja aplicar à cena são propriedades de Viewport3D. É importante preparar o caminho da propriedade para a animação cuidadosamente, porque a sintaxe pode ser detalhada.  
  
 Suponha que você deseja girar um objeto no local, mas também deseja aplicar um movimento de balanço para expor mais do objeto para a exibição. Você pode optar por aplicar uma RotateTransform3D ao modelo e animar o eixo de sua rotação de um vetor para outro. O exemplo de código <xref:System.Windows.Media.Animation.Vector3DAnimation> a seguir demonstra a aplicação a a a na propriedade Axis da Rotation3D da transformação, <xref:System.Windows.Media.TransformGroup>assumindo que o RotateTransform3D seja uma das várias transformações aplicadas ao modelo com um .  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Use uma sintaxe semelhante para direcionar outras propriedades de transformação para mover ou ajustar a escala o objeto.  Por exemplo, você <xref:System.Windows.Media.Animation.Point3DAnimation> pode aplicar a na propriedade ScaleCenter em uma transformação de escala para fazer com que um modelo distorça suavemente sua forma.  
  
 Embora os exemplos anteriores <xref:System.Windows.Media.Media3D.GeometryModel3D>transformem as propriedades de, também é possível transformar as propriedades de outros modelos na cena.  Ao animar translações aplicadas a objetos de luz, por exemplo, você pode criar luz em movimento e efeitos de sombra que podem alterar drasticamente a aparência de seus modelos.  
  
 Como as câmeras são modelos, também é possível transformar propriedades de câmeras.  Enquanto você certamente pode alterar a aparência da cena transformando as distâncias de plano ou o local da câmera (com efeito, transformando toda a projeção da cena), observe que muitos dos efeitos conseguidos dessa maneira podem não fazer tanto "sentido visual" para o visualizador como as transformações aplicadas ao local ou à posição dos modelos na cena.  
  
## <a name="see-also"></a>Confira também

- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
- [Visão geral de transformações](transforms-overview.md)
- [2D transforma amostra](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
