---
title: Visão geral de transformações 3D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D transformations
- transformations [WPF], 3-D
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
ms.openlocfilehash: 427840430a37f675ccc0f0ee4f423370f2a55550
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646364"
---
# <a name="3-d-transformations-overview"></a>Visão geral de transformações 3D
Este tópico descreve como aplicar transformações a modelos 3D no sistema de elementos gráficos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. As transformações permitem ao desenvolvedor reposicionar, redimensionar e reorientar modelos sem alterar os valores base que os definem.  
  

  
## <a name="3-d-coordinate-space"></a>Espaço de coordenadas 3D  
 Conteúdo em elementos gráficos 3D [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é encapsulado em um elemento, <xref:System.Windows.Controls.Viewport3D>, que pode participar da estrutura bidimensional do elemento. O sistema de elementos gráficos trata o Viewport3D como um elemento visual bidimensional da mesma forma que muitos outros no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. O Viewport3D funciona como uma janela (um visor) em uma cena tridimensional. Mais precisamente, ele é uma superfície na qual uma cena 3D é projetada.  Embora você possa usar Viewport3D com outros objetos de desenho 2D no mesmo grafo da cena, não é possível mesclar objetos 2D e 3D em um Viewport3D. Na discussão a seguir, o espaço de coordenadas descrito está contido pelo elemento Viewport3D.  
  
 O sistema de coordenadas do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] para gráficos 2D localiza a origem na parte superior esquerda da superfície de renderização (geralmente a tela). No sistema 2D, os valores positivos do eixo x aumentam para a direita e valores positivos do eixo y aumentam para baixo. No sistema de coordenadas 3D, no entanto, a origem está localizada no centro da tela, com os valores positivos do eixo x aumentando para a direita, mas os valores positivos do eixo y aumentando para cima e os valores positivos do eixo z aumentando para fora da origem, em direção ao observador.  
  
 ![Sistemas de coordenadas](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem-1")  
Comparação do sistema de coordenadas  
  
 O espaço definido por esses eixos é o quadro estacionário de referência para objetos 3D no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Ao criar modelos nesse espaço e criar luzes e câmeras para exibi-los, é útil distinguir este quadro estacionário de referência ou "espaço de mundo", do quadro de referência local que você cria para cada modelo, quando você aplica transformações a ele. Lembre-se também de que objetos no espaço de mundo podem parecer totalmente diferentes ou até mesmo não serem visíveis, dependendo das configurações de câmera e de luz, mas a posição da câmera não altera o local dos objetos no espaço de mundo.  
  
## <a name="transforming-models"></a>Transformando modelos  
 Quando você cria modelos, eles têm uma localização específica na cena. Para mover esses modelos na cena, girá-los ou alterar seus tamanhos, não é prático alterar os vértices que definem os próprios modelos. Em vez disso, assim como em 2D, você aplica transformações a modelos.  
  
 Cada objeto de modelo tem um <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> propriedade com o qual você pode mover, reorientar ou redimensionar o modelo. Ao aplicar uma transformação, você efetivamente desloca todos os pontos do modelo por meio de qualquer vetor ou valor que é especificado pela transformação. Em outras palavras, você transformou o espaço de coordenadas no qual o modelo está definido ("espaço do modelo"), mas você não alterou os valores que compõem a geometria do modelo no sistema de coordenadas de toda a cena ("espaço de mundo").  
  
## <a name="translation-transformations"></a>Transformações de translação  
 As transformações 3D herdam da classe base abstrata <xref:System.Windows.Media.Media3D.Transform3D>; isso inclui as classes de transformação afim <xref:System.Windows.Media.Media3D.TranslateTransform3D>, <xref:System.Windows.Media.Media3D.ScaleTransform3D>, e <xref:System.Windows.Media.Media3D.RotateTransform3D>. O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sistema 3D também fornece um <xref:System.Windows.Media.Media3D.MatrixTransform3D> classe que lhe permite especificar as mesmas transformações em operações de matrizes mais concisas.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D> Move todos os pontos do Model3D na direção do vetor de deslocamento especificado com o <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>, <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>, e <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A> propriedades. Por exemplo, dado um vértice de um cubo em (2,2,2), um vetor de deslocamento de (0,1.6,1) moveria esse vértice (2,2,2) para (2,3.6,3). O vértice o cubo do ainda é (2,2,2) no espaço do modelo, mas agora esse espaço do modelo mudou sua relação com espaço de mundo para que (2,2,2) no espaço de modelo seja (2,3.6,3) no espaço de mundo.  
  
 ![Valor de translação](../../../../docs/framework/wpf/graphics-multimedia/media/transforms-translate.png "traduzir de transformações")  
Translação com deslocamento  
  
 Os exemplos de código a seguir mostram como aplicar uma translação.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Dimensionar transformações  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D> Altera a escala do modelo por um vetor de escala especificado com referência a um ponto central. Especifique uma escala uniforme, que ajusta a escala do modelo com o mesmo valor nos eixos X, Y e Z, para alterar o tamanho do modelo proporcionalmente. Por exemplo, a configuração da transformação <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>, e <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> propriedades como 0,5 reduz pela metade o tamanho do modelo; definindo as mesmas propriedades como 2, dobra sua escala em todos os três eixos.  
  
 ![Uniforme ScaleTransform3D](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
Exemplo de ScaleVector  
  
 Ao especificar uma transformação de escala não uniforme (uma transformação de escala cujos valores X, Y e Z não são todos iguais), você pode fazer com um modelo se alongue ou contraia em uma ou duas dimensões sem afetar as outras. Por exemplo, definindo <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> como 1, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> como 2, e <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> como 1, faria com que o modelo transformado dobrasse de altura, mas permanecesse inalterado ao longo dos eixos X e Z.  
  
 Por padrão, o ScaleTransform3D faz com que os vértices se expandam ou contraiam em relação à origem (0,0,0). No entanto, se o modelo que você deseja transformar não é desenhado em relação à origem, a colocação do modelo em escala com base na origem não ajustará a escala do modelo "in-loco". Em vez disso, quando os vértices do modelo forem multiplicados pelo vetor de escala, a operação de ajuste de escala terá o efeito de transladar o modelo, bem como de colocá-lo em escala.  
  
 ![Três cubos dimensionados com o ponto central especificado](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Exemplo de centro de escala  
  
 Para dimensionar um modelo "in-loco", especifique o centro do modelo, definindo o ScaleTransform3D <xref:System.Windows.Media.ScaleTransform.CenterX%2A>, <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, e <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> propriedades. Isso garante que o sistema de elementos gráficos dimensiona o espaço do modelo e, em seguida, translada-o para centralizar no especificado <xref:System.Windows.Media.Media3D.Point3D>. Por outro lado, se você tiver criado o modelo sobre a origem e especificar um ponto central diferente, observe que o modelo será movido para longe da origem.  
  
## <a name="rotation-transformations"></a>Transformações de rotação  
 Você pode girar um modelo em 3D de várias maneiras diferentes. Uma típica transformação de rotação especifica um eixo e um ângulo de rotação em torno desse eixo. O <xref:System.Windows.Media.Media3D.RotateTransform3D> classe permite que você defina uma <xref:System.Windows.Media.Media3D.Rotation3D> com seu <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> propriedade. Você, em seguida, especifique <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> e <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> as propriedades no Rotation3D, neste caso, um <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>, para definir a transformação. Os exemplos a seguir giram um modelo por 60 graus em torno do eixo Y.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Observação:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-d é um sistema destro, o que significa que um valor positivo de ângulo para uma rotação resulta em uma rotação no sentido anti-horário sobre o eixo.  
  
 Rotações eixo-ângulo assumirão a rotação sobre a origem se um valor não for especificado para o <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>, <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>, e <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> propriedades no RotateTransform3D. Assim como na colocação em escala, é útil lembrar que a rotação transforma todo espaço de coordenadas do modelo. Se o modelo não tiver sido criado sobre a origem ou tiver sido movido anteriormente, a rotação poderá "girar" em relação à origem em vez de rotacionar no lugar.  
  
 ![Rotação com o novo ponto central](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Rotação com o novo centro especificado  
  
 Para girar o modelo "in-loco", especifique o centro real do modelo como o centro de rotação. Como a geometria normalmente é modelada em relação à origem, você geralmente poderá obter o resultado esperado de um conjunto de transformações primeiro dimensionando o modelo (colocando-o em escala), em seguida, configurando sua orientação (girando-o) e, finalmente, movendo-o para o local desejado (transladando-o).  
  
 ![Rotação de 60 graus em x&#45; e y&#45;eixos](../../../../docs/framework/wpf/graphics-multimedia/media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Exemplo de rotação  
  
 As rotações eixo-ângulo funcionam bem para transformações estáticas e para algumas animações. No entanto, considere girar um modelo de cubo em 60 graus ao redor do eixo X e, em seguida, 45 graus em torno do eixo Z. Você pode descrever essa transformação como duas transformações afins discretas ou como uma matriz. No entanto, pode ser difícil animar suavemente uma rotação definida dessa maneira. Embora as posições inicial e final do modelo, calculadas por qualquer uma das abordagens, sejam as mesmas, as posições intermediárias assumidas pelo modelo são computacionalmente incertas. Os quatérnions representam uma maneira alternativa para calcular a interpolação entre o início e fim de uma rotação.  
  
 Um quatérnion representa um eixo no espaço 3D em uma rotação em torno desse eixo. Por exemplo, um quatérnion pode representar um eixo (1,1,2) e uma rotação de 50 graus. O poder dos quatérnions ao definir rotações é proveniente das duas operações que você pode realizar neles: composição e interpolação. A composição de dois quatérnions aplicados a uma geometria significa "girar a geometria ao redor do eixo 2 por rotação 2 e, em seguida, girá-la ao redor do eixo 1 por rotação 1". Ao usar a composição, você pode combinar as duas rotações na geometria para obter um único quatérnion que representa o resultado. Como a interpolação de quatérnions pode calcular um caminho suave e razoável de um eixo e de uma orientação à outra, é possível interpolar do quatérnion original para o composto para alcançar uma transição suave de um para outro, permitindo que você anime a transformação. Para modelos que você deseja animar, você pode especificar um destino <xref:System.Windows.Media.Media3D.Quaternion> para a rotação, usando um <xref:System.Windows.Media.Media3D.QuaternionRotation3D> para o <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> propriedade.  
  
## <a name="using-transformation-collections"></a>Usando coleções de transformações  
 Ao criar uma cena, é comum aplicar mais de uma transformação a um modelo. Adicione transformações para o <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> coleção do <xref:System.Windows.Media.Media3D.Transform3DGroup> classe agrupar transformações convenientemente para aplicar a diversos modelos na cena. Muitas vezes, é conveniente reutilizar uma transformação em vários grupos diferentes, da mesma maneira que você pode reutilizar um modelo, aplicando um conjunto diferente de transformações para cada instância. Observe que a ordem na qual as transformações são adicionadas à coleção é significativa: as transformações na coleção são aplicadas da primeira à última.  
  
## <a name="animating-transformations"></a>Animando transformações  
 A implementação 3D do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] participa do mesmo sistema de animação e tempo que os gráficos 2D. Em outras palavras, para animar uma cena 3D, anime as propriedades de seus modelos. É possível animar propriedades de primitivas diretamente, mas é geralmente mais fácil animar transformações que alteram a posição ou a aparência de modelos. Como as transformações podem ser aplicadas para <xref:System.Windows.Media.Media3D.Model3DGroup> objetos, bem como modelos individuais, é possível aplicar um conjunto de animações para os filhos de um Model3Dgroup e outro conjunto de animações a um grupo de objetos.  Para obter informações básicas sobre o sistema de animação e timing do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consulte [Visão geral de animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) e [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Para animar um objeto no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], crie uma linha do tempo, defina uma animação (que é, na verdade, uma alteração em alguns valores da propriedade ao longo do tempo) e especifique a propriedade à qual aplicar a animação. Essa propriedade deve ser uma propriedade de um FrameworkElement. Como todos os objetos em uma cena 3D são filhos do Viewport3D, as propriedades direcionadas por qualquer animação que você deseja aplicar à cena são propriedades das propriedades do Viewport3D. É importante preparar o caminho da propriedade para a animação cuidadosamente, porque a sintaxe pode ser detalhada.  
  
 Suponha que você deseja girar um objeto no local, mas também deseja aplicar um movimento de balanço para expor mais do objeto para a exibição. Você pode optar por aplicar uma RotateTransform3D ao modelo e animar o eixo de sua rotação de um vetor para outro. O exemplo de código a seguir demonstra a aplicação de uma <xref:System.Windows.Media.Animation.Vector3DAnimation> à propriedade do eixo da Rotation3D da transformação, supondo que a RotateTransform3D seja uma das várias transformações aplicadas ao modelo com um <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Use uma sintaxe semelhante para direcionar outras propriedades de transformação para mover ou ajustar a escala o objeto.  Por exemplo, você pode aplicar um <xref:System.Windows.Media.Animation.Point3DAnimation> à propriedade ScaleCenter em uma transformação de escala para fazer com que um modelo distorça suavemente sua forma.  
  
 Embora os exemplos anteriores transformem as propriedades de <xref:System.Windows.Media.Media3D.GeometryModel3D>, também é possível transformar as propriedades de outros modelos na cena.  Ao animar translações aplicadas a objetos de luz, por exemplo, você pode criar luz em movimento e efeitos de sombra que podem alterar drasticamente a aparência de seus modelos.  
  
 Como as câmeras são modelos, também é possível transformar propriedades de câmeras.  Enquanto você certamente pode alterar a aparência da cena transformando as distâncias de plano ou o local da câmera (com efeito, transformando toda a projeção da cena), observe que muitos dos efeitos conseguidos dessa maneira podem não fazer tanto "sentido visual" para o visualizador como as transformações aplicadas ao local ou à posição dos modelos na cena.  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de elementos gráficos 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [Visão geral de transformações](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [Exemplo de transformações 2D](https://go.microsoft.com/fwlink/?LinkID=158252)
