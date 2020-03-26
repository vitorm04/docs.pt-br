---
title: Visão geral de gráficos 3D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D graphics [WPF]
- graphics [WPF], 3D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: e4918f7737bbe57a4f29c6c5cff1099f4f21674b
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291813"
---
# <a name="3d-graphics-overview"></a>Visão geral de gráficos 3D
<a name="introduction"></a>A funcionalidade 3D [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permite que os desenvolvedores desenhem, transformem e animem gráficos 3D tanto em marcação quanto em código processual. Os desenvolvedores podem combinar gráficos 2D e 3D para criar controles ricos, fornecer ilustrações complexas de dados ou melhorar a experiência do usuário da interface de um aplicativo. O suporte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3D não foi projetado para fornecer uma plataforma completa de desenvolvimento de jogos. Este tópico fornece uma visão geral da [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funcionalidade 3D no sistema gráfico.  

<a name="threed_in_2d"></a>
## <a name="3d-in-a-2d-container"></a>3D em um recipiente 2D  
 O conteúdo gráfico [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3D é encapsulado em um elemento, <xref:System.Windows.Controls.Viewport3D>que pode participar da estrutura de elementos bidimensionais. O sistema <xref:System.Windows.Controls.Viewport3D> gráfico trata como um elemento visual [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bidimensional como muitos outros em . <xref:System.Windows.Controls.Viewport3D>funciona como uma janela — uma porta de visualização — em uma cena tridimensional. Mais precisamente, é uma superfície na qual uma cena 3D é projetada.  
  
 Em uma aplicação 2D <xref:System.Windows.Controls.Viewport3D> convencional, use como faria com outro elemento de contêiner como Grid ou Canvas.  Embora você <xref:System.Windows.Controls.Viewport3D> possa usar com outros objetos de desenho 2D no mesmo gráfico <xref:System.Windows.Controls.Viewport3D>de cena, você não pode interpenetrar objetos 2D e 3D dentro de um .  Este tópico se concentrará em como <xref:System.Windows.Controls.Viewport3D>desenhar gráficos 3D dentro do .  
  
<a name="coord_space"></a>
## <a name="3d-coordinate-space"></a>Espaço de Coordenadas 3D  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de coordenadas para gráficos 2D localiza a origem no canto superior esquerdo da área de renderização (tipicamente a tela). No sistema 2D, os valores positivos do eixo x prosseguem para os valores do eixo y certo e positivos procedem para baixo.  No sistema de coordenadas 3D, no entanto, a origem está localizada no centro da área de renderização, com valores positivos do eixo x seguindo para a direita, mas positivos valores do eixo y procedendo para cima, e valores positivos do eixo z procedendo para fora da origem, em direção ao espectador.  
  
 ![Sistemas de coordenadas](./media/coordsystem-1.png "CoordSystem-1")  
Representações convencionais do sistema de coordenadas 2D e 3D  
  
 O espaço definido por esses eixos é o quadro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]estacionário de referência para objetos 3D em . Ao compilar modelos nesse espaço e criar luzes e câmeras para exibi-los, é útil distinguir esse quadro estacionário de referência, ou “espaço de mundo”, do quadro local da referência que você cria para cada modelo quando aplica transformações a ele. Lembre-se também de que objetos no espaço de mundo podem parecer totalmente diferentes ou até mesmo não serem visíveis, dependendo das configurações de câmera e de luz, mas a posição da câmera não altera o local dos objetos no espaço de mundo.  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>Câmeras e projeções  
 Desenvolvedores que trabalham em 2D estão acostumados a posicionar os primitivos de desenho em uma tela bidimensional. Quando você cria uma cena 3D, é importante lembrar que você está realmente criando uma representação 2D de objetos 3D. Como uma cena 3D parece diferente dependendo do ponto de vista do espectador, você deve especificar esse ponto de vista. A <xref:System.Windows.Media.Media3D.Camera> classe permite que você especifique este ponto de vista para uma cena 3D.  
  
 Outra maneira de entender como uma cena 3D é representada em uma superfície 2D é descrevendo a cena como uma projeção na superfície de visualização. O <xref:System.Windows.Media.Media3D.ProjectionCamera> permite especificar diferentes projeções e suas propriedades para alterar a forma como o espectador vê modelos 3D. A <xref:System.Windows.Media.Media3D.PerspectiveCamera> especifica uma projeção que encurta a cena.  Em outras <xref:System.Windows.Media.Media3D.PerspectiveCamera> palavras, o ponto de fuga fornece perspectiva de ponto de fuga.  Você pode especificar a posição da câmera no espaço de coordenadas da cena, a direção e o campo de visão da câmera e um vetor que define a direção “para cima” na cena. O diagrama a <xref:System.Windows.Media.Media3D.PerspectiveCamera>seguir ilustra a projeção.  
  
 As <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> propriedades <xref:System.Windows.Media.Media3D.ProjectionCamera> de limitar o alcance da projeção da câmera. Como as câmeras podem estar localizadas em qualquer lugar na cena, é possível que a câmera esteja realmente posicionada dentro de um modelo ou muito próximo a ele, dificultando a distinção correta de objetos.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>permite especificar uma distância mínima da câmera além da qual os objetos não serão desenhados.  Por outro <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> lado, permite especificar uma distância da câmera além da qual os objetos não serão desenhados, o que garante que objetos muito distantes para serem reconhecíveis não serão incluídos na cena.  
  
 ![Instalação da câmera](./media/coordsystem-6.png "CoordSystem-6")  
Posição da câmera  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>especifica uma projeção ortogonal de um modelo 3D para uma superfície visual 2D. Como outras câmeras, ela especifica uma posição, direção de visualização e direção “para cima”. Ao <xref:System.Windows.Media.Media3D.PerspectiveCamera>contrário, <xref:System.Windows.Media.Media3D.OrthographicCamera> no entanto, descreve uma projeção que não inclui o encurtamento da perspectiva. Em outras <xref:System.Windows.Media.Media3D.OrthographicCamera> palavras, descreve uma caixa de visualização cujos lados são paralelos, em vez de um cujos lados se encontram em um ponto para a câmera. A imagem a seguir mostra <xref:System.Windows.Media.Media3D.PerspectiveCamera> o <xref:System.Windows.Media.Media3D.OrthographicCamera>mesmo modelo visto usando e .  
  
 ![Projeções de perspectiva e ortográficas](./media/camera-projections4.png "Camera_projections4")  
Projeções de perspectiva e ortográficas  
  
 O código a seguir mostra algumas configurações típicas da câmera.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>Modelo e primitivos de malha  
  
 <xref:System.Windows.Media.Media3D.Model3D>é a classe base abstrata que representa um objeto 3D genérico. Para construir uma cena 3D, você precisa de alguns objetos para <xref:System.Windows.Media.Media3D.Model3D>visualizar, e os objetos que compõem o gráfico de cena derivam de . Atualmente, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o suporte modela <xref:System.Windows.Media.Media3D.GeometryModel3D>geometrias com . A <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> propriedade deste modelo tem uma malha primitiva.  
  
 Para compilar um modelo, comece criando um primitivo, ou uma malha. Um primitivo 3D é uma coleção de vértices que forma uma única entidade 3D. A maioria dos sistemas 3D fornece primitivos modelados na figura fechada mais simples: um triângulo definido por três vértices.  Como os três pontos de um triângulo são coplanares, você pode continuar adicionando triângulos para modelar formas mais complexas, chamadas malhas.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema 3D fornece <xref:System.Windows.Media.Media3D.MeshGeometry3D> atualmente a classe, o que permite especificar qualquer geometria; atualmente não suporta primitivos 3D predefinidos como esferas e formas cúbicas. Comece a <xref:System.Windows.Media.Media3D.MeshGeometry3D> criar um especificando uma lista <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> de vértices triangulares como sua propriedade. Cada vértice é <xref:System.Windows.Media.Media3D.Point3D>especificado como a .  (In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], especificar esta propriedade como uma lista de números agrupados em três que representam as coordenadas de cada vértice.) Dependendo de sua geometria, sua malha pode ser composta de muitos triângulos, alguns dos quais compartilham os mesmos cantos (vértices). Para desenhar a malha corretamente, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] precisa de informações sobre quais vértices são compartilhados por quais triângulos. Você fornece essas informações especificando uma lista <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> de índices de triângulo com a propriedade. Esta lista especifica a ordem na qual <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> os pontos especificados na lista determinarão um triângulo.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 No exemplo anterior, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> a lista especifica oito vértices para definir uma malha em forma de cubo. A <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> propriedade especifica uma lista de doze grupos de três índices.  Cada número da lista refere-se <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> a uma compensação na lista.  Por exemplo, os três primeiros vértices especificados pela <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> lista são (1,1,0), (0,1,0) e (0,0,0). Os três primeiros índices <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> especificados pela lista são 0, 2 e 1, que correspondem ao primeiro, terceiro e segundo pontos da <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> lista. Como resultado, o primeiro triângulo que compõe o modelo de cubo será composto de (1,1,0) para (0,1,0) e (0, 0,0) e os onze triângulos restantes serão determinados da mesma forma.  
  
 Você pode continuar definindo o modelo <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> especificando valores para as propriedades e propriedades.  Para renderizar a superfície do modelo, o sistema de elementos gráficos precisa de informações sobre para qual direção a superfície está voltada em um triângulo específico. Ele usa essas informações para fazer cálculos de iluminação para o modelo: as superfícies voltadas diretamente para uma fonte de luz parecem mais brilhantes do que aquelas que têm ângulos distantes da luz. Embora o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] possa determinar vetores normais padrão usando as coordenadas de posição, também é possível especificar vetores normais diferentes para aproximar a aparência de superfícies curvas.  
  
 A <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> propriedade especifica uma <xref:System.Windows.Point>coleção de s que dizem ao sistema gráfico como mapear as coordenadas que determinam como uma textura é atraída para os vértices da malha. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>são especificados como um valor entre zero e 1, inclusive.  Assim como <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> na propriedade, o sistema gráfico pode calcular coordenadas de textura padrão, mas você pode optar por definir diferentes coordenadas de textura para controlar o mapeamento de uma textura que inclui parte de um padrão repetitivo, por exemplo. Encontre mais informações sobre coordenadas de textura nos próximos tópicos ou no SDK do Direct3D Gerenciado.  
  
 O exemplo a seguir mostra como criar uma face do modelo de cubo no código de procedimento. Você pode desenhar o cubo inteiro como um único GeometryModel3D; este exemplo desenha o rosto do cubo como um modelo distinto, a fim de aplicar texturas separadas em cada rosto mais tarde.  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>'
## <a name="applying-materials-to-the-model"></a>Aplicando materiais ao modelo  
  
 Para que uma malha tenha a aparência de um objeto tridimensional, ela deve ter uma textura aplicada para cobrir a superfície definida por seus vértices e triângulos, de forma que ela possa ser iluminada e projetada pela câmera. Em 2D, você <xref:System.Windows.Media.Brush> usa a classe para aplicar cores, padrões, gradientes ou outros conteúdos visuais em áreas da tela.  O aparecimento de objetos 3D, no entanto, é uma função do modelo de iluminação, não apenas da cor ou padrão aplicado a eles. Objetos do mundo real refletem a luz de maneira diferente dependendo da qualidade de suas superfícies: superfícies brilhantes não têm a mesma aparência que superfícies ásperas ou foscas, e alguns objetos parecem absorver luz, enquanto outros brilham. Você pode aplicar todos os mesmos pincéis a objetos 3D que você pode aplicar a objetos 2D, mas você não pode aplicá-los diretamente.  
  
 Para definir as características da superfície [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de <xref:System.Windows.Media.Media3D.Material> um modelo, utiliza-se a classe abstrata. As subclasses concretas de Material determinam algumas das características de aparência da superfície do modelo, e cada uma delas também fornece uma propriedade Brush para a qual você pode passar um SolidColorBrush, TileBrush ou VisualBrush.  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial>especifica que o pincel será aplicado ao modelo como se esse modelo fosse iluminado difusamente. O uso de DiffuseMaterial se assemelha mais ao uso de pincéis diretamente em modelos 2D; superfícies modelo não refletem a luz como se brilhante.  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial>especifica que o pincel será aplicado ao modelo como se a superfície do modelo fosse dura ou brilhante, capaz de refletir destaques. Você pode definir o grau em que a textura sugerirá essa qualidade reflexiva, ou "brilho", especificando um valor para a <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> propriedade.  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial>permite especificar que a textura será aplicada como se o modelo estivesse emitindo luz igual à cor do pincel. Isso não faz do modelo uma luz; no entanto, ele participará de maneira diferente do sombreamento comparado ao que ocorreria caso fosse texturizado com DiffuseMaterial ou SpecularMaterial.  
  
 Para um melhor desempenho, <xref:System.Windows.Media.Media3D.GeometryModel3D> os backfaces de a (aqueles rostos que estão fora de vista porque estão no lado oposto do modelo da câmera) são retirados da cena.  Para especificar um <xref:System.Windows.Media.Media3D.Material> para aplicar no backface de um modelo <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> como um plano, defina a propriedade do modelo.  
  
 Para obter algumas qualidades de superfície, como efeitos brilhantes ou reflexivos, talvez você deseje aplicar vários pincéis diferentes a um modelo em sucessão. Você pode aplicar e reutilizar <xref:System.Windows.Media.Media3D.MaterialGroup> vários materiais usando a classe. Os filhos do MaterialGroup são aplicados do primeiro ao último em várias aplicações de renderização.  
  
 Os exemplos de código a seguir mostram como aplicar uma cor sólida e um desenho como pincéis para modelos 3D.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  ' [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
 ' [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
  [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>Iluminando a cena  
 Luzes em gráficos 3D fazem o que as luzes fazem no mundo real: tornam as superfícies visíveis. Mais especificamente, as luzes determinam qual parte de uma cena será incluída na projeção. Os objetos de luz do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] criam uma variedade de efeitos de luz e sombra e são modelados com o comportamento de várias luzes do mundo real. Inclua pelo menos uma luz em sua cena, ou nenhum modelo será visível.  
  
 As seguintes luzes derivam da classe <xref:System.Windows.Media.Media3D.Light>base:  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>: Fornece iluminação ambiente que ilumina todos os objetos uniformemente, independentemente de sua localização ou orientação.  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>: Ilumina-se como uma fonte de luz distante.  As luzes direcionais têm um <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> Vector3D especificado, mas nenhum local especificado.  
  
- <xref:System.Windows.Media.Media3D.PointLight>: Ilumina-se como uma fonte de luz próxima. As PointLights têm uma posição e lançam uma luz a dessa posição. Os objetos na cena são iluminados dependendo de sua posição e distância com relação à luz. <xref:System.Windows.Media.Media3D.PointLightBase>expõe uma <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> propriedade, que determina uma distância além da qual os modelos não serão iluminados pela luz. PointLight também expõe propriedades de atenuação, que determinam como a intensidade da luz diminui ao longo da distância. Você pode especificar interpolações constantes, lineares ou quadráticas para a atenuação da luz.  
  
- <xref:System.Windows.Media.Media3D.SpotLight>: Herda <xref:System.Windows.Media.Media3D.PointLight>de . Os destaques iluminam como PointLight e têm posição e direção. Eles projetam luz em uma área <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> em <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> forma de cone definida por e propriedades, especificada em graus.  
  
 As <xref:System.Windows.Media.Media3D.Model3D> luzes são objetos, para que você possa transformar e animar propriedades de luz, incluindo posição, cor, direção e alcance.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>
## <a name="transforming-models"></a>Transformando modelos  
 Quando você cria modelos, eles têm uma localização específica na cena. Para mover esses modelos na cena, girá-los ou alterar seus tamanhos, não é prático alterar os vértices que definem os próprios modelos.  Em vez disso, assim como em 2D, você aplica transformações em modelos.  
  
 Cada objeto modelo <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> tem uma propriedade com a qual você pode mover, reorientar ou redimensionar o modelo.  Ao aplicar uma transformação, você efetivamente desloca todos os pontos do modelo por meio de qualquer vetor ou valor especificado pela transformação. Em outras palavras, você transformou o espaço de coordenadas no qual o modelo está definido (“espaço do modelo”), mas não alterou os valores que compõem a geometria do modelo no sistema de coordenadas de toda a cena (“espaço de mundo”).  
  
 Para obter mais informações sobre a transformação de [modelos, consulte visão geral de transformações 3D](3-d-transformations-overview.md).  
  
<a name="animations"></a>
## <a name="animating-models"></a>Animando modelos  
 A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementação 3D participa do mesmo sistema de tempo e animação que os gráficos 2D. Ou seja, animar uma cena 3D, animar as propriedades de seus modelos. É possível animar propriedades de primitivas diretamente, mas é geralmente mais fácil animar transformações que alteram a posição ou a aparência de modelos. Como as transformações podem <xref:System.Windows.Media.Media3D.Model3DGroup> ser aplicadas a objetos, bem como modelos individuais, é possível aplicar um conjunto de animações a uma criança de um Model3DGroup e outro conjunto de animações a um grupo de objetos infantis. Você também pode obter uma variedade de efeitos visuais animando as propriedades de iluminação da cena. Por fim, é possível optar por animar a própria projeção animando a posição ou o campo de visão da câmera. Para obter informações básicas sobre o sistema de animação e tempo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte os tópicos [Visão geral da animação](animation-overview.md), [Visão geral dos storyboards](storyboards-overview.md) e [Visão geral dos objetos congeláveis](../advanced/freezable-objects-overview.md).  
  
 Para animar um objeto no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você cria uma linha do tempo, define uma animação (que é, na verdade, uma alteração em alguns valores da propriedade ao longo do tempo) e especifica a propriedade à qual aplicar a animação. Como todos os objetos em uma <xref:System.Windows.Controls.Viewport3D>cena 3D são crianças, as propriedades direcionadas por qualquer animação que você deseja aplicar à cena são propriedades do Viewport3D.  
  
 Suponha que você deseje fazer com que um modelo pareça se mexer no lugar. Você pode optar <xref:System.Windows.Media.Media3D.RotateTransform3D> por aplicar um ao modelo, e animar o eixo de sua rotação de um vetor para outro. O exemplo de código a seguir demonstra a aplicação de uma Vector3DAnimation à propriedade do Eixo da Rotation3D da transformação, supondo que a RotateTransform3D seja uma das várias transformações aplicadas ao modelo com um TransformGroup.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>
## <a name="add-3d-content-to-the-window"></a>Adicionar conteúdo 3D à janela  
 Para renderizar a cena, adicione <xref:System.Windows.Media.Media3D.Model3DGroup>modelos <xref:System.Windows.Media.Media3D.Model3DGroup> e <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> luzes <xref:System.Windows.Media.Media3D.ModelVisual3D>a um , em seguida, defina o como o de um . Adicione <xref:System.Windows.Media.Media3D.ModelVisual3D> o <xref:System.Windows.Controls.Viewport3D.Children%2A> à coleção <xref:System.Windows.Controls.Viewport3D>do . Adicione câmeras <xref:System.Windows.Controls.Viewport3D> ao definindo sua <xref:System.Windows.Controls.Viewport3D.Camera%2A> propriedade.  
  
 Finalmente, adicione <xref:System.Windows.Controls.Viewport3D> a janela. Quando <xref:System.Windows.Controls.Viewport3D> o conteúdo de um elemento de layout como o Canvas, especifique <xref:System.Windows.FrameworkElement.Width%2A> o tamanho <xref:System.Windows.FrameworkElement>do Viewport3D definindo suas <xref:System.Windows.FrameworkElement.Height%2A> propriedades (herdadas de ).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [Visão geral das transformações 3D](3-d-transformations-overview.md)
- [Maximizar o desempenho 3D do WPF](maximize-wpf-3d-performance.md)
- [Tópicos de como fazer](3-d-graphics-how-to-topics.md)
- [Visão geral de formas e desenhos básicos no WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
