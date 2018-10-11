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
manager: douge
ms.openlocfilehash: 27acdac5d34b96dd04fec1bb763edec9077ff928
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46493601"
---
# <a name="walkthrough-create-a-windows-service-app"></a><span data-ttu-id="5fb55-102">Passo a passo: criar um aplicativo de serviço Windows</span><span class="sxs-lookup"><span data-stu-id="5fb55-102">Walkthrough: Create a Windows service app</span></span>

<span data-ttu-id="5fb55-103">Este artigo demonstra como criar um aplicativo de serviço Windows simples no Visual Studio que escreve mensagens em um log de eventos.</span><span class="sxs-lookup"><span data-stu-id="5fb55-103">This article demonstrates how to create a simple Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="5fb55-104">Criar um serviço</span><span class="sxs-lookup"><span data-stu-id="5fb55-104">Create a service</span></span>

<span data-ttu-id="5fb55-105">Para começar, crie o projeto e defina os valores necessários para o serviço funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="5fb55-105">To begin, create the project and set values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="5fb55-106">No Visual Studio, na barra de menus, escolha **Arquivo** > **Novo** > **Projeto** (ou pressione **Ctrl**+**Shift**+**N**) para abrir a caixa de diálogo **Novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-106">In Visual Studio, on the menu bar, choose **File** > **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** dialog.</span></span>

2. <span data-ttu-id="5fb55-107">Navegue e selecione o modelo de projeto **Serviço Windows**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-107">Navigate to and select the **Windows Service** project template.</span></span> <span data-ttu-id="5fb55-108">Expanda **Instalado** > [**Visual C#** ou **Visual Basic**] > **Área de Trabalho do Windows** ou digite **Serviço Windows** na caixa de pesquisa no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="5fb55-108">Expand **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, or type **Windows Service** in the search box on the upper right.</span></span>

   ![Modelo de Serviço Windows na caixa de diálogo Novo Projeto no Visual Studio](media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="5fb55-110">Se você não vir o modelo **Serviço Windows**, talvez seja necessário instalar a carga de trabalho **Desenvolvimento de área de trabalho do .NET**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-110">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload.</span></span> <span data-ttu-id="5fb55-111">Na caixa de diálogo **Novo Projeto**, clique no link que diz **Abrir o Instalador do Visual Studio** à esquerda.</span><span class="sxs-lookup"><span data-stu-id="5fb55-111">In the **New Project** dialog, click the link that says **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="5fb55-112">No **Instalador do Visual Studio**, selecione a carga de trabalho **desenvolvimento para área de trabalho do .NET** e, em seguida, escolha **Modificar**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-112">In **Visual Studio Installer**, select the **.NET desktop development** workload and then choose **Modify**.</span></span>

3. <span data-ttu-id="5fb55-113">Dê ao projeto o nome **MyNewService** e, em seguida, escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-113">Name the project **MyNewService**, and then choose **OK**.</span></span>

   <span data-ttu-id="5fb55-114">O modelo de projeto inclui uma classe de componente denominada `Service1` herdada de <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5fb55-114">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5fb55-115">Isso inclui grande parte do código de serviço básico, como o código para iniciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="5fb55-115">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="5fb55-116">Renomear o serviço</span><span class="sxs-lookup"><span data-stu-id="5fb55-116">Rename the service</span></span>

<span data-ttu-id="5fb55-117">Renomeie o serviço de **Service1** para **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-117">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="5fb55-118">No modo de exibição de **Design** para Service1.cs (ou Service1.vb), clique no link para **alternar para o modo de exibição de código**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-118">In the **Design** view for Service1.cs (or Service1.vb), click the link to **switch to code view**.</span></span> <span data-ttu-id="5fb55-119">Clique com o botão direito do mouse em **Service1** e selecione **Renomear** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="5fb55-119">Right-click on **Service1** and select **Rename** from the context menu.</span></span> <span data-ttu-id="5fb55-120">Insira **MyNewService** e, em seguida, pressione **Inserir** ou clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-120">Enter **MyNewService** and then press **Enter** or click **Apply**.</span></span>

2. <span data-ttu-id="5fb55-121">Na janela **Propriedades** para **Service1.cs [Design]** ou **Service1.vb [Design]**, altere o valor **ServiceName** para **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-121">In the **Properties** window for **Service1.cs [Design]** or **Service1.vb [Design]**, change the **ServiceName** value to **MyNewService**.</span></span>

3. <span data-ttu-id="5fb55-122">No **Gerenciador de Soluções**, renomeie **Service1.cs** para **MyNewService.cs** ou **Service1.vb** para **MyNewService.vb**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-122">In **Solution Explorer**, rename **Service1.cs** to **MyNewService.cs**, or rename **Service1.vb** to **MyNewService.vb**.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="5fb55-123">Adicionar recursos ao serviços</span><span class="sxs-lookup"><span data-stu-id="5fb55-123">Add features to the service</span></span>

<span data-ttu-id="5fb55-124">Na próxima seção, adicione um log de eventos personalizado ao serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="5fb55-124">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="5fb55-125">Os logs de eventos não são associados de forma alguma aos Windows Services.</span><span class="sxs-lookup"><span data-stu-id="5fb55-125">Event logs are not associated in any way with Windows services.</span></span> <span data-ttu-id="5fb55-126">O componente <xref:System.Diagnostics.EventLog> é usado aqui como um exemplo do tipo de componente que pode ser adicionado a um serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="5fb55-126">The <xref:System.Diagnostics.EventLog> component is used here as an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="5fb55-127">Adicionar a funcionalidade de log de eventos personalizado</span><span class="sxs-lookup"><span data-stu-id="5fb55-127">Add custom event log functionality</span></span>

1. <span data-ttu-id="5fb55-128">No **Gerenciador de Soluções**, abra o menu de contexto de **MyNewService.cs** ou **MyNewService.vb** e, em seguida, escolha **Designer de Exibição**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-128">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>

2. <span data-ttu-id="5fb55-129">Na seção **Componentes** da **Caixa de Ferramentas**, arraste um componente <xref:System.Diagnostics.EventLog> para o designer.</span><span class="sxs-lookup"><span data-stu-id="5fb55-129">From the **Components** section of the **Toolbox**, drag an <xref:System.Diagnostics.EventLog> component to the designer.</span></span>

3. <span data-ttu-id="5fb55-130">No **Gerenciador de Soluções**, abra o menu de contexto de **MyNewService.cs** ou **MyNewService.vb** e escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-130">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Code**.</span></span>

4. <span data-ttu-id="5fb55-131">Edite o construtor para definir um log de eventos personalizado:</span><span class="sxs-lookup"><span data-stu-id="5fb55-131">Edit the constructor to define a custom event log:</span></span>

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

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="5fb55-132">Definir o que ocorre quando o serviço é iniciado</span><span class="sxs-lookup"><span data-stu-id="5fb55-132">Define what occurs when the service starts</span></span>

<span data-ttu-id="5fb55-133">No editor do código, localize o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> que foi substituído automaticamente quando você criou o projeto.</span><span class="sxs-lookup"><span data-stu-id="5fb55-133">In the code editor, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method that was automatically overridden when you created the project.</span></span> <span data-ttu-id="5fb55-134">Adicione uma linha de código que escreve uma entrada no log de eventos quando o serviço é iniciado:</span><span class="sxs-lookup"><span data-stu-id="5fb55-134">Add a line of code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

<span data-ttu-id="5fb55-135">Um aplicativo de serviço foi projetado para executado a longo prazo, por isso ele geralmente controla ou monitora algo no sistema.</span><span class="sxs-lookup"><span data-stu-id="5fb55-135">A service application is designed to be long-running, so it usually polls or monitors something in the system.</span></span> <span data-ttu-id="5fb55-136">O monitoramento é configurado no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>.</span><span class="sxs-lookup"><span data-stu-id="5fb55-136">The monitoring is set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="5fb55-137">No entanto, o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> não realiza, de fato, o monitoramento.</span><span class="sxs-lookup"><span data-stu-id="5fb55-137">However, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> doesn’t actually do the monitoring.</span></span> <span data-ttu-id="5fb55-138">O método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> deve ser retornado ao sistema operacional depois que a operação do serviço tiver começado.</span><span class="sxs-lookup"><span data-stu-id="5fb55-138">The <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method must return to the operating system after the service's operation has begun.</span></span> <span data-ttu-id="5fb55-139">Ele não deve fazer loop para sempre nem bloqueios.</span><span class="sxs-lookup"><span data-stu-id="5fb55-139">It must not loop forever or block.</span></span> <span data-ttu-id="5fb55-140">Para configurar um mecanismo de pesquisa simples, você pode usar o componente <xref:System.Timers.Timer?displayProperty=nameWithType> da seguinte forma: no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, defina os parâmetros no componente e, em seguida, defina a propriedade <xref:System.Timers.Timer.Enabled%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="5fb55-140">To set up a simple polling mechanism, you can use the <xref:System.Timers.Timer?displayProperty=nameWithType> component as follows: In the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, set parameters on the component, and then set the <xref:System.Timers.Timer.Enabled%2A> property to `true`.</span></span> <span data-ttu-id="5fb55-141">O temporizador gera eventos no seu código periodicamente, no tempo em que seu serviço faria o monitoramento.</span><span class="sxs-lookup"><span data-stu-id="5fb55-141">The timer raises events in your code periodically, at which time your service could do its monitoring.</span></span> <span data-ttu-id="5fb55-142">Você pode usar o código a seguir para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="5fb55-142">You can use the following code to do this:</span></span>

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

<span data-ttu-id="5fb55-143">Adicione uma variável de membro à classe.</span><span class="sxs-lookup"><span data-stu-id="5fb55-143">Add a member variable to the class.</span></span> <span data-ttu-id="5fb55-144">Ela contém o identificador do próximo evento a ser gravado no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="5fb55-144">It contains the identifier of the next event to write into the event log.</span></span>

```csharp
private int eventId = 1;
```

```vb
Private eventId As Integer = 1
```

<span data-ttu-id="5fb55-145">Adicione um novo método para manipular o evento do temporizador:</span><span class="sxs-lookup"><span data-stu-id="5fb55-145">Add a new method to handle the timer event:</span></span>

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

<span data-ttu-id="5fb55-146">Você pode desejar executar tarefas usando segmentos de trabalho em segundo plano em vez de executar todo o seu trabalho no thread principal.</span><span class="sxs-lookup"><span data-stu-id="5fb55-146">You might want to perform tasks by using background worker threads instead of running all your work on the main thread.</span></span> <span data-ttu-id="5fb55-147">Para obter mais informações, consulte <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="5fb55-147">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="5fb55-148">Definir o que ocorre quando o serviço é interrompido</span><span class="sxs-lookup"><span data-stu-id="5fb55-148">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="5fb55-149">Adicione uma linha de código ao método <xref:System.ServiceProcess.ServiceBase.OnStop%2A> que adiciona uma entrada ao log de eventos quando o serviço é interrompido:</span><span class="sxs-lookup"><span data-stu-id="5fb55-149">Add a line of code to the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

```csharp
eventLog1.WriteEntry("In OnStop.");
```

[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="5fb55-150">Definir outras ações para o serviço</span><span class="sxs-lookup"><span data-stu-id="5fb55-150">Define other actions for the service</span></span>

<span data-ttu-id="5fb55-151">Também é possível substituir os métodos <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> e <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> para definir o processamento adicional para seu componente.</span><span class="sxs-lookup"><span data-stu-id="5fb55-151">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span> <span data-ttu-id="5fb55-152">O código a seguir mostra como você pode substituir o método <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>:</span><span class="sxs-lookup"><span data-stu-id="5fb55-152">The following code shows how you can override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

<span data-ttu-id="5fb55-153">Algumas ações personalizadas precisam ocorrer quando um serviço Windows é instalado pela classe <xref:System.Configuration.Install.Installer>.</span><span class="sxs-lookup"><span data-stu-id="5fb55-153">Some custom actions have to occur when a Windows service is installed by the <xref:System.Configuration.Install.Installer> class.</span></span> <span data-ttu-id="5fb55-154">O Visual Studio pode criar esses instaladores especificamente para um Windows Service e adicioná-los ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5fb55-154">Visual Studio can create these installers specifically for a Windows service and add them to your project.</span></span>

## <a name="set-service-status"></a><span data-ttu-id="5fb55-155">Definir status do serviço</span><span class="sxs-lookup"><span data-stu-id="5fb55-155">Set service status</span></span>

<span data-ttu-id="5fb55-156">Serviços relatam seu status para o Gerenciador de Controle de Serviço, para que os usuários possam determinar se um serviço está funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="5fb55-156">Services report their status to the Service Control Manager, so that users can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="5fb55-157">Por padrão, os serviços herdados de <xref:System.ServiceProcess.ServiceBase> relatam um conjunto limitado de configurações de status, inclusive Interrompido, Pausado e Em execução.</span><span class="sxs-lookup"><span data-stu-id="5fb55-157">By default, services that inherit from <xref:System.ServiceProcess.ServiceBase> report a limited set of status settings, including Stopped, Paused, and Running.</span></span> <span data-ttu-id="5fb55-158">Se um serviço demora um pouco para inicializar, ele pode ser útil relatar um status Iniciar pendente.</span><span class="sxs-lookup"><span data-stu-id="5fb55-158">If a service takes a little while to start up, it might be helpful to report a Start Pending status.</span></span> <span data-ttu-id="5fb55-159">Você também pode implementar as configurações de status Iniciar Pendente e Parar Pendente, adicionando o código que chama a [função SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) do Windows.</span><span class="sxs-lookup"><span data-stu-id="5fb55-159">You can also implement the Start Pending and Stop Pending status settings by adding code that calls into the Windows [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).</span></span>

<span data-ttu-id="5fb55-160">Para implementar o status pendente do serviço:</span><span class="sxs-lookup"><span data-stu-id="5fb55-160">To implement service pending status:</span></span>

1. <span data-ttu-id="5fb55-161">Adicione uma instrução `using` ou declaração `Imports` para o namespace <xref:System.Runtime.InteropServices?displayProperty=nameWithType> no arquivo MyNewService.cs ou MyNewService.vb:</span><span class="sxs-lookup"><span data-stu-id="5fb55-161">Add a `using` statement or `Imports` declaration for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace in the MyNewService.cs or MyNewService.vb file:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="5fb55-162">Adicione o seguinte código ao MyNewService.cs declarar os valores de `ServiceState` e para adicionar uma estrutura ao status, que você usará em uma chamada de invocação de plataforma:</span><span class="sxs-lookup"><span data-stu-id="5fb55-162">Add the following code to MyNewService.cs to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

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

3. <span data-ttu-id="5fb55-163">Agora, na classe `MyNewService`, declare a [função SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) usando a [inovação de plataforma](../interop/consuming-unmanaged-dll-functions.md):</span><span class="sxs-lookup"><span data-stu-id="5fb55-163">Now, in the `MyNewService` class, declare the [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="5fb55-164">Para implementar o status Iniciar pendente, adicione o seguinte código ao início do método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>:</span><span class="sxs-lookup"><span data-stu-id="5fb55-164">To implement the Start Pending status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

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

5. <span data-ttu-id="5fb55-165">Adicione o código para definir o status Em execução no final do método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>.</span><span class="sxs-lookup"><span data-stu-id="5fb55-165">Add code to set the status to Running at the end of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span>

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

6. <span data-ttu-id="5fb55-166">(Opcional) Repita esse procedimento para o método <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.</span><span class="sxs-lookup"><span data-stu-id="5fb55-166">(Optional) Repeat this procedure for the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="5fb55-167">O [Gerenciador de Controle de Serviço](/windows/desktop/Services/service-control-manager) usa os membros `dwWaitHint` e `dwCheckpoint` da [estrutura SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status) para determinar quanto tempo esperar para que um serviço Windows seja iniciado ou desligado.</span><span class="sxs-lookup"><span data-stu-id="5fb55-167">The [Service Control Manager](/windows/desktop/Services/service-control-manager) uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/desktop/api/winsvc/ns-winsvc-_service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="5fb55-168">Se os métodos <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> tiverem uma execução longa, o serviço poderá solicitar mais tempo chamando [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) novamente com um valor de `dwCheckPoint` incrementado.</span><span class="sxs-lookup"><span data-stu-id="5fb55-168">If your <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods run long, your service can request more time by calling [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) again with an incremented `dwCheckPoint` value.</span></span>

## <a name="add-installers-to-the-service"></a><span data-ttu-id="5fb55-169">Adicionar instaladores ao serviço</span><span class="sxs-lookup"><span data-stu-id="5fb55-169">Add installers to the service</span></span>

<span data-ttu-id="5fb55-170">Antes de executar um serviço Windows, é necessário instalá-lo, o que o registra com o Gerenciador de Controle de Serviço.</span><span class="sxs-lookup"><span data-stu-id="5fb55-170">Before you can run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="5fb55-171">Você pode adicionar instaladores ao seu projeto que lida com os detalhes de registro.</span><span class="sxs-lookup"><span data-stu-id="5fb55-171">You can add installers to your project that handle the registration details.</span></span>

1. <span data-ttu-id="5fb55-172">No **Gerenciador de Soluções**, abra o menu de contexto de **MyNewService.cs** ou **MyNewService.vb** e, em seguida, escolha **Designer de Exibição**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-172">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>

2. <span data-ttu-id="5fb55-173">Clique no plano de fundo do designer para selecionar o próprio serviço, e não um de seus conteúdos.</span><span class="sxs-lookup"><span data-stu-id="5fb55-173">Click the background of the designer to select the service itself, instead of any of its contents.</span></span>

3. <span data-ttu-id="5fb55-174">Abra o menu de contexto da janela do designer (se você estiver usando um dispositivo apontador, clique com o botão direito do mouse dentro da janela) e, em seguida, escolha **Adicionar Instalador**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-174">Open the context menu for the designer window (if you’re using a pointing device, right-click inside the window), and then choose **Add Installer**.</span></span>

   <span data-ttu-id="5fb55-175">Por padrão, uma classe de componente que contém dois instaladores é adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="5fb55-175">By default, a component class that contains two installers is added to your project.</span></span> <span data-ttu-id="5fb55-176">O componente é chamado **ProjectInstaller** e os instaladores que ele contém são o instalador do serviço e o instalador do processo associado ao serviço.</span><span class="sxs-lookup"><span data-stu-id="5fb55-176">The component is named **ProjectInstaller**, and the installers it contains are the installer for your service and the installer for the service's associated process.</span></span>

4. <span data-ttu-id="5fb55-177">Na exibição **Design** de **ProjectInstaller**, escolha **serviceInstaller1** para um projeto Visual C# ou **ServiceInstaller1** para um projeto Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5fb55-177">In **Design** view for **ProjectInstaller**, choose **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project.</span></span>

5. <span data-ttu-id="5fb55-178">Na janela **Propriedades**, verifique se a propriedade <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> está definida como **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-178">In the **Properties** window, make sure the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

6. <span data-ttu-id="5fb55-179">Defina a propriedade **Descrição** para um texto, como "Um exemplo de serviço".</span><span class="sxs-lookup"><span data-stu-id="5fb55-179">Set the **Description** property to some text, such as "A sample service".</span></span> <span data-ttu-id="5fb55-180">Este texto é exibido na janela Serviços e ajuda o usuário a identificar o serviço e entender para que ele é usado.</span><span class="sxs-lookup"><span data-stu-id="5fb55-180">This text appears in the Services window and helps the user identify the service and understand what it’s used for.</span></span>

7. <span data-ttu-id="5fb55-181">Defina a propriedade <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> para o texto que você deseja exibir na janela Serviços na coluna **Nome**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-181">Set the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property to the text that you want to appear in the Services window in the **Name** column.</span></span> <span data-ttu-id="5fb55-182">Por exemplo, você pode inserir "Nome de exibição do MyNewService".</span><span class="sxs-lookup"><span data-stu-id="5fb55-182">For example, you can enter "MyNewService Display Name".</span></span> <span data-ttu-id="5fb55-183">Esse nome pode ser diferente da propriedade <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>, que é o nome usado pelo sistema (por exemplo, quando você usa o comando `net start` para iniciar o serviço).</span><span class="sxs-lookup"><span data-stu-id="5fb55-183">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name used by the system (for example, when you use the `net start` command to start your service).</span></span>

8. <span data-ttu-id="5fb55-184">Defina a propriedade <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> como <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="5fb55-184">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span></span>

     <span data-ttu-id="5fb55-185">![Propriedades do instalador para um Serviço Windows](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span><span class="sxs-lookup"><span data-stu-id="5fb55-185">![Installer Properties for a Windows service](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span></span>

9. <span data-ttu-id="5fb55-186">No designer, escolha **serviceProcessInstaller1** para um projeto Visual C# ou **ServiceProcessInstaller1** para um projeto Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5fb55-186">In the designer, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project.</span></span> <span data-ttu-id="5fb55-187">Defina a propriedade <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> como <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span><span class="sxs-lookup"><span data-stu-id="5fb55-187">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span></span> <span data-ttu-id="5fb55-188">Isso faz o serviço ser instalado e executado usando a conta do sistema local.</span><span class="sxs-lookup"><span data-stu-id="5fb55-188">This causes the service to be installed and to run using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="5fb55-189">A conta <xref:System.ServiceProcess.ServiceAccount.LocalSystem> tem amplas permissões, incluindo a capacidade de gravar no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="5fb55-189">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="5fb55-190">Use essa conta com cuidado, pois ela pode aumentar o risco de ataques de software mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="5fb55-190">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="5fb55-191">Para outras tarefas, pense em usar a conta <xref:System.ServiceProcess.ServiceAccount.LocalService>, que atua como um usuário não privilegiado no computador local e apresenta credenciais anônimas a qualquer servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="5fb55-191">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="5fb55-192">Este exemplo falhará se você tentar usar a conta <xref:System.ServiceProcess.ServiceAccount.LocalService>, pois ele precisa de permissão para gravar no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="5fb55-192">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="5fb55-193">Para obter mais informações sobre instaladores, confira [Como adicionar instaladores ao aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="5fb55-193">For more information about installers, see [How to: Add Installers to Your service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="5fb55-194">(Opcional) Defina os parâmetros de inicialização</span><span class="sxs-lookup"><span data-stu-id="5fb55-194">(Optional) Set startup parameters</span></span>

<span data-ttu-id="5fb55-195">Um serviço Windows, como qualquer outro executável, pode aceitar argumentos de linha de comando ou parâmetros de inicialização.</span><span class="sxs-lookup"><span data-stu-id="5fb55-195">A Windows service, like any other executable, can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="5fb55-196">Quando você adiciona o código aos parâmetros de inicialização do processo, os usuários podem iniciar o serviço com seus próprios parâmetros de inicialização personalizada usando a janela de Serviços no Painel de Controle do Windows.</span><span class="sxs-lookup"><span data-stu-id="5fb55-196">When you add code to process startup parameters, users can start your service with their own custom startup parameters by using the Services window in the Windows Control Panel.</span></span> <span data-ttu-id="5fb55-197">No entanto, esses parâmetros de inicialização não são persistentes na próxima vez em que o serviço é iniciado.</span><span class="sxs-lookup"><span data-stu-id="5fb55-197">However, these startup parameters are not persisted the next time the service starts.</span></span> <span data-ttu-id="5fb55-198">Para definir os parâmetros de inicialização permanentemente, você pode defini-las no registro, conforme mostrado neste procedimento.</span><span class="sxs-lookup"><span data-stu-id="5fb55-198">To set startup parameters permanently, you can set them in the registry, as shown in this procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="5fb55-199">Antes de decidir adicionar parâmetros de inicialização, considere se esta é a melhor maneira de passar informações para o serviço.</span><span class="sxs-lookup"><span data-stu-id="5fb55-199">Before you decide to add startup parameters, consider whether that is the best way to pass information to your service.</span></span> <span data-ttu-id="5fb55-200">Embora os parâmetros de inicialização sejam fáceis de usar e analisar, e os usuários possam substituí-los facilmente, eles podem ser mais difíceis para os usuários descobrem e usarem sem a documentação.</span><span class="sxs-lookup"><span data-stu-id="5fb55-200">Although startup parameters are easy to use and to parse, and users can easily override them, they might be harder for users to discover and use without documentation.</span></span> <span data-ttu-id="5fb55-201">Em geral, se o serviço exigir mais do que apenas alguns parâmetros de inicialização, você deve considerar usar o registro ou um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5fb55-201">Generally, if your service requires more than just a few startup parameters, you should consider using the registry or a configuration file instead.</span></span> <span data-ttu-id="5fb55-202">Cada serviço Windows tem uma entrada no Registro em **HKLM\System\CurrentControlSet\services**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-202">Every Windows service has an entry in the registry under **HKLM\System\CurrentControlSet\services**.</span></span> <span data-ttu-id="5fb55-203">Na chave do serviço, você pode usar a subchave de **Parâmetros** para armazenar as informações que o serviço pode acessar.</span><span class="sxs-lookup"><span data-stu-id="5fb55-203">Under the service's key, you can use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="5fb55-204">É possível usar arquivos de configuração de aplicativo para um serviço Windows da mesma forma que faz para outros tipos de programas.</span><span class="sxs-lookup"><span data-stu-id="5fb55-204">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="5fb55-205">Para obter um exemplo de código, consulte <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span><span class="sxs-lookup"><span data-stu-id="5fb55-205">For example code, see <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span></span>

<span data-ttu-id="5fb55-206">Para adicionar parâmetros de inicialização:</span><span class="sxs-lookup"><span data-stu-id="5fb55-206">To add startup parameters:</span></span>

1. <span data-ttu-id="5fb55-207">No método `Main` no Program.cs ou MyNewService.Designer.vb, adicione um parâmetro de entrada para passar para o construtor do serviço:</span><span class="sxs-lookup"><span data-stu-id="5fb55-207">In the `Main` method in Program.cs or in MyNewService.Designer.vb, add an input parameter to pass to the service constructor:</span></span>

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

2. <span data-ttu-id="5fb55-208">Altere o construtor `MyNewService` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5fb55-208">Change the `MyNewService` constructor as follows:</span></span>

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

   <span data-ttu-id="5fb55-209">Esse código define o nome de origem e de log de eventos de acordo com os parâmetros de inicialização fornecidos ou usa os valores padrão se nenhum argumento for especificado.</span><span class="sxs-lookup"><span data-stu-id="5fb55-209">This code sets the event source and log name according to the supplied startup parameters, or uses default values if no arguments are supplied.</span></span>

3. <span data-ttu-id="5fb55-210">Para especificar os argumentos de linha de comando, adicione o seguinte código à classe `ProjectInstaller` em ProjectInstaller.cs ou ProjectInstaller.vb:</span><span class="sxs-lookup"><span data-stu-id="5fb55-210">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in ProjectInstaller.cs or ProjectInstaller.vb:</span></span>

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

   <span data-ttu-id="5fb55-211">Esse código modifica a chave do Registro **ImagePath**, que normalmente contém o caminho completo para o executável do serviço Windows adicionando os valores de parâmetro padrão.</span><span class="sxs-lookup"><span data-stu-id="5fb55-211">This code modifies the **ImagePath** registry key, which typically contains the full path to the executable for the Windows service, by adding the default parameter values.</span></span> <span data-ttu-id="5fb55-212">As aspas em torno do caminho (e em torno de cada parâmetro individual) são necessárias para o serviço ser inicializado corretamente.</span><span class="sxs-lookup"><span data-stu-id="5fb55-212">The quotation marks around the path (and around each individual parameter) are required for the service to start up correctly.</span></span> <span data-ttu-id="5fb55-213">Para alterar os parâmetros de inicialização desse serviço Windows, os usuários podem alterar os parâmetros fornecidos na chave do Registro **ImagePath**, embora seja melhor alterá-los de forma programática e expor a funcionalidade aos usuários de uma maneira amigável (por exemplo, em um utilitário de gerenciamento ou de configuração).</span><span class="sxs-lookup"><span data-stu-id="5fb55-213">To change the startup parameters for this Windows service, users can change the parameters given in the **ImagePath** registry key, although the better way is to change it programmatically and expose the functionality to users in a friendly way (for example, in a management or configuration utility).</span></span>

## <a name="build-the-service"></a><span data-ttu-id="5fb55-214">Compilar o serviço</span><span class="sxs-lookup"><span data-stu-id="5fb55-214">Build the service</span></span>

1. <span data-ttu-id="5fb55-215">No **Gerenciador de Soluções**, abra o menu de contexto do projeto e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-215">In **Solution Explorer**, open the context menu for your project, and then choose **Properties**.</span></span>

   <span data-ttu-id="5fb55-216">As páginas de propriedades do seu projeto aparecem.</span><span class="sxs-lookup"><span data-stu-id="5fb55-216">The property pages for your project appear.</span></span>

2. <span data-ttu-id="5fb55-217">Na guia **Aplicativo**, na lista **Objeto de inicialização**, escolha **MyNewService.Program**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-217">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**.</span></span>

3. <span data-ttu-id="5fb55-218">No **Gerenciador de Soluções**, abra o menu de contexto do seu projeto e, em seguida, escolha **Criar** para criar o projeto (ou pressione **Ctrl**+**Shift**+**B**).</span><span class="sxs-lookup"><span data-stu-id="5fb55-218">In **Solution Explorer**, open the context menu for your project, and then choose **Build** to build the project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="5fb55-219">Instalar o serviço</span><span class="sxs-lookup"><span data-stu-id="5fb55-219">Install the service</span></span>

<span data-ttu-id="5fb55-220">Agora que você criou o serviço Windows, poderá instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="5fb55-220">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="5fb55-221">Para instalar um serviço Windows, é necessário ter credenciais de administrador no computador no qual está sendo instalado.</span><span class="sxs-lookup"><span data-stu-id="5fb55-221">To install a Windows service, you must have administrator credentials on the computer on which you're installing it.</span></span>

1. <span data-ttu-id="5fb55-222">Abra o **Prompt de Comando do Desenvolvedor para Visual Studio** com credenciais administrativas.</span><span class="sxs-lookup"><span data-stu-id="5fb55-222">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span> <span data-ttu-id="5fb55-223">Se você estiver usando um mouse, clique com o botão direito dele em **Prompt de Comando do Desenvolvedor para VS 2017** no menu Iniciar do Windows e, em seguida, escolha **Mais** > **Executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-223">If you’re using a mouse, right-click on **Developer Command Prompt for VS 2017** in the Windows Start menu, and then choose **More** > **Run as Administrator**.</span></span>

2. <span data-ttu-id="5fb55-224">Na janela **Prompt de Comando do Desenvolvedor**, navegue até a pasta que contém a saída do seu projeto (por padrão, é o subdiretório *\bin\Debug* do seu projeto).</span><span class="sxs-lookup"><span data-stu-id="5fb55-224">In the **Developer Command Prompt** window, navigate to the folder that contains your project's output (by default, it's the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="5fb55-225">Insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="5fb55-225">Enter the following command:</span></span>

    ```shell
    installutil.exe MyNewService.exe
    ```

    <span data-ttu-id="5fb55-226">Se o serviço for instalado com êxito, **installutil.exe** relatará o sucesso.</span><span class="sxs-lookup"><span data-stu-id="5fb55-226">If the service installs successfully, **installutil.exe** reports success.</span></span> <span data-ttu-id="5fb55-227">Se o sistema não puder localizar **InstallUtil.exe**, certifique-se de que ele existe no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5fb55-227">If the system could not find **InstallUtil.exe**, make sure that it exists on your computer.</span></span> <span data-ttu-id="5fb55-228">Essa ferramenta é instalada com o .NET Framework na pasta *%windir%\Microsoft.NET\Framework[64]\\[versão do framework]*.</span><span class="sxs-lookup"><span data-stu-id="5fb55-228">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\[framework version]*.</span></span> <span data-ttu-id="5fb55-229">Por exemplo, o caminho padrão da versão de 32 bits é *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="5fb55-229">For example, the default path for the 32-bit version is *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="5fb55-230">Se o processo de **installutil.exe** relatar falha, verifique o log de instalação para saber o motivo.</span><span class="sxs-lookup"><span data-stu-id="5fb55-230">If the **installutil.exe** process reports failure, check the install log to find out why.</span></span> <span data-ttu-id="5fb55-231">Por padrão o log está na mesma pasta que o executável do serviço.</span><span class="sxs-lookup"><span data-stu-id="5fb55-231">By default the log is in the same folder as the service executable.</span></span> <span data-ttu-id="5fb55-232">A instalação poderá falhar se a classe <xref:System.ComponentModel.RunInstallerAttribute> não estiver presente na classe `ProjectInstaller`, se o atributo não estiver definido como **true** ou se a classe `ProjectInstaller` não for marcada **pública**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-232">The installation can fail if  the <xref:System.ComponentModel.RunInstallerAttribute> Class is not present on the `ProjectInstaller` class, if the attribute is not set to **true**, or if the `ProjectInstaller` class is not marked **public**.</span></span>

<span data-ttu-id="5fb55-233">Para obter mais informações, confira [Como instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="5fb55-233">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="5fb55-234">Iniciar e executar o serviço</span><span class="sxs-lookup"><span data-stu-id="5fb55-234">Start and run the service</span></span>

1. <span data-ttu-id="5fb55-235">No Windows, abra o aplicativo da área de trabalho **Serviços**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-235">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="5fb55-236">Pressione **Windows**+**R** para abrir a caixa **Executar** e, em seguida, insira **services.msc** e pressione **Enter** ou clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-236">Press **Windows**+**R** to open the **Run** box, and then enter **services.msc** and press **Enter** or click **OK**.</span></span>

     <span data-ttu-id="5fb55-237">Você deve ver o serviço listado em **Serviços**, exibido em ordem alfabética pelo nome de exibição definido para ele.</span><span class="sxs-lookup"><span data-stu-id="5fb55-237">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![MyNewService na janela Serviços.](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="5fb55-239">Em **Serviços**, abra o menu de atalho para seu serviço e, em seguida, escolha **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-239">In **Services**, open the shortcut menu for your service, and then choose **Start**.</span></span>

3. <span data-ttu-id="5fb55-240">Para interromper o serviço, abra o menu de atalho do serviço e, em seguida, escolha **Interromper**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-240">To stop the service, open the shortcut menu for the service, and then choose **Stop**.</span></span>

4. <span data-ttu-id="5fb55-241">(Opcional) Na linha de comando, você pode usar os comandos `net start ServiceName` e `net stop ServiceName` para iniciar e parar o serviço.</span><span class="sxs-lookup"><span data-stu-id="5fb55-241">(Optional) From the command line, you can use the commands `net start ServiceName` and `net stop ServiceName` to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="5fb55-242">Verificar a saída do log de eventos do seu serviço</span><span class="sxs-lookup"><span data-stu-id="5fb55-242">Verify the event log output of your service</span></span>

1. <span data-ttu-id="5fb55-243">Abra o **Visualizador de Eventos** começando a digitar **Visualizador de Eventos** na caixa de pesquisa na barra de tarefas do Windows e, em seguida, selecionando **Visualizador de Eventos** nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="5fb55-243">Open **Event Viewer** by starting to type **Event Viewer** in the search box on the Windows task bar, and then selecting **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="5fb55-244">No Visual Studio, é possível acessar logs de eventos abrindo **Gerenciador de Servidores** (Teclado: **Ctrl**+**Alt**+**S**) e expandindo o nó **Logs de Eventos** no computador local.</span><span class="sxs-lookup"><span data-stu-id="5fb55-244">In Visual Studio, you can access event logs by opening **Server Explorer** (Keyboard: **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="5fb55-245">No **Visualizador de Eventos**, expanda **Logs de Aplicativos e Serviços**.</span><span class="sxs-lookup"><span data-stu-id="5fb55-245">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="5fb55-246">Localize a listagem para **MyNewLog** (ou **MyLogFile1**, se você seguiu o procedimento opcional para adicionar argumentos de linha de comando) e expanda-a.</span><span class="sxs-lookup"><span data-stu-id="5fb55-246">Locate the listing for **MyNewLog** (or **MyLogFile1**, if you followed the optional procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="5fb55-247">Você deve ver entradas para as duas ações (iniciar e interromper) que seu serviço executou.</span><span class="sxs-lookup"><span data-stu-id="5fb55-247">You should see entries for the two actions (start and stop) that your service performed.</span></span>

     ![Use o Visualizador de Eventos para ver as entradas do log de eventos](../../../docs/framework/windows-services/media/windows-service-event-viewer.png)

## <a name="uninstall-the-service"></a><span data-ttu-id="5fb55-249">Desinstalar o serviço</span><span class="sxs-lookup"><span data-stu-id="5fb55-249">Uninstall the service</span></span>

1. <span data-ttu-id="5fb55-250">Abra o **Prompt de Comando do Desenvolvedor para Visual Studio** com credenciais administrativas.</span><span class="sxs-lookup"><span data-stu-id="5fb55-250">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="5fb55-251">Na janela do prompt de comando, navegue até a pasta que contém a saída do projeto.</span><span class="sxs-lookup"><span data-stu-id="5fb55-251">In the command prompt window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="5fb55-252">Insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="5fb55-252">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="5fb55-253">Se o serviço for desinstalado com êxito, **installutil.exe** relatará que seu serviço foi removido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="5fb55-253">If the service uninstalls successfully, **installutil.exe** reports that your service was successfully removed.</span></span> <span data-ttu-id="5fb55-254">Para obter mais informações, confira [Como instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="5fb55-254">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5fb55-255">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="5fb55-255">Next steps</span></span>

<span data-ttu-id="5fb55-256">Agora que você criou o serviço, crie um programa de instalação autônomo que outras pessoas possam usar para instalar seu serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="5fb55-256">Now that you've created the service, you might want to create a standalone setup program that others can use to install your Windows service.</span></span> <span data-ttu-id="5fb55-257">O ClickOnce não dá suporte a serviços Windows, mas é possível usar o [WiX Toolset](http://wixtoolset.org/) para criar um instalador para um serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="5fb55-257">ClickOnce doesn't support Windows services, but you can use the [WiX Toolset](http://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="5fb55-258">Para ver outras ideias, confira [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client) (Criar um pacote do instalador).</span><span class="sxs-lookup"><span data-stu-id="5fb55-258">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span></span>

<span data-ttu-id="5fb55-259">Você pode explorar o uso de um componente <xref:System.ServiceProcess.ServiceController>, que permite que você envie comandos ao serviço que instalou.</span><span class="sxs-lookup"><span data-stu-id="5fb55-259">You might explore the use of a <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

<span data-ttu-id="5fb55-260">É possível usar um instalador para criar um log de eventos quando o aplicativo é instalado, em vez de criá-lo quando o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="5fb55-260">You can use an installer to create an event log when the application is installed instead of creating the event log when the application runs.</span></span> <span data-ttu-id="5fb55-261">Além disso, o log de eventos será excluído pelo instalador quando o aplicativo for desinstalado.</span><span class="sxs-lookup"><span data-stu-id="5fb55-261">Additionally, the event log will be deleted by the installer when the application is uninstalled.</span></span> <span data-ttu-id="5fb55-262">Para obter mais informações, consulte a página de referência <xref:System.Diagnostics.EventLogInstaller>.</span><span class="sxs-lookup"><span data-stu-id="5fb55-262">For more information, see the <xref:System.Diagnostics.EventLogInstaller> reference page.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fb55-263">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fb55-263">See also</span></span>

- [<span data-ttu-id="5fb55-264">Aplicativos do serviço Windows</span><span class="sxs-lookup"><span data-stu-id="5fb55-264">Windows service applications</span></span>](../../../docs/framework/windows-services/index.md)
- [<span data-ttu-id="5fb55-265">Introdução aos aplicativos do serviço Windows</span><span class="sxs-lookup"><span data-stu-id="5fb55-265">Introduction to Windows service applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="5fb55-266">Como depurar aplicativos de serviço Windows</span><span class="sxs-lookup"><span data-stu-id="5fb55-266">How to: Debug Windows service applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="5fb55-267">Serviços (Windows)</span><span class="sxs-lookup"><span data-stu-id="5fb55-267">Services (Windows)</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
