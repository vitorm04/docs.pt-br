---
title: Visão geral de elementos gráficos 3D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D graphics [WPF]
- graphics [WPF], 3-D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: 7f9f3d21d14a8eac862186a41bd8771cffb7375c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352861"
---
# <a name="3-d-graphics-overview"></a>Visão geral de elementos gráficos 3D
<a name="introduction"></a> A funcionalidade [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permite aos desenvolvedores desenhar, transformar e animar elementos gráficos 3D na marcação e no código de procedimento. Os desenvolvedores podem combinar elementos gráficos [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] e [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] para criar controles sofisticados, fornecer ilustrações complexas de dados ou melhorar a experiência do usuário de uma interface do aplicativo. O suporte de [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não foi projetado para fornecer uma plataforma completa de desenvolvimento de jogos. Este tópico fornece uma visão geral da funcionalidade [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] do sistema de elementos gráficos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
 
  
<a name="threed_in_2d"></a>   
## <a name="3-d-in-a-2-d-container"></a>3D em um contêiner 2D  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] conteúdo em de elementos gráficos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é encapsulado em um elemento, <xref:System.Windows.Controls.Viewport3D>, que pode participar da estrutura bidimensional do elemento. O sistema de elementos gráficos trata <xref:System.Windows.Controls.Viewport3D> como um elemento visual bidimensional como muitos outros em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Viewport3D> funciona como uma janela — um visor – em uma cena tridimensional. Mais precisamente, ele é uma superfície na qual uma cena [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] é projetada.  
  
 Em um convencional [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] aplicativo, use <xref:System.Windows.Controls.Viewport3D> como faria com outro elemento contêiner como Grid ou Canvas.  Embora você possa usar <xref:System.Windows.Controls.Viewport3D> si [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] objetos de desenho no mesmo grafo da cena, não é possível mesclar [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] e [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objetos dentro de um <xref:System.Windows.Controls.Viewport3D>.  Este tópico abordará como desenhar [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] gráficos dentro de <xref:System.Windows.Controls.Viewport3D>.  
  
<a name="coord_space"></a>   
## <a name="3-d-coordinate-space"></a>Espaço de coordenadas 3D  
 O sistema de coordenadas do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para gráficos [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] localiza a origem na parte superior esquerda da área de renderização (geralmente a tela). No sistema [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], os valores positivos do eixo X se deslocam para a direita e os valores positivos do eixo Y se deslocam para baixo.  No entanto, no sistema de coordenadas [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)], a origem está localizada no centro da área de renderização, com os valores positivos do eixo x se deslocando para a direita, mas os valores positivos do eixo y se deslocando para cima e os valores positivos do eixo z se deslocando para fora da origem, em direção ao observador.  
  
 ![Sistemas de coordenadas](./media/coordsystem-1.png "CoordSystem-1")  
Representações convencionais do sistema de coordenadas 2D e 3D  
  
 O espaço definido por esses eixos é o quadro estacionário de referência para objetos [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ao compilar modelos nesse espaço e criar luzes e câmeras para exibi-los, é útil distinguir esse quadro estacionário de referência, ou “espaço de mundo”, do quadro local da referência que você cria para cada modelo quando aplica transformações a ele. Lembre-se também de que os objetos no espaço de mundo podem parecer totalmente diferentes, ou até mesmo não estarem visíveis, dependendo das configurações de câmera e de luz; porém, a posição da câmera não altera a localização dos objetos no espaço de mundo.  
  
<a name="cameras"></a>   
## <a name="cameras-and-projections"></a>Câmeras e projeções  
 Os desenvolvedores que trabalham no [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] estão acostumados a posicionar primitivos de desenho em uma tela bidimensional. Ao criar uma cena [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)], é importante lembrar de que você está realmente criando uma representação [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] de objetos [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]. Como uma cena [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] parece diferente dependendo do ponto de vista do observador, é necessário especificar esse ponto de vista. O <xref:System.Windows.Media.Media3D.Camera> classe permite que você especifique este ponto de vista de um [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] cena.  
  
 Outra maneira de entender como uma cena [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] é representada em uma superfície [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] é descrevendo a cena como uma projeção na superfície de exibição. O <xref:System.Windows.Media.Media3D.ProjectionCamera> permite especificar diferentes projeções e suas propriedades para alterar como o observador vê [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modelos. Um <xref:System.Windows.Media.Media3D.PerspectiveCamera> Especifica uma projeção que reduz as dimensões da cena.  Em outras palavras, o <xref:System.Windows.Media.Media3D.PerspectiveCamera> fornece uma perspectiva de ponto de fuga.  Você pode especificar a posição da câmera no espaço de coordenadas da cena, a direção e o campo de visão da câmera e um vetor que define a direção “para cima” na cena. O diagrama a seguir ilustra o <xref:System.Windows.Media.Media3D.PerspectiveCamera>da projeção.  
  
 O <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> e <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> propriedades de <xref:System.Windows.Media.Media3D.ProjectionCamera> limitar o intervalo de projeção da câmera. Como as câmeras podem estar localizadas em qualquer lugar na cena, é possível que a câmera esteja realmente posicionada dentro de um modelo ou muito próximo a ele, dificultando a distinção correta de objetos.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> permite que você especifique uma distância mínima da câmera além da qual os objetos não serão desenhados.  Por outro lado, <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> permite que você especifique uma distância da câmera além da qual os objetos não serão desenhados, o que garante que objetos muito distantes para serem reconhecidos não sejam incluídos na cena.  
  
 ![Instalação da câmera](./media/coordsystem-6.png "CoordSystem-6")  
Posição da câmera  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera> Especifica uma projeção ortogonal de um [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modelo para um [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] superfície visual. Como outras câmeras, ela especifica uma posição, direção de visualização e direção “para cima”. Diferentemente <xref:System.Windows.Media.Media3D.PerspectiveCamera>, no entanto, <xref:System.Windows.Media.Media3D.OrthographicCamera> descreve uma projeção que não inclui a redução das dimensões da perspectiva. Em outras palavras, <xref:System.Windows.Media.Media3D.OrthographicCamera> descreve uma caixa de visualização cujos lados são paralelos, em vez de uma cujos lados se encontram em um ponto na câmera. A imagem a seguir mostra o mesmo modelo exibido usando <xref:System.Windows.Media.Media3D.PerspectiveCamera> e <xref:System.Windows.Media.Media3D.OrthographicCamera>.  
  
 ![Projeção de perspectiva e ortográfica](./media/camera-projections4.png "Camera_projections4")  
Projeções de perspectiva e ortográficas  
  
 O código a seguir mostra algumas configurações típicas da câmera.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>   
## <a name="model-and-mesh-primitives"></a>Modelo e primitivos de malha  
  
 <xref:System.Windows.Media.Media3D.Model3D> é a classe base abstrata que representa um genérico [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objeto. Para criar uma [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] cena, você precisa de alguns objetos para exibir e os objetos que compõem o grafo de cena derivam de <xref:System.Windows.Media.Media3D.Model3D>. Atualmente, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte a geometrias de modelagem com <xref:System.Windows.Media.Media3D.GeometryModel3D>. O <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> propriedade desse modelo tem uma malha primitiva.  
  
 Para compilar um modelo, comece criando um primitivo, ou uma malha. Um primitivo [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] é uma coleção de vértices que formam uma única entidade [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]. A maioria dos sistemas [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] fornece primitivos modelados na figura fechada mais simples: um triângulo definido por três vértices.  Como os três pontos de um triângulo são coplanares, você pode continuar adicionando triângulos para modelar formas mais complexas, chamadas malhas.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sistema atualmente fornece as <xref:System.Windows.Media.Media3D.MeshGeometry3D> classe, que permite que você especificar qualquer geometria; ele não oferece suporte predefinido [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] primitivos como esferas ou formas cúbicas. Começar a criar uma <xref:System.Windows.Media.Media3D.MeshGeometry3D> especificando uma lista dos vértices de triângulo como sua <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> propriedade. Cada vértice é especificado como um <xref:System.Windows.Media.Media3D.Point3D>.  (No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], especifique essa propriedade como uma lista de números agrupados em três que representam as coordenadas de cada vértice.) Dependendo de sua geometria, a malha pode ser composta por vários triângulos, alguns dos quais compartilham os mesmos cantos (vértices). Para desenhar a malha corretamente, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] precisa de informações sobre quais vértices são compartilhados por quais triângulos. Fornecer essas informações especificando uma lista de índices de triângulo com a <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> propriedade. Essa lista especifica a ordem na qual os pontos especificados no <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> lista determinará um triângulo.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 No exemplo anterior, o <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> lista especifica oito vértices para definir uma malha em forma de cubo. O <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> propriedade especifica uma lista de doze grupos de três índices.  Cada número na lista refere-se a um deslocamento para o <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> lista.  Por exemplo, os três primeiros vértices especificados pela <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> lista são (1,1,0), (0, 1,0) e (0, 0,0). Os três primeiros índices especificados pela <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> lista são 0, 2 e 1, que correspondem ao primeiro, terceiro e segundo pontos o <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> lista. Como resultado, o primeiro triângulo que compõe o modelo de cubo será composto de (1,1,0) para (0,1,0) e (0, 0,0) e os onze triângulos restantes serão determinados da mesma forma.  
  
 Você pode continuar definindo o modelo especificando valores para o <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> e <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> propriedades.  Para renderizar a superfície do modelo, o sistema de elementos gráficos precisa de informações sobre para qual direção a superfície está voltada em um triângulo específico. Ele usa essas informações para fazer cálculos de iluminação para o modelo: as superfícies voltadas diretamente para uma fonte de luz parecem mais brilhantes do que aquelas que têm ângulos distantes da luz. Embora o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] possa determinar vetores normais padrão usando as coordenadas de posição, também é possível especificar vetores normais diferentes para aproximar a aparência de superfícies curvas.  
  
 O <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> propriedade especifica uma coleção de <xref:System.Windows.Point>que informam o sistema de elementos gráficos como mapear as coordenadas que determinam como uma textura é desenhada nos vértices da malha. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> são especificados como um valor entre zero e 1, inclusive.  Assim como acontece com o <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> propriedade, o sistema de elementos gráficos pode calcular coordenadas de textura padrão, mas você pode optar por definir outras coordenadas de textura para controlar o mapeamento de uma textura que inclui parte de um padrão de repetição, por exemplo. Encontre mais informações sobre coordenadas de textura nos próximos tópicos ou no SDK do Direct3D Gerenciado.  
  
 O exemplo a seguir mostra como criar uma face do modelo de cubo no código de procedimento. Observe que é possível desenhar o cubo todo como um único GeometryModel3D; esse exemplo desenha a face do cubo como um modelo distinto para aplicar texturas separadas a cada face posteriormente.  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>   
## <a name="applying-materials-to-the-model"></a>Aplicando materiais ao modelo  
  
 Para que uma malha tenha a aparência de um objeto tridimensional, ela deve ter uma textura aplicada para cobrir a superfície definida por seus vértices e triângulos, de forma que ela possa ser iluminada e projetada pela câmera. Na [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], você usa o <xref:System.Windows.Media.Brush> classe para aplicar cores, padrões, gradientes ou outro conteúdo visual às áreas da tela.  No entanto, a aparência de objetos [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] é uma função do modelo de iluminação, não apenas da cor ou do padrão aplicado a eles. Objetos do mundo real refletem a luz de maneira diferente dependendo da qualidade de suas superfícies: superfícies brilhantes não têm a mesma aparência que superfícies ásperas ou foscas, e alguns objetos parecem absorver luz, enquanto outros brilham. Você pode aplicar os mesmos pincéis a objetos [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] que podem ser aplicados a objetos [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], mas não pode aplicá-los diretamente.  
  
 Para definir as características de superfície um modelo da [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa o <xref:System.Windows.Media.Media3D.Material> classe abstrata. As subclasses concretas de Material determinam algumas das características de aparência da superfície do modelo, e cada uma delas também fornece uma propriedade Brush para a qual você pode passar um SolidColorBrush, TileBrush ou VisualBrush.  
  
-   <xref:System.Windows.Media.Media3D.DiffuseMaterial> Especifica que o pincel será aplicado ao modelo como se o modelo fosse iluminado difusa. O uso de DiffuseMaterial é semelhante ao uso de pincéis diretamente em modelos [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)]; as superfícies do modelo não refletem luz como se fossem brilhantes.  
  
-   <xref:System.Windows.Media.Media3D.SpecularMaterial> Especifica que o pincel será aplicado ao modelo como se superfície do modelo fosse rígida ou brilhante, capaz de refletir realces. Você pode definir o grau ao qual a textura fará sugestões essa qualidade reflexiva, ou "brilho", especificando um valor para o <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> propriedade.  
  
-   <xref:System.Windows.Media.Media3D.EmissiveMaterial> permite que você especifique que a textura será aplicada como se o modelo estivesse emitindo luz igual à cor do pincel. Isso não faz do modelo uma luz; no entanto, ele participará de maneira diferente do sombreamento comparado ao que ocorreria caso fosse texturizado com DiffuseMaterial ou SpecularMaterial.  
  
 Para obter melhor desempenho, as faces traseiras de um <xref:System.Windows.Media.Media3D.GeometryModel3D> (as faces que estão fora do modo de exibição por estarem no lado oposto do modelo da câmera) são cortadas da cena.  Para especificar uma <xref:System.Windows.Media.Media3D.Material> para aplicar a face traseira de um modelo como um plano, defina o modelo <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> propriedade.  
  
 Para obter algumas qualidades de superfície, como efeitos brilhantes ou reflexivos, talvez você deseje aplicar vários pincéis diferentes a um modelo em sucessão. Você pode aplicar e reutilizar vários Materials usando o <xref:System.Windows.Media.Media3D.MaterialGroup> classe. Os filhos do MaterialGroup são aplicados do primeiro ao último em várias aplicações de renderização.  
  
 Os seguintes exemplos de código mostram como aplicar uma cor sólida e um desenho como pincéis a modelos [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)].  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  
 [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
  
 [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
 [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>   
## <a name="illuminating-the-scene"></a>Iluminando a cena  
 As luzes em gráficos [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] fazem a mesma coisa que no mundo real: tornam as superfícies visíveis. Mais especificamente, as luzes determinam qual parte de uma cena será incluída na projeção. Os objetos de luz do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] criam uma variedade de efeitos de luz e sombra e são modelados com o comportamento de várias luzes do mundo real. É necessário incluir, no mínimo, uma luz na cena; caso contrário, nenhum modelo será visível.  
  
 As seguintes luzes são derivadas da classe base <xref:System.Windows.Media.Media3D.Light>:  
  
-   <xref:System.Windows.Media.Media3D.AmbientLight>: Fornece uma luz ambiente que ilumina todos os objetos de modo uniforme, independentemente de seu local ou orientação.  
  
-   <xref:System.Windows.Media.Media3D.DirectionalLight>: Ilumina como uma fonte de luz distante.  As luzes direcionais têm uma <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> especificada como um Vector3D, mas nenhum local especificado.  
  
-   <xref:System.Windows.Media.Media3D.PointLight>: Ilumina como uma fonte de luz próxima. As PointLights têm uma posição e lançam uma luz a dessa posição. Os objetos na cena são iluminados dependendo de sua posição e distância com relação à luz. <xref:System.Windows.Media.Media3D.PointLightBase> expõe um <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> propriedade, que determina uma distância além da qual os modelos não serão iluminados pela luz. A PointLight também expõe propriedades de atenuação que determinam como a intensidade da luz diminui com a distância. Você pode especificar interpolações constantes, lineares ou quadráticas para a atenuação da luz.  
  
-   <xref:System.Windows.Media.Media3D.SpotLight>: herda de <xref:System.Windows.Media.Media3D.PointLight>. Os destaques iluminam como PointLight e têm posição e direção. Eles projetam a luz em uma área em forma de cone definida pelas <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> e <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> propriedades, especificadas em graus.  
  
 Luzes são <xref:System.Windows.Media.Media3D.Model3D> objetos, portanto, você pode transformar e animar propriedades de luz, incluindo a posição, cor, direção e intervalo.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>   
## <a name="transforming-models"></a>Transformando modelos  
 Quando você cria modelos, eles têm uma localização específica na cena. Para mover esses modelos na cena, girá-los ou alterar seus tamanhos, não é prático alterar os vértices que definem os próprios modelos.  Em vez disso, assim como em [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], você aplica transformações a modelos.  
  
 Cada objeto de modelo tem um <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> propriedade com o qual você pode mover, reorientar ou redimensionar o modelo.  Ao aplicar uma transformação, você efetivamente desloca todos os pontos do modelo por meio de qualquer vetor ou valor especificado pela transformação. Em outras palavras, você transformou o espaço de coordenadas no qual o modelo está definido (“espaço do modelo”), mas não alterou os valores que compõem a geometria do modelo no sistema de coordenadas de toda a cena (“espaço de mundo”).  
  
 Para obter mais informações sobre como transformar modelos, consulte [Visão geral das transformações 3D](3-d-transformations-overview.md).  
  
<a name="animations"></a>   
## <a name="animating-models"></a>Animando modelos  
 A implementação [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] participa do mesmo sistema de animação e tempo que os gráficos [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)]. Em outras palavras, para animar uma cena 3D, anime as propriedades de seus modelos. É possível animar propriedades de primitivas diretamente, mas é geralmente mais fácil animar transformações que alteram a posição ou a aparência de modelos. Como as transformações podem ser aplicadas para <xref:System.Windows.Media.Media3D.Model3DGroup> objetos, bem como modelos individuais, é possível aplicar um conjunto de animações a um filho de um Model3DGroup e outro conjunto de animações a um grupo de objetos filho. Você também pode obter uma variedade de efeitos visuais animando as propriedades de iluminação da cena. Por fim, é possível optar por animar a própria projeção animando a posição ou o campo de visão da câmera. Para obter informações básicas sobre o sistema de animação e tempo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte os tópicos [Visão geral da animação](animation-overview.md), [Visão geral dos storyboards](storyboards-overview.md) e [Visão geral dos objetos congeláveis](../advanced/freezable-objects-overview.md).  
  
 Para animar um objeto no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você cria uma linha do tempo, define uma animação (que é, na verdade, uma alteração em alguns valores da propriedade ao longo do tempo) e especifica a propriedade à qual aplicar a animação. Porque todos os objetos em um [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] cena são filhos do <xref:System.Windows.Controls.Viewport3D>, as propriedades direcionadas por qualquer animação que você deseja aplicar à cena são propriedades das propriedades do Viewport3D.  
  
 Suponha que você deseje fazer com que um modelo pareça se mexer no lugar. Você pode optar por aplicar um <xref:System.Windows.Media.Media3D.RotateTransform3D> para o modelo e animar o eixo de sua rotação de um vetor para outro. O exemplo de código a seguir demonstra a aplicação de uma Vector3DAnimation à propriedade do Eixo da Rotation3D da transformação, supondo que a RotateTransform3D seja uma das várias transformações aplicadas ao modelo com um TransformGroup.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>   
## <a name="add-3-d-content-to-the-window"></a>Adicionar conteúdo 3D à janela  
 Para renderizar a cena, adicione modelos e luzes a um <xref:System.Windows.Media.Media3D.Model3DGroup>, em seguida, defina a <xref:System.Windows.Media.Media3D.Model3DGroup> como o <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> de um <xref:System.Windows.Media.Media3D.ModelVisual3D>. Adicione a <xref:System.Windows.Media.Media3D.ModelVisual3D> para o <xref:System.Windows.Controls.Viewport3D.Children%2A> coleção do <xref:System.Windows.Controls.Viewport3D>. Adicione câmeras para o <xref:System.Windows.Controls.Viewport3D> definindo seu <xref:System.Windows.Controls.Viewport3D.Camera%2A> propriedade.  
  
 Por fim, adicione o <xref:System.Windows.Controls.Viewport3D> à janela. Quando o <xref:System.Windows.Controls.Viewport3D> está incluído como o conteúdo de um elemento de layout como Canvas, especifique o tamanho do Viewport3D definindo suas <xref:System.Windows.FrameworkElement.Height%2A> e <xref:System.Windows.FrameworkElement.Width%2A> propriedades (herdado de <xref:System.Windows.FrameworkElement>).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [Visão geral das transformações 3D](3-d-transformations-overview.md)
- [Maximizar o desempenho 3D do WPF](maximize-wpf-3d-performance.md)
- [Tópicos de instruções](3-d-graphics-how-to-topics.md)
- [Visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
