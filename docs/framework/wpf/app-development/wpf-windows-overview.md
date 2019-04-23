---
title: Visão geral do WPF do Windows
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
ms.openlocfilehash: 5acebf0f88f3147bf274818f11697b480146701a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296115"
---
# <a name="wpf-windows-overview"></a>Visão geral do WPF do Windows
Os usuários interagem com aplicativos do Windows Presentation Foundation (WPF) autônomo por meio do windows. O objetivo principal de uma janela é hospedar conteúdo que visualiza dados e permite aos usuários interagir com os dados. Autônomo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos fornecem suas próprias janelas usando o <xref:System.Windows.Window> classe. Este tópico apresenta <xref:System.Windows.Window> antes de abranger os fundamentos da criação e gerenciamento de janelas em aplicativos autônomos.  
  
> [!NOTE]
>  Hospedados pelo navegador [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos, incluindo [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] fracamente acopladas [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] páginas, não fornecem suas próprias janelas. Em vez disso, eles são hospedados em janelas fornecidas pelo [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]. Ver [visão geral dos aplicativos de navegador XAML do WPF](wpf-xaml-browser-applications-overview.md).  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>A classe Window  
 A figura a seguir ilustra as partes constituintes de uma janela:  
  
 ![Captura de tela que mostra os elementos da janela.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Uma janela é dividida em duas áreas: a área de não cliente e a área de cliente.  
  
 O *área não cliente* de uma janela é implementada pelo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] e inclui as partes de uma janela que são comuns à maioria das janelas, incluindo o seguinte:  
  
-   Uma borda.  
  
-   Uma barra de título.  
  
-   Um ícone.  
  
-   Botões Minimizar, Maximizar e Restaurar.  
  
-   Um botão Fechar.  
  
-   Um menu Sistema com itens de menu que permitem aos usuários minimizar, maximizar, restaurar, mover, redimensionar e fechar uma janela.  
  
 O *área de cliente* de uma janela é a área dentro de uma área da janela não-cliente e é usado por desenvolvedores para adicionar conteúdo específico do aplicativo, como barras de menus, barras de ferramentas e controles.  
  
 Na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], uma janela é encapsulada pela <xref:System.Windows.Window> classe que você pode usar para fazer o seguinte:  
  
-   Exibir uma janela.  
  
-   Configurar o tamanho, posição e aparência de uma janela.  
  
-   Conteúdo específico do aplicativo host.  
  
-   Gerenciar o tempo de vida de uma janela.  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>Implementar uma janela  
 A implementação de uma janela típica compreende tanto aparência quanto comportamento, onde *aparência* define a aparência de uma janela para os usuários e *comportamento* define a forma como uma janela funciona conforme os usuários interagem com ele. Na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], você pode implementar a aparência e comportamento de uma janela usando código ou [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação.  
  
 Em geral, no entanto, a aparência de uma janela é implementada usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação e seu comportamento é implementado usando lógica, conforme mostrado no exemplo a seguir.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Para habilitar um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de marcação e o arquivo code-behind funcionem juntos, é necessário o seguinte:  
  
-   Na marcação, o `Window` elemento deve incluir o `x:Class` atributo. Quando o aplicativo é compilado, a existência de `x:Class` na marcação arquivo faz com que [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] para criar um `partial` classe que deriva de <xref:System.Windows.Window> e tem o nome especificado pelo `x:Class` atributo. Isso exige a adição de um [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] declaração de namespace para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] esquema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Gerado `partial` classe implementa o `InitializeComponent` método, que é chamado para registrar os eventos e definir as propriedades que são implementadas na marcação.  
  
-   No code-behind, a classe deve ser um `partial` classe com o mesmo nome que é especificado pelo `x:Class` atributo na marcação e deve derivar de <xref:System.Windows.Window>. Isso permite que o arquivo code-behind seja associado a `partial` classe que é gerada para o arquivo de marcação quando o aplicativo é compilado (consulte [criando um aplicativo WPF](building-a-wpf-application-wpf.md)).  
  
-   No code-behind, o <xref:System.Windows.Window> classe deve implementar um construtor que chama o `InitializeComponent` método. `InitializeComponent` é implementado pela marcação gerada pelo arquivo `partial` classe para registrar eventos e definir propriedades que são definidas na marcação.  
  
> [!NOTE]
>  Quando você adiciona um novo <xref:System.Windows.Window> ao seu projeto usando [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], o <xref:System.Windows.Window> é implementada usando marcação e code-behind e inclui a configuração necessária para criar a associação entre os arquivos de marcação e code-behind, como descrito aqui.  
  
 Com essa configuração, você pode se concentrar na definição da aparência da janela em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação e implementar seu comportamento no code-behind. O exemplo a seguir mostra uma janela com um botão, implementado em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação e um manipulador de eventos do botão <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento, implementado no code-behind.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>Configurar uma definição de janela para MSBuild  
 Como você implementa sua janela determina como ela é configurada para [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]. Para uma janela que é definida usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação e code-behind:  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos de marcação são configurados como [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` itens.  
  
-   Arquivos code-behind são configurados como [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` itens.  
  
 Isso é mostrado na seguinte [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] arquivo de projeto.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Para obter informações sobre a compilação [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos, consulte [criando um aplicativo WPF](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>Tempo de vida de janela  
 Assim como com qualquer classe, uma janela tem um tempo de vida que começa quando ela é instanciada pela primeira vez, fato após o qual ela é aberta, ativada e desativada e, eventualmente, fechada.  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>Abrir uma janela  
 Para abrir uma janela, você primeiro cria uma instância dela, o que é demonstrado no exemplo a seguir.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 Neste exemplo, o `MarkupAndCodeBehindWindow` é instanciado quando o aplicativo é iniciado, o que ocorre quando o <xref:System.Windows.Application.Startup> é gerado.  
  
 Quando uma janela é instanciada, uma referência a ele é automaticamente adicionada a uma lista do windows que é gerenciada pelo <xref:System.Windows.Application> objeto (consulte <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>). Além disso, a primeira janela a ser instanciada é, por padrão, definida <xref:System.Windows.Application> como a janela principal do aplicativo (consulte <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).  
  
 A janela é finalmente aberta chamando o <xref:System.Windows.Window.Show%2A> método; o resultado é mostrado na figura a seguir.  
  
 ![Uma janela aberta chamando Window. show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Uma janela que é aberta chamando <xref:System.Windows.Window.Show%2A> é uma janela não restrita, o que significa que o aplicativo opera em um modo que permite aos usuários ativar outras janelas no mesmo aplicativo.  
  
> [!NOTE]
>  <xref:System.Windows.Window.ShowDialog%2A> é chamado para abrir janelas como caixas de diálogo modalmente. Ver [visão geral das caixas de diálogo](dialog-boxes-overview.md) para obter mais informações.  
  
 Quando <xref:System.Windows.Window.Show%2A> é chamado, uma janela executa o trabalho de inicialização antes de ser mostrada para estabelecer a infraestrutura que permite que ele receba entrada do usuário. Quando a janela é inicializada, o <xref:System.Windows.Window.SourceInitialized> é gerado e a janela é mostrada.  
  
 Como um atalho, <xref:System.Windows.Application.StartupUri%2A> pode ser definido para especificar a primeira janela que é aberta automaticamente quando um aplicativo é iniciado.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Quando o aplicativo for iniciado, a janela especificada pelo valor de <xref:System.Windows.Application.StartupUri%2A> é aberto sem modo específico; internamente, a janela é aberta chamando seu <xref:System.Windows.Window.Show%2A> método.  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>Posse de janela  
 Uma janela que é aberta usando o <xref:System.Windows.Window.Show%2A> método não tem uma relação implícita com a janela que a criou; os usuários podem interagir com qualquer janela independentemente da outra, o que significa que qualquer janela pode fazer o seguinte:  
  
-   Cobrir a outra (a menos que uma das janelas tenha sua <xref:System.Windows.Window.Topmost%2A> propriedade definida como `true`).  
  
-   Ser minimizada, maximizada e restaurada sem afetar a outra.  
  
 Algumas janelas requerem uma relação com a janela que as abre. Por exemplo, um [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] aplicativo pode abrir janelas de propriedade e janelas de ferramenta cujo comportamento típico é para cobrir a janela que as cria. Além disso, janelas desse tipo devem sempre fechar, minimizar, maximizar e restaurar em conjunto com a janela que as criou. Essa relação pode ser estabelecida tornando uma janela *próprio* outro e é feito definindo o <xref:System.Windows.Window.Owner%2A> propriedade do *janela propriedade* com uma referência para o *proprietário janela*. Isso é mostrado no exemplo a seguir.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Depois que a posse é estabelecida:  
  
-   A janela propriedade pode fazer referência a respectiva janela proprietária inspecionando o valor de seu <xref:System.Windows.Window.Owner%2A> propriedade.  
  
-   A janela proprietária pode descobrir todas as janelas que possui inspecionando o valor de seu <xref:System.Windows.Window.OwnedWindows%2A> propriedade.  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>Impedindo a ativação de janela  
 Há cenários em que windows não devem ser ativadas quando mostradas, tais como janelas de conversa de um aplicativo estilo messenger da Internet ou janelas de notificação de um aplicativo de email.  
  
 Se seu aplicativo tem uma janela que não deve ser ativada quando mostrada, você pode definir seus <xref:System.Windows.Window.ShowActivated%2A> propriedade para `false` antes de chamar o <xref:System.Windows.Window.Show%2A> método pela primeira vez. Como consequência disso:  
  
-   A janela não é ativada.  
  
-   A janela <xref:System.Windows.Window.Activated> não é gerado.  
  
-   A janela ativada no momento permanece ativada.  
  
 A janela se tornará ativada, no entanto, assim que o usuário ativá-la clicando na área de cliente ou então na área não cliente. Nesse caso:  
  
-   A janela é ativada.  
  
-   A janela <xref:System.Windows.Window.Activated> é gerado.  
  
-   A janela ativada anteriormente é desativada.  
  
-   A janela <xref:System.Windows.Window.Deactivated> e <xref:System.Windows.Window.Activated> eventos são acionados subsequentemente, conforme o esperado em resposta às ações do usuário.  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>Ativação de janela  
 Quando uma janela é aberta pela primeira vez, ele se torna a janela ativa (a menos que ele é mostrado com <xref:System.Windows.Window.ShowActivated%2A> definido como `false`). O *janela ativa* é a janela que está atualmente capturando entrada do usuário, como pressionamentos de tecla e cliques do mouse. Quando uma janela fica ativa, ele gera o <xref:System.Windows.Window.Activated> eventos.  
  
> [!NOTE]
>  Quando uma janela é aberta pela primeira vez, o <xref:System.Windows.FrameworkElement.Loaded> e <xref:System.Windows.Window.ContentRendered> eventos são acionados somente após o <xref:System.Windows.Window.Activated> é gerado. Com isso em mente, uma janela pode efetivamente ser considerada aberta quando <xref:System.Windows.Window.ContentRendered> é gerado.  
  
 Depois que uma janela fica ativa, um usuário pode ativar outra janela no mesmo aplicativo ou então ativar outro aplicativo. Quando isso acontece, a janela ativa se torna desativada e aciona o <xref:System.Windows.Window.Deactivated> eventos. Da mesma forma, quando o usuário seleciona uma janela desativada no momento, a janela ficará ativa novamente e <xref:System.Windows.Window.Activated> é gerado.  
  
 Um motivo comum para manipular <xref:System.Windows.Window.Activated> e <xref:System.Windows.Window.Deactivated> é habilitar e desabilitar funcionalidades que podem executar apenas quando uma janela está ativa. Por exemplo, algumas janelas exibem conteúdo interativo que requer constante atenção ou entrada do usuário, incluindo players de vídeo e jogos. O exemplo a seguir é um player de vídeo simplificado que demonstra como manipular <xref:System.Windows.Window.Activated> e <xref:System.Windows.Window.Deactivated> para implementar esse comportamento.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Outros tipos de aplicativos podem ainda executar códigos em segundo plano quando uma janela é desativada. Por exemplo, um cliente de email pode continuar a sondagem do servidor de email enquanto o usuário está usando outros aplicativos. Aplicativos como esses geralmente apresentam comportamento diferente ou adicional enquanto a janela principal está desativada. Em relação ao programa de email, isso pode significar tanto adicionar o novo item de email à caixa de entrada quanto adicionar um ícone de notificação à bandeja do sistema. Um ícone de notificação só precisa ser exibido quando a janela de email não está ativa, que pode ser determinada inspecionando o <xref:System.Windows.Window.IsActive%2A> propriedade.  
  
 Se uma tarefa em segundo plano for concluída, uma janela pode querer notificar o usuário com mais urgência chamando <xref:System.Windows.Window.Activate%2A> método. Se o usuário está interagindo com outro aplicativo ativado quando <xref:System.Windows.Window.Activate%2A> é chamado, botão de barra de tarefas da janela piscará. Se um usuário estiver interagindo com o aplicativo atual, chamar <xref:System.Windows.Window.Activate%2A> trará a janela em primeiro plano.  
  
> [!NOTE]
>  Você pode manipular a ativação de escopo do aplicativo usando o <xref:System.Windows.Application.Activated?displayProperty=nameWithType> e <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> eventos.  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>Fechar uma janela  
 O fim da vida de uma janela se começa a se aproximar quando um usuário a fecha. Uma janela pode ser fechada pelo uso de elementos na área de não cliente, incluindo o seguinte:  
  
-   O **feche** item da **sistema** menu.  
  
-   Pressionar ALT + F4.  
  
-   Pressionar o **fechar** botão.  
  
 Você pode fornecer mecanismos adicionais à área de cliente para fechar uma janela, sendo que os mais comuns deles incluem os seguintes:  
  
-   Uma **Exit** item o **arquivo** menu, geralmente para janelas do aplicativo principal.  
  
-   Um **feche** item na **arquivo** menu, normalmente em uma janela do aplicativo secundário.  
  
-   Um **Cancelar** botão, normalmente em uma caixa de diálogo modal.  
  
-   Um **fechar** botão, normalmente em uma caixa de diálogo sem janela restrita.  
  
 Para fechar uma janela em resposta a um desses mecanismos personalizados, você precisará chamar o <xref:System.Windows.Window.Close%2A> método. O exemplo a seguir implementa a capacidade de fechar uma janela, escolhendo a **Exit** sobre o **arquivo** menu.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Quando uma janela fecha, ela gera dois eventos: <xref:System.Windows.Window.Closing> e <xref:System.Windows.Window.Closed>.  
  
 <xref:System.Windows.Window.Closing> é gerado antes que a janela for fechada, e ele fornece um mecanismo pelo qual janela fechamento pode ser impedido. Uma razão comum para evitar o fechamento da janela é caso o conteúdo da janela contenha dados modificados. Nessa situação, o <xref:System.Windows.Window.Closing> evento pode ser manipulado para determinar se os dados estão impróprios e, em caso afirmativo, perguntar ao usuário se continua o fechamento da janela sem salvar os dados ou para cancelar o fechamento da janela. O exemplo a seguir mostra os principais aspectos da manipulação de <xref:System.Windows.Window.Closing>.  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 O <xref:System.Windows.Window.Closing> manipulador de eventos recebe um <xref:System.ComponentModel.CancelEventArgs>, que implementa o `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propriedade definida como `true` para impedir que uma janela seja fechada.  
  
 Se <xref:System.Windows.Window.Closing> não for tratada, ou é tratado mas não cancelado, a janela será fechada. Antes de uma janela realmente fechar, <xref:System.Windows.Window.Closed> é gerado. Neste ponto, uma janela não pode ser impedida de fechar.  
  
> [!NOTE]
>  Um aplicativo pode ser configurado para desligar automaticamente quando fecha a janela principal do aplicativo (consulte <xref:System.Windows.Application.MainWindow%2A>) ou a última janela Fechar. Para obter detalhes, consulte <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Enquanto uma janela pode ser fechada explicitamente através de mecanismos fornecidos nas áreas não cliente e cliente, uma janela pode também ser implicitamente fechada como resultado de comportamento em outras partes do aplicativo ou [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], incluindo o seguinte:  
  
-   Um usuário efetua logoff ou desliga o Windows.  
  
-   Proprietário de uma janela fecha (consulte <xref:System.Windows.Window.Owner%2A>).  
  
-   A janela principal do aplicativo é fechada e <xref:System.Windows.Application.ShutdownMode%2A> é <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
-   <xref:System.Windows.Application.Shutdown%2A> é chamado.  
  
> [!NOTE]
>  Uma janela não pode ser reaberta depois que é fechada.  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>Eventos de tempo de vida da janela  
 A ilustração a seguir mostra a sequência dos eventos principais no tempo de vida de uma janela:  
  
 ![Diagrama que mostra os eventos no tempo de vida de uma janela.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 A ilustração a seguir mostra a sequência dos eventos principais no tempo de vida de uma janela que é mostrada sem ativação (<xref:System.Windows.Window.ShowActivated%2A> é definido como `false` antes que a janela é exibida):  
  
 ![Diagrama que mostra os eventos no tempo de vida de uma janela sem ativação.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>Localização da janela  
 Enquanto uma janela estiver aberta, ela terá uma localização nas dimensões x e y em relação à área de trabalho. Esse local pode ser determinado inspecionando o <xref:System.Windows.Window.Left%2A> e <xref:System.Windows.Window.Top%2A> propriedades, respectivamente. Você pode definir essas propriedades para alterar o local da janela.  
  
 Você também pode especificar o local inicial de um <xref:System.Windows.Window> quando ele for exibido pela primeira vez, definindo o <xref:System.Windows.Window.WindowStartupLocation%2A> propriedade com um dos seguintes <xref:System.Windows.WindowStartupLocation> valores de enumeração:  
  
-   <xref:System.Windows.WindowStartupLocation.CenterOwner> (padrão)  
  
-   <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
-   <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Se o local de inicialização é especificado como <xref:System.Windows.WindowStartupLocation.Manual>e o <xref:System.Windows.Window.Left%2A> e <xref:System.Windows.Window.Top%2A> propriedades não foram definidas, <xref:System.Windows.Window> solicitará que o Windows para um local sejam exibidos no.  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>Janela superior e ordem Z  
 Além de ter uma localização x e y, uma janela também tem uma localização na dimensão z, que determina a posição vertical em relação a outras janelas. Isso é conhecido como a ordem z da janela, e há dois tipos: ordem z normal e ordem z superior. O local de uma janela na *ordem z normal* é determinada por ela estar ativa no momento ou não. Por padrão, uma janela está localizada na ordem z normal. O local de uma janela na *ordem z superior* também é determinada por ela estar ativa no momento ou não. Além disso, janelas na ordem z superior sempre estão localizadas acima das janelas na ordem z normal. Uma janela está localizada na ordem z superior definindo sua <xref:System.Windows.Window.Topmost%2A> propriedade para `true`.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 Dentro de cada ordem z, a janela ativa no momento aparece acima de todas as outras janelas na mesma ordem z.  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>Tamanho da janela  
 Além de ter um local de área de trabalho, uma janela tem um tamanho que é determinado por várias propriedades, incluindo as várias propriedades de largura e altura e <xref:System.Windows.Window.SizeToContent%2A>.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, e <xref:System.Windows.FrameworkElement.MaxWidth%2A> são usados para gerenciar o intervalo de larguras que uma janela pode ter durante seu ciclo de vida e são configurados como mostrado no exemplo a seguir.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Altura da janela é gerenciada pelo <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, e <xref:System.Windows.FrameworkElement.MaxHeight%2A>e são configurados como mostrado no exemplo a seguir.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Já que os diversos valores de largura e de altura especificam um intervalo, é possível que a largura e altura de uma janela redimensionável estejam em qualquer lugar dentro do intervalo especificado para a respectiva dimensão. Para detectar sua altura e largura atual, inspecione <xref:System.Windows.FrameworkElement.ActualWidth%2A> e <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectivamente.  
  
 Se você quiser que a largura e altura da janela para ter um tamanho que se ajusta ao tamanho da janela do conteúdo, você pode usar o <xref:System.Windows.Window.SizeToContent%2A> propriedade, que tem os seguintes valores:  
  
-   <xref:System.Windows.SizeToContent.Manual>. Sem efeito (padrão).  
  
-   <xref:System.Windows.SizeToContent.Width>. Ajustar à largura do conteúdo, que tem o mesmo efeito que definir ambas <xref:System.Windows.FrameworkElement.MinWidth%2A> e <xref:System.Windows.FrameworkElement.MaxWidth%2A> para a largura do conteúdo.  
  
-   <xref:System.Windows.SizeToContent.Height>. Ajustar à altura do conteúdo, que tem o mesmo efeito que definir ambos <xref:System.Windows.FrameworkElement.MinHeight%2A> e <xref:System.Windows.FrameworkElement.MaxHeight%2A> à altura do conteúdo.  
  
-   <xref:System.Windows.SizeToContent.WidthAndHeight>. Ajustar à largura do conteúdo e a altura, que tem o mesmo efeito que definir ambas <xref:System.Windows.FrameworkElement.MinHeight%2A> e <xref:System.Windows.FrameworkElement.MaxHeight%2A> para a altura do conteúdo e definir ambas <xref:System.Windows.FrameworkElement.MinWidth%2A> e <xref:System.Windows.FrameworkElement.MaxWidth%2A> para a largura do conteúdo.  
  
 O exemplo a seguir mostra uma janela que se dimensiona automaticamente para ajustar-se ao próprio conteúdo, verticalmente e horizontalmente, quando mostrada pela primeira vez.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 O exemplo a seguir mostra como definir o <xref:System.Windows.Window.SizeToContent%2A> propriedade no código para especificar como uma janela é redimensionada para caber seu conteúdo.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>Ordem de precedência para propriedades de dimensionamento  
 Essencialmente, as diversas propriedades de tamanhos de uma janela são combinadas para definir o intervalo de largura e altura de uma janela redimensionável. Para garantir que um intervalo válido é mantido, <xref:System.Windows.Window> avalia os valores das propriedades de tamanho usando a ordem de precedência a seguir.  
  
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
  
 A ordem de precedência também pode determinar o tamanho de uma janela quando ela estiver maximizada, o que é gerenciado com o <xref:System.Windows.Window.WindowState%2A> propriedade.  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>Estado da janela  
 Durante o tempo de vida de uma janela redimensionável, ela pode ter três estados: normal, minimizada e maximizada. Uma janela com um *normal* estado é o estado padrão de uma janela. Uma janela com esse estado permitirá que um usuário a mova e a redimensione usando uma alça de redimensionamento ou a borda, se ela for redimensionável.  
  
 Uma janela com um *minimizada* estado recolhe a seu botão da barra de tarefas se <xref:System.Windows.Window.ShowInTaskbar%2A> é definido como `true`; caso contrário, ela se recolherá para o menor tamanho possível, ele pode ser e se realocará para o canto inferior esquerdo da área de trabalho. Nenhum tipo de janela minimizada pode ser redimensionado usando uma borda ou alça redimensionável, embora uma janela minimizada não mostrada na barra de tarefas possa ser arrastada pela área de trabalho.  
  
 Uma janela com um *maximizado* estado se expande para o seu tamanho máximo, o qual será apenas tão grande quanto seus <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, e <xref:System.Windows.Window.SizeToContent%2A> propriedades ditam. Assim como ocorre com uma janela minimizada, uma janela maximizada não pode ser redimensionada usando uma alça de redimensionamento ou arrastando a borda.  
  
> [!NOTE]
>  Os valores de <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, e <xref:System.Windows.FrameworkElement.Height%2A> propriedades de uma janela sempre representam os valores para o estado normal, mesmo quando a janela está maximizada ou minimizada.  
  
 O estado de uma janela pode ser configurado definindo sua <xref:System.Windows.Window.WindowState%2A> propriedade, que pode ter um dos seguintes <xref:System.Windows.WindowState> valores de enumeração:  
  
-   <xref:System.Windows.WindowState.Normal> (padrão)  
  
-   <xref:System.Windows.WindowState.Maximized>  
  
-   <xref:System.Windows.WindowState.Minimized>  
  
 O exemplo a seguir mostra como criar uma janela que é mostrada como maximizada quando é aberta.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Em geral, você deve definir <xref:System.Windows.Window.WindowState%2A> para configurar o estado inicial de uma janela. Assim que uma janela redimensionável é exibida, os usuários podem pressionar os botões minimizar, maximizar e restaurar na barra de título da janela para alterar o estado desta.  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>Aparência da janela  
 Você pode alterar a aparência da área de cliente de uma janela adicionando conteúdo específico de janela a ela, por exemplo, botões, rótulos e caixas de texto. Para configurar a área não cliente, <xref:System.Windows.Window> fornece várias propriedades, que incluem <xref:System.Windows.Window.Icon%2A> para definir um ícone de janela e <xref:System.Windows.Window.Title%2A> para definir seu título.  
  
 Você também pode alterar a aparência e o comportamento da borda da área de não cliente configurando o modo de redimensionamento da janela, o estilo da janela e definindo se essa janela aparece ou não como um botão na barra de tarefas da área de trabalho.  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>Modo de redimensionamento  
 Dependendo do <xref:System.Windows.Window.WindowStyle%2A> propriedade, você pode controlar como (e se) os usuários podem redimensionar a janela. A opção de estilo da janela afeta se um usuário pode redimensionar a janela arrastando sua borda com o mouse, se o **minimizar**, **maximizar**, e **redimensionar** botões aparecem na área não cliente, e, se eles forem exibidos, se elas estão habilitadas.  
  
 Você pode configurar como uma janela é redimensionada definindo sua <xref:System.Windows.Window.ResizeMode%2A> propriedade, que pode ser um dos seguintes <xref:System.Windows.ResizeMode> valores de enumeração:  
  
-   <xref:System.Windows.ResizeMode.NoResize>  
  
-   <xref:System.Windows.ResizeMode.CanMinimize>  
  
-   <xref:System.Windows.ResizeMode.CanResize> (padrão)  
  
-   <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Assim como acontece com <xref:System.Windows.Window.WindowStyle%2A>, o modo de redimensionamento de uma janela é improvável de ser alterado durante seu tempo de vida, o que significa que provavelmente irá defini-lo do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Observe que você pode detectar se uma janela é maximizada, minimizada ou restaurada inspecionando o <xref:System.Windows.Window.WindowState%2A> propriedade.  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>Estilo de Janela  
 A borda que é exposta da área de não cliente de uma janela é adequada para a maioria dos aplicativos. No entanto, existem circunstâncias em que diferentes tipos de bordas são necessários ou em que nenhuma borda é necessária, dependendo do tipo de janela.  
  
 Para controlar o tipo de borda de uma janela obtém, você define sua <xref:System.Windows.Window.WindowStyle%2A> propriedade com um dos seguintes valores da <xref:System.Windows.WindowStyle> enumeração:  
  
-   <xref:System.Windows.WindowStyle.None>  
  
-   <xref:System.Windows.WindowStyle.SingleBorderWindow> (padrão)  
  
-   <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
-   <xref:System.Windows.WindowStyle.ToolWindow>  
  
 O efeito desses estilos de janela são ilustradas na figura a seguir:  
  
 ![Ilustração de estilos de borda da janela.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Você pode definir <xref:System.Windows.Window.WindowStyle%2A> usando um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação ou código; porque é improvável de ser alterado durante o tempo de vida de uma janela, você provavelmente irá configurá-lo usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Estilo de janela não retangular  
 Também há situações em que a borda estilos que <xref:System.Windows.Window.WindowStyle%2A> permite que você tenha não é suficientes. Por exemplo, você talvez queira criar um aplicativo com uma borda não retangular, como [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] usa.  
  
 Por exemplo, considere a janela de balão de fala mostrada na figura a seguir:  
  
 ![Uma janela de bolhas de fala que diz que me arrastar.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Esse tipo de janela pode ser criado, definindo a <xref:System.Windows.Window.WindowStyle%2A> propriedade para <xref:System.Windows.WindowStyle.None>e usando suporte especial que <xref:System.Windows.Window> tem para transparência.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Essa combinação de valores instrui a janela a ser renderizada completamente transparente. Nesse estado, os adornos da área de não cliente da janela (o menu Fechar, botões Minimizar, Maximizar e Restaurar e assim por diante) não podem ser usados. Consequentemente, você precisa fornecer os seus próprios.  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>Presença da barra de tarefas  

A aparência padrão de uma janela inclui um botão de barra de tarefas, como a mostrada na figura a seguir:

 ![Captura de tela que mostra uma janela com um botão de barra de tarefas.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Alguns tipos de janelas não têm um botão de barra de tarefas, como caixas de mensagens e caixas de diálogo (consulte [visão geral das caixas de diálogo](dialog-boxes-overview.md)). Você pode controlar se o botão de barra de tarefas para uma janela é mostrado, definindo a <xref:System.Windows.Window.ShowInTaskbar%2A> propriedade (`true` por padrão).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>Considerações sobre segurança  
 <xref:System.Windows.Window> requer `UnmanagedCode` permissão de segurança a ser instanciado. Para aplicativos instalados e iniciados no computador local, isso se encaixa no conjunto de permissões concedidas ao aplicativo.  
  
 No entanto, isso fica fora do conjunto de permissões concedidas a aplicativos que são iniciados da Internet ou o Local da intranet zona usando [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]. Consequentemente, os usuários receberão um [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] aviso de segurança e precisarão elevar o conjunto de permissões para o aplicativo para confiança total.  
  
 Além disso, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] não é possível mostrar janelas ou caixas de diálogo por padrão. Para uma discussão sobre as considerações de segurança de aplicativo autônomo, consulte [estratégia de segurança do WPF – segurança da plataforma](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>Outros tipos de janelas  
 <xref:System.Windows.Navigation.NavigationWindow> é uma janela projetada para hospedar conteúdo navegável. Para obter mais informações, consulte [visão geral da navegação](navigation-overview.md)).  
  
 Caixas de diálogo são janelas que geralmente são usadas para coletar informações de um usuário para concluir uma função. Por exemplo, quando um usuário deseja abrir um arquivo, o **abrir arquivo** caixa de diálogo normalmente é exibida por um aplicativo para obter o nome do arquivo do usuário. Para obter mais informações, consulte [Visão geral das caixas de diálogo](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Visão geral das caixas de diálogo](dialog-boxes-overview.md)
- [Compilar um aplicativo WPF](building-a-wpf-application-wpf.md)
