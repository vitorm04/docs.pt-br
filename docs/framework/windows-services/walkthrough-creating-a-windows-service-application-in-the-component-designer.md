---
title: 'Tutorial: Criar um aplicativo de serviço Windows'
ms.date: 03/27/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: e5ff40d8413acf64e7a8a129a7b268f58780d591
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053478"
---
# <a name="tutorial-create-a-windows-service-app"></a><span data-ttu-id="56b09-102">Tutorial: Criar um aplicativo de serviço Windows</span><span class="sxs-lookup"><span data-stu-id="56b09-102">Tutorial: Create a Windows service app</span></span>

<span data-ttu-id="56b09-103">Este artigo demonstra como criar um aplicativo de serviço Windows no Visual Studio que grava mensagens em um log de eventos.</span><span class="sxs-lookup"><span data-stu-id="56b09-103">This article demonstrates how to create a Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="56b09-104">Criar um serviço</span><span class="sxs-lookup"><span data-stu-id="56b09-104">Create a service</span></span>

<span data-ttu-id="56b09-105">Para começar, crie o projeto e defina os valores necessários para o serviço funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="56b09-105">To begin, create the project and set the values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="56b09-106">No menu **Arquivo** do Visual Studio, selecione **Novo** > **Projeto** (ou pressione **Ctrl**+**Shift**+**N**) para abrir a janela **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="56b09-106">From the Visual Studio **File** menu, select **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** window.</span></span>

2. <span data-ttu-id="56b09-107">Navegue para o modelo de projeto **Serviço Windows (.NET Framework)** e selecione-o.</span><span class="sxs-lookup"><span data-stu-id="56b09-107">Navigate to and select the **Windows Service (.NET Framework)** project template.</span></span> <span data-ttu-id="56b09-108">Para encontrá-lo, expanda **Instalados** e **Visual C#** ou **Visual Basic** e, em seguida, selecione **Windows Desktop**.</span><span class="sxs-lookup"><span data-stu-id="56b09-108">To find it, expand **Installed** and **Visual C#** or **Visual Basic**, then select **Windows Desktop**.</span></span> <span data-ttu-id="56b09-109">Se preferir, insira *Serviço Windows* na caixa de pesquisa no canto superior direito e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="56b09-109">Or, enter *Windows Service* in the search box on the upper right and press **Enter**.</span></span>

   ![Modelo de Serviço Windows na caixa de diálogo Novo Projeto no Visual Studio](./media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="56b09-111">Se o modelo **Serviço Windows** não for exibido, talvez seja necessário instalar a carga de trabalho **Desenvolvimento para desktop com .NET**:</span><span class="sxs-lookup"><span data-stu-id="56b09-111">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload:</span></span>
   >
   > <span data-ttu-id="56b09-112">Na caixa de diálogo **Novo Projeto**, selecione **Abrir Instalador do Visual Studio** na parte inferior esquerda.</span><span class="sxs-lookup"><span data-stu-id="56b09-112">In the **New Project** dialog, select **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="56b09-113">Selecione a carga de trabalho **Desenvolvimento para desktop com .NET** e, em seguida, selecione **Modificar**.</span><span class="sxs-lookup"><span data-stu-id="56b09-113">Select the **.NET desktop development** workload, and then select **Modify**.</span></span>

3. <span data-ttu-id="56b09-114">Em **Nome**, insira *MyNewService* e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="56b09-114">For **Name**, enter *MyNewService*, and then select **OK**.</span></span>

   <span data-ttu-id="56b09-115">A guia **Design** será exibida (**Service1.cs [Design]** ou **Service1.vb [Design]** ).</span><span class="sxs-lookup"><span data-stu-id="56b09-115">The **Design** tab appears (**Service1.cs [Design]** or **Service1.vb [Design]**).</span></span>

   <span data-ttu-id="56b09-116">O modelo de projeto inclui uma classe de componente denominada `Service1` herdada de <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="56b09-116">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="56b09-117">Isso inclui grande parte do código de serviço básico, como o código para iniciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="56b09-117">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="56b09-118">Renomear o serviço</span><span class="sxs-lookup"><span data-stu-id="56b09-118">Rename the service</span></span>

<span data-ttu-id="56b09-119">Renomeie o serviço de **Service1** para **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="56b09-119">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="56b09-120">No **Gerenciador de Soluções**, selecione **Service1.cs** ou **Service1.vb** e escolha **Renomear** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="56b09-120">In **Solution Explorer**, select **Service1.cs**, or **Service1.vb**, and choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="56b09-121">Renomeie o arquivo como **MyNewService.cs** ou **MyNewService.vb** e, em seguida, pressione **Enter**</span><span class="sxs-lookup"><span data-stu-id="56b09-121">Rename the file to **MyNewService.cs**, or **MyNewService.vb**, and then press **Enter**</span></span>

    <span data-ttu-id="56b09-122">Uma janela pop-up será exibida perguntando se você deseja renomear todas as referências ao elemento de código *Service1*.</span><span class="sxs-lookup"><span data-stu-id="56b09-122">A pop-up window appears asking whether you would like to rename all references to the code element *Service1*.</span></span>

2. <span data-ttu-id="56b09-123">Na janela pop-up, selecione **Sim**.</span><span class="sxs-lookup"><span data-stu-id="56b09-123">In the pop-up window, select **Yes**.</span></span>

    <span data-ttu-id="56b09-124">![Prompt Renomear](./media/windows-service-rename.png "Prompt Renomear o serviço Windows")</span><span class="sxs-lookup"><span data-stu-id="56b09-124">![Rename prompt](./media/windows-service-rename.png "Windows service rename prompt")</span></span>

3. <span data-ttu-id="56b09-125">Na guia **Design**, selecione **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="56b09-125">In the **Design** tab, select **Properties** from the shortcut menu.</span></span> <span data-ttu-id="56b09-126">Na janela **Propriedades**, altere o valor **ServiceName** para *MyNewService*.</span><span class="sxs-lookup"><span data-stu-id="56b09-126">From the **Properties** window, change the **ServiceName** value to *MyNewService*.</span></span>

    <span data-ttu-id="56b09-127">![Propriedades do serviço](./media/windows-service-properties.png "Propriedades do serviço Windows")</span><span class="sxs-lookup"><span data-stu-id="56b09-127">![Service properties](./media/windows-service-properties.png "Windows service properties")</span></span>

4. <span data-ttu-id="56b09-128">Selecione **Salvar Tudo** no menu **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="56b09-128">Select **Save All** from the **File** menu.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="56b09-129">Adicionar recursos ao serviços</span><span class="sxs-lookup"><span data-stu-id="56b09-129">Add features to the service</span></span>

<span data-ttu-id="56b09-130">Na próxima seção, adicione um log de eventos personalizado ao serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="56b09-130">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="56b09-131">O componente <xref:System.Diagnostics.EventLog> é um exemplo do tipo de componente que pode ser adicionado a um serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="56b09-131">The <xref:System.Diagnostics.EventLog> component is an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="56b09-132">Adicionar a funcionalidade de log de eventos personalizado</span><span class="sxs-lookup"><span data-stu-id="56b09-132">Add custom event log functionality</span></span>

1. <span data-ttu-id="56b09-133">No **Gerenciador de Soluções**, no menu de atalho de **MyNewService.cs** ou **MyNewService.vb**, escolha **Designer de Exibição**.</span><span class="sxs-lookup"><span data-stu-id="56b09-133">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="56b09-134">Na **Caixa de Ferramentas**, expanda **Componentes** e, em seguida, arraste o componente **EventLog** para a guia **Service1.cs [Design]** ou **Service1.vb [Design]** .</span><span class="sxs-lookup"><span data-stu-id="56b09-134">In **Toolbox**, expand **Components**, and then drag the **EventLog** component to the **Service1.cs [Design]**, or **Service1.vb [Design]** tab.</span></span>

3. <span data-ttu-id="56b09-135">No **Gerenciador de Soluções**, no menu de atalho de **MyNewService.cs** ou **MyNewService.vb**, escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="56b09-135">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Code**.</span></span>

4. <span data-ttu-id="56b09-136">Defina um log de eventos personalizado.</span><span class="sxs-lookup"><span data-stu-id="56b09-136">Define a custom event log.</span></span> <span data-ttu-id="56b09-137">Para o C#, edite o construtor `MyNewService()` existente; para o Visual Basic, adicione o construtor `New()`:</span><span class="sxs-lookup"><span data-stu-id="56b09-137">For C#, edit the existing `MyNewService()` constructor; for Visual Basic, add the `New()` constructor:</span></span>

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. <span data-ttu-id="56b09-138">Adicione uma instrução `using` a **MyNewService.cs** (caso ela ainda não exista) ou uma instrução `Imports` a **MyNewService.vb** para o namespace <xref:System.Diagnostics?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="56b09-138">Add a `using` statement to **MyNewService.cs** (if it doesn't already exist), or an `Imports` statement **MyNewService.vb**, for the <xref:System.Diagnostics?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. <span data-ttu-id="56b09-139">Selecione **Salvar Tudo** no menu **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="56b09-139">Select **Save All** from the **File** menu.</span></span>

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="56b09-140">Definir o que ocorre quando o serviço é iniciado</span><span class="sxs-lookup"><span data-stu-id="56b09-140">Define what occurs when the service starts</span></span>

<span data-ttu-id="56b09-141">No editor de códigos de **MyNewService.cs** ou **MyNewService.vb**, localize o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>; o Visual Studio criou automaticamente uma definição de método vazia quando você criou o projeto.</span><span class="sxs-lookup"><span data-stu-id="56b09-141">In the code editor for **MyNewService.cs** or **MyNewService.vb**, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method; Visual Studio automatically created an empty method definition when you created the project.</span></span> <span data-ttu-id="56b09-142">Adicione um código que grava uma entrada no log de eventos quando o serviço é iniciado:</span><span class="sxs-lookup"><span data-stu-id="56b09-142">Add code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a><span data-ttu-id="56b09-143">Sondagem</span><span class="sxs-lookup"><span data-stu-id="56b09-143">Polling</span></span>

<span data-ttu-id="56b09-144">Como um aplicativo de serviço foi projetado para ser de execução longa, ele geralmente sonda ou monitora o sistema, que você configurou no método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>.</span><span class="sxs-lookup"><span data-stu-id="56b09-144">Because a service application is designed to be long-running, it usually polls or monitors the system, which you set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="56b09-145">O método `OnStart` precisa ser retornado ao sistema operacional depois que a operação do serviço é iniciada, de modo que o sistema não seja bloqueado.</span><span class="sxs-lookup"><span data-stu-id="56b09-145">The `OnStart` method must return to the operating system after the service's operation has begun so that the system isn't blocked.</span></span>

<span data-ttu-id="56b09-146">Para configurar um mecanismo simples de sondagem, use o componente <xref:System.Timers.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="56b09-146">To set up a simple polling mechanism, use the <xref:System.Timers.Timer?displayProperty=nameWithType> component.</span></span> <span data-ttu-id="56b09-147">O temporizador aciona um evento <xref:System.Timers.Timer.Elapsed> em intervalos regulares, momento em que o serviço pode fazer o monitoramento.</span><span class="sxs-lookup"><span data-stu-id="56b09-147">The timer raises an <xref:System.Timers.Timer.Elapsed> event at regular intervals, at which time your service can do its monitoring.</span></span> <span data-ttu-id="56b09-148">Use o componente <xref:System.Timers.Timer> da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="56b09-148">You use the <xref:System.Timers.Timer> component as follows:</span></span>

- <span data-ttu-id="56b09-149">Defina as propriedades do componente <xref:System.Timers.Timer> no método `MyNewService.OnStart`.</span><span class="sxs-lookup"><span data-stu-id="56b09-149">Set the properties of the <xref:System.Timers.Timer> component in the `MyNewService.OnStart` method.</span></span>
- <span data-ttu-id="56b09-150">Inicie o temporizador chamando o método <xref:System.Timers.Timer.Start%2A>.</span><span class="sxs-lookup"><span data-stu-id="56b09-150">Start the timer by calling the <xref:System.Timers.Timer.Start%2A> method.</span></span>

##### <a name="set-up-the-polling-mechanism"></a><span data-ttu-id="56b09-151">Configure o mecanismo de sondagem.</span><span class="sxs-lookup"><span data-stu-id="56b09-151">Set up the polling mechanism.</span></span>

1. <span data-ttu-id="56b09-152">Adicione o seguinte código ao evento `MyNewService.OnStart` para configurar o mecanismo de sondagem:</span><span class="sxs-lookup"><span data-stu-id="56b09-152">Add the following code in the `MyNewService.OnStart` event to set up the polling mechanism:</span></span>

   ```csharp
   // Set up a timer that triggers every minute.
   Timer timer = new Timer();
   timer.Interval = 60000; // 60 seconds
   timer.Elapsed += new ElapsedEventHandler(this.OnTimer);
   timer.Start();
   ```

   ```vb
   ' Set up a timer that triggers every minute.
   Dim timer As Timer = New Timer()
   timer.Interval = 60000 ' 60 seconds
   AddHandler timer.Elapsed, AddressOf Me.OnTimer
   timer.Start()
   ```

2. <span data-ttu-id="56b09-153">Adicione uma instrução `using` a **MyNewService.cs** ou uma instrução `Imports` a **MyNewService.vb** para o namespace <xref:System.Timers?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="56b09-153">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Timers?displayProperty=nameWithType> namespace:</span></span>

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. <span data-ttu-id="56b09-154">Na classe `MyNewService`, adicione o método `OnTimer` para manipular o evento <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="56b09-154">In the `MyNewService` class, add the `OnTimer` method to handle the <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> event:</span></span>

   ```csharp
   public void OnTimer(object sender, ElapsedEventArgs args)
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

4. <span data-ttu-id="56b09-155">Na classe `MyNewService`, adicione uma variável de membro.</span><span class="sxs-lookup"><span data-stu-id="56b09-155">In the `MyNewService` class, add a member variable.</span></span> <span data-ttu-id="56b09-156">Ela contém o identificador do próximo evento a ser gravado no log de eventos:</span><span class="sxs-lookup"><span data-stu-id="56b09-156">It contains the identifier of the next event to write into the event log:</span></span>

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

<span data-ttu-id="56b09-157">Em vez de executar todo o trabalho no thread principal, você pode executar tarefas usando threads de trabalho em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="56b09-157">Instead of running all your work on the main thread, you can run tasks by using background worker threads.</span></span> <span data-ttu-id="56b09-158">Para obter mais informações, consulte <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="56b09-158">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="56b09-159">Definir o que ocorre quando o serviço é interrompido</span><span class="sxs-lookup"><span data-stu-id="56b09-159">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="56b09-160">Insira uma linha de código no método <xref:System.ServiceProcess.ServiceBase.OnStop%2A> que adiciona uma entrada ao log de eventos quando o serviço é interrompido:</span><span class="sxs-lookup"><span data-stu-id="56b09-160">Insert a line of code in the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="56b09-161">Definir outras ações para o serviço</span><span class="sxs-lookup"><span data-stu-id="56b09-161">Define other actions for the service</span></span>

<span data-ttu-id="56b09-162">Também é possível substituir os métodos <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> e <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> para definir o processamento adicional para seu componente.</span><span class="sxs-lookup"><span data-stu-id="56b09-162">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span>

<span data-ttu-id="56b09-163">O seguinte código mostra como substituir o método <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> na classe `MyNewService`:</span><span class="sxs-lookup"><span data-stu-id="56b09-163">The following code shows how you to override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method in the `MyNewService` class:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a><span data-ttu-id="56b09-164">Definir status do serviço</span><span class="sxs-lookup"><span data-stu-id="56b09-164">Set service status</span></span>

<span data-ttu-id="56b09-165">Os serviços relatam seu status para o [Gerenciador de Controle de Serviço](/windows/desktop/Services/service-control-manager), de modo que um usuário possa determinar se um serviço está funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="56b09-165">Services report their status to the [Service Control Manager](/windows/desktop/Services/service-control-manager) so that a user can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="56b09-166">Por padrão, um serviço que herda de <xref:System.ServiceProcess.ServiceBase> relata um conjunto limitado de configurações de status, que incluem SERVICE_STOPPED, SERVICE_PAUSED e SERVICE_RUNNING.</span><span class="sxs-lookup"><span data-stu-id="56b09-166">By default, a service that inherits from <xref:System.ServiceProcess.ServiceBase> reports a limited set of status settings, which include SERVICE_STOPPED, SERVICE_PAUSED, and SERVICE_RUNNING.</span></span> <span data-ttu-id="56b09-167">Se um serviço leva um tempo para ser inicializado, é útil relatar um status SERVICE_START_PENDING.</span><span class="sxs-lookup"><span data-stu-id="56b09-167">If a service takes a while to start up, it's useful to report a SERVICE_START_PENDING status.</span></span>

<span data-ttu-id="56b09-168">Você pode implementar as configurações de status SERVICE_START_PENDING e SERVICE_STOP_PENDING adicionando o código que chama a função [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) do Windows.</span><span class="sxs-lookup"><span data-stu-id="56b09-168">You can implement the SERVICE_START_PENDING and SERVICE_STOP_PENDING status settings by adding code that calls the Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function.</span></span>

### <a name="implement-service-pending-status"></a><span data-ttu-id="56b09-169">Implementar o status pendente do serviço</span><span class="sxs-lookup"><span data-stu-id="56b09-169">Implement service pending status</span></span>

1. <span data-ttu-id="56b09-170">Adicione uma instrução `using` a **MyNewService.cs** ou uma instrução `Imports` a **MyNewService.vb** para o namespace <xref:System.Runtime.InteropServices?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="56b09-170">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="56b09-171">Adicione o seguinte código a **MyNewService.cs** ou **MyNewService.vb** para declarar os valores `ServiceState` e adicionar uma estrutura ao status, que você usará em uma chamada de invocação de plataforma:</span><span class="sxs-lookup"><span data-stu-id="56b09-171">Add the following code to **MyNewService.cs**, or **MyNewService.vb**, to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

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

    > [!NOTE]
    > <span data-ttu-id="56b09-172">O Gerenciador de Controle de Serviço usa os membros `dwWaitHint` e `dwCheckpoint` da [estrutura SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) para determinar quanto tempo aguardar um serviço Windows ser iniciado ou desligado.</span><span class="sxs-lookup"><span data-stu-id="56b09-172">The Service Control Manager uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/win32/api/winsvc/ns-winsvc-service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="56b09-173">Se os métodos `OnStart` e `OnStop` tiverem uma execução longa, o serviço poderá solicitar mais tempo chamando `SetServiceStatus` novamente com um valor `dwCheckPoint` incrementado.</span><span class="sxs-lookup"><span data-stu-id="56b09-173">If your `OnStart` and `OnStop` methods run long, your service can request more time by calling `SetServiceStatus` again with an incremented `dwCheckPoint` value.</span></span>

3. <span data-ttu-id="56b09-174">Na classe `MyNewService`, declare a função [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) usando a [inovação de plataforma](../interop/consuming-unmanaged-dll-functions.md):</span><span class="sxs-lookup"><span data-stu-id="56b09-174">In the `MyNewService` class, declare the [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="56b09-175">Para implementar o status SERVICE_START_PENDING, adicione o seguinte código ao início do método <xref:System.ServiceProcess.ServiceBase.OnStart%2A>:</span><span class="sxs-lookup"><span data-stu-id="56b09-175">To implement the SERVICE_START_PENDING status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

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

5. <span data-ttu-id="56b09-176">Adicione o código ao final do método `OnStart` para definir o status como SERVICE_RUNNING:</span><span class="sxs-lookup"><span data-stu-id="56b09-176">Add code to the end of the `OnStart` method to set the status to SERVICE_RUNNING:</span></span>

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

6. <span data-ttu-id="56b09-177">(Opcional) Se <xref:System.ServiceProcess.ServiceBase.OnStop%2A> for um método de execução longa, repita esse procedimento no método `OnStop`.</span><span class="sxs-lookup"><span data-stu-id="56b09-177">(Optional) If <xref:System.ServiceProcess.ServiceBase.OnStop%2A> is a long-running method, repeat this procedure in the `OnStop` method.</span></span> <span data-ttu-id="56b09-178">Implemente o status SERVICE_STOP_PENDING e retorne o status SERVICE_STOPPED antes da saída do método `OnStop`.</span><span class="sxs-lookup"><span data-stu-id="56b09-178">Implement the SERVICE_STOP_PENDING status and return the SERVICE_STOPPED status before the `OnStop` method exits.</span></span>

   <span data-ttu-id="56b09-179">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="56b09-179">For example:</span></span>

    ```csharp
    // Update the service state to Stop Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);

    // Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Stop Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)

    ' Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

## <a name="add-installers-to-the-service"></a><span data-ttu-id="56b09-180">Adicionar instaladores ao serviço</span><span class="sxs-lookup"><span data-stu-id="56b09-180">Add installers to the service</span></span>

<span data-ttu-id="56b09-181">Antes de executar um serviço Windows, é necessário instalá-lo, o que o registra no Gerenciador de Controle de Serviço.</span><span class="sxs-lookup"><span data-stu-id="56b09-181">Before you run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="56b09-182">Adicione instaladores ao projeto para lidar com os detalhes de registro.</span><span class="sxs-lookup"><span data-stu-id="56b09-182">Add installers to your project to handle the registration details.</span></span>

1. <span data-ttu-id="56b09-183">No **Gerenciador de Soluções**, no menu de atalho de **MyNewService.cs** ou **MyNewService.vb**, escolha **Designer de Exibição**.</span><span class="sxs-lookup"><span data-stu-id="56b09-183">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="56b09-184">Na exibição **Design**, selecione a área em segundo plano e, em seguida, escolha **Adicionar Instalador** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="56b09-184">In the **Design** view, select the background area, then choose **Add Installer** from the shortcut menu.</span></span>

     <span data-ttu-id="56b09-185">Por padrão, o Visual Studio adiciona uma classe de componente chamada `ProjectInstaller`, que contém dois instaladores, ao projeto.</span><span class="sxs-lookup"><span data-stu-id="56b09-185">By default, Visual Studio adds a component class named `ProjectInstaller`, which contains two installers, to your project.</span></span> <span data-ttu-id="56b09-186">Esses instaladores destinam-se ao serviço e ao processo associado do serviço.</span><span class="sxs-lookup"><span data-stu-id="56b09-186">These installers are for your service and for the service's associated process.</span></span>

3. <span data-ttu-id="56b09-187">Na exibição **Design** de **ProjectInstaller**, selecione **serviceInstaller1** para um projeto do Visual C# ou **ServiceInstaller1** para um projeto do Visual Basic e, em seguida, escolha **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="56b09-187">In the **Design** view for **ProjectInstaller**, select **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="56b09-188">Na janela **Propriedades**, verifique se a propriedade <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> está definida como **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="56b09-188">In the **Properties** window, verify the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

5. <span data-ttu-id="56b09-189">Adicione um texto à propriedade <xref:System.ServiceProcess.ServiceInstaller.Description%2A>, como *Um serviço de exemplo*.</span><span class="sxs-lookup"><span data-stu-id="56b09-189">Add text to the <xref:System.ServiceProcess.ServiceInstaller.Description%2A> property, such as *A sample service*.</span></span>

     <span data-ttu-id="56b09-190">Esse texto é exibido na coluna **Descrição** da janela **Serviços** e descreve o serviço para o usuário.</span><span class="sxs-lookup"><span data-stu-id="56b09-190">This text appears in the **Description** column of the **Services** window and describes the service to the user.</span></span>

    <span data-ttu-id="56b09-191">![Descrição do serviço na janela Serviços.](./media/windows-service-description.png "Descrição do serviço")</span><span class="sxs-lookup"><span data-stu-id="56b09-191">![Service description in the Services window.](./media/windows-service-description.png "Service description")</span></span>

6. <span data-ttu-id="56b09-192">Adicione o texto à propriedade <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A>.</span><span class="sxs-lookup"><span data-stu-id="56b09-192">Add text to the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property.</span></span> <span data-ttu-id="56b09-193">Por exemplo, *Nome de Exibição do MyNewService*.</span><span class="sxs-lookup"><span data-stu-id="56b09-193">For example, *MyNewService Display Name*.</span></span>

     <span data-ttu-id="56b09-194">Esse texto é exibido na coluna **Nome de Exibição** da janela **Serviços**.</span><span class="sxs-lookup"><span data-stu-id="56b09-194">This text appears in the **Display Name** column of the **Services** window.</span></span> <span data-ttu-id="56b09-195">Esse nome pode ser diferente da propriedade <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>, que é o nome usado pelo sistema (por exemplo, o nome usado para o comando `net start` para iniciar o serviço).</span><span class="sxs-lookup"><span data-stu-id="56b09-195">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name the system uses (for example, the name you use for the `net start` command to start your service).</span></span>

7. <span data-ttu-id="56b09-196">Defina a propriedade <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> como <xref:System.ServiceProcess.ServiceStartMode.Automatic> na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="56b09-196">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic> from the drop-down list.</span></span>

8. <span data-ttu-id="56b09-197">Quando terminar, as janelas **Propriedades** deverão ser semelhantes à seguinte figura:</span><span class="sxs-lookup"><span data-stu-id="56b09-197">When you're finished, the **Properties** windows should look like the following figure:</span></span>

     <span data-ttu-id="56b09-198">![Propriedades do instalador para um serviço Windows](./media/windows-service-installer-properties.png "Windows service installer properties")</span><span class="sxs-lookup"><span data-stu-id="56b09-198">![Installer Properties for a Windows service](./media/windows-service-installer-properties.png "Windows service installer properties")</span></span>

9. <span data-ttu-id="56b09-199">Na exibição **Design** de **ProjectInstaller**, escolha **serviceProcessInstaller1** para um projeto do Visual C# ou **ServiceProcessInstaller1** para um projeto do Visual Basic e, em seguida, escolha **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="56b09-199">In the **Design** view for **ProjectInstaller**, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="56b09-200">Defina a propriedade <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> como <xref:System.ServiceProcess.ServiceAccount.LocalSystem> na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="56b09-200">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem> from the drop-down list.</span></span>

     <span data-ttu-id="56b09-201">Essa configuração instala o serviço e o executa usando a conta Sistema Local.</span><span class="sxs-lookup"><span data-stu-id="56b09-201">This setting installs the service and runs it by using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="56b09-202">A conta <xref:System.ServiceProcess.ServiceAccount.LocalSystem> tem amplas permissões, incluindo a capacidade de gravar no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="56b09-202">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="56b09-203">Use essa conta com cuidado, pois ela pode aumentar o risco de ataques de software mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="56b09-203">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="56b09-204">Para outras tarefas, pense em usar a conta <xref:System.ServiceProcess.ServiceAccount.LocalService>, que atua como um usuário não privilegiado no computador local e apresenta credenciais anônimas a qualquer servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="56b09-204">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="56b09-205">Este exemplo falhará se você tentar usar a conta <xref:System.ServiceProcess.ServiceAccount.LocalService>, pois ele precisa de permissão para gravar no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="56b09-205">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="56b09-206">Para saber mais sobre os instaladores, consulte [Como Adicionar instaladores ao aplicativo de serviço](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="56b09-206">For more information about installers, see [How to: Add installers to your service application](how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="56b09-207">(Opcional) Defina os parâmetros de inicialização</span><span class="sxs-lookup"><span data-stu-id="56b09-207">(Optional) Set startup parameters</span></span>

> [!NOTE]
> <span data-ttu-id="56b09-208">Antes de decidir adicionar parâmetros de inicialização, considere se esta é a melhor maneira de passar informações para o serviço.</span><span class="sxs-lookup"><span data-stu-id="56b09-208">Before you decide to add startup parameters, consider whether it's the best way to pass information to your service.</span></span> <span data-ttu-id="56b09-209">Embora elas sejam fáceis de serem usadas e analisadas e um usuário possa substituí-las com facilidade, elas podem ser mais difíceis para um usuário descobrir e usá-las sem a documentação.</span><span class="sxs-lookup"><span data-stu-id="56b09-209">Although they're easy to use and parse, and a user can easily override them, they might be harder for a user to discover and use without documentation.</span></span> <span data-ttu-id="56b09-210">Em geral, se o serviço exigir mais do que apenas alguns parâmetros de inicialização, você deverá usar o Registro ou um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="56b09-210">Generally, if your service requires more than just a few startup parameters, you should use the registry or a configuration file instead.</span></span>

<span data-ttu-id="56b09-211">Um serviço Windows pode aceitar argumentos de linha de comando ou parâmetros de inicialização.</span><span class="sxs-lookup"><span data-stu-id="56b09-211">A Windows service can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="56b09-212">Quando você adiciona um código aos parâmetros de inicialização do processo, um usuário pode iniciar o serviço com seus próprios parâmetros de inicialização personalizados na janela Propriedades do serviço.</span><span class="sxs-lookup"><span data-stu-id="56b09-212">When you add code to process startup parameters, a user can start your service with their own custom startup parameters in the service properties window.</span></span> <span data-ttu-id="56b09-213">No entanto, esses parâmetros de inicialização não são persistentes na próxima vez que o serviço é iniciado.</span><span class="sxs-lookup"><span data-stu-id="56b09-213">However, these startup parameters aren't persisted the next time the service starts.</span></span> <span data-ttu-id="56b09-214">Para definir parâmetros de inicialização permanentemente, defina-os no Registro.</span><span class="sxs-lookup"><span data-stu-id="56b09-214">To set startup parameters permanently, set them in the registry.</span></span>

<span data-ttu-id="56b09-215">Cada serviço Windows tem uma entrada do Registro na subchave **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services**.</span><span class="sxs-lookup"><span data-stu-id="56b09-215">Each Windows service has a registry entry under the **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** subkey.</span></span> <span data-ttu-id="56b09-216">Na subchave de cada serviço, use a subchave **Parâmetros** para armazenar informações que o serviço pode acessar.</span><span class="sxs-lookup"><span data-stu-id="56b09-216">Under each service's subkey, use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="56b09-217">É possível usar arquivos de configuração de aplicativo para um serviço Windows da mesma forma que faz para outros tipos de programas.</span><span class="sxs-lookup"><span data-stu-id="56b09-217">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="56b09-218">Para obter um código de exemplo, confira <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="56b09-218">For sample code, see <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span></span>

### <a name="to-add-startup-parameters"></a><span data-ttu-id="56b09-219">Para adicionar parâmetros de inicialização</span><span class="sxs-lookup"><span data-stu-id="56b09-219">To add startup parameters</span></span>

1. <span data-ttu-id="56b09-220">Selecione **Program.cs** ou **MyNewService.Designer.vb** e, em seguida, escolha **Exibir Código** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="56b09-220">Select **Program.cs**, or **MyNewService.Designer.vb**, then choose **View Code** from the shortcut menu.</span></span> <span data-ttu-id="56b09-221">No método `Main`, altere o código para adicionar um parâmetro de entrada e passá-lo para o construtor do serviço:</span><span class="sxs-lookup"><span data-stu-id="56b09-221">In the `Main` method, change the code to add an input parameter and pass it to the service constructor:</span></span>

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. <span data-ttu-id="56b09-222">Em **MyNewService.cs** ou **MyNewService.vb**, altere o construtor `MyNewService` para processar o parâmetro de entrada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="56b09-222">In **MyNewService.cs**, or **MyNewService.vb**, change the `MyNewService` constructor to process the input parameter as follows:</span></span>

   ```csharp
   using System.Diagnostics;

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

       eventLog1 = new EventLog();

       if (!EventLog.SourceExists(eventSourceName))
       {
           EventLog.CreateEventSource(eventSourceName, logName);
       }

       eventLog1.Source = eventSourceName;
       eventLog1.Log = logName;
   }
   ```

   ```vb
   Imports System.Diagnostics

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
       eventLog1 = New EventLog()
       If (Not EventLog.SourceExists(eventSourceName)) Then
           EventLog.CreateEventSource(eventSourceName, logName)
       End If
       eventLog1.Source = eventSourceName
       eventLog1.Log = logName
   End Sub
   ```

   <span data-ttu-id="56b09-223">Esse código define o nome do log e da origem do evento, de acordo com os parâmetros de inicialização fornecidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="56b09-223">This code sets the event source and log name according to the startup parameters that the user supplies.</span></span> <span data-ttu-id="56b09-224">Se nenhum argumento for fornecido, ele usará valores padrão.</span><span class="sxs-lookup"><span data-stu-id="56b09-224">If no arguments are supplied, it uses default values.</span></span>

3. <span data-ttu-id="56b09-225">Para especificar os argumentos de linha de comando, adicione o seguinte código à classe `ProjectInstaller` em **ProjectInstaller.cs** ou **ProjectInstaller.vb**:</span><span class="sxs-lookup"><span data-stu-id="56b09-225">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in **ProjectInstaller.cs**, or **ProjectInstaller.vb**:</span></span>

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

   <span data-ttu-id="56b09-226">Normalmente, esse valor contém o caminho completo para o executável do serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="56b09-226">Typically, this value contains the full path to the executable for the Windows service.</span></span> <span data-ttu-id="56b09-227">Para que o serviço seja iniciado corretamente, o usuário precisará inserir aspas no caminho e em cada parâmetro individual.</span><span class="sxs-lookup"><span data-stu-id="56b09-227">For the service to start up correctly, the user must supply quotation marks for the path and each individual parameter.</span></span> <span data-ttu-id="56b09-228">Um usuário pode alterar os parâmetros na entrada do Registro **ImagePath** para alterar os parâmetros de inicialização do serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="56b09-228">A user can change the parameters in the **ImagePath** registry entry to change the startup parameters for the Windows service.</span></span> <span data-ttu-id="56b09-229">No entanto, uma maneira melhor é alterar o valor de forma programática e expor a funcionalidade de forma amigável, como por meio de um utilitário de configuração ou gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="56b09-229">However, a better way is to change the value programmatically and expose the functionality in a user-friendly way, such as by using a management or configuration utility.</span></span>

## <a name="build-the-service"></a><span data-ttu-id="56b09-230">Compilar o serviço</span><span class="sxs-lookup"><span data-stu-id="56b09-230">Build the service</span></span>

1. <span data-ttu-id="56b09-231">No **Gerenciador de Soluções**, escolha **Propriedades** no menu de atalho do projeto **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="56b09-231">In **Solution Explorer**, choose **Properties** from the shortcut menu for the **MyNewService** project.</span></span>

   <span data-ttu-id="56b09-232">As páginas de propriedades do seu projeto aparecem.</span><span class="sxs-lookup"><span data-stu-id="56b09-232">The property pages for your project appear.</span></span>

2. <span data-ttu-id="56b09-233">Na guia **Aplicativo**, na lista **Objeto de inicialização**, escolha **MyNewService.Program** ou **Sub Main** para projetos do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="56b09-233">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**, or **Sub Main** for Visual Basic projects.</span></span>

3. <span data-ttu-id="56b09-234">Para compilar o projeto, no **Gerenciador de Soluções**, escolha **Compilar** no menu de atalho do projeto (ou pressione **Ctrl**+**Shift**+**B**).</span><span class="sxs-lookup"><span data-stu-id="56b09-234">To build the project, in **Solution Explorer**, choose **Build** from the shortcut menu for your project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="56b09-235">Instalar o serviço</span><span class="sxs-lookup"><span data-stu-id="56b09-235">Install the service</span></span>

<span data-ttu-id="56b09-236">Agora que você criou o serviço Windows, poderá instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="56b09-236">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="56b09-237">Para instalar um serviço Windows, é necessário ter credenciais de administrador no computador no qual ele é instalado.</span><span class="sxs-lookup"><span data-stu-id="56b09-237">To install a Windows service, you must have administrator credentials on the computer where it's installed.</span></span>

1. <span data-ttu-id="56b09-238">Abra o [Prompt de Comando do Desenvolvedor para Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) com credenciais administrativas.</span><span class="sxs-lookup"><span data-stu-id="56b09-238">Open [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) with administrative credentials.</span></span> <span data-ttu-id="56b09-239">No menu **Iniciar** do Windows, selecione **Prompt de Comando do Desenvolvedor para VS 2017** na pasta Visual Studio e, em seguida, selecione **Mais** > **Executar como Administrador** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="56b09-239">From the Windows **Start** menu, select **Developer Command Prompt for VS 2017** in the Visual Studio folder, then select **More** > **Run as Administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="56b09-240">Na janela **Prompt de Comando do Desenvolvedor para Visual Studio**, navegue para a pasta que contém a saída do projeto (por padrão, o subdiretório *\bin\Debug* do projeto).</span><span class="sxs-lookup"><span data-stu-id="56b09-240">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output (by default, the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="56b09-241">Insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="56b09-241">Enter the following command:</span></span>

    ```shell
    installutil MyNewService.exe
    ```

    <span data-ttu-id="56b09-242">Se o serviço for instalado com êxito, o comando relatará o êxito.</span><span class="sxs-lookup"><span data-stu-id="56b09-242">If the service installs successfully, the command reports success.</span></span>

    <span data-ttu-id="56b09-243">Se o sistema não puder localizar *installutil.exe*, verifique se ele existe no computador.</span><span class="sxs-lookup"><span data-stu-id="56b09-243">If the system can't find *installutil.exe*, make sure that it exists on your computer.</span></span> <span data-ttu-id="56b09-244">Essa ferramenta é instalada com o .NET Framework na pasta *%windir%\Microsoft.NET\Framework[64]\\&lt;versão do Framework&gt;* .</span><span class="sxs-lookup"><span data-stu-id="56b09-244">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\&lt;framework version&gt;*.</span></span> <span data-ttu-id="56b09-245">Por exemplo, o caminho padrão da versão de 64 bits é *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="56b09-245">For example, the default path for the 64-bit version is *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="56b09-246">Se o processo **installutil.exe** falhar, verifique o log de instalação para saber o motivo.</span><span class="sxs-lookup"><span data-stu-id="56b09-246">If the **installutil.exe** process fails, check the install log to find out why.</span></span> <span data-ttu-id="56b09-247">Por padrão, o log está localizado na mesma pasta do executável do serviço.</span><span class="sxs-lookup"><span data-stu-id="56b09-247">By default, the log is in the same folder as the service executable.</span></span> <span data-ttu-id="56b09-248">A instalação poderá falhar se:</span><span class="sxs-lookup"><span data-stu-id="56b09-248">The installation can fail if:</span></span>
    - <span data-ttu-id="56b09-249">A classe <xref:System.ComponentModel.RunInstallerAttribute> não estiver presente na classe `ProjectInstaller`.</span><span class="sxs-lookup"><span data-stu-id="56b09-249">The <xref:System.ComponentModel.RunInstallerAttribute> class isn't present on the `ProjectInstaller` class.</span></span>
    - <span data-ttu-id="56b09-250">O atributo não estiver definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="56b09-250">The attribute isn't set to `true`.</span></span>
    - <span data-ttu-id="56b09-251">A classe `ProjectInstaller` não estiver definida como `public`.</span><span class="sxs-lookup"><span data-stu-id="56b09-251">The `ProjectInstaller` class isn't defined as `public`.</span></span>

<span data-ttu-id="56b09-252">Para obter mais informações, confira [Como: Instalar e desinstalar serviços](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="56b09-252">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="56b09-253">Iniciar e executar o serviço</span><span class="sxs-lookup"><span data-stu-id="56b09-253">Start and run the service</span></span>

1. <span data-ttu-id="56b09-254">No Windows, abra o aplicativo da área de trabalho **Serviços**.</span><span class="sxs-lookup"><span data-stu-id="56b09-254">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="56b09-255">Pressione **Windows**+**R** para abrir a caixa **Executar**, insira *services.msc* e, em seguida, pressione **Enter** ou selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="56b09-255">Press **Windows**+**R** to open the **Run** box, enter *services.msc*, and then press **Enter** or select **OK**.</span></span>

     <span data-ttu-id="56b09-256">Você deve ver o serviço listado em **Serviços**, exibido em ordem alfabética pelo nome de exibição definido para ele.</span><span class="sxs-lookup"><span data-stu-id="56b09-256">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![MyNewService na janela Serviços.](./media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="56b09-258">Para iniciar o serviço, escolha **Iniciar** no menu de atalho do serviço.</span><span class="sxs-lookup"><span data-stu-id="56b09-258">To start the service, choose **Start** from the service's shortcut menu.</span></span>

3. <span data-ttu-id="56b09-259">Para interromper o serviço, escolha **Parar** no menu de atalho do serviço.</span><span class="sxs-lookup"><span data-stu-id="56b09-259">To stop the service, choose **Stop** from the service's shortcut menu.</span></span>

4. <span data-ttu-id="56b09-260">(Opcional) Na linha de comando, use os comandos **net start &lt;nome do serviço&gt;** e **net stop &lt;nome do serviço&gt;** para iniciar e parar o serviço.</span><span class="sxs-lookup"><span data-stu-id="56b09-260">(Optional) From the command line, use the commands **net start &lt;service name&gt;** and **net stop &lt;service name&gt;** to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="56b09-261">Verificar a saída do log de eventos do seu serviço</span><span class="sxs-lookup"><span data-stu-id="56b09-261">Verify the event log output of your service</span></span>

1. <span data-ttu-id="56b09-262">No Windows, abra o aplicativo da área de trabalho **Visualizador de Eventos**.</span><span class="sxs-lookup"><span data-stu-id="56b09-262">In Windows, open the **Event Viewer** desktop app.</span></span> <span data-ttu-id="56b09-263">Insira *Visualizador de Eventos* na barra de pesquisa do Windows e, em seguida, selecione **Visualizador de Eventos** nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="56b09-263">Enter *Event Viewer* in the Windows search bar, and then select **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="56b09-264">No Visual Studio, é possível acessar logs de eventos abrindo **Gerenciador de Servidores** do menu **Exibir** (ou pressione **Ctrl**+**Alt**+**S**) e expandindo o nó **Logs de Eventos** no computador local.</span><span class="sxs-lookup"><span data-stu-id="56b09-264">In Visual Studio, you can access event logs by opening **Server Explorer** from the **View** menu (or press **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="56b09-265">No **Visualizador de Eventos**, expanda **Logs de Aplicativos e Serviços**.</span><span class="sxs-lookup"><span data-stu-id="56b09-265">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="56b09-266">Localize a listagem de **MyNewLog** (ou **MyLogFile1**, se você seguiu o procedimento para adicionar argumentos de linha de comando) e expanda-a.</span><span class="sxs-lookup"><span data-stu-id="56b09-266">Locate the listing for **MyNewLog** (or **MyLogFile1** if you followed the procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="56b09-267">Você deverá ver as entradas para as duas ações (iniciar e parar) executadas pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="56b09-267">You should see the entries for the two actions (start and stop) that your service performed.</span></span>

     ![Use o Visualizador de Eventos para ver as entradas do log de eventos](./media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a><span data-ttu-id="56b09-269">Limpar recursos</span><span class="sxs-lookup"><span data-stu-id="56b09-269">Clean up resources</span></span>

<span data-ttu-id="56b09-270">Caso não precise mais do aplicativo serviço Windows, remova-o.</span><span class="sxs-lookup"><span data-stu-id="56b09-270">If you no longer need the Windows service app, you can remove it.</span></span>

1. <span data-ttu-id="56b09-271">Abra o **Prompt de Comando do Desenvolvedor para Visual Studio** com credenciais administrativas.</span><span class="sxs-lookup"><span data-stu-id="56b09-271">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="56b09-272">Na janela **Prompt de Comando do Desenvolvedor para Visual Studio**, navegue para a pasta que contém a saída do projeto.</span><span class="sxs-lookup"><span data-stu-id="56b09-272">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="56b09-273">Insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="56b09-273">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="56b09-274">Se o serviço for desinstalado com êxito, o comando relatará que o serviço foi removido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="56b09-274">If the service uninstalls successfully, the command reports that your service was successfully removed.</span></span> <span data-ttu-id="56b09-275">Para obter mais informações, confira [Como: Instalar e desinstalar serviços](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="56b09-275">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="56b09-276">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="56b09-276">Next steps</span></span>

<span data-ttu-id="56b09-277">Agora que você criou o serviço, você poderá:</span><span class="sxs-lookup"><span data-stu-id="56b09-277">Now that you've created the service, you can:</span></span>

- <span data-ttu-id="56b09-278">Criar um programa de instalação autônoma para que outros possam usá-lo para instalar o serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="56b09-278">Create a standalone setup program for others to use to install your Windows service.</span></span> <span data-ttu-id="56b09-279">Usar o [Conjunto de ferramentas do WiX](https://wixtoolset.org/) para criar um instalador para um serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="56b09-279">Use the [WiX Toolset](https://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="56b09-280">Para ver outras ideias, confira [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop) (Criar um pacote do instalador).</span><span class="sxs-lookup"><span data-stu-id="56b09-280">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

- <span data-ttu-id="56b09-281">Explorar o componente <xref:System.ServiceProcess.ServiceController>, que permite enviar comandos ao serviço instalado.</span><span class="sxs-lookup"><span data-stu-id="56b09-281">Explore the <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

- <span data-ttu-id="56b09-282">Em vez de criar o log de eventos quando o aplicativo é executado, use um instalador para criar um log de eventos ao instalar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="56b09-282">Instead of creating the event log when the application runs, use an installer to create an event log when you install the application.</span></span> <span data-ttu-id="56b09-283">O log de eventos é excluído pelo instalador quando você desinstala o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="56b09-283">The event log is deleted by the installer when you uninstall the application.</span></span> <span data-ttu-id="56b09-284">Para obter mais informações, consulte <xref:System.Diagnostics.EventLogInstaller>.</span><span class="sxs-lookup"><span data-stu-id="56b09-284">For more information, see <xref:System.Diagnostics.EventLogInstaller>.</span></span>

## <a name="see-also"></a><span data-ttu-id="56b09-285">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56b09-285">See also</span></span>

- [<span data-ttu-id="56b09-286">Aplicativos do serviço Windows</span><span class="sxs-lookup"><span data-stu-id="56b09-286">Windows service applications</span></span>](index.md)
- [<span data-ttu-id="56b09-287">Introdução aos aplicativos do serviço Windows</span><span class="sxs-lookup"><span data-stu-id="56b09-287">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="56b09-288">Como: Depurar aplicativos do serviço Windows</span><span class="sxs-lookup"><span data-stu-id="56b09-288">How to: Debug Windows service applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="56b09-289">Serviços (Windows)</span><span class="sxs-lookup"><span data-stu-id="56b09-289">Services (Windows)</span></span>](/windows/desktop/Services/services)
