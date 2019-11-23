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
ms.openlocfilehash: 09f5f026ed320aaa253d8cdf6e0b271235aff604
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004172"
---
# <a name="wpf-graphics-rendering-overview"></a>Visão geral de renderização de gráficos do WPF
Este tópico fornece uma visão geral da camada visual do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ele se concentra na função da classe <xref:System.Windows.Media.Visual> para suporte de renderização no modelo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="role_of_visual_object"></a>   
## <a name="role-of-the-visual-object"></a>Função do objeto visual  
 A classe <xref:System.Windows.Media.Visual> é a abstração básica da qual cada objeto de <xref:System.Windows.FrameworkElement> deriva. Ela também serve como o ponto de entrada para escrever novos controles em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e, de muitas formas, pode ser pensada como o HWND (identificador de janela) no modelo de aplicativo Win32.  
  
 O objeto <xref:System.Windows.Media.Visual> é um objeto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] principal, cuja função principal é fornecer suporte à renderização. Controles de interface do usuário, como <xref:System.Windows.Controls.Button> e <xref:System.Windows.Controls.TextBox>, derivam da classe <xref:System.Windows.Media.Visual> e usam-os para persistir seus dados de renderização. O objeto <xref:System.Windows.Media.Visual> fornece suporte para:  
  
- Exibição de saída: renderização do conteúdo de desenho persistentes e serializado de um visual.  
  
- Transformações: executando transformações em um Visual.  
  
- Recorte: dar suporte à área de recorte para um visual.  
  
- Teste de clique: determinar se uma coordenada ou geometria está contida dentro dos limites de um visual.  
  
- Cálculos de caixa delimitadora: determinar o retângulo delimitador de um visual.  
  
 No entanto, o objeto <xref:System.Windows.Media.Visual> não inclui suporte para recursos de não renderização, como:  
  
- Manipulação de eventos  
  
- {1&gt;Layout&lt;1}  
  
- Estilos  
  
- Associação de dados  
  
- Globalização  
  
 <xref:System.Windows.Media.Visual> é exposta como uma classe abstrata pública da qual as classes filhas devem ser derivadas. A ilustração a seguir mostra a hierarquia dos objetos visuais que são expostos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 ![Diagrama de classes derivadas do objeto visual](./media/wpf-graphics-rendering-overview/classes-derived-visual-object.png)    
  
### <a name="drawingvisual-class"></a>Classe DrawingVisual  
 A <xref:System.Windows.Media.DrawingVisual> é uma classe leve de desenho que é usada para renderizar formas, imagens ou texto. Essa classe é considerada leve porque não fornece layout ou manipulação de eventos, o que melhora o desempenho de runtime. Por esse motivo, desenhos são ideais para planos de fundo e clip-art. O <xref:System.Windows.Media.DrawingVisual> pode ser usado para criar um objeto visual personalizado. Para obter mais informações, consulte [Usando objetos DrawingVisual](using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Classe Viewport3DVisual  
 O <xref:System.Windows.Media.Media3D.Viewport3DVisual> fornece uma ponte entre <xref:System.Windows.Media.Visual> 2D e objetos de <xref:System.Windows.Media.Media3D.Visual3D>. A classe <xref:System.Windows.Media.Media3D.Visual3D> é a classe base para todos os elementos visuais 3D. O <xref:System.Windows.Media.Media3D.Viewport3DVisual> requer que você defina um valor de <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> e um valor de <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A>. A câmera permite que você exiba a cena. O visor estabelece o local para o qual a projeção é mapeada na superfície 2D. Para obter mais informações sobre 3D em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>Classe ContainerVisual  
 A classe <xref:System.Windows.Media.ContainerVisual> é usada como um contêiner para uma coleção de objetos <xref:System.Windows.Media.Visual>. A classe <xref:System.Windows.Media.DrawingVisual> deriva da classe <xref:System.Windows.Media.ContainerVisual>, permitindo que ela contenha uma coleção de objetos visuais.  
  
### <a name="drawing-content-in-visual-objects"></a>Desenhar conteúdo em objetos visuais  
 Um objeto de <xref:System.Windows.Media.Visual> armazena seus dados de renderização como uma **lista de instruções de gráficos de vetor**. Cada item na lista de instruções representa um conjunto de baixo nível de dados gráficos e recursos associados em um formato serializado. Há quatro tipos diferentes de dados de renderização que podem conter conteúdo de desenho.  
  
|Tipo de conteúdo de desenho|Descrição|  
|--------------------------|-----------------|  
|Gráficos vetoriais|Representa dados de gráficos vetoriais e quaisquer informações <xref:System.Windows.Media.Brush> e <xref:System.Windows.Media.Pen> associadas.|  
|Imagem|Representa uma imagem em uma região definida por um <xref:System.Windows.Rect>.|  
|Glifo|Representa um desenho que renderiza um <xref:System.Windows.Media.GlyphRun>, que é uma sequência de glifos de um recurso de fonte especificado. Este é o modo pelo qual o texto é representado.|  
|Vídeo|Representa um desenho que renderiza vídeo.|  
  
 O <xref:System.Windows.Media.DrawingContext> permite popular um <xref:System.Windows.Media.Visual> com conteúdo visual. Quando você usa os comandos Draw de um objeto <xref:System.Windows.Media.DrawingContext>, na verdade você está armazenando um conjunto de dados de renderização que serão usados posteriormente pelo sistema de gráficos; Você não está desenhando na tela em tempo real.  
  
 Quando você cria um controle de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], como um <xref:System.Windows.Controls.Button>, o controle gera implicitamente dados de renderização para o próprio desenho. Por exemplo, definir a propriedade <xref:System.Windows.Controls.ContentControl.Content%2A> da <xref:System.Windows.Controls.Button> faz com que o controle armazene uma representação de renderização de um glifo.  
  
 Uma <xref:System.Windows.Media.Visual> descreve seu conteúdo como um ou mais objetos de <xref:System.Windows.Media.Drawing> contidos em um <xref:System.Windows.Media.DrawingGroup>. Uma <xref:System.Windows.Media.DrawingGroup> também descreve máscaras de opacidade, transformações, efeitos de bitmap e outras operações que são aplicadas ao seu conteúdo. <xref:System.Windows.Media.DrawingGroup> operações são aplicadas na seguinte ordem quando o conteúdo é renderizado: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>e, em seguida, <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 A ilustração a seguir mostra a ordem na qual <xref:System.Windows.Media.DrawingGroup> operações são aplicadas durante a sequência de renderização.  
  
 ![Ordem das operações do drawinggroup](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Ordem das operações do DrawingGroup  
  
 Para obter mais informações, consulte a [Visão geral de objetos de desenho](drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Conteúdo de desenho na camada visual  
 Você nunca instancia diretamente um <xref:System.Windows.Media.DrawingContext>; no entanto, você pode adquirir um contexto de desenho de determinados métodos, como <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> e <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>. O exemplo a seguir recupera um <xref:System.Windows.Media.DrawingContext> de um <xref:System.Windows.Media.DrawingVisual> e o usa para desenhar um retângulo.  
  
 [!code-csharp[drawingvisualsample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Enumerar conteúdo de desenho na camada visual  
 Além de seus outros usos, <xref:System.Windows.Media.Drawing> objetos também fornecem um modelo de objeto para enumerar o conteúdo de um <xref:System.Windows.Media.Visual>.  
  
> [!NOTE]
> Ao enumerar o conteúdo do Visual, você está recuperando <xref:System.Windows.Media.Drawing> objetos e não a representação subjacente da lista de instruções renderizar dados como um gráfico vetorial.  
  
 O exemplo a seguir usa o método <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> para recuperar o valor de <xref:System.Windows.Media.DrawingGroup> de um <xref:System.Windows.Media.Visual> e enumerá-lo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>   
## <a name="how-visual-objects-are-used-to-build-controls"></a>Como objetos visuais são usados para compilar controles  
 Muitos dos objetos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são compostos de outros objetos visuais, o que significa que eles podem conter diversas hierarquias de objetos descendentes. Muitos dos elementos da interface do usuário no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tais como controles, são compostos de múltiplos objetos visuais que representam diferentes tipos de elementos de renderização. Por exemplo, o controle de <xref:System.Windows.Controls.Button> pode conter vários outros objetos, incluindo <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, <xref:System.Windows.Controls.ContentPresenter>e <xref:System.Windows.Controls.TextBlock>.  
  
 O código a seguir mostra um controle <xref:System.Windows.Controls.Button> definido na marcação.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Se você fosse enumerar os objetos visuais que compõem o controle de <xref:System.Windows.Controls.Button> padrão, encontraria a hierarquia dos objetos visuais ilustrada abaixo:  
  
 ![Diagrama de hierarquia de árvore visual](./media/wpf-graphics-rendering-overview/visual-object-diagram.gif) 
  
 O controle <xref:System.Windows.Controls.Button> contém um elemento <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, que, por sua vez, contém um elemento <xref:System.Windows.Controls.ContentPresenter>. O elemento <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> é responsável por desenhar uma borda e um plano de fundo para a <xref:System.Windows.Controls.Button>. O elemento <xref:System.Windows.Controls.ContentPresenter> é responsável por exibir o conteúdo da <xref:System.Windows.Controls.Button>. Nesse caso, como você está exibindo texto, o elemento <xref:System.Windows.Controls.ContentPresenter> contém um elemento <xref:System.Windows.Controls.TextBlock>. O fato de que o controle de <xref:System.Windows.Controls.Button> usa uma <xref:System.Windows.Controls.ContentPresenter> significa que o conteúdo pode ser representado por outros elementos, como um <xref:System.Windows.Controls.Image> ou uma geometria, como um <xref:System.Windows.Media.EllipseGeometry>.  
  
### <a name="control-templates"></a>Modelos de controle  
 A chave para a expansão de um controle em uma hierarquia de controles é a <xref:System.Windows.Controls.ControlTemplate>. Um modelo de controle especifica a hierarquia visual de um controle. Quando você referencia um controle explicitamente, você referencia implicitamente sua hierarquia visual. Você pode substituir os valores padrão de um modelo de controle para criar uma aparência visual personalizada para um controle. Por exemplo, você pode modificar o valor de cor do plano de fundo do controle de <xref:System.Windows.Controls.Button> para que ele use um valor de cor de gradiente linear em vez de um valor de cor sólido. Para obter mais informações, consulte [Estilos e modelos de botão](../controls/button-styles-and-templates.md).  
  
 Um elemento de interface do usuário, como um controle de <xref:System.Windows.Controls.Button>, contém várias listas de instruções de gráficos vetoriais que descrevem toda a definição de renderização de um controle. O código a seguir mostra um controle <xref:System.Windows.Controls.Button> definido na marcação.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Se você fosse enumerar os objetos visuais e as listas de instruções de gráficos vetoriais que compõem o controle <xref:System.Windows.Controls.Button>, você encontraria a hierarquia de objetos ilustrada abaixo:  
  
 ![Diagrama de árvore visual e dados de renderização](./media/wpf-graphics-rendering-overview/visual-tree-rendering-data.png)  
  
 O controle <xref:System.Windows.Controls.Button> contém um elemento <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, que, por sua vez, contém um elemento <xref:System.Windows.Controls.ContentPresenter>. O elemento <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> é responsável por desenhar todos os elementos gráficos discretos que compõem a borda e o plano de fundo de um botão. O elemento <xref:System.Windows.Controls.ContentPresenter> é responsável por exibir o conteúdo da <xref:System.Windows.Controls.Button>. Nesse caso, como você está exibindo uma imagem, o elemento <xref:System.Windows.Controls.ContentPresenter> contém um elemento <xref:System.Windows.Controls.Image>.  
  
 Há diversos pontos a observar sobre a hierarquia de objetos visuais e listas de instruções de gráficos vetoriais:  
  
- A ordem na hierarquia representa a ordem de renderização das informações de desenho. Do elemento visual raiz, a ordem de renderização passa pelos elementos filho da esquerda para a direita, de cima para baixo. Se um determinado elemento tem elementos visuais filho, a ordem de renderização passa por eles antes de passar pelos irmãos desse elemento.  
  
- Elementos de nó não folha na hierarquia, como <xref:System.Windows.Controls.ContentPresenter>, são usados para conter elementos filho — eles não contêm listas de instruções.  
  
- Se um elemento visual contém uma lista de instruções de gráfico vetorial e filhos visuais, a lista de instruções no elemento visual pai é renderizada antes de desenhos em qualquer um dos objetos filho visuais.  
  
- Os itens na lista de instruções de gráficos vetoriais são renderizados da esquerda para a direita.  
  
<a name="visual_tree"></a>   
## <a name="visual-tree"></a>Árvore visual  
 A árvore visual contém todos os elementos visuais usados na interface do usuário de um aplicativo. Já que um elemento visual contém informações de desenho persistentes, você pode pensar na árvore visual como um grafo de cena, contendo todas as informações de renderização necessárias para compor a saída para o dispositivo de vídeo. Esta árvore é o acúmulo de todos os elementos visuais criados diretamente pelo aplicativo, seja no código ou em marcação. A árvore visual também contém todos os elementos visuais criados pela expansão de modelo de elementos tais como controles e objetos de dados.  
  
 O código a seguir mostra um elemento <xref:System.Windows.Controls.StackPanel> definido na marcação.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Se você fosse enumerar os objetos visuais que compõem o elemento <xref:System.Windows.Controls.StackPanel> no exemplo de marcação, você encontraria a hierarquia de objetos visuais ilustrada abaixo:  
  
 ![Diagrama de hierarquia de árvore visual](./media/wpf-graphics-rendering-overview/visual-tree-hierarchy.gif)  
  
### <a name="rendering-order"></a>Ordem de renderização  
 A árvore visual determina a ordem de renderização de objetos visuais e de desenho do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. A ordem de passagem inicia com o visual raiz, que é o nó mais alto na árvore visual. Em seguida, passa-se pelos filhos do visual raiz, da esquerda para a direita. Se um visual tiver filhos, a passagem por eles ocorrerá primeiro do que a passagem pelos irmãos do visual. Isso significa que o conteúdo de um visual filho é renderizado na frente do conteúdo do próprio visual.  
  
 ![Diagrama da ordem de renderização da árvore visual](./media/wpf-graphics-rendering-overview/visual-tree-rendering-order.gif) 
  
### <a name="root-visual"></a>Visual raiz  
 O **visual raiz** é o elemento mais alto em uma hierarquia de árvore visual. Na maioria dos aplicativos, a classe base do Visual raiz é <xref:System.Windows.Window> ou <xref:System.Windows.Navigation.NavigationWindow>. No entanto, se você estivesse hospedando objetos visuais em um aplicativo Win32, o visual raiz seria o visual mais alto que você estivesse hospedando na janela Win32. Para obter mais informações, consulte [Tutorial: hospedando objetos visuais em um aplicativo Win32](tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Relacionamento com a árvore lógica  
 A árvore lógica no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] representa os elementos de um aplicativo em tempo de execução. Embora você não manipule esta árvore diretamente, essa exibição do aplicativo é útil para entender a herança de propriedades e o roteamento de eventos. Ao contrário da árvore visual, a árvore lógica pode representar objetos de dados não visuais, como <xref:System.Windows.Documents.ListItem>. Em muitos casos, a árvore lógica mapeia de modo muito próximo às definições de marcação de um aplicativo. O código a seguir mostra um elemento <xref:System.Windows.Controls.DockPanel> definido na marcação.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Se você fosse enumerar os objetos lógicos que compõem o elemento <xref:System.Windows.Controls.DockPanel> no exemplo de marcação, você encontraria a hierarquia de objetos lógicos ilustrada abaixo:  
  
 ![Diagrama de árvore](./media/tree1-wcp.gif "Tree1_wcp")  
Diagrama de árvore lógica  
  
 A árvore visual e a árvore lógica são sincronizadas com o conjunto atual de elementos do aplicativo, refletindo qualquer adição, exclusão ou modificação de elementos. No entanto, as árvores apresentam diferentes exibições do aplicativo. Diferentemente da árvore visual, a árvore lógica não expande o elemento de <xref:System.Windows.Controls.ContentPresenter> de um controle. Isso significa que não há uma correspondência um para um direta entre uma árvore lógica e uma árvore visual para o mesmo conjunto de objetos. Na verdade, invocar o método <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> do objeto **LogicalTreeHelper** e o método <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> do objeto **VisualTreeHelper** usando o mesmo elemento que um parâmetro produz resultados diferentes.  
  
 Para obter mais informações sobre a árvore lógica, consulte [Árvores no WPF](../advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Exibindo a árvore visual com XamlPad  
 A ferramenta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], XamlPad, fornece uma opção para exibir e explorar a árvore visual que corresponde ao conteúdo XAML definido no momento. Clique no botão **Mostrar Árvore Visual** na barra de menus para exibir a árvore visual. O seguinte ilustra a expansão do conteúdo XAML em nós de árvore visual no painel do **Visual Tree Explorer** do XamlPad:  
  
 ![Painel Gerenciador de Árvore Visual no XamlPad](./media/wpf-graphics-rendering-overview/visual-tree-explorer.png)  

 Observe como os controles <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>e <xref:System.Windows.Controls.Button> exibem uma hierarquia de objetos visuais separada no painel do **Visual Tree Explorer** do XamlPad. Isso ocorre porque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controles têm uma <xref:System.Windows.Controls.ControlTemplate> que contém a árvore visual desse controle. Quando você referencia um controle explicitamente, você referencia implicitamente sua hierarquia visual.  
  
### <a name="profiling-visual-performance"></a>Criação de perfil de desempenho Visual  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece um pacote de ferramentas de criação de perfil de desempenho que permitem analisar o comportamento de tempo de execução do aplicativo e determinar os tipos de otimização de desempenho que você pode aplicar. A ferramenta Visual Profiler fornece uma exibição gráfica sofisticada de dados de desempenho, por meio do mapeamento diretamente para a árvore visual do aplicativo. Nessa tela, a seção **Uso de CPU** do Visual Profiler lhe dá um detalhamento preciso do uso de um objeto de serviços do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], assim como renderização e layout.  
  
 (./media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04") de ![saída de exibição do Visual Profiler]  
Saída de exibição do Visual Profiler  
  
<a name="visual_rendering_behavior"></a>   
## <a name="visual-rendering-behavior"></a>Comportamento de renderização visual  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] introduz diversos recursos que afetam o comportamento de renderização de objetos visuais: gráficos de modo retido, gráficos vetoriais e gráficos independentes de dispositivo.  
  
### <a name="retained-mode-graphics"></a>Gráficos de modo retido  
 Uma das chaves para entender o papel do objeto Visual é entender a diferença entre sistemas gráficos de **modo imediato** e de **modo retido**. Um aplicativo Win32 padrão baseado em GDI ou GDI+ utiliza um sistema gráfico de modo imediato. Isso significa que o aplicativo é responsável por repintar a parte da área de cliente que for invalidada, devido a uma ação como um redimensionamento de janela ou a alteração da aparência visual de um objeto.  
  
 ![Diagrama de sequência de renderização Win32](./media/wpf-graphics-rendering-overview/win32-rendering-squence.png)  
  
 Por outro lado, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa um sistema de modo retido. Isso significa que os objetos de aplicativo que têm uma aparência visual definem um conjunto de dados de desenho serializados. A partir do momento em que os dados de desenho são definidos, o sistema torna-se responsável por responder a todas as solicitações de repintura para renderizar os objetos de aplicativo. Mesmo em tempo de execução, você pode modificar ou criar objetos de aplicativo e, ainda assim, contar com o sistema para responder às solicitações e pintura. O poder existente em um sistema gráfico de modo retido é que informações de desenho sempre são persistentes em um estado serializado pelo aplicativo, mas a responsabilidade pela renderização é deixada para o sistema. O diagrama a seguir mostra como o aplicativo depende do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para responder a solicitações de pintura.  
  
 ![Diagrama de sequência de renderização do WPF](./media/wpf-graphics-rendering-overview/wpf-rendering-sequence.png)  

#### <a name="intelligent-redrawing"></a>Redesenho inteligente  
 Um dos maiores benefícios de usar gráficos de modo retido é que o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode otimizar de forma eficiente o que precisa ser redesenhado no aplicativo. Mesmo que você tenha uma cena complexa com diversos níveis de opacidade, você geralmente não precisa escrever código com propósito especial para otimizar o redesenho. Compare isso com programação em Win32, na qual você pode despender uma grande quantidade de esforço para otimizar seu aplicativo por meio da minimização da quantidade de redesenho na região de atualização. Consulte [Redesenho na região de atualização](/windows/desktop/gdi/redrawing-in-the-update-region) para obter um exemplo do tipo de complexidade envolvida na otimização de redesenho em aplicativos Win32.  
  
### <a name="vector-graphics"></a>Gráficos vetoriais  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa **gráficos vetoriais** como seu formato de dados de renderização. Gráficos vetoriais – que incluem SVG (Scalable Vector Graphics), metarquivos do Windows (.wmf) e fontes TrueType – armazenam dados de renderização e transmitem-nos como uma lista de instruções que descrevem como recriar uma imagem usando primitivos gráficos. Por exemplo, fontes TrueType são fontes geométricas que descrevem um conjunto de linhas, curvas e comandos, em vez de uma matriz de pixels. Um dos principais benefícios dos gráficos vetoriais é a capacidade de dimensionar para qualquer tamanho e resolução.  
  
 Diferente de gráficos vetoriais, gráficos de bitmap armazenam dados de renderização como uma representação pixel por pixel de uma imagem, pré-renderizada para uma determinada resolução. Uma das principais diferenças entre formatos de gráficos de bitmap e vetoriais é a fidelidade à imagem original. Por exemplo, quando o tamanho de uma imagem de origem é modificado, sistemas de gráficos de bitmap alongam a imagem, ao passo que sistemas de gráficos vetoriais redimensionam a imagem, preservando sua fidelidade.  
  
 A ilustração a seguir mostra uma imagem original que foi redimensionada em 300%. Observe as distorções que aparecem quando a imagem original é alongada como uma imagem de bitmap em vez de uma imagem de gráficos vetoriais.  
  
 ![Diferenças entre grafos rasterizados e vetoriais](./media/wpf-graphics-rendering-overview/raster-vector-differences.png)  
  
 A marcação a seguir mostra dois elementos <xref:System.Windows.Shapes.Path> definidos. O segundo elemento usa um <xref:System.Windows.Media.ScaleTransform> para redimensionar as instruções de desenho do primeiro elemento em 300%. Observe que as instruções de desenho no <xref:System.Windows.Shapes.Path> elementos permanecem inalteradas.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>Sobre elementos gráficos independentes de resolução e de dispositivo  
 Há dois fatores de sistema que determinam o tamanho do texto e de elementos gráficos na sua tela: resolução e DPI. A resolução descreve o número de pixels que aparecem na tela. Conforme a resolução aumenta, os pixels ficam menores, fazendo com que elementos gráficos e texto apareçam menores. Um elemento gráfico exibido em um monitor definido para 1024 x 768 aparecerá bem menor quando a resolução for alterada para 1600 x 1200.  
  
 A configuração de sistema, DPI, descreve o tamanho de uma polegada de tela em pixels. A maioria dos sistemas Windows tem um DPI de 96, o que significa que uma polegada de tela é de 96 pixels. Aumentar a configuração de DPI torna a polegada de tela maior; diminuir o DPI torna a polegada de tela menor. Isso significa que uma polegada de tela não é do mesmo tamanho que uma polegada real; na maioria dos sistemas, provavelmente não é. Conforme você aumenta o DPI, texto e gráficos com reconhecimento de DPI se tornam maiores porque você aumentou o tamanho da polegada de tela. Aumentar o DPI pode tornar o texto mais fácil de ler, especialmente em resoluções altas.  
  
 Nem todos os aplicativos realizam reconhecimento de DPI: alguns utilizam pixels de hardware como a unidade principal de medida; alterar o DPI do sistema não tem nenhum efeito nesses aplicativos. Muitos outros aplicativos usam unidades com reconhecimento de DPI para descrever os tamanhos da fonte, mas utilizam pixels para descrever todo o resto. Tornar o DPI muito grande ou muito pequeno pode causar problemas de layout para esses aplicativos; o motivo disso é que o texto do aplicativo é dimensionado de acordo com a configuração de DPI do sistema, enquanto a interface do usuário não. Esse problema foi eliminado de aplicativos desenvolvidos usando o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte ao dimensionamento automático usando o pixel independente de dispositivo como sua principal unidade de medida, em vez de pixels de hardware; texto e elementos gráficos são redimensionados adequadamente sem nenhum trabalho extra do desenvolvedor do aplicativo. A ilustração a seguir mostra um exemplo de como texto e elementos gráficos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparecem em diferentes configurações de DPI.  
  
 ![Gráficos e texto em diferentes configurações de DPI](./media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Elementos gráficos e texto em diferentes configurações de DPI  
  
<a name="visualtreehelper_class"></a>   
## <a name="visualtreehelper-class"></a>Classe VisualTreeHelper  
 A classe <xref:System.Windows.Media.VisualTreeHelper> é uma classe auxiliar estática que fornece funcionalidade de baixo nível para programação no nível de objeto visual, que é útil em cenários muito específicos, como o desenvolvimento de controles personalizados de alto desempenho. Na maioria dos casos, os objetos de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Framework de nível superior, como <xref:System.Windows.Controls.Canvas> e <xref:System.Windows.Controls.TextBlock>, oferecem maior flexibilidade e facilidade de uso.  
  
### <a name="hit-testing"></a>Testes de clique  
 A classe <xref:System.Windows.Media.VisualTreeHelper> fornece métodos para teste de clique em objetos visuais quando o suporte de teste de clique padrão não atende às suas necessidades. Você pode usar os métodos de <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> na classe <xref:System.Windows.Media.VisualTreeHelper> para determinar se um valor de geometria ou coordenada de ponto está dentro do limite de um determinado objeto, como um controle ou elemento gráfico. Por exemplo, você pode usar o teste de clique para determinar se um clique do mouse dentro do retângulo delimitador de um objeto está dentro da geometria de um círculo. Você também pode optar por substituir a implementação padrão de teste de clique para executar seus próprios cálculos de teste de clique personalizados.  
  
 Para obter mais informações sobre teste de clique, consulte [Teste de clique na camada visual](hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Enumerar a árvore Visual  
 A classe <xref:System.Windows.Media.VisualTreeHelper> fornece funcionalidade para enumerar os membros de uma árvore visual. Para recuperar um pai, chame o método <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A>. Para recuperar um filho ou um descendente direto de um objeto visual, chame o método <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A>. Esse método retorna um <xref:System.Windows.Media.Visual> filho do pai no índice especificado.  
  
 O exemplo a seguir mostra como enumerar todos os descendentes de um objeto visual, que é uma técnica que talvez você queira usar caso esteja interessado em serializar a informação de renderização de uma hierarquia de objetos visuais.  
  
 [!code-csharp[VisualsOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 Na maioria dos casos, a árvore lógica é uma representação mais útil dos elementos em um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Embora você não modifique a árvore lógica diretamente, essa exibição do aplicativo é útil para entender a herança de propriedades e o roteamento de eventos. Ao contrário da árvore visual, a árvore lógica pode representar objetos de dados não visuais, como <xref:System.Windows.Documents.ListItem>. Para obter mais informações sobre a árvore lógica, consulte [Árvores no WPF](../advanced/trees-in-wpf.md).  
  
 A classe <xref:System.Windows.Media.VisualTreeHelper> fornece métodos para retornar o retângulo delimitador de objetos visuais. Você pode retornar o retângulo delimitador de um objeto visual chamando <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>. Você pode retornar o retângulo delimitador de todos os descendentes de um objeto visual, incluindo o próprio objeto visual, chamando <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>. O código a seguir mostra como você calcularia o retângulo delimitador de um objeto visual e todos os seus descendentes.  
  
 [!code-csharp[VisualsOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Teste de clique na camada visual](hit-testing-in-the-visual-layer.md)
- [Usando objetos DrawingVisual](using-drawingvisual-objects.md)
- [Tutorial: hospedando objetos visuais em um aplicativo Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
- [Otimizando o desempenho do aplicativo WPF](../advanced/optimizing-wpf-application-performance.md)
