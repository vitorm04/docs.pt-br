---
title: Visão geral de renderização de gráficos do WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rendering
- rendering graphics [WPF]
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
ms.openlocfilehash: 6323d27158855e5ded1698401835b35632bedebe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603827"
---
# <a name="wpf-graphics-rendering-overview"></a>Visão geral de renderização de gráficos do WPF
Este tópico fornece uma visão geral da camada visual do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ele se concentra na função do <xref:System.Windows.Media.Visual> classe para suporte à renderização no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelo.  
  
  
<a name="role_of_visual_object"></a>   
## <a name="role-of-the-visual-object"></a>Função do objeto visual  
 O <xref:System.Windows.Media.Visual> classe é a abstração básica a partir do qual cada <xref:System.Windows.FrameworkElement> deriva do objeto. Ela também serve como o ponto de entrada para escrever novos controles em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e, de muitas formas, pode ser pensada como o HWND (identificador de janela) no modelo de aplicativo Win32.  
  
 O <xref:System.Windows.Media.Visual> objeto é um núcleo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objeto, cuja função principal é fornecer suporte a renderização. Controles de interface do usuário, como <xref:System.Windows.Controls.Button> e <xref:System.Windows.Controls.TextBox>, derivam o <xref:System.Windows.Media.Visual> de classe e usá-lo para persistir seus dados de renderização. O <xref:System.Windows.Media.Visual> objeto oferece suporte para:  
  
-   Exibição de saída: Renderizando o persistente, serializado conteúdo de desenho de um visual.  
  
-   Transformações: Execução de transformações em um visual.  
  
-   Recorte: Fornecendo suporte de região de recorte para um visual.  
  
-   O teste de clique: Determinando se uma coordenada ou geometria está contida dentro dos limites de um visual.  
  
-   Cálculos de caixa delimitadora: Determinando o retângulo delimitador de um visual.  
  
 No entanto, o <xref:System.Windows.Media.Visual> objeto não inclui suporte para recursos de não renderização, tais como:  
  
-   Manipulação de eventos  
  
-   Layout  
  
-   Estilos  
  
-   Associação de dados  
  
-   Globalização  
  
 <xref:System.Windows.Media.Visual> é exposta como uma classe abstrata pública da qual classes filho devem ser derivadas. A ilustração a seguir mostra a hierarquia dos objetos visuais que são expostos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 ![Diagrama de classes derivadas do objeto Visual](../../../../docs/framework/wpf/graphics-multimedia/media/visualclass01.png "VisualClass01")  
Hierarquia de classes visuais  
  
### <a name="drawingvisual-class"></a>Classe DrawingVisual  
 O <xref:System.Windows.Media.DrawingVisual> é uma classe que é usada para renderizar formas, imagens ou texto leve. Essa classe é considerada leve porque não fornece layout ou manipulação de eventos, o que melhora o desempenho de tempo de execução. Por esse motivo, desenhos são ideais para planos de fundo e clip-art. O <xref:System.Windows.Media.DrawingVisual> pode ser usado para criar um objeto visual personalizado. Para obter mais informações, consulte [Usando objetos DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Classe Viewport3DVisual  
 O <xref:System.Windows.Media.Media3D.Viewport3DVisual> fornece uma ponte entre 2D <xref:System.Windows.Media.Visual> e <xref:System.Windows.Media.Media3D.Visual3D> objetos. O <xref:System.Windows.Media.Media3D.Visual3D> é a classe base para todos os elementos visuais 3D. O <xref:System.Windows.Media.Media3D.Viewport3DVisual> requer que você defina uma <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> valor e um <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A> valor. A câmera permite que você exiba a cena. O visor estabelece o local para o qual a projeção é mapeada na superfície 2D. Para obter mais informações sobre 3D em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Visão geral de elementos gráficos 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>Classe ContainerVisual  
 O <xref:System.Windows.Media.ContainerVisual> classe é usada como um contêiner para uma coleção de <xref:System.Windows.Media.Visual> objetos. O <xref:System.Windows.Media.DrawingVisual> classe deriva de <xref:System.Windows.Media.ContainerVisual> classe, permitindo que ela contenha uma coleção de objetos visuais.  
  
### <a name="drawing-content-in-visual-objects"></a>Desenhar conteúdo em objetos visuais  
 Um <xref:System.Windows.Media.Visual> objeto armazena seus dados de renderização como uma **lista de instruções de gráficos vetoriais**. Cada item na lista de instruções representa um conjunto de baixo nível de dados gráficos e recursos associados em um formato serializado. Há quatro tipos diferentes de dados de renderização que podem conter conteúdo de desenho.  
  
|Tipo de conteúdo de desenho|Descrição|  
|--------------------------|-----------------|  
|Gráficos vetoriais|Representa vetoriais dados gráficos e associados <xref:System.Windows.Media.Brush> e <xref:System.Windows.Media.Pen> informações.|  
|Image|Representa uma imagem dentro de uma região definida por um <xref:System.Windows.Rect>.|  
|Glifo|Representa um desenho que renderiza um <xref:System.Windows.Media.GlyphRun>, que é uma sequência de glifos de um recurso de fonte especificado. Este é o modo pelo qual o texto é representado.|  
|Vídeo|Representa um desenho que renderiza vídeo.|  
  
 O <xref:System.Windows.Media.DrawingContext> permite que você popule um <xref:System.Windows.Media.Visual> com conteúdo visual. Quando você usa um <xref:System.Windows.Media.DrawingContext> comandos de desenho do objeto, na verdade, você está armazenando um conjunto de dados de renderização que serão usados mais tarde pelo sistema gráfico; você não está desenhando na tela em tempo real.  
  
 Quando você cria um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controlar, como um <xref:System.Windows.Controls.Button>, o controle implicitamente gera dados de renderização para o próprio desenho. Por exemplo, definindo a <xref:System.Windows.Controls.ContentControl.Content%2A> propriedade do <xref:System.Windows.Controls.Button> faz com que o controle armazene uma representação renderizada de um glifo.  
  
 Um <xref:System.Windows.Media.Visual> descreve seu conteúdo como um ou mais <xref:System.Windows.Media.Drawing> objetos contidos em um <xref:System.Windows.Media.DrawingGroup>. Um <xref:System.Windows.Media.DrawingGroup> também descreve máscaras de opacidade, transformações, efeitos de bitmap e outras operações que são aplicadas ao seu conteúdo. <xref:System.Windows.Media.DrawingGroup> operações são aplicadas na seguinte ordem quando o conteúdo é renderizado: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>e, em seguida, <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 A ilustração a seguir mostra a ordem na qual <xref:System.Windows.Media.DrawingGroup> operações são aplicadas durante a sequência de renderização.  
  
 ![DrawingGroup ordem das operações](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Ordem das operações do DrawingGroup  
  
 Para obter mais informações, consulte a [Visão geral de objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Conteúdo de desenho na camada visual  
 Você nunca instancia diretamente uma <xref:System.Windows.Media.DrawingContext>; no entanto, você pode, adquirir um contexto de desenho de alguns métodos, tais como <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> e <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>. O exemplo a seguir recupera uma <xref:System.Windows.Media.DrawingContext> de um <xref:System.Windows.Media.DrawingVisual> e usa-o para desenhar um retângulo.  
  
 [!code-csharp[drawingvisualsample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Enumerar conteúdo de desenho na camada visual  
 Além de seus outros usos <xref:System.Windows.Media.Drawing> objetos também fornecem um modelo de objeto para enumerar o conteúdo de um <xref:System.Windows.Media.Visual>.  
  
> [!NOTE]
>  Quando você está enumerando o conteúdo do visual, você está recuperando <xref:System.Windows.Media.Drawing> objetos e não a representação subjacente dos dados de renderização como uma lista de instruções de gráficos de vetor.  
  
 O exemplo a seguir usa o <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> método para recuperar o <xref:System.Windows.Media.DrawingGroup> valor de um <xref:System.Windows.Media.Visual> e enumerá-lo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>   
## <a name="how-visual-objects-are-used-to-build-controls"></a>Como objetos visuais são usados para compilar controles  
 Muitos dos objetos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são compostos de outros objetos visuais, o que significa que eles podem conter diversas hierarquias de objetos descendentes. Muitos dos elementos da interface do usuário no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tais como controles, são compostos de múltiplos objetos visuais que representam diferentes tipos de elementos de renderização. Por exemplo, o <xref:System.Windows.Controls.Button> controle pode conter um número de outros objetos, incluindo <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, <xref:System.Windows.Controls.ContentPresenter>, e <xref:System.Windows.Controls.TextBlock>.  
  
 O código a seguir mostra um <xref:System.Windows.Controls.Button> definido na marcação de controle.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Se você fosse enumerar os objetos visuais que compreendem o padrão <xref:System.Windows.Controls.Button> controle, você encontraria a hierarquia de objetos visuais ilustrada abaixo:  
  
 ![Diagrama de hierarquia de árvore visual](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview03.gif "VisualLayerOverview03")  
Diagrama de hierarquia de árvore visual  
  
 O <xref:System.Windows.Controls.Button> controle contiver um <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> elemento, que por sua vez, contém um <xref:System.Windows.Controls.ContentPresenter> elemento. O <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> elemento é responsável por desenhar uma borda e um plano de fundo para o <xref:System.Windows.Controls.Button>. O <xref:System.Windows.Controls.ContentPresenter> elemento é responsável por exibir o conteúdo do <xref:System.Windows.Controls.Button>. Nesse caso, como você está exibindo texto, o <xref:System.Windows.Controls.ContentPresenter> elemento contém um <xref:System.Windows.Controls.TextBlock> elemento. O fato de que o <xref:System.Windows.Controls.Button> controlar usa um <xref:System.Windows.Controls.ContentPresenter> significa que o conteúdo poderia ser representado por outros elementos, como um <xref:System.Windows.Controls.Image> ou uma geometria, como um <xref:System.Windows.Media.EllipseGeometry>.  
  
### <a name="control-templates"></a>Modelos de controle  
 A chave para a expansão de um controle em uma hierarquia de controles é o <xref:System.Windows.Controls.ControlTemplate>. Um modelo de controle especifica a hierarquia visual de um controle. Quando você referencia um controle explicitamente, você referencia implicitamente sua hierarquia visual. Você pode substituir os valores padrão de um modelo de controle para criar uma aparência visual personalizada para um controle. Por exemplo, você poderia modificar o valor de cor do plano de fundo para o <xref:System.Windows.Controls.Button> controlar de forma que ele usa um valor de cor gradiente linear em vez de um valor de cor sólida. Para obter mais informações, consulte [Estilos e modelos de botão](../../../../docs/framework/wpf/controls/button-styles-and-templates.md).  
  
 Interface do usuário de um elemento, como um <xref:System.Windows.Controls.Button> de controle, que contém várias listas de instruções de gráficos vetoriais que descrevem a definição inteira de renderização de um controle. O código a seguir mostra um <xref:System.Windows.Controls.Button> definido na marcação de controle.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Se você enumerasse os objetos visuais e vetoriais listas de instruções de gráficos que compõem o <xref:System.Windows.Controls.Button> controle, você encontraria a hierarquia de objetos ilustrada abaixo:  
  
 ![Diagrama de árvore visual e dados de renderização](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview04.png "VisualLayerOverview04")  
Diagrama de árvore visual e dados de renderização  
  
 O <xref:System.Windows.Controls.Button> controle contiver um <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> elemento, que por sua vez, contém um <xref:System.Windows.Controls.ContentPresenter> elemento. O <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> elemento é responsável por desenhar todos os elementos gráficos discretos que compõem a borda e o plano de fundo de um botão. O <xref:System.Windows.Controls.ContentPresenter> elemento é responsável por exibir o conteúdo do <xref:System.Windows.Controls.Button>. Nesse caso, como você está exibindo uma imagem, o <xref:System.Windows.Controls.ContentPresenter> elemento contém um <xref:System.Windows.Controls.Image> elemento.  
  
 Há diversos pontos a observar sobre a hierarquia de objetos visuais e listas de instruções de gráficos vetoriais:  
  
-   A ordem na hierarquia representa a ordem de renderização das informações de desenho. Do elemento visual raiz, a ordem de renderização passa pelos elementos filho da esquerda para a direita, de cima para baixo. Se um determinado elemento tem elementos visuais filho, a ordem de renderização passa por eles antes de passar pelos irmãos desse elemento.  
  
-   Elementos de nós não folha na hierarquia, como <xref:System.Windows.Controls.ContentPresenter>, são usados para conter elementos filho – eles não contêm listas de instruções.  
  
-   Se um elemento visual contém uma lista de instruções de gráfico vetorial e filhos visuais, a lista de instruções no elemento visual pai é renderizada antes de desenhos em qualquer um dos objetos filho visuais.  
  
-   Os itens na lista de instruções de gráficos vetoriais são renderizados da esquerda para a direita.  
  
<a name="visual_tree"></a>   
## <a name="visual-tree"></a>Árvore visual  
 A árvore visual contém todos os elementos visuais usados na interface do usuário de um aplicativo. Já que um elemento visual contém informações de desenho persistentes, você pode pensar na árvore visual como um grafo de cena, contendo todas as informações de renderização necessárias para compor a saída para o dispositivo de vídeo. Esta árvore é o acúmulo de todos os elementos visuais criados diretamente pelo aplicativo, seja no código ou em marcação. A árvore visual também contém todos os elementos visuais criados pela expansão de modelo de elementos tais como controles e objetos de dados.  
  
 O código a seguir mostra um <xref:System.Windows.Controls.StackPanel> elemento definido na marcação.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Se você fosse enumerar os objetos visuais que compreendem o <xref:System.Windows.Controls.StackPanel> elemento no exemplo de marcação, encontraria a hierarquia de objetos visuais ilustrada abaixo:  
  
 ![Diagrama de hierarquia de árvore visual](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview05.gif "VisualLayerOverview05")  
Diagrama de hierarquia de árvore visual  
  
### <a name="rendering-order"></a>Ordem de renderização  
 A árvore visual determina a ordem de renderização de objetos visuais e de desenho do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. A ordem de passagem inicia com o visual raiz, que é o nó mais alto na árvore visual. Em seguida, passa-se pelos filhos do visual raiz, da esquerda para a direita. Se um visual tiver filhos, a passagem por eles ocorrerá primeiro do que a passagem pelos irmãos do visual. Isso significa que o conteúdo de um visual filho é renderizado na frente do conteúdo do próprio visual.  
  
 ![Diagrama da ordem de renderização da árvore visual](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview06.gif "VisualLayerOverview06")  
Diagrama da ordem de renderização da árvore visual  
  
### <a name="root-visual"></a>Visual raiz  
 O **visual raiz** é o elemento mais alto em uma hierarquia de árvore visual. Na maioria dos aplicativos, a classe base do visual raiz seja <xref:System.Windows.Window> ou <xref:System.Windows.Navigation.NavigationWindow>. No entanto, se você estivesse hospedando objetos visuais em um aplicativo Win32, o visual raiz seria o visual mais alto que você estivesse hospedando na janela Win32. Para obter mais informações, confira [Tutorial: Hospedando objetos visuais em um aplicativo Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Relacionamento com a árvore lógica  
 A árvore lógica no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] representa os elementos de um aplicativo em tempo de execução. Embora você não manipule esta árvore diretamente, essa exibição do aplicativo é útil para entender a herança de propriedades e o roteamento de eventos. Diferentemente da árvore visual, a árvore lógica pode representar objetos de dados não visuais, tais como <xref:System.Windows.Documents.ListItem>. Em muitos casos, a árvore lógica mapeia de modo muito próximo às definições de marcação de um aplicativo. O código a seguir mostra um <xref:System.Windows.Controls.DockPanel> elemento definido na marcação.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Se você fosse enumerar os objetos lógicos que constituem o <xref:System.Windows.Controls.DockPanel> elemento no exemplo de marcação, encontraria a hierarquia de objetos lógicos ilustrada abaixo:  
  
 ![Diagrama de árvore](../../../../docs/framework/wpf/graphics-multimedia/media/tree1-wcp.gif "Tree1_wcp")  
Diagrama de árvore lógica  
  
 A árvore visual e a árvore lógica são sincronizadas com o conjunto atual de elementos do aplicativo, refletindo qualquer adição, exclusão ou modificação de elementos. No entanto, as árvores apresentam diferentes exibições do aplicativo. Diferentemente da árvore visual, a árvore lógica não expande um controle <xref:System.Windows.Controls.ContentPresenter> elemento. Isso significa que não há uma correspondência um para um direta entre uma árvore lógica e uma árvore visual para o mesmo conjunto de objetos. Na verdade, invocar o **LogicalTreeHelper** do objeto <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> método e o **VisualTreeHelper** do objeto <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> método usando o mesmo elemento como um parâmetro produz resultados diferentes .  
  
 Para obter mais informações sobre a árvore lógica, consulte [Árvores no WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Exibindo a árvore visual com XamlPad  
 A ferramenta do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], XamlPad, fornece uma opção para visualizar e explorar a árvore visual que corresponde ao conteúdo [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] definido atualmente. Clique no botão **Mostrar Árvore Visual** na barra de menus para exibir a árvore visual. A seguir, ilustra a expansão de conteúdo [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] em nós de árvore visual no painel **Gerenciador de Árvore Visual** do XamlPad:  
  
 ![Painel do Gerenciador de árvore visual no XamlPad](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview08.png "VisualLayerOverview08")  
Painel Gerenciador de Árvore Visual no XamlPad  
  
 Observe como o <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, e <xref:System.Windows.Controls.Button> cada controle exibe uma hierarquia de objetos visuais separada no **Gerenciador de árvore Visual** painel do XamlPad. Isso ocorre porque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controles têm um <xref:System.Windows.Controls.ControlTemplate> que contém a árvore visual desse controle. Quando você referencia um controle explicitamente, você referencia implicitamente sua hierarquia visual.  
  
### <a name="profiling-visual-performance"></a>Criação de perfil de desempenho Visual  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece um conjunto de ferramentas de criação de perfil de desempenho que permitem analisar o comportamento de tempo de execução do aplicativo e determinar os tipos de otimização de desempenho que você pode aplicar. A ferramenta Visual Profiler fornece uma exibição gráfica sofisticada de dados de desempenho, por meio do mapeamento diretamente para a árvore visual do aplicativo. Nessa tela, a seção **Uso de CPU** do Visual Profiler lhe dá um detalhamento preciso do uso de um objeto de serviços do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], assim como renderização e layout.  
  
 ![Visual Profiler display output](../../../../docs/framework/wpf/graphics-multimedia/media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Saída de exibição do Visual Profiler  
  
<a name="visual_rendering_behavior"></a>   
## <a name="visual-rendering-behavior"></a>Comportamento de renderização visual  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] introduz diversos recursos que afetam o comportamento de renderização de objetos visuais: gráficos de modo retido, gráficos vetoriais e gráficos independentes de dispositivo.  
  
### <a name="retained-mode-graphics"></a>Gráficos de modo retido  
 Uma das chaves para entender o papel do objeto Visual é entender a diferença entre sistemas gráficos de **modo imediato** e de **modo retido**. Um aplicativo Win32 padrão baseado em GDI ou GDI+ utiliza um sistema gráfico de modo imediato. Isso significa que o aplicativo é responsável por repintar a parte da área de cliente que for invalidada, devido a uma ação como um redimensionamento de janela ou a alteração da aparência visual de um objeto.  
  
 ![Diagrama de sequência de renderização Win32](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview01.png "VisualLayerOverview01")  
Diagrama de sequência de renderização Win32  
  
 Por outro lado, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa um sistema de modo retido. Isso significa que os objetos de aplicativo que têm uma aparência visual definem um conjunto de dados de desenho serializados. A partir do momento em que os dados de desenho são definidos, o sistema torna-se responsável por responder a todas as solicitações de repintura para renderizar os objetos de aplicativo. Mesmo em tempo de execução, você pode modificar ou criar objetos de aplicativo e, ainda assim, contar com o sistema para responder às solicitações e pintura. O poder existente em um sistema gráfico de modo retido é que informações de desenho sempre são persistentes em um estado serializado pelo aplicativo, mas a responsabilidade pela renderização é deixada para o sistema. O diagrama a seguir mostra como o aplicativo depende do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para responder a solicitações de pintura.  
  
 ![Diagrama de sequência de renderização do WPF](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview02.png "VisualLayerOverview02")  
Diagrama de sequência de renderização do WPF  
  
#### <a name="intelligent-redrawing"></a>Redesenho inteligente  
 Um dos maiores benefícios de usar gráficos de modo retido é que o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode otimizar de forma eficiente o que precisa ser redesenhado no aplicativo. Mesmo que você tenha uma cena complexa com diversos níveis de opacidade, você geralmente não precisa escrever código com propósito especial para otimizar o redesenho. Compare isso com programação em Win32, na qual você pode despender uma grande quantidade de esforço para otimizar seu aplicativo por meio da minimização da quantidade de redesenho na região de atualização. Consulte [Redesenho na região de atualização](/windows/desktop/gdi/redrawing-in-the-update-region) para obter um exemplo do tipo de complexidade envolvida na otimização de redesenho em aplicativos Win32.  
  
### <a name="vector-graphics"></a>Gráficos vetoriais  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa **gráficos vetoriais** como seu formato de dados de renderização. Gráficos vetoriais – que incluem SVG (Scalable Vector Graphics), metarquivos do Windows (.wmf) e fontes TrueType – armazenam dados de renderização e transmitem-nos como uma lista de instruções que descrevem como recriar uma imagem usando primitivos gráficos. Por exemplo, fontes TrueType são fontes geométricas que descrevem um conjunto de linhas, curvas e comandos, em vez de uma matriz de pixels. Um dos principais benefícios dos gráficos vetoriais é a capacidade de dimensionar para qualquer tamanho e resolução.  
  
 Diferente de gráficos vetoriais, gráficos de bitmap armazenam dados de renderização como uma representação pixel por pixel de uma imagem, pré-renderizada para uma determinada resolução. Uma das principais diferenças entre formatos de gráficos de bitmap e vetoriais é a fidelidade à imagem original. Por exemplo, quando o tamanho de uma imagem de origem é modificado, sistemas de gráficos de bitmap alongam a imagem, ao passo que sistemas de gráficos vetoriais redimensionam a imagem, preservando sua fidelidade.  
  
 A ilustração a seguir mostra uma imagem original que foi redimensionada em 300%. Observe as distorções que aparecem quando a imagem original é alongada como uma imagem de bitmap em vez de uma imagem de gráficos vetoriais.  
  
 ![Diferenças entre grafos rasterizados e vetoriais](../../../../docs/framework/wpf/graphics-multimedia/media/vectorgraphics01.png "VectorGraphics01")  
Diferenças entre grafos rasterizados e vetoriais  
  
 A marcação a seguir mostra dois <xref:System.Windows.Shapes.Path> elementos definidos. O segundo elemento utiliza um <xref:System.Windows.Media.ScaleTransform> para redimensionar as instruções de desenho do primeiro elemento em 300%. Observe que as instruções de desenho no <xref:System.Windows.Shapes.Path> elementos permanecem inalterados.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>Sobre elementos gráficos independentes de resolução e de dispositivo  
 Há dois fatores de sistema que determinam o tamanho do texto e de elementos gráficos na sua tela: resolução e DPI. A resolução descreve o número de pixels que aparecem na tela. Conforme a resolução aumenta, os pixels ficam menores, fazendo com que elementos gráficos e texto apareçam menores. Um elemento gráfico exibido em um monitor definido para 1024 x 768 aparecerá bem menor quando a resolução for alterada para 1600 x 1200.  
  
 A configuração de sistema, DPI, descreve o tamanho de uma polegada de tela em pixels. A maioria dos sistemas [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] têm 96 DPI, o que significa que uma polegada de tela tem 96 pixels. Aumentar a configuração de DPI torna a polegada de tela maior; diminuir o DPI torna a polegada de tela menor. Isso significa que uma polegada de tela não é do mesmo tamanho que uma polegada real; na maioria dos sistemas, provavelmente não é. Conforme você aumenta o DPI, texto e gráficos com reconhecimento de DPI se tornam maiores porque você aumentou o tamanho da polegada de tela. Aumentar o DPI pode tornar o texto mais fácil de ler, especialmente em resoluções altas.  
  
 Nem todos os aplicativos realizam reconhecimento de DPI: alguns utilizam pixels de hardware como a unidade principal de medida; alterar o DPI do sistema não tem nenhum efeito nesses aplicativos. Muitos outros aplicativos usam unidades com reconhecimento de DPI para descrever os tamanhos da fonte, mas utilizam pixels para descrever todo o resto. Tornar o DPI muito grande ou muito pequeno pode causar problemas de layout para esses aplicativos; o motivo disso é que o texto do aplicativo é dimensionado de acordo com a configuração de DPI do sistema, enquanto a interface do usuário não. Esse problema foi eliminado de aplicativos desenvolvidos usando o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte ao dimensionamento automático usando o pixel independente de dispositivo como sua principal unidade de medida, em vez de pixels de hardware; texto e elementos gráficos são redimensionados adequadamente sem nenhum trabalho extra do desenvolvedor do aplicativo. A ilustração a seguir mostra um exemplo de como texto e elementos gráficos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparecem em diferentes configurações de DPI.  
  
 ![Elementos gráficos e texto em diferentes configurações de DPI](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Elementos gráficos e texto em diferentes configurações de DPI  
  
<a name="visualtreehelper_class"></a>   
## <a name="visualtreehelper-class"></a>Classe VisualTreeHelper  
 O <xref:System.Windows.Media.VisualTreeHelper> é uma classe auxiliar estática que fornece funcionalidade de baixo nível para programação no nível do objeto visual, que é útil em cenários muito específicos, como desenvolvimento de controles personalizados de alto desempenho. Na maioria dos casos, o nível mais alto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] estrutura de objetos, como <xref:System.Windows.Controls.Canvas> e <xref:System.Windows.Controls.TextBlock>, oferecem maior flexibilidade e facilidade de uso.  
  
### <a name="hit-testing"></a>Testes de clique  
 O <xref:System.Windows.Media.VisualTreeHelper> classe fornece métodos para teste de clique em objetos visuais quando o suporte de teste de clique de padrão não atender às suas necessidades. Você pode usar o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> métodos de <xref:System.Windows.Media.VisualTreeHelper> classe para determinar se um valor de coordenada de geometria ou de ponto está dentro dos limites de um determinado objeto, como um controle ou elemento gráfico. Por exemplo, você pode usar o teste de clique para determinar se um clique do mouse dentro do retângulo delimitador de um objeto está dentro da geometria de um círculo. Você também pode optar por substituir a implementação padrão de teste de clique para executar seus próprios cálculos de teste de clique personalizados.  
  
 Para obter mais informações sobre teste de clique, consulte [Teste de clique na camada visual](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Enumerar a árvore Visual  
 O <xref:System.Windows.Media.VisualTreeHelper> classe fornece funcionalidade para enumerar os membros de uma árvore visual. Para recuperar um pai, chame o <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> método. Para recuperar um filho ou descendente direto de um objeto visual, chame o <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> método. Esse método retornará um filho <xref:System.Windows.Media.Visual> do pai no índice especificado.  
  
 O exemplo a seguir mostra como enumerar todos os descendentes de um objeto visual, que é uma técnica que talvez você queira usar caso esteja interessado em serializar a informação de renderização de uma hierarquia de objetos visuais.  
  
 [!code-csharp[VisualsOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 Na maioria dos casos, a árvore lógica é uma representação mais útil dos elementos em um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Embora você não modifique a árvore lógica diretamente, essa exibição do aplicativo é útil para entender a herança de propriedades e o roteamento de eventos. Diferentemente da árvore visual, a árvore lógica pode representar objetos de dados não visuais, tais como <xref:System.Windows.Documents.ListItem>. Para obter mais informações sobre a árvore lógica, consulte [Árvores no WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
 O <xref:System.Windows.Media.VisualTreeHelper> classe fornece métodos para retornar o retângulo delimitador de objetos visuais. Você pode retornar o retângulo delimitador de um objeto visual chamando <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>. Você pode retornar o retângulo delimitador de todos os descendentes de um objeto visual, incluindo o próprio objeto visual chamando <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>. O código a seguir mostra como você calcularia o retângulo delimitador de um objeto visual e todos os seus descendentes.  
  
 [!code-csharp[VisualsOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [Elementos gráficos e geração de imagens 2D](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Teste de clique na camada visual](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
- [Usando objetos DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
- [Tutorial: Hospedando objetos visuais em um aplicativo Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
- [Otimizando o desempenho do aplicativo WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)
