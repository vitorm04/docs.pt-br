---
title: Configurando o rastreamento para um fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: c3e73c3801a41a9401ac2e636fda6362487a05af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052762"
---
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="c308a-102">Configurando o rastreamento para um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c308a-102">Configuring Tracking for a Workflow</span></span>

<span data-ttu-id="c308a-103">Um fluxo de trabalho pode executar em três maneiras:</span><span class="sxs-lookup"><span data-stu-id="c308a-103">A workflow can execute in three ways:</span></span>

- <span data-ttu-id="c308a-104">Hospedado em <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="c308a-104">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>

- <span data-ttu-id="c308a-105">Executado como <xref:System.Activities.WorkflowApplication></span><span class="sxs-lookup"><span data-stu-id="c308a-105">Executed as a <xref:System.Activities.WorkflowApplication></span></span>

- <span data-ttu-id="c308a-106">Executado diretamente usando <xref:System.Activities.WorkflowInvoker></span><span class="sxs-lookup"><span data-stu-id="c308a-106">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>

<span data-ttu-id="c308a-107">Dependendo do fluxo de trabalho que hospeda a opção, um participante de rastreamento pode ser adicionado ao código ou em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c308a-107">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="c308a-108">Este tópico descreve como controlando é configurado adicionando um participante de rastreamento a <xref:System.Activities.WorkflowApplication> e a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, e como ativar o rastreamento para usar <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="c308a-108">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>

## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="c308a-109">Configurando o rastreamento de aplicativo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c308a-109">Configuring Workflow Application Tracking</span></span>

<span data-ttu-id="c308a-110">Um fluxo de trabalho pode executar usando a classe de <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="c308a-110">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="c308a-111">Este tópico demonstra como controlando é configurado para um aplicativo de fluxo de trabalho [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] adicionando um participante de rastreamento para o host do fluxo de trabalho <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="c308a-111">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="c308a-112">Nesse caso, o fluxo de trabalho é executado como um aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c308a-112">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="c308a-113">Você configura um aplicativo de fluxo de trabalho com o código (em vez de usar um arquivo de configuração), que é um arquivo .exe são hospedado usando a classe de <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="c308a-113">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="c308a-114">O participante de rastreamento é adicionado como uma extensão para instância de <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="c308a-114">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="c308a-115">Isso é feito adicionando <xref:System.Activities.Tracking.TrackingParticipant> a coleção de extensões para a instância de WorkflowApplication.</span><span class="sxs-lookup"><span data-stu-id="c308a-115">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>

<span data-ttu-id="c308a-116">Para um aplicativo de fluxo de trabalho, você pode adicionar a extensão do comportamento de <xref:System.Activities.Tracking.EtwTrackingParticipant> conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c308a-116">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>

```csharp
LogActivity activity = new LogActivity();

WorkflowApplication instance = new WorkflowApplication(activity);
EtwTrackingParticipant trackingParticipant =
    new EtwTrackingParticipant
{

        TrackingProfile = new TrackingProfile
           {
               Name = "SampleTrackingProfile",
               ActivityDefinitionId = "ProcessOrder",
               Queries = new WorkflowInstanceQuery
               {
                  States = { "*" }
              }
          }
       };
instance.Extensions.Add(trackingParticipant);
```

### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="c308a-117">Configurando acompanhar de Serviço de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="c308a-117">Configuring Workflow Service Tracking</span></span>

<span data-ttu-id="c308a-118">Um fluxo de trabalho pode ser exposto como um serviço WCF quando hospedados no <xref:System.ServiceModel.Activities.WorkflowServiceHost> host de serviço.</span><span class="sxs-lookup"><span data-stu-id="c308a-118">A workflow can be exposed as a WCF service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="c308a-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> é uma implementação específica do .NET ServiceHost para um serviço fluxo de trabalho- base.</span><span class="sxs-lookup"><span data-stu-id="c308a-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="c308a-120">Esta seção explica como configurar o controle para uma execução de serviço do fluxo de trabalho [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] em <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c308a-120">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="c308a-121">É configurada por um arquivo web.config (para um serviço web hospedado) ou um arquivo App.config (para um serviço hospedado em um aplicativo autônomo, como um aplicativo de console) especificando um comportamento do serviço ou com o código adicionando um comportamento acompanhamento- específico à coleção de <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> para o host serviço.</span><span class="sxs-lookup"><span data-stu-id="c308a-121">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>

<span data-ttu-id="c308a-122">Para um serviço de fluxo de trabalho hospedados no <xref:System.ServiceModel.WorkflowServiceHost>, você pode adicionar a <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o <`behavior`> elemento em um arquivo de configuração, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c308a-122">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
<behaviors>
```

<span data-ttu-id="c308a-123">Como alternativa, para um serviço de fluxo de trabalho hospedado em <xref:System.ServiceModel.WorkflowServiceHost>, você pode adicionar a extensão do comportamento de <xref:System.Activities.Tracking.EtwTrackingParticipant> com o código.</span><span class="sxs-lookup"><span data-stu-id="c308a-123">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="c308a-124">Para adicionar um participante personalizado de rastreamento, criar uma nova extensão do comportamento e adicioná-lo a <xref:System.ServiceModel.ServiceHost> conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c308a-124">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>

> [!NOTE]
> <span data-ttu-id="c308a-125">Se você deseja exibir o código de exemplo que mostra como criar um elemento de comportamento personalizado que adiciona um participante personalizado, consulte a [acompanhamento](./samples/tracking.md) exemplos.</span><span class="sxs-lookup"><span data-stu-id="c308a-125">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](./samples/tracking.md) samples.</span></span>

```csharp
ServiceHost svcHost = new ServiceHost(typeof(WorkflowService), new
                                 Uri("http://localhost:8001/Sample"));
EtwTrackingBehavior trackingBehavior =
    new EtwTrackingBehavior
    {
        ProfileName = "Sample Tracking Profile"
    };
svcHost.Description.Behaviors.Add(trackingBehavior);
svcHost.Open();
```

<span data-ttu-id="c308a-126">O participante de rastreamento é adicionado ao host serviço de fluxo de trabalho como uma extensão para o comportamento.</span><span class="sxs-lookup"><span data-stu-id="c308a-126">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>

<span data-ttu-id="c308a-127">Este exemplo de código abaixo mostra como ler um perfil de rastreamento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c308a-127">This sample code below shows how to read a tracking profile from configuration file.</span></span>

```csharp
TrackingProfile GetProfile(string profileName, string displayName)
        {
            TrackingProfile trackingProfile = null;
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");
            if (trackingSection == null)
            {
                return null;
            }

            if (profileName == null)
            {
                profileName = "";
            }

            //Find the profile with the specified profile name in the list of profile found in config
            var match = from p in new List<TrackingProfile>(trackingSection.TrackingProfiles)
                        where (p.Name == profileName) && ((p.ActivityDefinitionId == displayName) || (p.ActivityDefinitionId == "*"))
                        select p;

            if (match.Count() == 0)
            {
                //return an empty profile
                trackingProfile = new TrackingProfile()
                {
                    ActivityDefinitionId = displayName
                };

            }
            else
            {
                trackingProfile = match.First();
            }

            return trackingProfile;
```

<span data-ttu-id="c308a-128">Este exemplo de código mostra como adicionar um perfil de rastreamento a um host de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c308a-128">This sample code shows how to add a tracking profile to a workflow host.</span></span>

```csharp
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;
if (null != workflowServiceHost)
{
    string workflowDisplayName = workflowServiceHost.Activity.DisplayName;
    TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);
    workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant {
        TrackingProfile = trackingProfile
    });
 }
```

> [!NOTE]
> <span data-ttu-id="c308a-129">Para obter mais informações sobre perfis de rastreamento, consulte [perfis de acompanhamento](https://go.microsoft.com/fwlink/?LinkId=201310).</span><span class="sxs-lookup"><span data-stu-id="c308a-129">For more information on tracking profiles, refer to [Tracking Profiles](https://go.microsoft.com/fwlink/?LinkId=201310).</span></span>

### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="c308a-130">Configurando o rastreamento usando WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="c308a-130">Configuring tracking using WorkflowInvoker</span></span>

<span data-ttu-id="c308a-131">Para configurar o rastreamento para um fluxo de trabalho foi executado usando <xref:System.Activities.WorkflowInvoker>, adicione o provedor de rastreamento como uma extensão para uma instância de <xref:System.Activities.WorkflowInvoker> .</span><span class="sxs-lookup"><span data-stu-id="c308a-131">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="c308a-132">O exemplo de código a seguir é do [acompanhamento personalizado](./samples/custom-tracking.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="c308a-132">The following code example is from the [Custom Tracking](./samples/custom-tracking.md) sample.</span></span>

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="c308a-133">Registros de exibição de rastreamento no visualizador de eventos</span><span class="sxs-lookup"><span data-stu-id="c308a-133">Viewing tracking records in Event Viewer</span></span>

<span data-ttu-id="c308a-134">Há dois logs do visualizador de eventos de interesse específico exibir quando controlando a execução de WF - o log analítico e depuração de log.</span><span class="sxs-lookup"><span data-stu-id="c308a-134">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="c308a-135">Ambos residem em Microsoft&#124;Windows&#124;nó de aplicativos de servidor.</span><span class="sxs-lookup"><span data-stu-id="c308a-135">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span> <span data-ttu-id="c308a-136">Os logs dentro desta seção contêm eventos de um único aplicativo em vez de eventos que têm um impacto no sistema inteiro.</span><span class="sxs-lookup"><span data-stu-id="c308a-136">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>

<span data-ttu-id="c308a-137">Os eventos de rastreamento de depuração são gravados no log de depuração.</span><span class="sxs-lookup"><span data-stu-id="c308a-137">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="c308a-138">Para coletar eventos de rastreamento de depuração de WF no visualizador de eventos, ative o log de depuração.</span><span class="sxs-lookup"><span data-stu-id="c308a-138">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>

1. <span data-ttu-id="c308a-139">Para abrir o Visualizador de eventos, clique em **inicie**e, em seguida, clique em **executar.**</span><span class="sxs-lookup"><span data-stu-id="c308a-139">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="c308a-140">Na caixa de diálogo Executar, digite `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="c308a-140">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="c308a-141">Na caixa de diálogo Visualizador de eventos, expanda o **Applications and Services Logs** nó.</span><span class="sxs-lookup"><span data-stu-id="c308a-141">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="c308a-142">Expanda o **Microsoft**, **Windows**, e **aplicativos de servidor** nós.</span><span class="sxs-lookup"><span data-stu-id="c308a-142">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="c308a-143">Clique com botão direito a **Debug** nó sob o **aplicativos de servidor** nó e selecione **Habilitar Log**.</span><span class="sxs-lookup"><span data-stu-id="c308a-143">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="c308a-144">Execute o aplicativo rastreamento ativado gerar eventos de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c308a-144">Execute your tracing-enabled application to generate tracing events.</span></span>

6. <span data-ttu-id="c308a-145">Clique com botão direito do **Debug** nó e selecione **atualizar.**</span><span class="sxs-lookup"><span data-stu-id="c308a-145">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="c308a-146">Os eventos de rastreamento devem ser no centro painel visível.</span><span class="sxs-lookup"><span data-stu-id="c308a-146">Tracing events should be visible in the center pane.</span></span>

<span data-ttu-id="c308a-147">WF 4 fornece um participante de rastreamento que grava registros de rastreamento a uma sessão de rastreamento (ETW de evento para o Windows).</span><span class="sxs-lookup"><span data-stu-id="c308a-147">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="c308a-148">O participante de rastreamento de ETW é configurado com um perfil de rastreamento para assinar a acompanhar registros.</span><span class="sxs-lookup"><span data-stu-id="c308a-148">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="c308a-149">Quando você estiver ativado, os erros que acompanham registros são emitidas a ETW.</span><span class="sxs-lookup"><span data-stu-id="c308a-149">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="c308a-150">Eventos de controle de (ETW entre o intervalo de 100-113) que correspondem aos eventos de rastreamento emissores por participante de rastreamento de ETW são gravados no log analítico.</span><span class="sxs-lookup"><span data-stu-id="c308a-150">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>

<span data-ttu-id="c308a-151">Para exibir registros de rastreamento, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="c308a-151">To view tracking records, follow these steps.</span></span>

1. <span data-ttu-id="c308a-152">Para abrir o Visualizador de eventos, clique em **inicie**e, em seguida, clique em **executar.**</span><span class="sxs-lookup"><span data-stu-id="c308a-152">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="c308a-153">Na caixa de diálogo Executar, digite `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="c308a-153">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="c308a-154">Na caixa de diálogo Visualizador de eventos, expanda o **Applications and Services Logs** nó.</span><span class="sxs-lookup"><span data-stu-id="c308a-154">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="c308a-155">Expanda o **Microsoft**, **Windows**, e **aplicativos de servidor** nós.</span><span class="sxs-lookup"><span data-stu-id="c308a-155">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="c308a-156">Com o botão direito do **analítico** nó sob o **aplicativos de servidor** nó e selecione **Habilitar Log**.</span><span class="sxs-lookup"><span data-stu-id="c308a-156">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="c308a-157">Executar o aplicativo acompanhamento- ativado gerar registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c308a-157">Execute your tracking-enabled application to generate tracking records.</span></span>

6. <span data-ttu-id="c308a-158">Clique com botão direito do **analítico** nó e selecione **atualizar.**</span><span class="sxs-lookup"><span data-stu-id="c308a-158">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="c308a-159">Controlar registros deve ser no centro painel visível.</span><span class="sxs-lookup"><span data-stu-id="c308a-159">Tracking records should be visible in the center pane.</span></span>

<span data-ttu-id="c308a-160">A imagem a seguir mostra os eventos de rastreamento no Visualizador de eventos:</span><span class="sxs-lookup"><span data-stu-id="c308a-160">The following image shows tracking events in the event viewer:</span></span>

![Captura de tela mostrando o Visualizador de eventos que registros de acompanhamento.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="c308a-162">Registrando um ID específico do aplicativo provedor</span><span class="sxs-lookup"><span data-stu-id="c308a-162">Registering an application-specific provider ID</span></span>

<span data-ttu-id="c308a-163">Se os eventos precisam ser gravados em um log do aplicativo específico, siga estas etapas para registrar o novo manifesto do provedor.</span><span class="sxs-lookup"><span data-stu-id="c308a-163">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>

1. <span data-ttu-id="c308a-164">Declare a identificação do provedor no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c308a-164">Declare the provider ID in the application configuration file.</span></span>

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. <span data-ttu-id="c308a-165">Copiar o arquivo de manifesto de %windir%\Microsoft.NET\Framework\\< a versão mais recente do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man para um local temporário e renomeie-o como Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span><span class="sxs-lookup"><span data-stu-id="c308a-165">Copy the manifest file from %windir%\Microsoft.NET\Framework\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>

3. <span data-ttu-id="c308a-166">Altere o GUID no arquivo de manifesto a nova GUID.</span><span class="sxs-lookup"><span data-stu-id="c308a-166">Change the GUID in the manifest file to the new GUID.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

4. <span data-ttu-id="c308a-167">Altere o nome do provedor se você não desejar desinstalar o provedor padrão.</span><span class="sxs-lookup"><span data-stu-id="c308a-167">Change the provider name if you do not want to uninstall the default provider.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

5. <span data-ttu-id="c308a-168">Se você alterou o nome do provedor na etapa anterior, altere os nomes de canal no arquivo de manifesto para o novo nome do provedor.</span><span class="sxs-lookup"><span data-stu-id="c308a-168">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. <span data-ttu-id="c308a-169">Gerencia o DLL de recurso seguindo estas etapas.</span><span class="sxs-lookup"><span data-stu-id="c308a-169">Generate the resource DLL by following these steps.</span></span>

    1. <span data-ttu-id="c308a-170">Instalar o Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="c308a-170">Install the Windows SDK.</span></span> <span data-ttu-id="c308a-171">O SDK do Windows inclui o compilador de mensagens ([mc.exe](https://go.microsoft.com/fwlink/?LinkId=184606)) e o compilador de recurso ([rc.exe](https://go.microsoft.com/fwlink/?LinkId=184605)).</span><span class="sxs-lookup"><span data-stu-id="c308a-171">The Windows SDK includes the message compiler ([mc.exe](https://go.microsoft.com/fwlink/?LinkId=184606)) and resource compiler ([rc.exe](https://go.microsoft.com/fwlink/?LinkId=184605)).</span></span>

    2. <span data-ttu-id="c308a-172">Em um prompt de comando do Windows SDK, execução mc.exe no novo arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="c308a-172">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. <span data-ttu-id="c308a-173">Executar rc.exe no arquivo de recurso gerado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="c308a-173">Run rc.exe on the resource file generated in the previous step.</span></span>

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. <span data-ttu-id="c308a-174">Crie um arquivo vazio de Cs chamado NewProviderReg.cs.</span><span class="sxs-lookup"><span data-stu-id="c308a-174">Create an empty cs file called NewProviderReg.cs.</span></span>

    5. <span data-ttu-id="c308a-175">Criar uma DLL de recurso usando o compilador C#.</span><span class="sxs-lookup"><span data-stu-id="c308a-175">Create a resource DLL using the C# compiler.</span></span>

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. <span data-ttu-id="c308a-176">Altere o nome da dll de recurso e a mensagem no arquivo de manifesto de `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` para o novo nome de dll.</span><span class="sxs-lookup"><span data-stu-id="c308a-176">Change the resource and message dll name in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">
        ```

    7. <span data-ttu-id="c308a-177">Use [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) para registrar o manifesto.</span><span class="sxs-lookup"><span data-stu-id="c308a-177">Use [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) to register the manifest.</span></span>

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a><span data-ttu-id="c308a-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c308a-178">See also</span></span>

- [<span data-ttu-id="c308a-179">Monitoramento do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="c308a-179">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="c308a-180">Monitoramento de aplicativos com a malha de aplicativos</span><span class="sxs-lookup"><span data-stu-id="c308a-180">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
