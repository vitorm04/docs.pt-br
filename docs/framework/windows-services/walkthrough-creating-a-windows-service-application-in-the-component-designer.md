---
title: 'Instruções passo a passo: criando um aplicativo de Serviço Windows no Designer de Componente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Service applications, walkthroughs
- Windows Service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
manager: douge
ms.openlocfilehash: c33b8badcacd4e228d70f8e770d4bf27144c29eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-a-windows-service-application-in-the-component-designer"></a>Instruções passo a passo: criando um aplicativo de Serviço Windows no Designer de Componente
Este artigo demonstra como criar um aplicativo simples de serviço Windows no Visual Studio que grava mensagens em um log de eventos. Aqui estão as etapas básicas que podem ser executadas para criar e usar o serviço:  
  
1.  [Criando um serviço](#BK_CreateProject) usando o **Windows Service** modelo de projeto e configurá-lo. Esse modelo cria uma classe para você que é herdada de <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> e grava grande parte do código de serviço básico, como o código para iniciar o serviço.  
  
2.  [Adicionando recursos ao serviço](#BK_WriteCode) para o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedimentos e substitua quaisquer outros métodos que você deseja redefinir.  
  
3.  [Definir o Status do serviço](#BK_SetStatus). Por padrão, serviços criados com <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> implementam apenas um subconjunto dos sinalizadores de status disponíveis. Se o serviço levar muito tempo para iniciar, pausar ou interromper, você pode implementar os valores de status como Iniciar pendente ou Parar pendente para indicar que está funcionando em uma operação.  
  
4.  [Adicionando instaladores para o serviço](#BK_AddInstallers) para seu aplicativo de serviço.  
  
5.  (Opcional) [Definir parâmetros de inicialização](#BK_StartupParameters), especificar argumentos de inicialização padrão e permitir que os usuários substituir as configurações padrão quando os usuários iniciarem o serviço manualmente.  
  
6.  [Criando o serviço](#BK_Build).  
  
7.  [Instalar o serviço](#BK_Install) no computador local.  
  
8.  Acessar o Gerenciador de controle de serviço do Windows e [Iniciando e executando o serviço](#BK_StartService).  
  
9. [Desinstalando um serviço do Windows](#BK_Uninstall).  
  
> [!WARNING]
>  O modelo de projeto dos Windows Services que é exigido para este passo a passo não está disponível na edição Express do Visual Studio.  
  
 [!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]  
  
<a name="BK_CreateProject"></a>   
## <a name="creating-a-service"></a>Criando um serviço  
 Para começar, você cria o projeto e define valores que são exigidos para que o serviço funcione corretamente.  
  
#### <a name="to-create-and-configure-your-service"></a>Para criar e configurar o serviço  
  
1.  No Visual Studio, na barra de menus, escolha **arquivo**, **novo**, **projeto**.  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
2.  Na lista de modelos de projeto do Visual Basic ou Visual c#, escolha **Windows Service**e nomeie o projeto **MyNewService**. Escolha **OK**.  
  
     O modelo de projeto adiciona automaticamente uma classe de componente denominada `Service1` que é herdada de <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.  
  
3.  Sobre o **editar** menu, escolha **localizar e substituir**, **localizar nos arquivos** (teclado: Ctrl + Shift + F). Alterar todas as ocorrências de `Service1` para `MyNewService`. Você encontrará instâncias no Service1.cs, Program.cs e Service1.Designer.cs (ou seus equivalentes .vb).  
  
4.  No **propriedades** janela para **Service1 [Design]** ou **Service1 [Design]**, defina o <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> e **(nome)** propriedade `Service1` para **MyNewService**, se ainda não estiver definido.  
  
5.  No Solution Explorer, renomeie **Service1.cs** para **MyNewService.cs**, ou **Service1** para **MyNewService.vb**.  
  
<a name="BK_WriteCode"></a>   
## <a name="adding-features-to-the-service"></a>Adicionando recursos ao serviço  
 Na próxima seção, adicione um log de eventos personalizado ao serviço Windows. Os logs de eventos não são associados de forma alguma aos Windows Services. Aqui o componente <xref:System.Diagnostics.EventLog> é usado como um exemplo do tipo de componente que você poderia adicionar a um Windows Service.  
  
#### <a name="to-add-custom-event-log-functionality-to-your-service"></a>Para adicionar a funcionalidade de log de eventos personalizado ao seu serviço  
  
1.  Em **Solution Explorer**, abra o menu de contexto de **MyNewService.cs** ou **MyNewService.vb**e, em seguida, escolha **Designer de exibição**.  
  
2.  Do **componentes** seção o **caixa de ferramentas**, arraste um <xref:System.Diagnostics.EventLog> componente para o designer.  
  
3.  Em **Solution Explorer**, abra o menu de contexto de **MyNewService.cs** ou **MyNewService.vb**e, em seguida, escolha **Exibir código**.  
  
4.  Adicione uma declaração para o **eventLog** objeto o `MyNewService` classe, logo após a linha que declara o `components` variável:  
  
     [!code-csharp[VbRadconService#16](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#16)]
     [!code-vb[VbRadconService#16](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#16)]  
  
5.  Adicione ou edite o construtor para definir um log de eventos personalizado:  
  
     [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
     [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]  
  
#### <a name="to-define-what-occurs-when-the-service-starts"></a>Para definir o que ocorre quando o serviço é iniciado  
  
-   No Editor do Código, localize o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> que foi substituído automaticamente quando você criou o projeto e substitua o código a seguir. Isso adiciona uma entrada no log de eventos quando o serviço começa a ser executado:  
  
     [!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
     [!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]  
  
     Um aplicativo de serviço foi projetado para executado a longo prazo, por isso ele geralmente controla ou monitora algo no sistema. O monitoramento é configurado no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>. No entanto, o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> não realiza, de fato, o monitoramento. O método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> deve ser retornado ao sistema operacional depois que a operação do serviço tiver começado. Ele não deve fazer loop para sempre nem bloqueios. Para configurar um mecanismo de pesquisa simples, você pode usar o componente <xref:System.Timers.Timer?displayProperty=nameWithType> da seguinte forma: no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, defina os parâmetros no componente e, em seguida, defina a propriedade <xref:System.Timers.Timer.Enabled%2A> como `true`. O temporizador gera eventos no seu código periodicamente, no tempo em que seu serviço faria o monitoramento. Você pode usar o código a seguir para fazer isso:  
  
    ```csharp  
    // Set up a timer to trigger every minute.  
    System.Timers.Timer timer = new System.Timers.Timer();  
    timer.Interval = 60000; // 60 seconds  
    timer.Elapsed += new System.Timers.ElapsedEventHandler(this.OnTimer);  
    timer.Start();  
    ```  
  
    ```vb  
    ' Set up a timer to trigger every minute.  
    Dim timer As System.Timers.Timer = New System.Timers.Timer()  
    timer.Interval = 60000 ' 60 seconds  
    AddHandler timer.Elapsed, AddressOf Me.OnTimer  
    timer.Start()  
    ```  
     Adicione uma variável de membro para a classe. Ele conterá o identificador do próximo evento para gravar no log de eventos.

    ```csharp
    private int eventId = 1;
    ```

    ```vb
    Private eventId As Integer = 1
    ```

     Adicione o código para manipular o evento do temporizador:  
  
    ```csharp  
    public void OnTimer(object sender, System.Timers.ElapsedEventArgs args)  
    {  
        // TODO: Insert monitoring activities here.  
        eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId++);  
    }  
    ```  
  
    ```vb  
    Private Sub OnTimer(sender As Object, e As Timers.ElapsedEventArgs)  
        ' TODO: Insert monitoring activities here.  
        eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId)  
        eventId = eventId + 1  
    End Sub  
    ```  
  
     Você pode desejar executar tarefas usando segmentos de trabalho em segundo plano em vez de executar todo o seu trabalho no thread principal. Para obter um exemplo disso, consulte a página de referência <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.  
  
#### <a name="to-define-what-occurs-when-the-service-is-stopped"></a>Para definir o que ocorre quando o serviço é interrompido  
  
-   Substitua o código para o método <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pelo seguinte. Isso adiciona uma entrada no log de eventos quando o serviço é interrompido:  
  
     [!code-csharp[VbRadconService#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
     [!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]  
  
 Na próxima seção, você pode substituir os métodos <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> e <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> para definir o processamento adicional para o componente.  
  
#### <a name="to-define-other-actions-for-the-service"></a>Para definir outras ações para o serviço  
  
-   Localize o método que deseja manipular, e substitua-o para definir o que você quer que aconteça.  
  
     O código a seguir mostra como você pode substituir o método <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>:  
  
     [!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
     [!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]  
  
 Algumas ações personalizadas precisam ocorrer quando um serviço Windows é instalado pela classe <xref:System.Configuration.Install.Installer>. O Visual Studio pode criar esses instaladores especificamente para um Windows Service e adicioná-los ao seu projeto.  
  
<a name="BK_SetStatus"></a>   
## <a name="setting-service-status"></a>Definindo o status de serviço  
 Serviços relatam seu status para o Gerenciador de Controle de Serviço, para que os usuários possam determinar se um serviço está funcionando corretamente. Por padrão, os serviços herdados de <xref:System.ServiceProcess.ServiceBase> relatam um conjunto limitado de configurações de status, inclusive Interrompido, Pausado e Em execução. Se um serviço demora um pouco para inicializar, ele pode ser útil relatar um status Iniciar pendente. Você também pode implementar as configurações de status pendente iniciar e parar pendente, adicionando o código que chama o Windows [função SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx).  
  
#### <a name="to-implement-service-pending-status"></a>Para implementar o status pendente do serviço  
  
1.  Adicione uma instrução `using` ou declaração `Imports` ao namespace <xref:System.Runtime.InteropServices?displayProperty=nameWithType> no arquivo MyNewService.cs ou MyNewService.vb:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    ```  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    ```  
  
2.  Adicione o seguinte código ao MyNewService.cs declarar os valores de `ServiceState` e para adicionar uma estrutura ao status, que você usará em uma chamada de invocação de plataforma:  
  
    ```csharp  
    public enum ServiceState  
      {  
          SERVICE_STOPPED = 0x00000001,  
          SERVICE_START_PENDING = 0x00000002,  
          SERVICE_STOP_PENDING = 0x00000003,  
          SERVICE_RUNNING = 0x00000004,  
          SERVICE_CONTINUE_PENDING = 0x00000005,  
          SERVICE_PAUSE_PENDING = 0x00000006,  
          SERVICE_PAUSED = 0x00000007,  
      }  
  
      [StructLayout(LayoutKind.Sequential)]  
      public struct ServiceStatus  
      {  
          public int dwServiceType;  
          public ServiceState dwCurrentState;  
          public int dwControlsAccepted;  
          public int dwWin32ExitCode;  
          public int dwServiceSpecificExitCode;  
          public int dwCheckPoint;  
          public int dwWaitHint;  
      };  
    ```  
  
    ```vb  
    Public Enum ServiceState  
        SERVICE_STOPPED = 1  
        SERVICE_START_PENDING = 2  
        SERVICE_STOP_PENDING = 3  
        SERVICE_RUNNING = 4  
        SERVICE_CONTINUE_PENDING = 5  
        SERVICE_PAUSE_PENDING = 6  
        SERVICE_PAUSED = 7  
    End Enum  
  
    <StructLayout(LayoutKind.Sequential)>  
    Public Structure ServiceStatus  
        Public dwServiceType As Long  
        Public dwCurrentState As ServiceState  
        Public dwControlsAccepted As Long  
        Public dwWin32ExitCode As Long  
        Public dwServiceSpecificExitCode As Long  
        Public dwCheckPoint As Long  
        Public dwWaitHint As Long  
    End Structure  
    ```  
  
3.  Agora, no `MyNewService` classe, declare o [função SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) usando a plataforma chamar:  
  
    ```csharp  
    [DllImport("advapi32.dll", SetLastError=true)]  
            private static extern bool SetServiceStatus(IntPtr handle, ref ServiceStatus serviceStatus);  
    ```  
  
    ```vb  
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean  
    ```  
  
4.  Para implementar o status Iniciar pendente, adicione o seguinte código ao início do método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>:  
  
    ```csharp  
    // Update the service state to Start Pending.  
    ServiceStatus serviceStatus = new ServiceStatus();  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING;  
    serviceStatus.dwWaitHint = 100000;  
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);  
    ```  
  
    ```vb  
    ' Update the service state to Start Pending.  
    Dim serviceStatus As ServiceStatus = New ServiceStatus()  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING  
    serviceStatus.dwWaitHint = 100000  
    SetServiceStatus(Me.ServiceHandle, serviceStatus)  
    ```  
  
5.  Adicione o código para definir o status Em execução no final do método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>.  
  
    ```csharp
    // Update the service state to Running.  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING;  
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);  
    ```  
  
    ```vb  
    ' Update the service state to Running.  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING  
    SetServiceStatus(Me.ServiceHandle, serviceStatus)  
    ```  
  
6.  (Opcional) Repita esse procedimento para o método <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.  
  
> [!CAUTION]
>  O [Service Control Manager](http://msdn.microsoft.com/library/windows/desktop/ms685150.aspx) usa o `dwWaitHint` e `dwCheckpoint` membros a [estrutura SERVICE_STATUS](http://msdn.microsoft.com/library/windows/desktop/ms685996.aspx) para determinar o tempo de espera para um serviço do Windows iniciar ou desligar. Se seu <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> métodos de execução longa, o serviço pode solicitar mais tempo chamando [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) novamente com um incrementado `dwCheckPoint` valor.  
  
<a name="BK_AddInstallers"></a>   
## <a name="adding-installers-to-the-service"></a>Adicionando instaladores ao serviço  
 Antes de executar um serviço Windows, é necessário instalá-lo, o que o registra com o Gerenciador de Controle de Serviço. Você pode adicionar instaladores ao seu projeto que lida com os detalhes de registro.  
  
#### <a name="to-create-the-installers-for-your-service"></a>Para criar os instaladores para seu serviço  
  
1.  Em **Solution Explorer**, abra o menu de contexto de **MyNewService.cs** ou **MyNewService.vb**e, em seguida, escolha **Designer de exibição**.  
  
2.  Clique no plano de fundo do designer para selecionar o próprio serviço, e não um de seus conteúdos.  
  
3.  Abra o menu de contexto para a janela do designer (se você estiver usando um dispositivo apontador, o botão direito do mouse dentro da janela) e, em seguida, escolha **adicionar instalador**.  
  
     Por padrão, uma classe de componente que contém dois instaladores é adicionada ao projeto. O componente é chamado **ProjectInstaller**e os instaladores que ele contém são o instalador para o serviço e o instalador para o serviço do processo associado.  
  
4.  Em **Design** exibir para **ProjectInstaller**, escolha **serviceInstaller1** para um projeto Visual c#, ou **ServiceInstaller1** para um Visual Projeto básico.  
  
5.  No **propriedades** janela, certifique-se de <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> está definida como **MyNewService**.  
  
6.  Definir o **descrição** propriedade a um texto, como "Um exemplo de serviço". Este texto é exibido na janela Serviços e ajuda o usuário a identificar o serviço e entender para que ele é usado.  
  
7.  Definir o <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> propriedade para o texto que você deseja exibir na janela Serviços no **nome** coluna. Por exemplo, você pode inserir "Nome de exibição do MyNewService". Esse nome pode ser diferente da propriedade <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>, que é o nome usado pelo sistema (por exemplo, quando você usa o comando `net start` para iniciar o serviço).  
  
8.  Defina a propriedade <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> como <xref:System.ServiceProcess.ServiceStartMode.Automatic>.  
  
     ![Propriedades de instalador para um serviço do Windows](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")  
  
9. No designer, escolha **serviceProcessInstaller1** para um projeto Visual c#, ou **ServiceProcessInstaller1** para um projeto do Visual Basic. Defina a propriedade <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> como <xref:System.ServiceProcess.ServiceAccount.LocalSystem>. Isso fará com que o serviço seja instalado e executado em uma conta de serviço local.  
  
    > [!IMPORTANT]
    >  A conta <xref:System.ServiceProcess.ServiceAccount.LocalSystem> tem amplas permissões, incluindo a capacidade de gravar no log de eventos. Use essa conta com cuidado, pois ela pode aumentar o risco de ataques de software mal-intencionado. Para outras tarefas, pense em usar a conta <xref:System.ServiceProcess.ServiceAccount.LocalService>, que atua como um usuário não privilegiado no computador local e apresenta credenciais anônimas a qualquer servidor remoto. Este exemplo falhará se você tentar usar a conta <xref:System.ServiceProcess.ServiceAccount.LocalService>, pois ele precisa de permissão para gravar no log de eventos.  
  
     Para obter mais informações sobre instaladores, consulte [como: adicionar instaladores ao seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
<a name="BK_StartupParameters"></a>   
## <a name="set-startup-parameters"></a>Defina os parâmetros de inicialização  
 Um serviço Windows, como qualquer outro executável, pode aceitar argumentos de linha de comando ou parâmetros de inicialização. Quando você adiciona o código aos parâmetros de inicialização do processo, os usuários podem iniciar o serviço com seus próprios parâmetros de inicialização personalizada usando a janela de Serviços no Painel de Controle do Windows. No entanto, esses parâmetros de inicialização não são persistentes na próxima vez em que o serviço é iniciado. Para definir os parâmetros de inicialização permanentemente, você pode defini-las no registro, conforme mostrado neste procedimento.  
  
> [!NOTE]
>  Antes de decidir adicionar parâmetros de inicialização, considere se esta é a melhor maneira de passar informações para o serviço. Embora os parâmetros de inicialização sejam fáceis de usar e analisar, e os usuários possam substituí-los facilmente, eles podem ser mais difíceis para os usuários descobrem e usarem sem a documentação. Em geral, se o serviço exigir mais do que apenas alguns parâmetros de inicialização, você deve considerar usar o registro ou um arquivo de configuração. Cada serviço Windows tem uma entrada no registro em HKLM\System\CurrentControlSet\services. Na chave do serviço, você pode usar o **parâmetros** subchave para armazenar informações que pode acessar seu serviço. Você pode usar arquivos de configuração do aplicativo para um serviço Windows da mesma forma que faria para outros tipos de programas. Para obter um exemplo de código, consulte <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.  
  
#### <a name="adding-startup-parameters"></a>Adicionando parâmetros de inicialização  
  
1.  No método `Main` no Program.cs ou MyNewService.Designer.vb, adicione um argumento da linha de comando:  
  
```csharp  
static void Main(string[] args)
{
    ServiceBase[] ServicesToRun = new ServiceBase[] { new MyNewService(args) };
    ServiceBase.Run(ServicesToRun);
}
```  
  
```vb
Shared Sub Main(ByVal cmdArgs() As String)
    Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewServiceVB(cmdArgs)}
    System.ServiceProcess.ServiceBase.Run(ServicesToRun)
End Sub
```  
  
2.  Altere o construtor `MyNewService` da seguinte maneira:  
  
```csharp  
public MyNewService(string[] args)
{
    InitializeComponent();
    string eventSourceName = "MySource";
    string logName = "MyNewLog";
    if (args.Count() > 0) 
    {
        eventSourceName = args[0];
    }
    if (args.Count() > 1)
    {
        logName = args[1];
    }
    eventLog1 = new System.Diagnostics.EventLog();
    if (!System.Diagnostics.EventLog.SourceExists(eventSourceName))
    {
        System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName);
    }
    eventLog1.Source = eventSourceName;
    eventLog1.Log = logName;        
}
```  
  
```vb  
Public Sub New(ByVal cmdArgs() As String)
    InitializeComponent()
    Dim eventSourceName As String = "MySource"
    Dim logName As String = "MyNewLog"
    If (cmdArgs.Count() > 0) Then
        eventSourceName = cmdArgs(0)
    End If
    If (cmdArgs.Count() > 1) Then
        logName = cmdArgs(1)
    End If
    eventLog1 = New System.Diagnostics.EventLog()
    If (Not System.Diagnostics.EventLog.SourceExists(eventSourceName)) Then
        System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName)
    End If
    eventLog1.Source = eventSourceName
    eventLog1.Log = logName
End Sub  
```  
  
Esse código define o nome de origem e de log de eventos de acordo com os parâmetros de inicialização fornecidos ou usa os valores padrão se nenhum argumento for especificado.  
  
3. Para especificar os argumentos de linha de comando, adicione o seguinte código à classe `ProjectInstaller` em ProjectInstaller.cs ou ProjectInstaller.vb:  
  
```csharp  
protected override void OnBeforeInstall(IDictionary savedState)
{
    string parameter = "MySource1\" \"MyLogFile1";
    Context.Parameters["assemblypath"] = "\"" + Context.Parameters["assemblypath"] + "\" \"" + parameter + "\"";
    base.OnBeforeInstall(savedState);
}
```

```vb  
Protected Overrides Sub OnBeforeInstall(ByVal savedState As IDictionary)
    Dim parameter As String = "MySource1"" ""MyLogFile1"
    Context.Parameters("assemblypath") = """" + Context.Parameters("assemblypath") + """ """ + parameter + """"
    MyBase.OnBeforeInstall(savedState)
End Sub  
```  
  
Esse código modifica o **ImagePath** chave do registro, que normalmente contém o caminho completo para o executável para o serviço do Windows, adicionando os valores de parâmetro padrão. As aspas em torno do caminho (e em torno de cada parâmetro individual) são necessárias para o serviço ser inicializado corretamente. Para alterar os parâmetros de inicialização para esse serviço do Windows, os usuários podem alterar os parâmetros fornecidos **ImagePath** chave do registro, embora a melhor maneira é alterá-la por meio de programação e expor a funcionalidade para usuários em um forma amigável (por exemplo, em um utilitário de configuração ou gerenciamento).  
  
<a name="BK_Build"></a>   
## <a name="building-the-service"></a>Criando o serviço  
  
#### <a name="to-build-your-service-project"></a>Para criar o projeto de serviço  
  
1.  Em **Solution Explorer**, abra o menu de contexto para o seu projeto e, em seguida, escolha **propriedades**. As páginas de propriedades do projeto são exibidas.  
  
2.  Na guia do aplicativo, no **objeto de inicialização** , escolha **MyNewService.Program**.  
  
3.  Em **Solution Explorer**, abra o menu de contexto para o seu projeto e, em seguida, escolha **Build** para compilar o projeto (teclado: Ctrl + Shift + B).  
  
<a name="BK_Install"></a>   
## <a name="installing-the-service"></a>Instalando o serviço  
 Agora que você criou o serviço Windows, poderá instalá-lo. Para instalar um serviço Windows, você deve ter credenciais administrativas no computador no qual está sendo instalado.  
  
#### <a name="to-install-a-windows-service"></a>Para instalar um serviço Windows  
  
1.  No Windows 7 e Windows Server, abra o **Prompt de comando do desenvolvedor** em **ferramentas do Visual Studio** no **iniciar** menu. No Windows 8 ou Windows 8.1, escolha o **ferramentas do Visual Studio** bloco de **iniciar** tela e, em seguida, executar o Prompt de comando do desenvolvedor com credenciais administrativas. (Se você estiver usando um mouse, clique duas vezes em **Prompt de comando do desenvolvedor**e, em seguida, escolha **executar como administrador**.)  
  
2.  Na janela do Prompt de comando, navegue até a pasta que contém a saída do projeto. Por exemplo, na pasta Meus Documentos, navegue até Visual Studio 2013\Projects\MyNewService\bin\Debug.  
  
3.  Insira o seguinte comando:  
  
    ```  
    installutil.exe MyNewService.exe  
    ```  
  
     Se o serviço for instalado com êxito, installutil.exe relatará o sucesso. Se o sistema não puder localizar o InstallUtil.exe, certifique-se de que ela exista no seu computador. Essa ferramenta é instalada com o .NET Framework para a pasta `%WINDIR%\Microsoft.NET\Framework[64]\` *framework_version*. Por exemplo, é o caminho padrão para a versão de 32 bits do .NET Framework 4, 4.5, 4.5.1 e 4.5.2 é `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.  
  
     Se o processo de installutil.exe relata falha, verifique o log de instalação para saber o motivo. Por padrão o log está na mesma pasta do executável do serviço. A instalação pode falhar se o <xref:System.ComponentModel.RunInstallerAttribute> classe não está presente no `ProjectInstaller` classe, caso contrário, o atributo não está definido como `true`, ou então `ProjectInstaller` a classe não é `public`.  
  
     Para obter mais informações, consulte [como: instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
<a name="BK_StartService"></a>   
## <a name="starting-and-running-the-service"></a>Iniciando e executando o serviço  
  
#### <a name="to-start-and-stop-your-service"></a>Para iniciar e interromper o serviço  
  
1.  No Windows, abra o **iniciar** tela ou **iniciar** menu e tipo `services.msc`.  
  
     Agora você deve ver **MyNewService** listadas no **serviços** janela.  
  
     ![MyNewService na janela Serviços. ] (../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG "WindowsServices_ServicesWindow")  
  
2.  No **serviços** janela, abra o menu de atalho para o serviço e, em seguida, escolha **iniciar**.  
  
3.  Abra o menu de atalho para o serviço e, em seguida, escolha **parar**.  
  
4.  (Opcional) Na linha de comando, você pode usar os comandos `net start``ServiceName` e `net stop``ServiceName` para iniciar e parar o serviço.  
  
#### <a name="to-verify-the-event-log-output-of-your-service"></a>Para verificar a saído do log de eventos do seu serviço  
  
1.  No Visual Studio, abra **Server Explorer** (teclado: Ctrl + Alt + S) e acessar o **Logs de eventos** nó para o computador local.  
  
2.  Localize a listagem para **MyNewLog** (ou **MyLogFile1**, se você usou o procedimento opcional para adicionar argumentos de linha de comando) e expandi-lo. Você deverá ver entradas para as duas ações (iniciar e parar) que seu serviço executou.  
  
     ![Use o Visualizador de eventos para ver as entradas de log de eventos. ] (../../../docs/framework/windows-services/media/windowsservices-eventviewer.PNG "WindowsServices_EventViewer")  
  
<a name="BK_Uninstall"></a>   
## <a name="uninstalling-a-windows-service"></a>Desinstalando um serviço Windows  
  
#### <a name="to-uninstall-your-service"></a>Para desinstalar o serviço  
  
1.  Abra um prompt de comando do desenvolvedor com credenciais administrativas.  
  
2.  Na janela do Prompt de comando, navegue até a pasta que contém a saída do projeto. Por exemplo, na pasta Meus Documentos, navegue até Visual Studio 2013\Projects\MyNewService\bin\Debug.  
  
3.  Insira o seguinte comando:  
  
    ```  
    installutil.exe /u MyNewService.exe  
    ```  
  
     Se o serviço for desinstalado com êxito, installutil.exe relatará que seu serviço foi removido com sucesso. Para obter mais informações, consulte [como: instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode criar um programa de instalação autônomo que outras pessoas podem usar para instalar o serviço Windows, mas ele necessita de etapas adicionais. O ClickOnce não oferece suporte aos Windows Services, de modo que não é possível usar o Assistente de Publicação. Você pode usar a edição completa do InstallShield, que não é fornecido pela Microsoft. Para obter mais informações sobre o InstallShield, consulte [InstallShield Limited Edition](/visualstudio/deployment/installshield-limited-edition). Você também pode usar o [o conjunto de ferramentas do Windows Installer XML](http://go.microsoft.com/fwlink/?LinkId=249067) para criar um instalador para um serviço do Windows.  
  
 Você pode explorar o uso de um componente <xref:System.ServiceProcess.ServiceController> para permitir que você envie comandos ao serviço que instalou.  
  
 É possível usar um instalador para criar um log de eventos quando o aplicativo é instalado, em vez de criá-lo quando o aplicativo é executado. Além disso, o log de eventos será excluído pelo instalador quando o aplicativo for desinstalado. Para obter mais informações, consulte a página de referência <xref:System.Diagnostics.EventLogInstaller>.  
  
## <a name="see-also"></a>Consulte também  
 [Aplicativos do Serviço Windows](../../../docs/framework/windows-services/index.md)  
 [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Como depurar aplicativos de Serviço Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Serviços (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
