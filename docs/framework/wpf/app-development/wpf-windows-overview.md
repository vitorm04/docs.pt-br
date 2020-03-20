---
title: Visão geral do Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
ms.openlocfilehash: b06afb56f43a874815cf9f679f1f7fefbdfd4565
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145534"
---
# <a name="wpf-windows-overview"></a>Visão geral do WPF do Windows
Os usuários interagem com aplicativos autônomos da Windows Presentation Foundation (WPF) através do windows. O objetivo principal de uma janela é hospedar conteúdo que visualiza dados e permite aos usuários interagir com os dados. Aplicativos WPF autônomos fornecem suas próprias janelas usando a <xref:System.Windows.Window> classe. Este tópico <xref:System.Windows.Window> introduz antes de cobrir os fundamentos da criação e gerenciamento de janelas em aplicativos autônomos.  
  
> [!NOTE]
> Os aplicativos WPF hospedados no navegador, incluindo xbaps (xbaps) e páginas soltas, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] não fornecem suas próprias janelas. Em vez disso, eles estão hospedados em janelas fornecidas pelo Windows Internet Explorer. Consulte [a visão geral dos aplicativos do navegador WPF XAML](wpf-xaml-browser-applications-overview.md).  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a>A classe Window  
 A figura a seguir ilustra as partes constituintes de uma janela:  
  
 ![Captura de tela que mostra elementos da janela.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Uma janela é dividida em duas áreas: a área de não cliente e a área de cliente.  
  
 A *área não-cliente* de uma janela é implementada pelo WPF e inclui as partes de uma janela que são comuns à maioria das janelas, incluindo as seguintes:  
  
- Uma borda.  
  
- Uma barra de título.  
  
- Um ícone.  
  
- Botões Minimizar, Maximizar e Restaurar.  
  
- Um botão Fechar.  
  
- Um menu Sistema com itens de menu que permitem aos usuários minimizar, maximizar, restaurar, mover, redimensionar e fechar uma janela.  
  
 A *área cliente* de uma janela é a área dentro da área não cliente de uma janela e é usada por desenvolvedores para adicionar conteúdo específico de aplicativos, como barras de menu, barras de ferramentas e controles.  
  
 No WPF, uma janela é <xref:System.Windows.Window> encapsulada pela classe que você usa para fazer o seguinte:  
  
- Exibir uma janela.  
  
- Configurar o tamanho, posição e aparência de uma janela.  
  
- Conteúdo específico do aplicativo host.  
  
- Gerenciar o tempo de vida de uma janela.  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a>Implementar uma janela  
 A implementação de uma janela típica compreende tanto a aparência quanto o comportamento, onde *a aparência* define como uma janela olha para os usuários e o *comportamento* define a forma como uma janela funciona à medida que os usuários interagem com ela. No WPF, você pode implementar a aparência e [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] o comportamento de uma janela usando código ou marcação.  
  
 Em geral, no entanto, o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aparecimento de uma janela é implementado usando marcação, e seu comportamento é implementado usando código-atrás, como mostrado no exemplo a seguir.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Para habilitar um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de marcação e um arquivo de código para trabalhar em conjunto, são necessários os seguintes:  
  
- Na marcação, `Window` o elemento `x:Class` deve incluir o atributo. Quando o aplicativo é construído, a existência do arquivo `x:Class` de marcação faz `partial` com que o <xref:System.Windows.Window> Microsoft build engine (MSBuild) crie uma classe que deriva e tenha o nome especificado pelo atributo. `x:Class` Isso requer a adição de uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] declaração de `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` namespace XML para o esquema ( ). A `partial` classe gerada `InitializeComponent` implementa o método, que é chamado para registrar os eventos e definir as propriedades que são implementadas na marcação.  
  
- No code-behind, a classe `partial` deve ser uma classe com `x:Class` o mesmo nome especificado pelo <xref:System.Windows.Window>atributo na marcação, e deve derivar de . Isso permite que o arquivo de `partial` código traseiro seja associado à classe gerada para o arquivo de marcação quando o aplicativo é construído (consulte [Construindo um aplicativo WPF](building-a-wpf-application-wpf.md)).  
  
- No código atrás, <xref:System.Windows.Window> a classe deve implementar `InitializeComponent` um construtor que chame o método. `InitializeComponent`é implementado pela classe gerada `partial` do arquivo de marcação para registrar eventos e definir propriedades definidas na marcação.  
  
> [!NOTE]
> Quando você adiciona <xref:System.Windows.Window> um novo ao seu <xref:System.Windows.Window> projeto usando o Visual Studio, o é implementado usando marcação e código atrás, e inclui a configuração necessária para criar a associação entre a marcação e os arquivos de código-atrás como descrito aqui.  
  
 Com essa configuração em vigor, você pode se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] concentrar em definir a aparência da janela na marcação e implementar seu comportamento no code-behind. O exemplo a seguir mostra uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] janela com um botão, implementada na <xref:System.Windows.Controls.Primitives.ButtonBase.Click> marcação, e um manipulador de eventos para o evento do botão, implementado no code-behind.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a>Configurar uma definição de janela para MSBuild  
 A forma como você implementa sua janela determina como ela está configurada para o MSBuild. Para uma janela definida [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usando marcação e código atrás:  
  
- Os arquivos de marcação XAML `Page` são configurados como itens do MSBuild.  
  
- Os arquivos por trás do código `Compile` são configurados como itens do MSBuild.  
  
 Isso é mostrado no seguinte arquivo de projeto MSBuild.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Para obter informações sobre a construção de aplicativos WPF, consulte [Construindo um aplicativo WPF](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a>Tempo de vida de janela  
 Assim como com qualquer classe, uma janela tem um tempo de vida que começa quando ela é instanciada pela primeira vez, fato após o qual ela é aberta, ativada e desativada e, eventualmente, fechada.  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a>Abrir uma janela  
 Para abrir uma janela, você primeiro cria uma instância dela, o que é demonstrado no exemplo a seguir.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 Neste exemplo, `MarkupAndCodeBehindWindow` o é instanciado quando o aplicativo <xref:System.Windows.Application.Startup> é iniciado, o que ocorre quando o evento é levantado.  
  
 Quando uma janela é instanciada, uma referência a ela é automaticamente adicionada <xref:System.Windows.Application> a uma <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>lista de janelas que é gerenciada pelo objeto (ver ). Além disso, a primeira janela a ser instancinada <xref:System.Windows.Application> é, por padrão, definida como a janela principal do aplicativo (ver <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).  
  
 A janela é finalmente <xref:System.Windows.Window.Show%2A> aberta chamando o método; o resultado é mostrado na figura a seguir.  
  
 ![Uma janela aberta chamando Window.Show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Uma janela que é <xref:System.Windows.Window.Show%2A> aberta por chamada é uma janela modeless, o que significa que o aplicativo opera em um modo que permite que os usuários ativem outras janelas no mesmo aplicativo.  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A>é chamado para abrir janelas, como caixas de diálogo modally. Consulte [a visão geral das caixas de diálogo](dialog-boxes-overview.md) para obter mais informações.  
  
 Quando <xref:System.Windows.Window.Show%2A> é chamada, uma janela executa o trabalho de inicialização antes de ser mostrado para estabelecer uma infra-estrutura que lhe permita receber a entrada do usuário. Quando a janela é <xref:System.Windows.Window.SourceInitialized> inicializada, o evento é levantado e a janela é mostrada.  
  
 Como um <xref:System.Windows.Application.StartupUri%2A> atalho, pode ser definido para especificar a primeira janela aberta automaticamente quando um aplicativo é iniciado.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Quando o aplicativo é iniciado, a <xref:System.Windows.Application.StartupUri%2A> janela especificada pelo valor de é aberta modelessly; internamente, a janela é <xref:System.Windows.Window.Show%2A> aberta chamando seu método.  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a>Posse de janela  
 Uma janela que é <xref:System.Windows.Window.Show%2A> aberta usando o método não tem uma relação implícita com a janela que o criou; os usuários podem interagir com qualquer janela independentemente da outra, o que significa que qualquer janela pode fazer o seguinte:  
  
- Cubra a outra (a menos <xref:System.Windows.Window.Topmost%2A> que uma `true`das janelas tenha sua propriedade definida para ).  
  
- Ser minimizada, maximizada e restaurada sem afetar a outra.  
  
 Algumas janelas requerem uma relação com a janela que as abre. Por exemplo, um aplicativo IDE (Integrated Development Environment, ambiente de desenvolvimento integrado) pode abrir janelas de propriedade e janelas de ferramentas cujo comportamento típico é cobrir a janela que as cria. Além disso, janelas desse tipo devem sempre fechar, minimizar, maximizar e restaurar em conjunto com a janela que as criou. Tal relação pode ser estabelecida fazendo com que uma janela <xref:System.Windows.Window.Owner%2A> *possua* outra, e é alcançada definindo a propriedade da janela *própria* com uma referência à janela do *proprietário.* Isso é mostrado no exemplo a seguir.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Depois que a posse é estabelecida:  
  
- A janela de propriedade pode referenciar sua <xref:System.Windows.Window.Owner%2A> janela de proprietário inspecionando o valor de sua propriedade.  
  
- A janela do proprietário pode descobrir todas as janelas <xref:System.Windows.Window.OwnedWindows%2A> que possui inspecionando o valor de sua propriedade.  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a>Impedindo a ativação de janela  
 Existem cenários em que as janelas não devem ser ativadas quando mostradas, como janelas de conversação de um aplicativo estilo mensageiro da Internet ou janelas de notificação de um aplicativo de e-mail.  
  
 Se o aplicativo tiver uma janela que não deve ser <xref:System.Windows.Window.ShowActivated%2A> ativada `false` quando <xref:System.Windows.Window.Show%2A> mostrada, você pode definir sua propriedade antes de chamar o método pela primeira vez. Como consequência disso:  
  
- A janela não é ativada.  
  
- O evento <xref:System.Windows.Window.Activated> da janela não está levantado.  
  
- A janela ativada no momento permanece ativada.  
  
 A janela se tornará ativada, no entanto, assim que o usuário ativá-la clicando na área de cliente ou então na área não cliente. Nesse caso:  
  
- A janela é ativada.  
  
- O evento <xref:System.Windows.Window.Activated> da janela foi levantado.  
  
- A janela ativada anteriormente é desativada.  
  
- As janelas <xref:System.Windows.Window.Deactivated> e <xref:System.Windows.Window.Activated> os eventos são posteriormente levantados como esperado em resposta às ações do usuário.  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a>Ativação de janela  
 Quando uma janela é aberta pela primeira vez, ela <xref:System.Windows.Window.ShowActivated%2A> se `false`torna a janela ativa (a menos que seja mostrada com set para ). A *janela ativa* é a janela que está capturando a entrada do usuário no momento, como traçados de teclas e cliques do mouse. Quando uma janela se torna <xref:System.Windows.Window.Activated> ativa, ela levanta o evento.  
  
> [!NOTE]
> Quando uma janela é <xref:System.Windows.FrameworkElement.Loaded> aberta <xref:System.Windows.Window.ContentRendered> pela primeira vez, <xref:System.Windows.Window.Activated> os eventos e eventos são levantados somente após o evento ser levantado. Com isso em mente, uma janela pode <xref:System.Windows.Window.ContentRendered> ser efetivamente considerada aberta quando é levantada.  
  
 Depois que uma janela fica ativa, um usuário pode ativar outra janela no mesmo aplicativo ou então ativar outro aplicativo. Quando isso acontece, a janela ativa atualmente <xref:System.Windows.Window.Deactivated> fica desativada e levanta o evento. Da mesma forma, quando o usuário seleciona uma janela atualmente <xref:System.Windows.Window.Activated> desativada, a janela fica ativa novamente e é levantada.  
  
 Uma razão comum para lidar <xref:System.Windows.Window.Activated> e <xref:System.Windows.Window.Deactivated> é ativar e desativar funcionalidades que só podem ser executadas quando uma janela está ativa. Por exemplo, algumas janelas exibem conteúdo interativo que requer constante atenção ou entrada do usuário, incluindo players de vídeo e jogos. O exemplo a seguir é um reprodutor <xref:System.Windows.Window.Activated> <xref:System.Windows.Window.Deactivated> de vídeo simplificado que demonstra como lidar e implementar esse comportamento.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Outros tipos de aplicativos podem ainda executar códigos em segundo plano quando uma janela é desativada. Por exemplo, um cliente de email pode continuar a sondagem do servidor de email enquanto o usuário está usando outros aplicativos. Aplicativos como esses geralmente apresentam comportamento diferente ou adicional enquanto a janela principal está desativada. Em relação ao programa de email, isso pode significar tanto adicionar o novo item de email à caixa de entrada quanto adicionar um ícone de notificação à bandeja do sistema. Um ícone de notificação só precisa ser exibido quando a janela do e-mail não estiver ativa, o que pode ser determinado inspecionando a <xref:System.Windows.Window.IsActive%2A> propriedade.  
  
 Se uma tarefa em segundo plano for concluída, uma janela <xref:System.Windows.Window.Activate%2A> pode querer notificar o usuário com mais urgência, chamando o método. Se o usuário estiver interagindo com <xref:System.Windows.Window.Activate%2A> outro aplicativo ativado quando for chamado, o botão da barra de tarefas da janela será acionado. Se um usuário estiver interagindo com <xref:System.Windows.Window.Activate%2A> o aplicativo atual, a chamada levará a janela para o primeiro plano.  
  
> [!NOTE]
> Você pode lidar com a <xref:System.Windows.Application.Activated?displayProperty=nameWithType> <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> ativação do escopo do aplicativo usando os eventos e eventos.  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a>Fechar uma janela  
 O fim da vida de uma janela se começa a se aproximar quando um usuário a fecha. Uma janela pode ser fechada pelo uso de elementos na área de não cliente, incluindo o seguinte:  
  
- O item **Fechar** do menu **Sistema.**  
  
- Pressionar ALT + F4.  
  
- Pressionando o botão **Fechar.**  
  
 Você pode fornecer mecanismos adicionais à área de cliente para fechar uma janela, sendo que os mais comuns deles incluem os seguintes:  
  
- Um item **Sair** no menu **Arquivo,** normalmente para janelas principais de aplicativos.  
  
- Um item **Fechar** no menu **Arquivo,** normalmente em uma janela de aplicativo secundária.  
  
- Um botão **Cancelar,** normalmente em uma caixa de diálogo modal.  
  
- Um botão **Fechar,** normalmente em uma caixa de diálogo modeless.  
  
 Para fechar uma janela em resposta a um desses <xref:System.Windows.Window.Close%2A> mecanismos personalizados, você precisa chamar o método. O exemplo a seguir implementa a capacidade de fechar uma janela escolhendo a **saída** no menu **Arquivo.**  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Quando uma janela fecha, ela <xref:System.Windows.Window.Closing> levanta <xref:System.Windows.Window.Closed>dois eventos: e .  
  
 <xref:System.Windows.Window.Closing>é levantada antes que a janela feche, e fornece um mecanismo pelo qual o fechamento da janela pode ser evitado. Uma razão comum para evitar o fechamento da janela é caso o conteúdo da janela contenha dados modificados. Nesta situação, <xref:System.Windows.Window.Closing> o evento pode ser tratado para determinar se os dados estão sujos e, se for o caso, perguntar ao usuário se deve continuar fechando a janela sem salvar os dados ou cancelar o fechamento da janela. O exemplo a seguir mostra os <xref:System.Windows.Window.Closing>principais aspectos do manuseio .  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 O <xref:System.Windows.Window.Closing> manipulador de <xref:System.ComponentModel.CancelEventArgs>eventos é aprovado `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> a , `true` que implementa a propriedade que você definiu para evitar que uma janela feche.  
  
 Se <xref:System.Windows.Window.Closing> não for manuseado, ou for manuseado, mas não cancelado, a janela será fechada. Pouco antes de uma <xref:System.Windows.Window.Closed> janela realmente fechar, é levantada. Neste ponto, uma janela não pode ser impedida de fechar.  
  
> [!NOTE]
> Um aplicativo pode ser configurado para desligar automaticamente quando a <xref:System.Windows.Application.MainWindow%2A>janela principal do aplicativo fecha (veja) ou a última janela fecha. Para obter detalhes, consulte <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Embora uma janela possa ser explicitamente fechada através de mecanismos fornecidos nas áreas não cliente e cliente, uma janela também pode ser implicitamente fechada como resultado de comportamento em outras partes do aplicativo ou Windows, incluindo o seguinte:  
  
- Um usuário faz logoff ou desliga o Windows.  
  
- O dono de uma <xref:System.Windows.Window.Owner%2A>janela fecha (veja ).  
  
- A janela principal da <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>aplicação está fechada e é .  
  
- <xref:System.Windows.Application.Shutdown%2A> é chamado.  
  
> [!NOTE]
> Uma janela não pode ser reaberta depois que é fechada.  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a>Eventos de tempo de vida da janela  
 A ilustração a seguir mostra a seqüência dos principais eventos durante a vida de uma janela:  
  
 ![Diagrama que mostra eventos na vida de uma janela.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 A ilustração a seguir mostra a seqüência dos principais<xref:System.Windows.Window.ShowActivated%2A> eventos durante `false` a vida de uma janela que é mostrada sem ativação (é definida para antes da janela ser mostrada):  
  
 ![Diagrama que mostra eventos na vida de uma janela sem ativação.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a>Localização da janela  
 Enquanto uma janela estiver aberta, ela terá uma localização nas dimensões x e y em relação à área de trabalho. Este local pode ser determinado <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> inspecionando as propriedades e propriedades, respectivamente. Você pode definir essas propriedades para alterar o local da janela.  
  
 Você também pode especificar <xref:System.Windows.Window> a localização inicial de <xref:System.Windows.Window.WindowStartupLocation%2A> um quando ele <xref:System.Windows.WindowStartupLocation> aparece pela primeira vez definindo a propriedade com um dos seguintes valores de enumeração:  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner> (padrão)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Se o local de <xref:System.Windows.WindowStartupLocation.Manual>inicialização <xref:System.Windows.Window.Left%2A> for <xref:System.Windows.Window.Top%2A> especificado como <xref:System.Windows.Window> , e as propriedades e não foram definidas, pedirá ao Windows que um local seja exibido.  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a>Janela superior e ordem Z  
 Além de ter uma localização x e y, uma janela também tem uma localização na dimensão z, que determina a posição vertical em relação a outras janelas. Isso é conhecido como a ordem z da janela, e há dois tipos: ordem z normal e ordem z superior. A localização de uma janela na *ordem z normal* é determinada por estar ativa ou não. Por padrão, uma janela está localizada na ordem z normal. A localização de uma janela na *ordem z superior* também é determinada por estar ativa ou não. Além disso, janelas na ordem z superior sempre estão localizadas acima das janelas na ordem z normal. Uma janela está localizada na ordem z mais <xref:System.Windows.Window.Topmost%2A> superior, definindo sua propriedade para `true`.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 Dentro de cada ordem z, a janela ativa no momento aparece acima de todas as outras janelas na mesma ordem z.  
  
<a name="WindowSize"></a>
## <a name="window-size"></a>Tamanho da janela  
 Além de ter uma localização de desktop, uma janela tem um tamanho que <xref:System.Windows.Window.SizeToContent%2A>é determinado por várias propriedades, incluindo as várias propriedades de largura e altura e .  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>e <xref:System.Windows.FrameworkElement.MaxWidth%2A> são usados para gerenciar o intervalo de larguras que uma janela pode ter durante sua vida útil, e são configurados como mostrado no exemplo a seguir.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 A altura da <xref:System.Windows.FrameworkElement.MinHeight%2A>janela <xref:System.Windows.FrameworkElement.Height%2A>é <xref:System.Windows.FrameworkElement.MaxHeight%2A>gerenciada por , e , e são configuradas como mostrado no exemplo a seguir.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Já que os diversos valores de largura e de altura especificam um intervalo, é possível que a largura e altura de uma janela redimensionável estejam em qualquer lugar dentro do intervalo especificado para a respectiva dimensão. Para detectar sua largura e <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A>altura atuais, inspecione e, respectivamente.  
  
 Se você quiser que a largura e a altura da sua janela tenham um tamanho que <xref:System.Windows.Window.SizeToContent%2A> se encaixe no tamanho do conteúdo da janela, você pode usar a propriedade, que tem os seguintes valores:  
  
- <xref:System.Windows.SizeToContent.Manual>. Sem efeito (padrão).  
  
- <xref:System.Windows.SizeToContent.Width>. Ajuste à largura de conteúdo, que <xref:System.Windows.FrameworkElement.MinWidth%2A> tem <xref:System.Windows.FrameworkElement.MaxWidth%2A> o mesmo efeito de definir ambos e para a largura do conteúdo.  
  
- <xref:System.Windows.SizeToContent.Height>. Ajuste à altura do conteúdo, que <xref:System.Windows.FrameworkElement.MinHeight%2A> tem <xref:System.Windows.FrameworkElement.MaxHeight%2A> o mesmo efeito de definir tanto quanto à altura do conteúdo.  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. Ajuste-se à largura e altura do conteúdo, <xref:System.Windows.FrameworkElement.MaxHeight%2A> que tem o mesmo efeito <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> de definir tanto <xref:System.Windows.FrameworkElement.MinHeight%2A> quanto à altura do conteúdo, e definir tanto a largura do conteúdo.  
  
 O exemplo a seguir mostra uma janela que se dimensiona automaticamente para ajustar-se ao próprio conteúdo, verticalmente e horizontalmente, quando mostrada pela primeira vez.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 O exemplo a seguir <xref:System.Windows.Window.SizeToContent%2A> mostra como definir a propriedade em código para especificar como uma janela redimensiona para se adequar ao seu conteúdo .
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a>Ordem de precedência para propriedades de dimensionamento  
 Essencialmente, as diversas propriedades de tamanhos de uma janela são combinadas para definir o intervalo de largura e altura de uma janela redimensionável. Para garantir que um intervalo <xref:System.Windows.Window> válido seja mantido, avalia os valores das propriedades de tamanho usando as seguintes ordens de precedência.  
  
 **Para propriedades de altura:**  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Para propriedades de largura:**  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 A ordem de precedência também pode determinar o tamanho de uma <xref:System.Windows.Window.WindowState%2A> janela quando ela é maximizada, que é gerenciada com a propriedade.  
  
<a name="WindowState"></a>
## <a name="window-state"></a>Estado da janela  
 Durante o tempo de vida de uma janela redimensionável, ela pode ter três estados: normal, minimizada e maximizada. Uma janela com um estado *normal* é o estado padrão de uma janela. Uma janela com esse estado permitirá que um usuário a mova e a redimensione usando uma alça de redimensionamento ou a borda, se ela for redimensionável.  
  
 Uma janela com um estado *minimizado* entra <xref:System.Windows.Window.ShowInTaskbar%2A> em `true`colapso no botão da barra de tarefas se estiver definida como ; caso contrário, ele colapsa para o menor tamanho possível que pode ser e se realoca para o canto inferior esquerdo da área de trabalho. Nenhum tipo de janela minimizada pode ser redimensionado usando uma borda ou alça redimensionável, embora uma janela minimizada não mostrada na barra de tarefas possa ser arrastada pela área de trabalho.  
  
 Uma janela com um estado *maximizado* expande-se para o tamanho <xref:System.Windows.FrameworkElement.MaxWidth%2A>máximo <xref:System.Windows.FrameworkElement.MaxHeight%2A>que <xref:System.Windows.Window.SizeToContent%2A> pode ser, que será tão grande quanto a sua , e as propriedades ditam. Assim como ocorre com uma janela minimizada, uma janela maximizada não pode ser redimensionada usando uma alça de redimensionamento ou arrastando a borda.  
  
> [!NOTE]
> Os valores <xref:System.Windows.Window.Top%2A> <xref:System.Windows.Window.Left%2A>da <xref:System.Windows.FrameworkElement.Width%2A>janela <xref:System.Windows.FrameworkElement.Height%2A> sempre representam os valores para o estado normal, mesmo quando a janela é maximizada ou minimizada.  
  
 O estado de uma janela pode <xref:System.Windows.Window.WindowState%2A> ser configurado definindo sua <xref:System.Windows.WindowState> propriedade, que pode ter um dos seguintes valores de enumeração:  
  
- <xref:System.Windows.WindowState.Normal> (padrão)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 O exemplo a seguir mostra como criar uma janela que é mostrada como maximizada quando é aberta.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Em geral, você <xref:System.Windows.Window.WindowState%2A> deve definir para configurar o estado inicial de uma janela. Assim que uma janela redimensionável é exibida, os usuários podem pressionar os botões minimizar, maximizar e restaurar na barra de título da janela para alterar o estado desta.  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a>Aparência da janela  
 Você pode alterar a aparência da área de cliente de uma janela adicionando conteúdo específico de janela a ela, por exemplo, botões, rótulos e caixas de texto. Para configurar a área não <xref:System.Windows.Window> cliente, fornece <xref:System.Windows.Window.Icon%2A> várias propriedades, que <xref:System.Windows.Window.Title%2A> incluem definir o ícone de uma janela e definir seu título.  
  
 Você também pode alterar a aparência e o comportamento da borda da área de não cliente configurando o modo de redimensionamento da janela, o estilo da janela e definindo se essa janela aparece ou não como um botão na barra de tarefas da área de trabalho.  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a>Modo de redimensionamento  
 Dependendo da <xref:System.Windows.Window.WindowStyle%2A> propriedade, você pode controlar como (e se) os usuários podem redimensionar a janela. A escolha do estilo de janela afeta se um usuário pode redimensionar a janela arrastando sua borda com o mouse, se os botões **Minimizar**, **Maximizar**e **Redimensionar** aparecem na área não cliente e, se aparecerem, se estiverem habilitados.  
  
 Você pode configurar como uma janela redimensiona definindo sua <xref:System.Windows.Window.ResizeMode%2A> propriedade, que pode ser um dos seguintes <xref:System.Windows.ResizeMode> valores de enumeração:  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize> (padrão)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Como <xref:System.Windows.Window.WindowStyle%2A>com , o modo de redimensionamento de uma janela é improvável de mudar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] durante sua vida útil, o que significa que você provavelmente vai configurá-lo a partir da marcação.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Observe que você pode detectar se uma janela é maximizada, minimizada ou restaurada inspecionando a <xref:System.Windows.Window.WindowState%2A> propriedade.  
  
<a name="Window_Style"></a>
### <a name="window-style"></a>Estilo de Janela  
 A borda que é exposta da área de não cliente de uma janela é adequada para a maioria dos aplicativos. No entanto, existem circunstâncias em que diferentes tipos de bordas são necessários ou em que nenhuma borda é necessária, dependendo do tipo de janela.  
  
 Para controlar que tipo de borda uma <xref:System.Windows.Window.WindowStyle%2A> janela obtém, você <xref:System.Windows.WindowStyle> define sua propriedade com um dos seguintes valores da enumeração:  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow> (padrão)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 O efeito desses estilos de janela são ilustrados na seguinte figura:  
  
 ![Ilustração dos estilos de borda da janela.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Você pode <xref:System.Windows.Window.WindowStyle%2A> definir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usando marcação ou código; porque é improvável que mude durante a vida útil de uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] janela, você provavelmente irá configurá-la usando marcação.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Estilo de janela não retangular  
 Há também situações em <xref:System.Windows.Window.WindowStyle%2A> que os estilos de fronteira que permitem que você tenha não são suficientes. Por exemplo, você pode querer criar um aplicativo com uma borda não retangular, como o Microsoft Windows Media Player usa.  
  
 Por exemplo, considere a janela de bolha de fala mostrada na seguinte figura:  
  
 ![Uma janela de bolha de fala que diz "Me Arraste-me".](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Esse tipo de janela pode ser <xref:System.Windows.Window.WindowStyle%2A> criada <xref:System.Windows.WindowStyle.None>definindo a propriedade <xref:System.Windows.Window> para , e usando suporte especial que tem para transparência.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Essa combinação de valores instrui a janela a ser renderizada completamente transparente. Nesse estado, os adornos da área de não cliente da janela (o menu Fechar, botões Minimizar, Maximizar e Restaurar e assim por diante) não podem ser usados. Consequentemente, você precisa fornecer os seus próprios.  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a>Presença da barra de tarefas  

A aparência padrão de uma janela inclui um botão de barra de tarefas, como o mostrado na seguinte figura:

 ![Captura de tela que mostra uma janela com um botão de barra de tarefas.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Alguns tipos de janelas não possuem um botão de barra de tarefas, como caixas de mensagens e caixas de diálogo (ver [Visão geral das caixas de diálogo](dialog-boxes-overview.md)). Você pode controlar se o botão de barra <xref:System.Windows.Window.ShowInTaskbar%2A> de`true` tarefas para uma janela é mostrado definindo a propriedade (por padrão).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a>Considerações de segurança  
 <xref:System.Windows.Window>requer `UnmanagedCode` permissão de segurança para ser instanciado. Para aplicativos instalados e iniciados no computador local, isso se encaixa no conjunto de permissões concedidas ao aplicativo.  
  
 No entanto, isso está fora do conjunto de permissões concedidas a aplicativos que são lançados da região de internet ou intranet local usando o ClickOnce. Consequentemente, os usuários receberão um aviso de segurança ClickOnce e precisarão elevar a permissão definida para o aplicativo para total confiança.  
  
 Além disso, os XBAPs não podem mostrar janelas ou caixas de diálogo por padrão. Para uma discussão sobre considerações independentes de segurança de aplicativos, consulte [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a>Outros tipos de janelas  
 <xref:System.Windows.Navigation.NavigationWindow>é uma janela projetada para hospedar conteúdo navegável. Para obter mais informações, consulte [Visão geral da navegação](navigation-overview.md)).  
  
 Caixas de diálogo são janelas que geralmente são usadas para coletar informações de um usuário para concluir uma função. Por exemplo, quando um usuário deseja abrir um arquivo, a caixa de diálogo **Arquivo Aberto** geralmente é exibida por um aplicativo para obter o nome do arquivo do usuário. Para obter mais informações, consulte [Visão geral das caixas de diálogo](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Visão geral das caixas de diálogo](dialog-boxes-overview.md)
- [Compilando um aplicativo WPF](building-a-wpf-application-wpf.md)
