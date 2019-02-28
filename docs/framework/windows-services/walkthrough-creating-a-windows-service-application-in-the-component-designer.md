---
title: Criar um aplicativo de serviço Windows no Visual Studio
ms.date: 09/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: 52c2f64bbb71e07dcab1fd7cd42662f9ed2c8445
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56665024"
---
# <a name="walkthrough-create-a-windows-service-app"></a>Passo a passo: Criar um aplicativo de serviço Windows

Este artigo demonstra como criar um aplicativo de serviço Windows simples no Visual Studio que escreve mensagens em um log de eventos.

## <a name="create-a-service"></a>Criar um serviço

Para começar, crie o projeto e defina os valores necessários para o serviço funcionar corretamente.

1. No Visual Studio, na barra de menus, escolha **Arquivo** > **Novo** > **Projeto** (ou pressione **Ctrl**+**Shift**+**N**) para abrir a caixa de diálogo **Novo projeto**.

2. Navegue e selecione o modelo de projeto **Serviço Windows**. Expanda **Instalado** > [**Visual C#** ou **Visual Basic**] > **Área de Trabalho do Windows** ou digite **Serviço Windows** na caixa de pesquisa no canto superior direito.

   ![Modelo de Serviço Windows na caixa de diálogo Novo Projeto no Visual Studio](media/new-project-dialog.png)

   > [!NOTE]
   > Se você não vir o modelo **Serviço Windows**, talvez seja necessário instalar a carga de trabalho **Desenvolvimento de área de trabalho do .NET**. Na caixa de diálogo **Novo Projeto**, clique no link que diz **Abrir o Instalador do Visual Studio** à esquerda. No **Instalador do Visual Studio**, selecione a carga de trabalho **desenvolvimento para área de trabalho do .NET** e, em seguida, escolha **Modificar**.

3. Dê ao projeto o nome **MyNewService** e, em seguida, escolha **OK**.

   O modelo de projeto inclui uma classe de componente denominada `Service1` herdada de <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>. Isso inclui grande parte do código de serviço básico, como o código para iniciar o serviço.

## <a name="rename-the-service"></a>Renomear o serviço

Renomeie o serviço de **Service1** para **MyNewService**.

1. No modo de exibição de **Design** para Service1.cs (ou Service1.vb), clique no link para **alternar para o modo de exibição de código**. Clique com o botão direito do mouse em **Service1** e selecione **Renomear** no menu de contexto. Insira **MyNewService** e, em seguida, pressione **Inserir** ou clique em **Aplicar**.

2. Na janela **Propriedades** para **Service1.cs [Design]** ou **Service1.vb [Design]**, altere o valor **ServiceName** para **MyNewService**.

3. No **Gerenciador de Soluções**, renomeie **Service1.cs** para **MyNewService.cs** ou **Service1.vb** para **MyNewService.vb**.

## <a name="add-features-to-the-service"></a>Adicionar recursos ao serviços

Na próxima seção, adicione um log de eventos personalizado ao serviço Windows. Os logs de eventos não são associados de forma alguma aos Windows Services. O componente <xref:System.Diagnostics.EventLog> é usado aqui como um exemplo do tipo de componente que pode ser adicionado a um serviço Windows.

### <a name="add-custom-event-log-functionality"></a>Adicionar a funcionalidade de log de eventos personalizado

1. No **Gerenciador de Soluções**, abra o menu de contexto de **MyNewService.cs** ou **MyNewService.vb** e, em seguida, escolha **Designer de Exibição**.

2. Na seção **Componentes** da **Caixa de Ferramentas**, arraste um componente <xref:System.Diagnostics.EventLog> para o designer.

3. No **Gerenciador de Soluções**, abra o menu de contexto de **MyNewService.cs** ou **MyNewService.vb** e escolha **Exibir Código**.

4. Edite o construtor para definir um log de eventos personalizado:

   ```csharp
   public MyNewService()
   {
        InitializeComponent();

        eventLog1 = new System.Diagnostics.EventLog();
        if (!System.Diagnostics.EventLog.SourceExists("MySource"))
        {
            System.Diagnostics.EventLog.CreateEventSource(
                "MySource", "MyNewLog");
        }
        eventLog1.Source = "MySource";
        eventLog1.Log = "MyNewLog";
    }
   ```

   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

### <a name="define-what-occurs-when-the-service-starts"></a>Definir o que ocorre quando o serviço é iniciado

No editor do código, localize o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> que foi substituído automaticamente quando você criou o projeto. Adicione uma linha de código que escreve uma entrada no log de eventos quando o serviço é iniciado:

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

Um aplicativo de serviço foi projetado para executado a longo prazo, por isso ele geralmente controla ou monitora algo no sistema. O monitoramento é configurado no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>. No entanto, o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> não realiza, de fato, o monitoramento. O método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> deve ser retornado ao sistema operacional depois que a operação do serviço tiver começado. Ele não deve fazer loop para sempre nem bloqueios. Para configurar um mecanismo simples de sondagem, use o componente <xref:System.Timers.Timer?displayProperty=nameWithType>, da seguinte maneira: No método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, defina parâmetros no componente e, em seguida, defina a propriedade <xref:System.Timers.Timer.Enabled%2A> como `true`. O temporizador gera eventos no seu código periodicamente, no tempo em que seu serviço faria o monitoramento. Você pode usar o código a seguir para fazer isso:

```csharp
// Set up a timer that triggers every minute.
System.Timers.Timer timer = new System.Timers.Timer();
timer.Interval = 60000; // 60 seconds
timer.Elapsed += new System.Timers.ElapsedEventHandler(this.OnTimer);
timer.Start();
```

```vb
' Set up a timer that triggers every minute.
Dim timer As System.Timers.Timer = New System.Timers.Timer()
timer.Interval = 60000 ' 60 seconds
AddHandler timer.Elapsed, AddressOf Me.OnTimer
timer.Start()
```

Adicione uma variável de membro à classe. Ela contém o identificador do próximo evento a ser gravado no log de eventos.

```csharp
private int eventId = 1;
```

```vb
Private eventId As Integer = 1
```

Adicione um novo método para manipular o evento do temporizador:

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

Você pode desejar executar tarefas usando segmentos de trabalho em segundo plano em vez de executar todo o seu trabalho no thread principal. Para obter mais informações, consulte <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.

### <a name="define-what-occurs-when-the-service-is-stopped"></a>Definir o que ocorre quando o serviço é interrompido

Adicione uma linha de código ao método <xref:System.ServiceProcess.ServiceBase.OnStop%2A> que adiciona uma entrada ao log de eventos quando o serviço é interrompido:

```csharp
eventLog1.WriteEntry("In OnStop.");
```

[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a>Definir outras ações para o serviço

Também é possível substituir os métodos <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> e <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> para definir o processamento adicional para seu componente. O código a seguir mostra como você pode substituir o método <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>:

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

Algumas ações personalizadas precisam ocorrer quando um serviço Windows é instalado pela classe <xref:System.Configuration.Install.Installer>. O Visual Studio pode criar esses instaladores especificamente para um Windows Service e adicioná-los ao seu projeto.

## <a name="set-service-status"></a>Definir status do serviço

Serviços relatam seu status para o Gerenciador de Controle de Serviço, para que os usuários possam determinar se um serviço está funcionando corretamente. Por padrão, os serviços herdados de <xref:System.ServiceProcess.ServiceBase> relatam um conjunto limitado de configurações de status, inclusive Interrompido, Pausado e Em execução. Se um serviço demora um pouco para inicializar, ele pode ser útil relatar um status Iniciar pendente. Você também pode implementar as configurações de status Iniciar Pendente e Parar Pendente, adicionando o código que chama a [função SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) do Windows.

Para implementar o status pendente do serviço:

1. Adicione uma instrução `using` ou declaração `Imports` para o namespace <xref:System.Runtime.InteropServices?displayProperty=nameWithType> no arquivo MyNewService.cs ou MyNewService.vb:

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. Adicione o seguinte código ao MyNewService.cs declarar os valores de `ServiceState` e para adicionar uma estrutura ao status, que você usará em uma chamada de invocação de plataforma:

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

3. Agora, na classe `MyNewService`, declare a [função SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) usando a [inovação de plataforma](../interop/consuming-unmanaged-dll-functions.md):

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. Para implementar o status Iniciar pendente, adicione o seguinte código ao início do método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>:

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

5. Adicione o código para definir o status Em execução no final do método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>.

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

6. (Opcional) Repita esse procedimento para o método <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.

> [!NOTE]
> O [Gerenciador de Controle de Serviço](/windows/desktop/Services/service-control-manager) usa os membros `dwWaitHint` e `dwCheckpoint` da [estrutura SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status) para determinar quanto tempo esperar para que um serviço Windows seja iniciado ou desligado. Se os métodos <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> tiverem uma execução longa, o serviço poderá solicitar mais tempo chamando [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) novamente com um valor de `dwCheckPoint` incrementado.

## <a name="add-installers-to-the-service"></a>Adicionar instaladores ao serviço

Antes de executar um serviço Windows, é necessário instalá-lo, o que o registra com o Gerenciador de Controle de Serviço. Você pode adicionar instaladores ao seu projeto que lida com os detalhes de registro.

1. No **Gerenciador de Soluções**, abra o menu de contexto de **MyNewService.cs** ou **MyNewService.vb** e, em seguida, escolha **Designer de Exibição**.

2. Clique no plano de fundo do designer para selecionar o próprio serviço, e não um de seus conteúdos.

3. Abra o menu de contexto da janela do designer (se você estiver usando um dispositivo apontador, clique com o botão direito do mouse dentro da janela) e, em seguida, escolha **Adicionar Instalador**.

   Por padrão, uma classe de componente que contém dois instaladores é adicionada ao projeto. O componente é chamado **ProjectInstaller** e os instaladores que ele contém são o instalador do serviço e o instalador do processo associado ao serviço.

4. Na exibição **Design** de **ProjectInstaller**, escolha **serviceInstaller1** para um projeto Visual C# ou **ServiceInstaller1** para um projeto Visual Basic.

5. Na janela **Propriedades**, verifique se a propriedade <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> está definida como **MyNewService**.

6. Defina a propriedade **Descrição** para um texto, como "Um exemplo de serviço". Este texto é exibido na janela Serviços e ajuda o usuário a identificar o serviço e entender para que ele é usado.

7. Defina a propriedade <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> para o texto que você deseja exibir na janela Serviços na coluna **Nome**. Por exemplo, você pode inserir "Nome de exibição do MyNewService". Esse nome pode ser diferente da propriedade <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>, que é o nome usado pelo sistema (por exemplo, quando você usa o comando `net start` para iniciar o serviço).

8. Defina a propriedade <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> como <xref:System.ServiceProcess.ServiceStartMode.Automatic>.

     ![Propriedades do instalador para um Serviço Windows](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")

9. No designer, escolha **serviceProcessInstaller1** para um projeto Visual C# ou **ServiceProcessInstaller1** para um projeto Visual Basic. Defina a propriedade <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> como <xref:System.ServiceProcess.ServiceAccount.LocalSystem>. Isso faz o serviço ser instalado e executado usando a conta do sistema local.

    > [!IMPORTANT]
    > A conta <xref:System.ServiceProcess.ServiceAccount.LocalSystem> tem amplas permissões, incluindo a capacidade de gravar no log de eventos. Use essa conta com cuidado, pois ela pode aumentar o risco de ataques de software mal-intencionado. Para outras tarefas, pense em usar a conta <xref:System.ServiceProcess.ServiceAccount.LocalService>, que atua como um usuário não privilegiado no computador local e apresenta credenciais anônimas a qualquer servidor remoto. Este exemplo falhará se você tentar usar a conta <xref:System.ServiceProcess.ServiceAccount.LocalService>, pois ele precisa de permissão para gravar no log de eventos.

Para saber mais sobre os instaladores, consulte [Como adicionar instaladores ao seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).

## <a name="optional-set-startup-parameters"></a>(Opcional) Defina os parâmetros de inicialização

Um serviço Windows, como qualquer outro executável, pode aceitar argumentos de linha de comando ou parâmetros de inicialização. Quando você adiciona o código aos parâmetros de inicialização do processo, os usuários podem iniciar o serviço com seus próprios parâmetros de inicialização personalizada usando a janela de Serviços no Painel de Controle do Windows. No entanto, esses parâmetros de inicialização não são persistentes na próxima vez em que o serviço é iniciado. Para definir os parâmetros de inicialização permanentemente, você pode defini-las no registro, conforme mostrado neste procedimento.

> [!NOTE]
> Antes de decidir adicionar parâmetros de inicialização, considere se esta é a melhor maneira de passar informações para o serviço. Embora os parâmetros de inicialização sejam fáceis de usar e analisar, e os usuários possam substituí-los facilmente, eles podem ser mais difíceis para os usuários descobrem e usarem sem a documentação. Em geral, se o serviço exigir mais do que apenas alguns parâmetros de inicialização, você deve considerar usar o registro ou um arquivo de configuração. Cada serviço Windows tem uma entrada no Registro em **HKLM\System\CurrentControlSet\services**. Na chave do serviço, você pode usar a subchave de **Parâmetros** para armazenar as informações que o serviço pode acessar. É possível usar arquivos de configuração de aplicativo para um serviço Windows da mesma forma que faz para outros tipos de programas. Para obter um exemplo de código, consulte <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.

Para adicionar parâmetros de inicialização:

1. No método `Main` no Program.cs ou MyNewService.Designer.vb, adicione um parâmetro de entrada para passar para o construtor do serviço:

   ```csharp
   static void Main(string[] args)
   {
       ServiceBase[] ServicesToRun;
       ServicesToRun = new ServiceBase[]
       {
           new MyNewService(args)
       };
       ServiceBase.Run(ServicesToRun);
   }
   ```

   ```vb
   Shared Sub Main(ByVal cmdArgs() As String)
       Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewServiceVB(cmdArgs)}
       System.ServiceProcess.ServiceBase.Run(ServicesToRun)
   End Sub
   ```

2. Altere o construtor `MyNewService` da seguinte maneira:

   ```csharp
   public MyNewService(string[] args)
   {
       InitializeComponent();

        string eventSourceName = "MySource";
        string logName = "MyNewLog";

        if (args.Length > 0)
        {
            eventSourceName = args[0];
        }

        if (args.Length > 1)
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

   Esse código modifica a chave do Registro **ImagePath**, que normalmente contém o caminho completo para o executável do serviço Windows adicionando os valores de parâmetro padrão. As aspas em torno do caminho (e em torno de cada parâmetro individual) são necessárias para o serviço ser inicializado corretamente. Para alterar os parâmetros de inicialização desse serviço Windows, os usuários podem alterar os parâmetros fornecidos na chave do Registro **ImagePath**, embora seja melhor alterá-los de forma programática e expor a funcionalidade aos usuários de uma maneira amigável (por exemplo, em um utilitário de gerenciamento ou de configuração).

## <a name="build-the-service"></a>Compilar o serviço

1. No **Gerenciador de Soluções**, abra o menu de contexto do projeto e selecione **Propriedades**.

   As páginas de propriedades do seu projeto aparecem.

2. Na guia **Aplicativo**, na lista **Objeto de inicialização**, escolha **MyNewService.Program**.

3. No **Gerenciador de Soluções**, abra o menu de contexto do seu projeto e, em seguida, escolha **Criar** para criar o projeto (ou pressione **Ctrl**+**Shift**+**B**).

## <a name="install-the-service"></a>Instalar o serviço

Agora que você criou o serviço Windows, poderá instalá-lo. Para instalar um serviço Windows, é necessário ter credenciais de administrador no computador no qual está sendo instalado.

1. Abra o **Prompt de Comando do Desenvolvedor para Visual Studio** com credenciais administrativas. Se você estiver usando um mouse, clique com o botão direito dele em **Prompt de Comando do Desenvolvedor para VS 2017** no menu Iniciar do Windows e, em seguida, escolha **Mais** > **Executar como administrador**.

2. Na janela **Prompt de Comando do Desenvolvedor**, navegue até a pasta que contém a saída do seu projeto (por padrão, é o subdiretório *\bin\Debug* do seu projeto).

3. Insira o seguinte comando:

    ```shell
    installutil.exe MyNewService.exe
    ```

    Se o serviço for instalado com êxito, **installutil.exe** relatará o sucesso. Se o sistema não puder localizar **InstallUtil.exe**, certifique-se de que ele existe no seu computador. Essa ferramenta é instalada com o .NET Framework na pasta *%windir%\Microsoft.NET\Framework[64]\\[versão do framework]*. Por exemplo, o caminho padrão da versão de 32 bits é *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.

    Se o processo de **installutil.exe** relatar falha, verifique o log de instalação para saber o motivo. Por padrão o log está na mesma pasta que o executável do serviço. A instalação poderá falhar se a classe <xref:System.ComponentModel.RunInstallerAttribute> não estiver presente na classe `ProjectInstaller`, se o atributo não estiver definido como **true** ou se a classe `ProjectInstaller` não for marcada **pública**.

Para obter mais informações, confira [Como: Instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).

## <a name="start-and-run-the-service"></a>Iniciar e executar o serviço

1. No Windows, abra o aplicativo da área de trabalho **Serviços**. Pressione **Windows**+**R** para abrir a caixa **Executar** e, em seguida, insira **services.msc** e pressione **Enter** ou clique em **OK**.

     Você deve ver o serviço listado em **Serviços**, exibido em ordem alfabética pelo nome de exibição definido para ele.

     ![MyNewService na janela Serviços.](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG)

2. Em **Serviços**, abra o menu de atalho para seu serviço e, em seguida, escolha **Iniciar**.

3. Para interromper o serviço, abra o menu de atalho do serviço e, em seguida, escolha **Interromper**.

4. (Opcional) Na linha de comando, você pode usar os comandos `net start ServiceName` e `net stop ServiceName` para iniciar e parar o serviço.

### <a name="verify-the-event-log-output-of-your-service"></a>Verificar a saída do log de eventos do seu serviço

1. Abra o **Visualizador de Eventos** começando a digitar **Visualizador de Eventos** na caixa de pesquisa na barra de tarefas do Windows e, em seguida, selecionando **Visualizador de Eventos** nos resultados da pesquisa.

   > [!TIP]
   > No Visual Studio, acesse os logs de eventos abrindo o **Gerenciador de Servidores** (teclado: **CTRL**+**Alt**+**S**) e expandindo o nó **Logs de Eventos** para o computador local.

2. No **Visualizador de Eventos**, expanda **Logs de Aplicativos e Serviços**.

3. Localize a listagem para **MyNewLog** (ou **MyLogFile1**, se você seguiu o procedimento opcional para adicionar argumentos de linha de comando) e expanda-a. Você deve ver entradas para as duas ações (iniciar e interromper) que seu serviço executou.

     ![Use o Visualizador de Eventos para ver as entradas do log de eventos](../../../docs/framework/windows-services/media/windows-service-event-viewer.png)

## <a name="uninstall-the-service"></a>Desinstalar o serviço

1. Abra o **Prompt de Comando do Desenvolvedor para Visual Studio** com credenciais administrativas.

2. Na janela do prompt de comando, navegue até a pasta que contém a saída do projeto.

3. Insira o seguinte comando:

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   Se o serviço for desinstalado com êxito, **installutil.exe** relatará que seu serviço foi removido com sucesso. Para obter mais informações, confira [Como: Instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).

## <a name="next-steps"></a>Próximas etapas

Agora que você criou o serviço, crie um programa de instalação autônomo que outras pessoas possam usar para instalar seu serviço Windows. O ClickOnce não dá suporte a serviços Windows, mas é possível usar o [WiX Toolset](http://wixtoolset.org/) para criar um instalador para um serviço Windows. Para ver outras ideias, confira [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop) (Criar um pacote do instalador).

Você pode explorar o uso de um componente <xref:System.ServiceProcess.ServiceController>, que permite que você envie comandos ao serviço que instalou.

É possível usar um instalador para criar um log de eventos quando o aplicativo é instalado, em vez de criá-lo quando o aplicativo é executado. Além disso, o log de eventos será excluído pelo instalador quando o aplicativo for desinstalado. Para obter mais informações, consulte a página de referência <xref:System.Diagnostics.EventLogInstaller>.

## <a name="see-also"></a>Consulte também

- [Aplicativos do serviço Windows](../../../docs/framework/windows-services/index.md)
- [Introdução aos aplicativos do serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Como: Depurar aplicativos do serviço Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [Serviços (Windows)](/windows/desktop/Services/services)
