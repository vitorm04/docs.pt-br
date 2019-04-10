---
title: 'Como: criar um participante de acompanhamento personalizado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 64320a8f4799e79f54348e5381ed2d8ed49d496b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338170"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="b54bf-102">Como: criar um participante de acompanhamento personalizado</span><span class="sxs-lookup"><span data-stu-id="b54bf-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="b54bf-103">O rastreamento de fluxo de trabalho fornece a visibilidade ao status da execução do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b54bf-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="b54bf-104">O tempo de execução do fluxo de trabalho emite os registros de rastreamento que descrevem os eventos de ciclo de vida do fluxo de trabalho, os eventos de ciclo de vida da atividade, os reinícios do indicador e as falhas.</span><span class="sxs-lookup"><span data-stu-id="b54bf-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="b54bf-105">Esses registros de rastreamento são consumidos pelos participantes.</span><span class="sxs-lookup"><span data-stu-id="b54bf-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="b54bf-106">Windows Workflow Foundation (WF) inclui um participante de rastreamento padrão que grava registros de rastreamento como eventos do Event Tracing for Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="b54bf-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="b54bf-107">Se isso não atender aos requisitos, você também poderá escrever um participante de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="b54bf-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="b54bf-108">Esta etapa do tutorial descreve como criar um participante de rastreamento personalizado e um perfil de rastreamento que captura a saída das atividades `WriteLine` de forma que elas possam ser exibidas para o usuário.</span><span class="sxs-lookup"><span data-stu-id="b54bf-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b54bf-109">Cada tópico do tutorial de Introdução depende dos tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="b54bf-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="b54bf-110">Para concluir este tópico, primeiro você deve concluir os tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="b54bf-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="b54bf-111">Para baixar uma versão completa ou exibir uma vídeo passo a passo do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="b54bf-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="b54bf-112">Para criar o participante de rastreamento personalizado</span><span class="sxs-lookup"><span data-stu-id="b54bf-112">To create the custom tracking participant</span></span>  
  
1. <span data-ttu-id="b54bf-113">Clique com botão direito **NumberGuessWorkflowHost** na **Gerenciador de soluções** e escolha **Add**, **classe**.</span><span class="sxs-lookup"><span data-stu-id="b54bf-113">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="b54bf-114">Tipo de `StatusTrackingParticipant` para o **nome** caixa e, em seguida, clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="b54bf-114">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2. <span data-ttu-id="b54bf-115">Adicione as seguintes instruções `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="b54bf-115">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="b54bf-116">Modifique a classe `StatusTrackingParticipant` de forma que ela herde de `TrackingParticipant`.</span><span class="sxs-lookup"><span data-stu-id="b54bf-116">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4. <span data-ttu-id="b54bf-117">Adicione a substituição do método de `Track` a seguir.</span><span class="sxs-lookup"><span data-stu-id="b54bf-117">Add the following `Track` method override.</span></span> <span data-ttu-id="b54bf-118">Há vários tipos diferentes de registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b54bf-118">There are several different types of tracking records.</span></span> <span data-ttu-id="b54bf-119">Estamos interessados na saída das atividades de `WriteLine`, que estão contidas nos registros de rastreamento da atividade.</span><span class="sxs-lookup"><span data-stu-id="b54bf-119">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="b54bf-120">Se o `TrackingRecord` for um `ActivityTrackingRecord` para uma atividade `WriteLine`, o `Text` de `WriteLine` será acrescentado a um arquivo com o nome da `InstanceId` do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b54bf-120">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="b54bf-121">Neste tutorial, o arquivo é salvo na pasta atual do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="b54bf-121">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="b54bf-122">Quando nenhum perfil de rastreamento for especificado, o perfil padrão de rastreamento será usado.</span><span class="sxs-lookup"><span data-stu-id="b54bf-122">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="b54bf-123">Quando o perfil padrão do rastreamento for usado, os registros de rastreamento serão emitidos para todos os `ActivityStates`.</span><span class="sxs-lookup"><span data-stu-id="b54bf-123">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="b54bf-124">Como somente precisamos capturar o texto uma vez durante o ciclo de vida da atividade `WriteLine`, somente extraímos o texto do estado `ActivityStates.Executing`.</span><span class="sxs-lookup"><span data-stu-id="b54bf-124">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="b54bf-125">Na [para criar o perfil de rastreamento e registrar o participante de rastreamento](#to-create-the-tracking-profile-and-register-the-tracking-participant), um perfil de rastreamento é criado que especifica que somente `WriteLine` `ActivityStates.Executing` registros de rastreamento são emitidas.</span><span class="sxs-lookup"><span data-stu-id="b54bf-125">In [To create the tracking profile and register the tracking participant](#to-create-the-tracking-profile-and-register-the-tracking-participant), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="b54bf-126">Para criar o perfil de rastreamento e registrar o participante do rastreamento</span><span class="sxs-lookup"><span data-stu-id="b54bf-126">To create the tracking profile and register the tracking participant</span></span>  
  
1. <span data-ttu-id="b54bf-127">Clique com botão direito **WorkflowHostForm** na **Gerenciador de soluções** e escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="b54bf-127">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="b54bf-128">Adicione a seguinte instrução `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="b54bf-128">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. <span data-ttu-id="b54bf-129">Adicione o seguinte código ao `ConfigureWorkflowApplication` depois do código que adiciona o `StringWriter` às extensões de fluxo de trabalho e antes dos manipuladores de ciclo de vida de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b54bf-129">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =   
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     <span data-ttu-id="b54bf-130">Este perfil de rastreamento especifica que somente os registros de estado de atividade para atividades `WriteLine` no estado `Executing` são emitidos para o participante de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="b54bf-130">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="b54bf-131">Depois de adicionar o código, o início de `ConfigureWorkflowApplication` se parecerá com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b54bf-131">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =   
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="b54bf-132">Para exibir as informações de rastreamento</span><span class="sxs-lookup"><span data-stu-id="b54bf-132">To display the tracking information</span></span>  
  
1. <span data-ttu-id="b54bf-133">Clique com botão direito **WorkflowHostForm** na **Gerenciador de soluções** e escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="b54bf-133">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="b54bf-134">No manipulador `InstanceId_SelectedIndexChanged`, adicione o seguinte código imediatamente depois do código que limpa a janela de status.</span><span class="sxs-lookup"><span data-stu-id="b54bf-134">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     <span data-ttu-id="b54bf-135">Quando um novo fluxo de trabalho é selecionado na lista de fluxo de trabalho, os registros de rastreamento para esse fluxo de trabalho são carregados e exibidos na janela de status.</span><span class="sxs-lookup"><span data-stu-id="b54bf-135">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="b54bf-136">O exemplo a seguir é o manipulador `InstanceId_SelectedIndexChanged` concluído.</span><span class="sxs-lookup"><span data-stu-id="b54bf-136">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
        'Get the workflow version and display it.  
        'If the workflow is just starting then this info will not  
        'be available in the persistence store so do not try and retrieve it.  
        If Not WorkflowStarting Then  
            Dim instance As WorkflowApplicationInstance = _  
                WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
            WorkflowVersion.Text = _  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
            'Unload the instance.  
            instance.Abandon()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
        // Get the workflow version and display it.  
        // If the workflow is just starting then this info will not  
        // be available in the persistence store so do not try and retrieve it.  
        if (!WorkflowStarting)  
        {  
            WorkflowApplicationInstance instance =  
                WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
            WorkflowVersion.Text =  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
            // Unload the instance.  
            instance.Abandon();  
        }  
    }  
    ```  
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="b54bf-137">Para compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="b54bf-137">To build and run the application</span></span>  
  
1. <span data-ttu-id="b54bf-138">Pressione Ctrl+Shift+B para criar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b54bf-138">Press Ctrl+Shift+B to build the application.</span></span>  
  
2. <span data-ttu-id="b54bf-139">Pressione Ctrl+F5 para iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b54bf-139">Press Ctrl+F5 to start the application.</span></span>  
  
3. <span data-ttu-id="b54bf-140">Selecionar um intervalo para o jogo de estimativa e o tipo de fluxo de trabalho para iniciar e, em seguida, clique em **novo jogo**.</span><span class="sxs-lookup"><span data-stu-id="b54bf-140">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="b54bf-141">Insira um Palpite na **Palpite** caixa e clique em **vá** para enviar seu palpite.</span><span class="sxs-lookup"><span data-stu-id="b54bf-141">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="b54bf-142">Observe que o status do fluxo de trabalho é exibido na janela de status.</span><span class="sxs-lookup"><span data-stu-id="b54bf-142">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="b54bf-143">Essa saída é capturada das atividades `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="b54bf-143">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="b54bf-144">Alternar para um fluxo de trabalho diferente selecionando um dos **Id da instância de fluxo de trabalho** caixa de combinação e observe que o status do fluxo de trabalho atual é removido.</span><span class="sxs-lookup"><span data-stu-id="b54bf-144">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="b54bf-145">Alterne novamente para o fluxo de trabalho e observe que o status é restaurado, semelhante ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b54bf-145">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b54bf-146">Se você alternar para um fluxo de trabalho que foi iniciado antes que o rastreamento foi habilitado, nenhum status será exibido.</span><span class="sxs-lookup"><span data-stu-id="b54bf-146">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="b54bf-147">No entanto, se você fizer previsões adicionais, seu status será salvo porque o rastreamento agora estará habilitado.</span><span class="sxs-lookup"><span data-stu-id="b54bf-147">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > <span data-ttu-id="b54bf-148">Essas informações são úteis para determinar o intervalo do número aleatório, mas ele não contém informações sobre os palpites que já foram feitos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b54bf-148">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="b54bf-149">Essas informações estão na próxima etapa, [como: Hospedar várias versões de uma fluxo de trabalho lado a lado](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="b54bf-149">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="b54bf-150">Faça uma anotação da ID de instância de fluxo de trabalho e jogue até o final.</span><span class="sxs-lookup"><span data-stu-id="b54bf-150">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4. <span data-ttu-id="b54bf-151">Abra o Windows Explorer e navegue até a **NumberGuessWorkflowHost\bin\debug** pasta (ou **bin\release** dependendo de suas configurações de projeto).</span><span class="sxs-lookup"><span data-stu-id="b54bf-151">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="b54bf-152">Observe que, além dos arquivos executáveis de projeto, há arquivos com nomes de arquivo de GUID.</span><span class="sxs-lookup"><span data-stu-id="b54bf-152">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="b54bf-153">Identifique o que corresponde à ID da instância do fluxo de trabalho concluído na etapa anterior e abra-o no Bloco De Notas.</span><span class="sxs-lookup"><span data-stu-id="b54bf-153">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="b54bf-154">As informações de rastreamento contêm informações semelhantes ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="b54bf-154">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="b54bf-155">Além da ausência de palpites do usuário, esses dados de rastreamento não contêm informações sobre o palpite final do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b54bf-155">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="b54bf-156">Isso ocorre porque as informações de rastreamento consistem apenas na saída de `WriteLine` do fluxo de trabalho, e a mensagem final que é exibida é feita a partir do manipulador `Completed` depois que o fluxo de trabalho é concluído.</span><span class="sxs-lookup"><span data-stu-id="b54bf-156">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="b54bf-157">Na próxima etapa do tutorial, [como: Hospedar várias versões de uma fluxo de trabalho lado a lado](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), existente `WriteLine` atividades são alteradas para exibir as previsões do usuário e uma outra `WriteLine` atividade é adicionada que exibe os resultados finais.</span><span class="sxs-lookup"><span data-stu-id="b54bf-157">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="b54bf-158">Depois que essas alterações são integradas, [como: Hospedar várias versões de uma fluxo de trabalho lado a lado](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstra como hospedar várias versões de um fluxo de trabalho ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="b54bf-158">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
