---
title: Visão geral de gerenciamento do aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: ba8d07a26b7e6abc511e5b24db26162b46a2b0a1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042251"
---
# <a name="application-management-overview"></a>Visão geral de gerenciamento do aplicativo
Todos os aplicativos tendem a compartilhar um conjunto comum de funcionalidades que se aplicam à implementação e ao gerenciamento do aplicativo. Este tópico fornece uma visão geral da funcionalidade no <xref:System.Windows.Application> classe para criar e gerenciar aplicativos.  
   
  
## <a name="the-application-class"></a>A classe do aplicativo  
 Na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], funcionalidade comum no escopo do aplicativo é encapsulada no <xref:System.Windows.Application> classe. O <xref:System.Windows.Application> classe inclui as seguintes funcionalidades:  
  
-   Acompanhamento e interação com o tempo de vida do aplicativo.  
  
-   Recuperação e processamento de parâmetros de linha de comando.  
  
-   Detecção e resposta a exceções sem tratamento.  
  
-   Compartilhamento de recursos e propriedades no escopo do aplicativo.  
  
-   Gerenciamento de janelas de aplicativos autônomos.  
  
-   Acompanhamento e gerenciamento da navegação.  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Como realizar tarefas comuns usando a classe do aplicativo  
 Se você não estiver interessado em todos os detalhes do <xref:System.Windows.Application> classe, a tabela a seguir lista algumas das tarefas comuns para <xref:System.Windows.Application> e como realizá-las. Ao exibir a API e os tópicos relacionados, você pode encontrar mais informações e o código de exemplo.  
  
|Tarefa|Abordagem|  
|----------|--------------|  
|Obter um objeto que representa o aplicativo atual|Use a propriedade <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType>.|  
|Adicionar uma tela de inicialização a um aplicativo|Ver [adicionar uma tela inicial a um aplicativo WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).|  
|Iniciar um aplicativo|Use o método <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType>.|  
|Parar um aplicativo|Use o <xref:System.Windows.Application.Shutdown%2A> método da <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> objeto.|  
|Obter os argumentos da linha de comando|Lidar com o <xref:System.Windows.Application.Startup?displayProperty=nameWithType> evento e use o <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> propriedade. Por exemplo, consulte o <xref:System.Windows.Application.Startup?displayProperty=nameWithType> eventos.|  
|Obter e definir o código de saída do aplicativo|Definir o <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> propriedade no <xref:System.Windows.Application.Exit?displayProperty=nameWithType> manipulador de eventos ou a chamada a <xref:System.Windows.Application.Shutdown%2A> método e passar em um número inteiro.|  
|Detectar e responder a exceções sem tratamento|Manipular o <xref:System.Windows.Application.DispatcherUnhandledException> eventos.|  
|Obter e definir recursos no escopo do aplicativo|Use a propriedade <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>.|  
|Usar um dicionário de recursos no escopo do aplicativo|Ver [usar um dicionário de recursos de escopo do aplicativo](../../../../docs/framework/wpf/app-development/how-to-use-an-application-scope-resource-dictionary.md).|  
|Obter e definir propriedades no escopo do aplicativo|Use a propriedade <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType>.|  
|Obter e salvar o estado de um aplicativo|Ver [persistir e restaurar propriedades de escopo do aplicativo em sessões de aplicativo](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).|  
|Gerencie arquivos de dados que não são de código, incluindo arquivos de recursos, arquivos de conteúdo e arquivos do site de origem.|Ver [recurso de aplicativo do WPF, conteúdo e arquivos de dados](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).|  
|Gerenciar janelas em aplicativos autônomos|Consulte [Visão geral do WPF do Windows](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).|  
|Acompanhar e gerenciar a navegação|Ver [visão geral da navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md).|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>A definição de aplicativo  
 Para utilizar a funcionalidade do <xref:System.Windows.Application> classe, você deve implementar uma definição de aplicativo. Um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definição de aplicativo é uma classe que deriva de <xref:System.Windows.Application> e está configurado com um especial [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] configuração.  
  
### <a name="implementing-an-application-definition"></a>Implementando uma definição de aplicativo  
 Um típico [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definição de aplicativo é implementada usando marcação e code-behind. Isso permite usar a marcação para definir de forma declarativa propriedades de aplicativo e recursos e registrar eventos durante a manipulação de eventos e a implementação de um comportamento específico ao aplicativo no code-behind.  
  
 O seguinte exemplo mostra como implementar uma definição de aplicativo usando a marcação e o code-behind:  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 Para permitir que um arquivo de marcação e o arquivo code-behind funcionem juntos, deve ocorrer o seguinte:  
  
-   Na marcação, o `Application` elemento deve incluir o `x:Class` atributo. Quando o aplicativo é compilado, a existência de `x:Class` na marcação arquivo faz com que [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] para criar um `partial` classe que deriva de <xref:System.Windows.Application> e tem o nome especificado pelo `x:Class` atributo. Isso exige a adição de um [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] declaração de namespace para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] esquema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).  
  
-   No code-behind, a classe deve ser um `partial` classe com o mesmo nome que é especificado pelo `x:Class` do atributo na marcação e deve derivar de <xref:System.Windows.Application>. Isso permite que o arquivo code-behind seja associado a `partial` classe que é gerada para o arquivo de marcação quando o aplicativo é compilado (consulte [criando um aplicativo WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
> [!NOTE]
>  Quando você cria um novo projeto de aplicativo do WPF ou o projeto de aplicativo de navegador WPF usando [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], uma definição de aplicativo é incluída por padrão e é definida usando marcação e code-behind.  
  
 Esse código é o mínimo necessário para implementar uma definição de aplicativo. No entanto, adicional [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] configuração precisa ser feita à definição de aplicativo antes de compilar e executar o aplicativo.  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>Configurando a definição de aplicativo no MSBuild  
 Aplicativos autônomos e [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] exigir a implementação de um certo nível de infraestrutura antes de serem executados. A parte mais importante dessa infraestrutura é o ponto de entrada. Quando um aplicativo é iniciado por um usuário, o sistema operacional chama o ponto de entrada, que é uma função bem conhecida para a inicialização de aplicativos.  
  
 Tradicionalmente, os desenvolvedores precisam escrever parte ou todo esse código por conta própria, dependendo da tecnologia. No entanto, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gera esse código para você quando o arquivo de marcação da definição de aplicativo é configurado como um [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` do item, conforme mostrado na seguinte [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] arquivo de projeto:  
  
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
  
 Porque o arquivo code-behind contém código, ele é marcado como um [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` de item, como é normal.  
  
 A aplicação dessas [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] faz com que as configurações para os arquivos de marcação e code-behind de uma definição de aplicativo [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] para gerar um código semelhante ao seguinte:  
  
 [!code-csharp[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode1)]
 [!code-vb[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode1)]  
[!code-csharp[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode2)]
[!code-vb[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode2)]  
  
 O código resultante aumenta sua definição de aplicativo com código de infraestrutura adicional, que inclui o método de ponto de entrada `Main`. O <xref:System.STAThreadAttribute> atributo é aplicado a `Main` método para indicar que principal [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread para o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo é um thread STA, que é necessário para [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos. Quando chamado, `Main` cria uma nova instância da `App` antes de chamar o `InitializeComponent` método para registrar os eventos e definir as propriedades que são implementadas na marcação. Porque `InitializeComponent` é gerado para você, você não precisa chamar explicitamente `InitializeComponent` de uma definição de aplicativo como faria para <xref:System.Windows.Controls.Page> e <xref:System.Windows.Window> implementações. Por fim, o <xref:System.Windows.Application.Run%2A> método é chamado para iniciar o aplicativo.  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>Obtendo o aplicativo atual  
 Porque a funcionalidade dos <xref:System.Windows.Application> classe são compartilhados entre um aplicativo, pode haver apenas uma instância das <xref:System.Windows.Application> classe por <xref:System.AppDomain>. Para impor isso, o <xref:System.Windows.Application> classe é implementada como uma classe singleton (consulte [implementando Singleton no c#](https://go.microsoft.com/fwlink/?LinkId=100567)), que cria uma única instância de si mesma e fornece acesso compartilhado a com o `static` <xref:System.Windows.Application.Current%2A> propriedade.  
  
 O código a seguir mostra como adquirir uma referência para o <xref:System.Windows.Application> objeto atual <xref:System.AppDomain>.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A> Retorna uma referência a uma instância da <xref:System.Windows.Application> classe. Se você quiser que uma referência ao seu <xref:System.Windows.Application> você deve converter o valor de classe derivada a <xref:System.Windows.Application.Current%2A> propriedade, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 Você pode inspecionar o valor de <xref:System.Windows.Application.Current%2A> em qualquer ponto no tempo de vida de um <xref:System.Windows.Application> objeto. No entanto, é necessário ter cuidado. Após o <xref:System.Windows.Application> classe é instanciada, há um período durante o qual o estado do <xref:System.Windows.Application> objeto está inconsistente. Durante esse período, <xref:System.Windows.Application> executar várias tarefas de inicialização que são necessárias para o código em execução, incluindo estabelecendo uma infraestrutura de aplicativo, definir propriedades e registro de eventos. Se você tentar usar o <xref:System.Windows.Application> do objeto durante esse período, seu código pode ter resultados inesperados, especialmente se ele depende das várias <xref:System.Windows.Application> propriedades sendo definidas.  
  
 Quando <xref:System.Windows.Application> conclui seu trabalho de inicialização, seu tempo de vida realmente será iniciado.  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>Tempo de vida do aplicativo  
 O tempo de vida de um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo é marcado por vários eventos que são gerados por <xref:System.Windows.Application> para que você saiba quando seu aplicativo foi iniciada, foi ativado e desativado e foi desligado.  
  
  
<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>Splash Screen  
 A partir de [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], você pode especificar uma imagem a ser usada em uma janela de inicialização, ou *tela inicial*. O <xref:System.Windows.SplashScreen> classe torna fácil exibir uma janela de inicialização, enquanto o carregamento do aplicativo. O <xref:System.Windows.SplashScreen> janela é criada e mostrada antes <xref:System.Windows.Application.Run%2A> é chamado. Para obter mais informações, consulte [tempo de inicialização do aplicativo](../../../../docs/framework/wpf/advanced/application-startup-time.md) e [adicionar uma tela inicial a um aplicativo WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>Iniciando um aplicativo  
 Depois de <xref:System.Windows.Application.Run%2A> é chamado e o aplicativo é inicializado, o aplicativo está pronto para ser executado. Neste momento é sinalizado quando o <xref:System.Windows.Application.Startup> é gerado:  
  
 [!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind1)]
 [!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind1)]  
[!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind2)]
[!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind2)]  
  
 Neste ponto no tempo de vida do aplicativo, a coisa mais comum a fazer é mostrar um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Showing_a_User_Interface"></a>   
### <a name="showing-a-user-interface"></a>Mostrando uma interface do usuário  
 A maioria dos aplicativos do Windows autônomo abrir um <xref:System.Windows.Window> quando começa a executar. O <xref:System.Windows.Application.Startup> manipulador de eventos é um local de onde você pode fazer isso, conforme demonstrado pelo código a seguir.  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  A primeira <xref:System.Windows.Window> para ser instanciado em um autônomo do aplicativo se torna a janela principal do aplicativo por padrão. Isso <xref:System.Windows.Window> objeto é referenciado pelo <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> propriedade. O valor da <xref:System.Windows.Application.MainWindow%2A> propriedade pode ser alterada programaticamente se uma janela diferente do que a primeira instanciado <xref:System.Windows.Window> deve ser a janela principal.  
  
 Quando um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] inicia a primeira vez, ele provavelmente vai navegar para um <xref:System.Windows.Controls.Page>. Isso será mostrado no código a seguir.  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 Se você manipular <xref:System.Windows.Application.Startup> para abrir somente um <xref:System.Windows.Window> ou navegue até um <xref:System.Windows.Controls.Page>, você pode definir o `StartupUri` atributo na marcação, em vez disso.  
  
 O exemplo a seguir mostra como usar o <xref:System.Windows.Application.StartupUri%2A> de um aplicativo autônomo para abrir um <xref:System.Windows.Window>.  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 O exemplo a seguir mostra como usar <xref:System.Windows.Application.StartupUri%2A> de um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] para navegar até um <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 Essa marcação tem o mesmo efeito que o código anterior para abrir uma janela.  
  
> [!NOTE]
>  Para obter mais informações sobre navegação, consulte [visão geral da navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
 Você precisa lidar com o <xref:System.Windows.Application.Startup> evento para abrir um <xref:System.Windows.Window> se você precisa criar uma instância dele usando um construtor não padrão, ou você precisa definir suas propriedades ou assinar seus eventos antes de mostrá-lo, ou você precisa processar argumentos de linha de comando que foram fornecidos quando o aplicativo foi iniciado.  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>Processando argumentos de linha de comando  
 No Windows, aplicativos autônomos podem ser iniciados a partir de um prompt de comando ou a área de trabalho. Em ambos os casos, os argumentos de linha de comando podem ser passados para o aplicativo. O exemplo a seguir mostra um aplicativo iniciado com um único argumento de linha de comando “/StartMinimized”:  
  
 `wpfapplication.exe /StartMinimized`  
  
 Durante a inicialização do aplicativo, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] recupera os argumentos de linha de comando do sistema operacional e os passa para o <xref:System.Windows.Application.Startup> manipulador de eventos por meio de <xref:System.Windows.StartupEventArgs.Args%2A> propriedade do <xref:System.Windows.StartupEventArgs> parâmetro. É possível recuperar e armazenar os argumentos de linha de comando usando um código semelhante ao mostrado a seguir.  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 O código manipula <xref:System.Windows.Application.Startup> para verificar se o **/StartMinimized** argumento de linha de comando foi fornecido; nesse caso, ele abre a janela principal com um <xref:System.Windows.WindowState> de <xref:System.Windows.WindowState.Minimized>. Observe que, como o <xref:System.Windows.Window.WindowState%2A> propriedade deve ser definida programaticamente, principal <xref:System.Windows.Window> precisa ser aberta explicitamente no código.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] não é possível recuperar e processar argumentos de linha de comando porque eles são iniciados usando [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] implantação (consulte [Implantando um aplicativo WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)). No entanto, eles podem recuperar e processar parâmetros de cadeia de caracteres de consulta de URLs usadas para iniciá-los.  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>Ativação e desativação de aplicativos  
 Windows permite que os usuários alternem entre aplicativos. A maneira mais comum é usar a combinação de teclas ALT+TAB. Um aplicativo só pode ser alternado para se ele tiver um visível <xref:System.Windows.Window> que um usuário pode selecionar. Selecionado no momento <xref:System.Windows.Window> é o *janela ativa* (também conhecido como o *janela em primeiro plano*) e é o <xref:System.Windows.Window> que recebe entrada do usuário. O aplicativo com a janela ativa é o *aplicativo ativo* (ou *aplicativo em primeiro plano*). Um aplicativo se torna o aplicativo ativo nas seguintes circunstâncias:  
  
-   Ele é iniciado e mostra um <xref:System.Windows.Window>.  
  
-   Um usuário alterna de outro aplicativo, selecionando um <xref:System.Windows.Window> no aplicativo.  
  
 Você pode detectar quando um aplicativo se torna ativo manipulando o <xref:System.Windows.Application.Activated?displayProperty=nameWithType> eventos.  
  
 Da mesma forma, um aplicativo pode se tornar inativo nas seguintes circunstâncias:  
  
-   Um usuário muda para outro aplicativo do aplicativo atual.  
  
-   Quando o aplicativo é desligado.  
  
 Você pode detectar quando um aplicativo se torna inativo manipulando o <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> eventos.  
  
 O código a seguir mostra como lidar com o <xref:System.Windows.Application.Activated> e <xref:System.Windows.Application.Deactivated> eventos para determinar se um aplicativo está ativo.  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 Um <xref:System.Windows.Window> também pode ser ativado e desativado. Consulte <xref:System.Windows.Window.Activated?displayProperty=nameWithType> e <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType> para obter mais informações.  
  
> [!NOTE]
>  Nem <xref:System.Windows.Application.Activated?displayProperty=nameWithType> nem <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> é gerado para [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>Desligamento do aplicativo  
 A vida de um aplicativo termina quando ele é desligado, o que pode ocorrer pelos seguintes motivos:  
  
-   Um usuário fecha cada <xref:System.Windows.Window>.  
  
-   Um usuário fecha principal <xref:System.Windows.Window>.  
  
-   Um usuário encerra a sessão do Windows fazendo logoff ou desligando.  
  
-   Uma condição específica ao aplicativo foi atendida.  
  
 Para ajudá-lo a gerenciar o desligamento do aplicativo <xref:System.Windows.Application> fornece a <xref:System.Windows.Application.Shutdown%2A> método, o <xref:System.Windows.Application.ShutdownMode%2A> propriedade e o <xref:System.Windows.Application.SessionEnding> e <xref:System.Windows.Application.Exit> eventos.  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A> só pode ser chamado de aplicativos que possuem <xref:System.Security.Permissions.UIPermission>. Autônomo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos sempre têm essa permissão. No entanto, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] em execução na área de restrita de segurança de confiança parcial de zona da Internet não fizer isso.  
  
#### <a name="shutdown-mode"></a>Modo de desligamento  
 A maioria dos aplicativos é desligada quando todas as janelas são fechadas ou quando a janela principal é fechada. No entanto, às vezes, outras condições específicas ao aplicativo podem determinar quando um aplicativo é desligado. Você pode especificar as condições sob as quais seu aplicativo será desligado configurando <xref:System.Windows.Application.ShutdownMode%2A> com um dos seguintes <xref:System.Windows.ShutdownMode> valores de enumeração:  
  
-   <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 O valor padrão de <xref:System.Windows.Application.ShutdownMode%2A> é <xref:System.Windows.ShutdownMode.OnLastWindowClose>, que significa que um aplicativo encerra automaticamente quando a última janela do aplicativo é fechada pelo usuário. No entanto, se seu aplicativo deve ser desligado quando a janela principal é fechada, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] faz isso automaticamente se você definir <xref:System.Windows.Application.ShutdownMode%2A> para <xref:System.Windows.ShutdownMode.OnMainWindowClose>. Isso é mostrado no exemplo a seguir.  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 Quando você tem condições de desligamento específicas do aplicativo, você definir <xref:System.Windows.Application.ShutdownMode%2A> para <xref:System.Windows.ShutdownMode.OnExplicitShutdown>. Nesse caso, é sua responsabilidade desligar um aplicativo explicitamente chamando o <xref:System.Windows.Application.Shutdown%2A> método; caso contrário, seu aplicativo continuará em execução, mesmo se todas as janelas estiverem fechadas. Observe que <xref:System.Windows.Application.Shutdown%2A> é chamado implicitamente quando o <xref:System.Windows.Application.ShutdownMode%2A> seja <xref:System.Windows.ShutdownMode.OnLastWindowClose> ou <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A> pode ser definido de uma [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], mas é ignorada; um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] é sempre desligado quando ele é navegado para fora em um navegador ou quando o navegador que hospeda o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] está fechado. Para obter mais informações, consulte [Visão geral de navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
#### <a name="session-ending"></a>Encerramento da sessão  
 As condições de desligamento descritas pela <xref:System.Windows.Application.ShutdownMode%2A> propriedade são específicas para um aplicativo. No entanto, em alguns casos, um aplicativo pode ser desligado como resultado de uma condição externa. A condição externa mais comum ocorre quando um usuário encerra a sessão do Windows com as seguintes ações:  
  
-   Logoff  
  
-   Desligamento  
  
-   Reinicialização  
  
-   Hibernação  
  
 Para detectar quando termina de uma sessão do Windows, você pode manipular o <xref:System.Windows.Application.SessionEnding> evento, conforme ilustrado no exemplo a seguir.  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 Neste exemplo, o código inspeciona o <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> propriedade para determinar como a sessão do Windows está terminando. Ele usa esse valor para exibir uma mensagem de confirmação para o usuário. Se o usuário não quiser que a sessão seja encerrada, o código define <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> para `true` para impedir que a sessão do Windows de terminação.  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding> não é gerado para [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
#### <a name="exit"></a>Sair  
 Quando um aplicativo é desligado, ele pode precisar executar algum processamento final, como persistir o estado do aplicativo. Nessas situações, você pode manipular o <xref:System.Windows.Application.Exit> eventos.  
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml1)]  
[!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml2)]  
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind1)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind1)]  
[!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind2)]
[!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind2)]  
  
 Para o exemplo completo, consulte [persistir e restaurar propriedades de escopo do aplicativo em sessões de aplicativo](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).  
  
 <xref:System.Windows.Application.Exit> pode ser tratado por aplicativos autônomos e [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Para [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], <xref:System.Windows.Application.Exit> é acionado nas seguintes circunstâncias:  
  
-   Um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] é navegado para fora.  
  
-   Na [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)], quando a guia que está hospedando o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] está fechado.  
  
-   Quando o navegador é fechado.  
  
#### <a name="exit-code"></a>Código de Saída  
 Na maioria das vezes, os aplicativos são iniciados pelo sistema operacional em resposta a uma solicitação do usuário. No entanto, um aplicativo pode ser iniciado por outro aplicativo para executar uma tarefa específica. Quando o aplicativo iniciado é desligado, o aplicativo que o iniciou talvez deseje saber a condição na qual o aplicativo iniciado foi desligado. Nessas situações, o Windows permite que aplicativos retornar um código de saída do aplicativo durante o desligamento. Por padrão, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos retornar um valor de código de saída igual a 0.  
  
> [!NOTE]
>  Quando você depura da [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], o código de saída do aplicativo é exibido em de **saída** janela quando o aplicativo é desligado, em uma mensagem é semelhante ao seguinte:  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  Você abre o **saída** janela clicando **saída** no **exibição** menu.  
  
 Para alterar o código de saída, você pode chamar o <xref:System.Windows.Application.Shutdown%28System.Int32%29> sobrecarregar, que aceita um argumento de inteiro para ser o código de saída:  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 Você pode detectar o valor do código de saída e alterá-la, manipulando o <xref:System.Windows.Application.Exit> eventos. O <xref:System.Windows.Application.Exit> manipulador de eventos recebe um <xref:System.Windows.ExitEventArgs> que fornece acesso ao código de saída com o <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> propriedade. Para obter mais informações, consulte <xref:System.Windows.Application.Exit>.  
  
> [!NOTE]
>  Você pode definir o código de saída em aplicativos autônomos e [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. No entanto, o valor do código de saída é ignorado para [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>Exceções sem tratamento  
 Às vezes, um aplicativo pode ser desligado em condições anormais, como quando uma exceção não esperada é gerada. Nesse caso, o aplicativo pode não ter o código para detectar e processar a exceção. Esse tipo de exceção é uma exceção sem tratamento; é exibida uma notificação semelhante à mostrada na figura a seguir antes de o aplicativo ser fechado.  
  
 ![Notificação de exceção sem tratamento](../../../../docs/framework/wpf/app-development/media/applicationmanagementoverviewfigure2.png "ApplicationManagementOverviewFigure2")  
  
 Da perspectiva da experiência do usuário, é melhor que um aplicativo evite esse comportamento padrão fazendo algumas ou todas as seguintes opções:  
  
-   Exibição de informações amigáveis.  
  
-   Tentativa de manter um aplicativo em execução.  
  
-   Gravação, amigável para desenvolvedores, exceção informações detalhadas no log de eventos do Windows.  
  
 Implementar esse suporte depende do que está sendo capaz de detectar exceções sem tratamento, que é o que o <xref:System.Windows.Application.DispatcherUnhandledException> é gerado para.  
  
 [!code-xaml[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
 [!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind1)]
 [!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind1)]  
[!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind2)]
[!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind2)]  
  
 O <xref:System.Windows.Application.DispatcherUnhandledException> manipulador de eventos recebe um <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> parâmetro que contém informações contextuais sobre a exceção sem tratamento, incluindo a própria exceção (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>). Você pode usar essas informações para determinar como tratar a exceção.  
  
 Quando você manipula <xref:System.Windows.Application.DispatcherUnhandledException>, você deve definir o <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> propriedade `true`; caso contrário, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ainda considerará a exceção sem tratamento e reverterá para o comportamento padrão descrito anteriormente. Se uma exceção sem tratamento é gerada e o <xref:System.Windows.Application.DispatcherUnhandledException> evento não for tratado ou o evento é manipulado e <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> é definido como `false`, o aplicativo será desligado imediatamente. Além disso, nenhum outro <xref:System.Windows.Application> eventos são gerados. Consequentemente, você precisa tratar <xref:System.Windows.Application.DispatcherUnhandledException> se seu aplicativo tiver um código que deve ser executado antes que o aplicativo é desligado.  
  
 Embora um aplicativo possa ser desligado como resultado de uma exceção sem tratamento, geralmente, um aplicativo é desligado em resposta a uma solicitação do usuário, conforme abordado na próxima seção.  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>Eventos de Vida Útil do Aplicativo  
 Aplicativos autônomos e [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] não tem exatamente os mesmos tempos de vida. A figura a seguir ilustra os principais eventos no tempo de vida de um aplicativo autônomo e mostra a sequência na qual são acionados.  
  
 ![Aplicativo autônomo &#45; Eventos de objeto do aplicativo](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 Da mesma forma, a figura a seguir ilustra os principais eventos no tempo de vida de um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]e mostra a sequência na qual eles são gerados.  
  
 ![XBAP &#45; Eventos de objeto do aplicativo](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Application>  
 [Visão geral das janelas do WPF](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)  
 [Visão geral de navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [Arquivos de recursos, de conteúdo e de dados de aplicativos do WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)  
 [URIs "pack://" no WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Modelo de aplicativo: Tópicos de instruções](https://msdn.microsoft.com/library/76771b09-3688-4d1c-8818-9b3f4cf39a30)  
 [Desenvolvimento de aplicativos](../../../../docs/framework/wpf/app-development/index.md)
