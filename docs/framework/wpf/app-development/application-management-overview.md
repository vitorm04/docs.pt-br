---
title: Visão geral de gerenciamento do aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: a5808261ec9fe957ee993177590446389f219609
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68818014"
---
# <a name="application-management-overview"></a>Visão geral de gerenciamento do aplicativo
Todos os aplicativos tendem a compartilhar um conjunto comum de funcionalidades que se aplicam à implementação e ao gerenciamento do aplicativo. Este tópico fornece uma visão geral da funcionalidade na <xref:System.Windows.Application> classe para criar e gerenciar aplicativos.  

## <a name="the-application-class"></a>A classe do aplicativo  
 No WPF, a funcionalidade comum no escopo do <xref:System.Windows.Application> aplicativo é encapsulada na classe. A <xref:System.Windows.Application> classe inclui a seguinte funcionalidade:  
  
- Acompanhamento e interação com o tempo de vida do aplicativo.  
  
- Recuperação e processamento de parâmetros de linha de comando.  
  
- Detecção e resposta a exceções sem tratamento.  
  
- Compartilhamento de recursos e propriedades no escopo do aplicativo.  
  
- Gerenciamento de janelas de aplicativos autônomos.  
  
- Acompanhamento e gerenciamento da navegação.  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Como realizar tarefas comuns usando a classe do aplicativo  
 Se você não estiver interessado em todos os detalhes da <xref:System.Windows.Application> classe, a tabela a seguir lista algumas das tarefas comuns para <xref:System.Windows.Application> o e como realizá-las. Ao exibir a API e os tópicos relacionados, você pode encontrar mais informações e o código de exemplo.  
  
|Tarefa|Abordagem|  
|----------|--------------|  
|Obter um objeto que representa o aplicativo atual|Use a propriedade <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType>.|  
|Adicionar uma tela de inicialização a um aplicativo|Consulte [Adicionar uma tela inicial a um aplicativo WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).|  
|Iniciar um aplicativo|Use o método <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType>.|  
|Parar um aplicativo|Use o <xref:System.Windows.Application.Shutdown%2A> método <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> do objeto.|  
|Obter os argumentos da linha de comando|Manipule o <xref:System.Windows.Application.Startup?displayProperty=nameWithType> evento e use a <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> propriedade. Para obter um exemplo, consulte <xref:System.Windows.Application.Startup?displayProperty=nameWithType> o evento.|  
|Obter e definir o código de saída do aplicativo|Defina a <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> propriedade <xref:System.Windows.Application.Exit?displayProperty=nameWithType> no manipulador de eventos ou chame o <xref:System.Windows.Application.Shutdown%2A> método e passe um inteiro.|  
|Detectar e responder a exceções sem tratamento|Manipule o <xref:System.Windows.Application.DispatcherUnhandledException> evento.|  
|Obter e definir recursos no escopo do aplicativo|Use a propriedade <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>.|  
|Usar um dicionário de recursos no escopo do aplicativo|Consulte [usar um dicionário de recursos de escopo de aplicativo](how-to-use-an-application-scope-resource-dictionary.md).|  
|Obter e definir propriedades no escopo do aplicativo|Use a propriedade <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType>.|  
|Obter e salvar o estado de um aplicativo|Consulte [persistir e restaurar Propriedades de escopo de aplicativo entre sessões de aplicativo](persist-and-restore-application-scope-properties.md).|  
|Gerencie arquivos de dados que não são de código, incluindo arquivos de recursos, arquivos de conteúdo e arquivos do site de origem.|Consulte [recursos do aplicativo WPF, conteúdo e arquivos de dados](wpf-application-resource-content-and-data-files.md).|  
|Gerenciar janelas em aplicativos autônomos|Consulte [Visão geral do WPF do Windows](wpf-windows-overview.md).|  
|Acompanhar e gerenciar a navegação|Consulte [visão geral de navegação](navigation-overview.md).|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>A definição de aplicativo  
 Para utilizar a funcionalidade da <xref:System.Windows.Application> classe, você deve implementar uma definição de aplicativo. Uma definição de aplicativo do WPF é uma classe derivada de <xref:System.Windows.Application> e é configurada com uma configuração especial do MSBuild.  

### <a name="implementing-an-application-definition"></a>Implementando uma definição de aplicativo  
 Uma definição de aplicativo WPF típica é implementada usando marcação e code-behind. Isso permite usar a marcação para definir de forma declarativa propriedades de aplicativo e recursos e registrar eventos durante a manipulação de eventos e a implementação de um comportamento específico ao aplicativo no code-behind.  
  
 O seguinte exemplo mostra como implementar uma definição de aplicativo usando a marcação e o code-behind:  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 Para permitir que um arquivo de marcação e o arquivo code-behind funcionem juntos, deve ocorrer o seguinte:  
  
- Na marcação, o `Application` elemento deve incluir o `x:Class` atributo. Quando o aplicativo é compilado, a existência do `x:Class` no arquivo de marcação faz com que o MSBuild `partial` crie uma classe derivada de <xref:System.Windows.Application> e que `x:Class` tem o nome especificado pelo atributo. Isso requer a adição de uma declaração de namespace XML para o esquema XAML`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`().
  
- No code-behind, a classe deve ser uma `partial` classe com o mesmo nome que é especificado `x:Class` pelo atributo na marcação e deve derivar de <xref:System.Windows.Application>. Isso permite que o arquivo code-behind seja associado `partial` à classe gerada para o arquivo de marcação quando o aplicativo é compilado (consulte [criando um aplicativo WPF](building-a-wpf-application-wpf.md)).  
  
> [!NOTE]
>  Quando você cria um novo projeto de aplicativo WPF ou projeto de aplicativo de navegador WPF usando o Visual Studio, uma definição de aplicativo é incluída por padrão e é definida usando a marcação e o code-behind.  
  
 Esse código é o mínimo necessário para implementar uma definição de aplicativo. No entanto, uma configuração adicional do MSBuild precisa ser feita à definição do aplicativo antes de compilar e executar o aplicativo.  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>Configurando a definição de aplicativo no MSBuild  
 Aplicativos autônomos e aplicativos de navegador XAML (XBAPs) exigem a implementação de um determinado nível de infraestrutura antes que eles possam ser executados. A parte mais importante dessa infraestrutura é o ponto de entrada. Quando um aplicativo é iniciado por um usuário, o sistema operacional chama o ponto de entrada, que é uma função bem conhecida para a inicialização de aplicativos.  
  
 Tradicionalmente, os desenvolvedores precisam escrever parte ou todo esse código por conta própria, dependendo da tecnologia. No entanto, o WPF gera esse código para você quando o arquivo de marcação da definição do aplicativo é `ApplicationDefinition` configurado como um item do MSBuild, conforme mostrado no seguinte arquivo de projeto do MSBuild:  
  
```xml  
<Project   
  DefaultTargets="Build"  
                        xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  ...  
  <ApplicationDefinition Include="App.xaml" />  
  <Compile Include="App.xaml.cs" />  
  ...  
</Project>  
```  
  
 Como o arquivo code-behind contém o código, ele é marcado como um `Compile` item do MSBuild, como é normal.  
  
 O aplicativo dessas configurações do MSBuild para a marcação e os arquivos code-behind de uma definição de aplicativo faz com que o MSBuild gere um código semelhante ao seguinte:  
  
 [!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
 [!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]  
  
 O código resultante aumenta a definição do aplicativo com o código de infraestrutura adicional, que inclui o método `Main`de ponto de entrada. O <xref:System.STAThreadAttribute> atributo é aplicado `Main` ao método para indicar que o thread principal da interface do usuário para o aplicativo do WPF é um thread STA, que é necessário para aplicativos do WPF. Quando chamado, `Main` o cria uma nova instância `App` do antes de `InitializeComponent` chamar o método para registrar os eventos e definir as propriedades que são implementadas na marcação. Como `InitializeComponent` é gerado para você, você não precisa chamar `InitializeComponent` explicitamente de uma definição de aplicativo como você faz para <xref:System.Windows.Controls.Page> e <xref:System.Windows.Window> implementações. Por fim, <xref:System.Windows.Application.Run%2A> o método é chamado para iniciar o aplicativo.  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>Obtendo o aplicativo atual  
 Como a funcionalidade da <xref:System.Windows.Application> classe é compartilhada em um aplicativo, pode haver apenas uma instância <xref:System.Windows.Application> da classe por <xref:System.AppDomain>. Para impor isso, a <xref:System.Windows.Application> classe é implementada como uma classe singleton (consulte [implementando C#singleton in ](https://go.microsoft.com/fwlink/?LinkId=100567)), que cria uma única instância de si mesma e fornece acesso compartilhado a `static` ela com a <xref:System.Windows.Application.Current%2A> propriedade.  
  
 O código a seguir mostra como adquirir uma referência ao <xref:System.Windows.Application> objeto para o atual. <xref:System.AppDomain>  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A>Retorna uma referência a uma instância da <xref:System.Windows.Application> classe. Se você quiser uma referência à <xref:System.Windows.Application> classe derivada, deverá converter o valor <xref:System.Windows.Application.Current%2A> da propriedade, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 Você pode inspecionar o valor <xref:System.Windows.Application.Current%2A> de a qualquer momento no tempo de vida <xref:System.Windows.Application> de um objeto. No entanto, é necessário ter cuidado. Depois que <xref:System.Windows.Application> a classe é instanciada, há um período durante o qual o estado <xref:System.Windows.Application> do objeto é inconsistente. Durante esse período, <xref:System.Windows.Application> o está executando as várias tarefas de inicialização que são exigidas pelo seu código para execução, incluindo o estabelecimento da infraestrutura do aplicativo, a definição de propriedades e o registro de eventos. Se você tentar usar o <xref:System.Windows.Application> objeto durante esse período, seu código poderá ter resultados inesperados, especialmente se depender das várias <xref:System.Windows.Application> propriedades que estão sendo definidas.  
  
 Quando <xref:System.Windows.Application> conclui seu trabalho de inicialização, seu tempo de vida é realmente iniciado.  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>Tempo de vida do aplicativo  
 O tempo de vida de um aplicativo do WPF é marcado por vários eventos que <xref:System.Windows.Application> são gerados pelo para permitir que você saiba quando seu aplicativo foi iniciado, foi ativado e desativado e foi desligado.  

<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>Splash Screen  
 A partir do .NET Framework 3,5 SP1, você pode especificar uma imagem a ser usada em uma janela de inicialização ou na *tela inicial*. A <xref:System.Windows.SplashScreen> classe facilita a exibição de uma janela de inicialização enquanto seu aplicativo está sendo carregado. A <xref:System.Windows.SplashScreen> janela é criada e exibida antes <xref:System.Windows.Application.Run%2A> de ser chamada. Para obter mais informações, consulte [tempo de inicialização do aplicativo](../advanced/application-startup-time.md) e [Adicionar uma tela inicial a um aplicativo WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>Iniciando um aplicativo  
 Depois <xref:System.Windows.Application.Run%2A> que o for chamado e o aplicativo for inicializado, o aplicativo estará pronto para ser executado. Esse momento é representado quando o <xref:System.Windows.Application.Startup> evento é gerado:  
  
[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]
  
 Neste ponto do tempo de vida de um aplicativo, a coisa mais comum é mostrar uma interface do usuário.  
  
<a name="Showing_a_User_Interface"></a>
### <a name="showing-a-user-interface"></a>Mostrando uma interface do usuário  
 A maioria dos aplicativos Windows autônomos abre um quando eles começam a <xref:System.Windows.Window> ser executados. O <xref:System.Windows.Application.Startup> manipulador de eventos é um local do qual você pode fazer isso, conforme demonstrado pelo código a seguir.  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  O primeiro <xref:System.Windows.Window> a ser instanciado em um aplicativo autônomo torna-se a janela principal do aplicativo por padrão. Esse <xref:System.Windows.Window> objeto é referenciado <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> pela propriedade. O valor da <xref:System.Windows.Application.MainWindow%2A> propriedade pode ser alterado programaticamente se uma janela diferente da primeira <xref:System.Windows.Window> instanciada deve ser a janela principal.  
  
 Quando um XBAP é iniciado pela primeira vez, é mais provável que <xref:System.Windows.Controls.Page>ele navegue para um. Isso será mostrado no código a seguir.  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 Se você manipular <xref:System.Windows.Application.Startup> para abrir apenas um <xref:System.Windows.Window> ou navegar para um <xref:System.Windows.Controls.Page>, você pode definir o `StartupUri` atributo na marcação em vez disso.  
  
 O exemplo a seguir mostra como usar o <xref:System.Windows.Application.StartupUri%2A> de um aplicativo autônomo para abrir um <xref:System.Windows.Window>.  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 O exemplo a seguir mostra como usar <xref:System.Windows.Application.StartupUri%2A> de um XBAP para navegar para um <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 Essa marcação tem o mesmo efeito que o código anterior para abrir uma janela.  
  
> [!NOTE]
>  Para obter mais informações sobre navegação, consulte [visão geral de navegação](navigation-overview.md).  
  
 Você precisa manipular o <xref:System.Windows.Application.Startup> evento para abrir um <xref:System.Windows.Window> se precisar instanciá-lo usando um construtor sem parâmetros ou se precisar definir suas propriedades ou assinar seus eventos antes de mostrá-lo ou precisar processar quaisquer argumentos de linha de comando que foram fornecidos quando o aplicativo foi iniciado.  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>Processando argumentos de linha de comando  
 No Windows, aplicativos autônomos podem ser iniciados por meio de um prompt de comando ou da área de trabalho. Em ambos os casos, os argumentos de linha de comando podem ser passados para o aplicativo. O exemplo a seguir mostra um aplicativo iniciado com um único argumento de linha de comando “/StartMinimized”:  
  
 `wpfapplication.exe /StartMinimized`  
  
 Durante a inicialização do aplicativo, o WPF recupera os argumentos de linha de comando do sistema operacional e os <xref:System.Windows.Application.Startup> passa para o manipulador <xref:System.Windows.StartupEventArgs.Args%2A> de eventos por <xref:System.Windows.StartupEventArgs> meio da Propriedade do parâmetro. É possível recuperar e armazenar os argumentos de linha de comando usando um código semelhante ao mostrado a seguir.  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 O código manipula <xref:System.Windows.Application.Startup> para verificar se o argumento de linha de comando **/StartMinimized** foi fornecido; nesse caso, ele abre a janela principal com <xref:System.Windows.WindowState> um <xref:System.Windows.WindowState.Minimized>de. Observe que, como <xref:System.Windows.Window.WindowState%2A> a propriedade deve ser definida programaticamente <xref:System.Windows.Window> , a principal deve ser aberta explicitamente no código.  
  
 XBAPs não podem recuperar e processar argumentos de linha de comando porque eles são iniciados usando a implantação do ClickOnce (consulte Implantando [um aplicativo do WPF](deploying-a-wpf-application-wpf.md)). No entanto, eles podem recuperar e processar parâmetros de cadeia de caracteres de consulta de URLs usadas para iniciá-los.  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>Ativação e desativação de aplicativos  
 O Windows permite que os usuários alternem entre aplicativos. A maneira mais comum é usar a combinação de teclas ALT+TAB. Um aplicativo só poderá ser alternado se tiver um visível <xref:System.Windows.Window> que um usuário possa selecionar. O atualmente selecionado <xref:System.Windows.Window> é a *janela ativa* (também conhecida como a *janela em primeiro plano*) e <xref:System.Windows.Window> é o que recebe a entrada do usuário. O aplicativo com a janela ativa é o *aplicativo ativo* (ou *aplicativo de primeiro plano*). Um aplicativo se torna o aplicativo ativo nas seguintes circunstâncias:  
  
- Ele é iniciado e mostra um <xref:System.Windows.Window>.  
  
- Um usuário alterna de outro aplicativo selecionando um <xref:System.Windows.Window> no aplicativo.  
  
 Você pode detectar quando um aplicativo se torna ativo manipulando <xref:System.Windows.Application.Activated?displayProperty=nameWithType> o evento.  
  
 Da mesma forma, um aplicativo pode se tornar inativo nas seguintes circunstâncias:  
  
- Um usuário muda para outro aplicativo do aplicativo atual.  
  
- Quando o aplicativo é desligado.  
  
 Você pode detectar quando um aplicativo se torna inativo manipulando <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> o evento.  
  
 O código a seguir mostra como manipular os <xref:System.Windows.Application.Activated> eventos <xref:System.Windows.Application.Deactivated> e para determinar se um aplicativo está ativo.  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 Um <xref:System.Windows.Window> também pode ser ativado e desativado. Consulte <xref:System.Windows.Window.Activated?displayProperty=nameWithType> e <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType> para obter mais informações.  
  
> [!NOTE]
>  Nem <xref:System.Windows.Application.Activated?displayProperty=nameWithType> nem<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> é gerado para XBAPs.  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>Desligamento do aplicativo  
 A vida de um aplicativo termina quando ele é desligado, o que pode ocorrer pelos seguintes motivos:  
  
- Um usuário fecha A <xref:System.Windows.Window>cada.  
  
- Um usuário fecha o principal <xref:System.Windows.Window>.  
  
- Um usuário encerra a sessão do Windows fazendo logoff ou desligando.  
  
- Uma condição específica ao aplicativo foi atendida.  
  
 Para ajudá-lo a gerenciar o <xref:System.Windows.Application> desligamento de aplicativo <xref:System.Windows.Application.ShutdownMode%2A> , o fornece o <xref:System.Windows.Application.SessionEnding> <xref:System.Windows.Application.Shutdown%2A> método <xref:System.Windows.Application.Exit> , a propriedade e os eventos e.  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A>Só pode ser chamado a partir de aplicativos <xref:System.Security.Permissions.UIPermission>que tenham o. Os aplicativos autônomos do WPF sempre têm essa permissão. No entanto, os XBAPs executados na área de segurança de confiança parcial da zona da Internet não têm.  
  
#### <a name="shutdown-mode"></a>Modo de desligamento  
 A maioria dos aplicativos é desligada quando todas as janelas são fechadas ou quando a janela principal é fechada. No entanto, às vezes, outras condições específicas ao aplicativo podem determinar quando um aplicativo é desligado. Você pode especificar as condições sob as quais seu aplicativo será desligado Configurando <xref:System.Windows.Application.ShutdownMode%2A> com um dos seguintes <xref:System.Windows.ShutdownMode> valores de enumeração:  
  
- <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 O valor padrão de <xref:System.Windows.Application.ShutdownMode%2A> é <xref:System.Windows.ShutdownMode.OnLastWindowClose>, o que significa que um aplicativo é desligado automaticamente quando a última janela do aplicativo é fechada pelo usuário. No entanto, se seu aplicativo deve ser desligado quando a janela principal é fechada, o WPF faz isso automaticamente se <xref:System.Windows.Application.ShutdownMode%2A> você <xref:System.Windows.ShutdownMode.OnMainWindowClose>definir como. Isso é mostrado no exemplo a seguir.  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 Quando você tiver condições de desligamento específicas do aplicativo <xref:System.Windows.Application.ShutdownMode%2A> , <xref:System.Windows.ShutdownMode.OnExplicitShutdown>defina como. Nesse caso, é sua responsabilidade encerrar um aplicativo chamando explicitamente o <xref:System.Windows.Application.Shutdown%2A> método; caso contrário, seu aplicativo continuará em execução mesmo se todas as janelas estiverem fechadas. Observe que <xref:System.Windows.Application.Shutdown%2A> é chamado implicitamente quando o <xref:System.Windows.Application.ShutdownMode%2A> é <xref:System.Windows.ShutdownMode.OnLastWindowClose> ou <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A>pode ser definido de um XBAP, mas é ignorado; um XBAP é sempre desligado quando é navegado para fora de um navegador ou quando o navegador que hospeda o XBAP é fechado. Para obter mais informações, consulte [Visão geral de navegação](navigation-overview.md).  
  
#### <a name="session-ending"></a>Encerramento da sessão  
 As condições de desligamento que são <xref:System.Windows.Application.ShutdownMode%2A> descritas pela propriedade são específicas de um aplicativo. No entanto, em alguns casos, um aplicativo pode ser desligado como resultado de uma condição externa. A condição externa mais comum ocorre quando um usuário encerra a sessão do Windows seguindo as seguintes ações:  
  
- Logoff  
  
- Desligamento  
  
- Reinicialização  
  
- Hibernação  
  
 Para detectar quando uma sessão do Windows termina, você pode manipular <xref:System.Windows.Application.SessionEnding> o evento, conforme ilustrado no exemplo a seguir.  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 Neste exemplo, o código inspeciona a <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> propriedade para determinar como a sessão do Windows está terminando. Ele usa esse valor para exibir uma mensagem de confirmação para o usuário. Se o usuário não quiser que a sessão seja encerrada, o código <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> será `true` definido como para impedir que a sessão do Windows seja encerrada.  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding>Não é gerado para XBAPs.

#### <a name="exit"></a>Sair  
 Quando um aplicativo é desligado, ele pode precisar executar algum processamento final, como persistir o estado do aplicativo. Para essas situações, você pode manipular o <xref:System.Windows.Application.Exit> evento, como o `App_Exit` manipulador de eventos faz no exemplo a seguir. Ele é definido como um manipulador de eventos no arquivo *app. XAML* . Sua implementação é realçada nos arquivos *app.XAML.cs* e *Application. XAML. vb* .
  
[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]  
  
 [!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
 [!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]  
  
 Para obter o exemplo completo, consulte [persistir e restaurar Propriedades de escopo de aplicativo entre sessões de aplicativo](persist-and-restore-application-scope-properties.md).  
  
 <xref:System.Windows.Application.Exit>pode ser tratado por aplicativos autônomos e XBAPs. Para XBAPs, <xref:System.Windows.Application.Exit> é gerado quando nas seguintes circunstâncias:  
  
- Um XBAP é navegado para fora do.  
  
- No Internet Explorer, quando a guia que está hospedando o XBAP é fechada.  
  
- Quando o navegador é fechado.  
  
#### <a name="exit-code"></a>Código de Saída  
 Na maioria das vezes, os aplicativos são iniciados pelo sistema operacional em resposta a uma solicitação do usuário. No entanto, um aplicativo pode ser iniciado por outro aplicativo para executar uma tarefa específica. Quando o aplicativo iniciado é desligado, o aplicativo que o iniciou talvez deseje saber a condição na qual o aplicativo iniciado foi desligado. Nessas situações, o Windows permite que os aplicativos retornem um código de saída do aplicativo no desligamento. Por padrão, os aplicativos do WPF retornam um valor de código de saída de 0.  
  
> [!NOTE]
>  Quando você depura do Visual Studio, o código de saída do aplicativo é exibido na janela de **saída** quando o aplicativo é desligado, em uma mensagem semelhante à seguinte:  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  Abra a janela **saída** clicando em **saída** no menu **Exibir** .  
  
 Para alterar o código de saída, você pode chamar <xref:System.Windows.Application.Shutdown%28System.Int32%29> a sobrecarga, que aceita um argumento inteiro para ser o código de saída:  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 Você pode detectar o valor do código de saída e alterá-lo, manipulando <xref:System.Windows.Application.Exit> o evento. O <xref:System.Windows.Application.Exit> manipulador de eventos é passado <xref:System.Windows.ExitEventArgs> para um que fornece acesso ao código de saída <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> com a propriedade. Para obter mais informações, consulte <xref:System.Windows.Application.Exit>.  
  
> [!NOTE]
>  Você pode definir o código de saída em aplicativos autônomos e XBAPs. No entanto, o valor do código de saída é ignorado para XBAPs.  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>Exceções sem tratamento  
 Às vezes, um aplicativo pode ser desligado em condições anormais, como quando uma exceção não esperada é gerada. Nesse caso, o aplicativo pode não ter o código para detectar e processar a exceção. Esse tipo de exceção é uma exceção sem tratamento; é exibida uma notificação semelhante à mostrada na figura a seguir antes de o aplicativo ser fechado.  
  
 ![Captura de tela que mostra uma notificação de exceção sem tratamento.](./media/application-management-overview/unhandled-exception-notification.png)  
  
 Da perspectiva da experiência do usuário, é melhor que um aplicativo evite esse comportamento padrão fazendo algumas ou todas as seguintes opções:  
  
- Exibição de informações amigáveis.  
  
- Tentativa de manter um aplicativo em execução.  
  
- Registrando informações detalhadas de exceção amigável do desenvolvedor no log de eventos do Windows.  
  
 A implementação desse suporte depende da capacidade de detectar exceções sem tratamento, para as quais o <xref:System.Windows.Application.DispatcherUnhandledException> evento é gerado.  
  
[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]  
  
 O <xref:System.Windows.Application.DispatcherUnhandledException> manipulador de eventos é passado <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> a um parâmetro que contém informações contextuais sobre a exceção sem tratamento, incluindo a exceção<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>em si (). Você pode usar essas informações para determinar como tratar a exceção.  
  
 Quando você manipula <xref:System.Windows.Application.DispatcherUnhandledException>, você deve definir a <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> Propriedade como `true`; caso contrário, o WPF ainda considera a exceção como sem tratamento e reverte para o comportamento padrão descrito anteriormente. Se uma exceção sem tratamento for gerada e o <xref:System.Windows.Application.DispatcherUnhandledException> evento não for tratado ou se o evento for manipulado e <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> for definido como `false`, o aplicativo será desligado imediatamente. Além disso, nenhum <xref:System.Windows.Application> outro evento é gerado. Consequentemente, você precisa manipular <xref:System.Windows.Application.DispatcherUnhandledException> se seu aplicativo tem código que deve ser executado antes de o aplicativo ser desligado.  
  
 Embora um aplicativo possa ser desligado como resultado de uma exceção sem tratamento, geralmente, um aplicativo é desligado em resposta a uma solicitação do usuário, conforme abordado na próxima seção.  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>Eventos de Vida Útil do Aplicativo  
 Os aplicativos e XBAPs autônomos não têm exatamente os mesmos tempos de vida. A figura a seguir ilustra os principais eventos no tempo de vida de um aplicativo autônomo e mostra a sequência na qual são acionados.  
  
 ![Aplicativo autônomo &#45; Eventos de objeto do aplicativo](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 Da mesma forma, a figura a seguir ilustra os principais eventos no tempo de vida de um XBAP e mostra a sequência na qual eles são gerados.  
  
 ![XBAP &#45; Eventos de objeto do aplicativo](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Application>
- [Visão geral das janelas do WPF](wpf-windows-overview.md)
- [Visão geral de navegação](navigation-overview.md)
- [Arquivos de recursos, de conteúdo e de dados de aplicativos do WPF](wpf-application-resource-content-and-data-files.md)
- [URIs "pack://" no WPF](pack-uris-in-wpf.md)
- [Modelo de aplicativo: Tópicos de instruções](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))
- [Desenvolvimento de aplicativos](index.md)
