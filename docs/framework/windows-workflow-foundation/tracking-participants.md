---
title: Participantes de rastreamento
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: e346e0df3417f6ac83854bd96d6e64dcf103ea93
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488268"
---
# <a name="tracking-participants"></a><span data-ttu-id="1c25a-102">Participantes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="1c25a-102">Tracking Participants</span></span>
<span data-ttu-id="1c25a-103">Os participantes de rastreamento são os pontos de extensibilidade que permitem que um desenvolvedor de fluxo de trabalho acessar objetos de <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> e processe os.</span><span class="sxs-lookup"><span data-stu-id="1c25a-103">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> <span data-ttu-id="1c25a-104">O [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] inclui um participante padrão de rastreamento que grava registros de rastreamento como eventos de Rastreamento de Eventos para Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="1c25a-104">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="1c25a-105">Se isso não atender aos requisitos, você também poderá escrever um participante de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="1c25a-105">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="1c25a-106">Participantes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="1c25a-106">Tracking Participants</span></span>  
 <span data-ttu-id="1c25a-107">A infraestrutura de rastreamento permite que o aplicativo de um filtro os registros de saída de rastreamento para que um participante pode assinar um subconjunto de registros.</span><span class="sxs-lookup"><span data-stu-id="1c25a-107">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="1c25a-108">O mecanismo para aplicar um filtro é com um perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1c25a-108">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 <span data-ttu-id="1c25a-109">Windows Workflow Foundation (WF) no [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] fornece um participante de rastreamento que grava os registros de rastreamento em uma sessão do ETW.</span><span class="sxs-lookup"><span data-stu-id="1c25a-109">Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="1c25a-110">O participante é configurado em um serviço de fluxo de trabalho adicionando um comportamento acompanhamento- específico em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1c25a-110">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="1c25a-111">Ativar um participante de rastreamento de ETW permite controlar os registros a serem exibidos no visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="1c25a-111">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="1c25a-112">O exemplo SDK para o rastreamento ETW- base é uma boa maneira para obter o familiarizado com rastreamento de WF usando o participante controlando ETW- base.</span><span class="sxs-lookup"><span data-stu-id="1c25a-112">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="1c25a-113">Participante de rastreamento de ETW</span><span class="sxs-lookup"><span data-stu-id="1c25a-113">ETW Tracking Participant</span></span>  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="1c25a-114"> inclui um participante de rastreamento de ETW que grava os registros de rastreamento a uma sessão de ETW.</span><span class="sxs-lookup"><span data-stu-id="1c25a-114"> includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="1c25a-115">Isso é feito em uma maneira muito eficiente com um impacto mínimo o desempenho do aplicativo ou à produção de servidor.</span><span class="sxs-lookup"><span data-stu-id="1c25a-115">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="1c25a-116">Uma vantagem de usar o participante de acompanhamento de ETW padrão é que os registros que o controle receba podem ser exibidos com o outro aplicativo e o sistema entra no visualizador de eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="1c25a-116">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="1c25a-117">O participante de rastreamento do padrão ETW é configurado no arquivo web.config conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="1c25a-117">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
   <tracking>  
      <profiles>  
        <trackingProfile name="Sample Tracking Profile">  
        ….  
       </trackingProfile>  
      </profiles>  
    </tracking>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="1c25a-118">Se um nome de `trackingProfile` não for especificado, como apenas `<etwTracking/>` ou `<etwTracking profileName=""/>`, então o perfil padrão de rastreamento instalado com [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] no arquivo Machine.config é usado.</span><span class="sxs-lookup"><span data-stu-id="1c25a-118">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="1c25a-119">No arquivo Machine.config, o perfil padrão de rastreamento assina os registros e a falhas de instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1c25a-119">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="1c25a-120">Em ETW, os eventos são gravados para a sessão de ETW com uma identificação do provedor</span><span class="sxs-lookup"><span data-stu-id="1c25a-120">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="1c25a-121">O provedor que o ID que o participante de rastreamento de ETW usa gravar o rastreamento registra a ETW é definido na seção de diagnóstico do arquivo web.config (em `<system.serviceModel><diagnostics>`).</span><span class="sxs-lookup"><span data-stu-id="1c25a-121">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="1c25a-122">Por padrão, o participante de rastreamento de ETW usa um padrão de identificação do provedor quando se não foi especificado, conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="1c25a-122">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="1c25a-123">A ilustração a seguir mostra o fluxo de dados de rastreamento através de participante de rastreamento de ETW.</span><span class="sxs-lookup"><span data-stu-id="1c25a-123">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="1c25a-124">Uma vez que os dados de acompanhamento alcançam a sessão de ETW, podem ser acessados de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="1c25a-124">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="1c25a-125">Uma das maneiras mais úteis de acessar esses eventos é através do visualizador de eventos, uma ferramenta do Windows comuns usada exibindo efetua logon e rastreamentos de aplicativos e serviços.</span><span class="sxs-lookup"><span data-stu-id="1c25a-125">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 <span data-ttu-id="1c25a-126">![O fluxo de controle e o provedor de rastreamento ETW](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")</span><span class="sxs-lookup"><span data-stu-id="1c25a-126">![The flow of Tracking and ETW Tracking Provider](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")</span></span>  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="1c25a-127">Dados do evento de participante de rastreamento</span><span class="sxs-lookup"><span data-stu-id="1c25a-127">Tracking Participant Event Data</span></span>  
 <span data-ttu-id="1c25a-128">Um participante de rastreamento serializa dados controlados de evento a uma sessão de ETW no formato de um evento pelo registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1c25a-128">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="1c25a-129">Um evento é identificado usando um identificador dentro do intervalo de 100 a 199.</span><span class="sxs-lookup"><span data-stu-id="1c25a-129">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="1c25a-130">Para obter definições de evento de acompanhamento emitidos por um participante de rastreamento, os registros, consulte a [referência de rastreamento de eventos](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="1c25a-130">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="1c25a-131">O tamanho de um evento de ETW é limitado pelo tamanho do buffer de ETW, ou pela carga útil máximo para um evento de ETW, qualquer valor é menor.</span><span class="sxs-lookup"><span data-stu-id="1c25a-131">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="1c25a-132">Se o tamanho do evento excede qualquer um desses limites de ETW, o evento será truncado e seu conteúdo é removido de uma maneira arbitrária.</span><span class="sxs-lookup"><span data-stu-id="1c25a-132">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="1c25a-133">Variáveis, os argumentos, anotações e os dados personalizado não são removidos seletivamente.</span><span class="sxs-lookup"><span data-stu-id="1c25a-133">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="1c25a-134">No caso de truncamento, todos estes é truncada independentemente do valor que fez com que o tamanho do evento excede o limite de ETW.</span><span class="sxs-lookup"><span data-stu-id="1c25a-134">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="1c25a-135">Os dados são removidos substituídos por `<item>..<item>`.</span><span class="sxs-lookup"><span data-stu-id="1c25a-135">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="1c25a-136">Tipos complexos em variáveis, argumentos, e itens de dados personalizados são serializados para o registro de eventos ETW usando o [classe NetDataContractSerializer](https://go.microsoft.com/fwlink/?LinkId=177537).</span><span class="sxs-lookup"><span data-stu-id="1c25a-136">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the [NetDataContractSerializer Class](https://go.microsoft.com/fwlink/?LinkId=177537).</span></span> <span data-ttu-id="1c25a-137">Essa classe inclui informações de CLR- tipo no vapor serializado XML.</span><span class="sxs-lookup"><span data-stu-id="1c25a-137">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="1c25a-138">Truncamento de dados de carregamento útil devido aos limites de ETW pode resultar em duplicado através dos registros que estão sendo enviados a uma sessão de ETW.</span><span class="sxs-lookup"><span data-stu-id="1c25a-138">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="1c25a-139">Isso pode ocorrer se mais de uma sessão é escutando eventos e as sessões têm diferentes limites de carregamento útil para os eventos.</span><span class="sxs-lookup"><span data-stu-id="1c25a-139">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="1c25a-140">Para a sessão com o limite inferior o evento pode ser truncado.</span><span class="sxs-lookup"><span data-stu-id="1c25a-140">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="1c25a-141">O participante de rastreamento de ETW não tem conhecimento do número de sessões que escutam por eventos; se um evento é truncado para uma sessão no participante de ETW tentar de volta para o evento uma vez.</span><span class="sxs-lookup"><span data-stu-id="1c25a-141">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="1c25a-142">Nesse caso a sessão que está configurada para aceitar um tamanho maior de carregamento útil obterá o evento duas vezes (o evento não truncado e truncado).</span><span class="sxs-lookup"><span data-stu-id="1c25a-142">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="1c25a-143">Duplicação pode ser impedida configurando todas as sessões de ETW com os mesmos limites de tamanho do buffer.</span><span class="sxs-lookup"><span data-stu-id="1c25a-143">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="1c25a-144">Acessando dados de acompanhamento de um participante de ETW no visualizador de eventos</span><span class="sxs-lookup"><span data-stu-id="1c25a-144">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  
 <span data-ttu-id="1c25a-145">Os eventos que são gravados em uma sessão de ETW por participante de rastreamento de ETW podem ser acessados através do visualizador de eventos (para usar o padrão de identificação do provedor).</span><span class="sxs-lookup"><span data-stu-id="1c25a-145">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="1c25a-146">Isso permite rapidamente exibindo os registros de rastreamento que foram emitidos pelo fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1c25a-146">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c25a-147">Controlando o registro os eventos emissores a uma sessão de ETW usam IDs de evento no intervalo de 100 a 199.</span><span class="sxs-lookup"><span data-stu-id="1c25a-147">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="1c25a-148">Para ativar exibir os registros de rastreamento no visualizador de eventos</span><span class="sxs-lookup"><span data-stu-id="1c25a-148">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1.  <span data-ttu-id="1c25a-149">Ligue o visualizador de eventos (EVENTVWR.EXE)</span><span class="sxs-lookup"><span data-stu-id="1c25a-149">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2.  <span data-ttu-id="1c25a-150">Selecione **Visualizador de eventos, Applications and Services Logs, Microsoft, Windows, aplicativos de servidor**.</span><span class="sxs-lookup"><span data-stu-id="1c25a-150">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3.  <span data-ttu-id="1c25a-151">Clique com botão direito e certifique-se de que **exibição, mostrar logs analíticos e depuração** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="1c25a-151">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="1c25a-152">Se não, selecione-o para que a marca de seleção aparece próxima a ela.</span><span class="sxs-lookup"><span data-stu-id="1c25a-152">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="1c25a-153">Isso exibe a **analítico**, **Perf**, e **depurar** logs.</span><span class="sxs-lookup"><span data-stu-id="1c25a-153">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4.  <span data-ttu-id="1c25a-154">Clique com botão direito do **analítico** faça logon e, em seguida, selecione **Habilitar Log**.</span><span class="sxs-lookup"><span data-stu-id="1c25a-154">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="1c25a-155">O log existirá no diretório %SystemRoot% \ arquivo de Winevt System32 \ \ \ application logs Server-Applications%4Analytic.etl.</span><span class="sxs-lookup"><span data-stu-id="1c25a-155">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="1c25a-156">Participante de rastreamento personalizada</span><span class="sxs-lookup"><span data-stu-id="1c25a-156">Custom Tracking Participant</span></span>  
 <span data-ttu-id="1c25a-157">O participante de rastreamento API permite a extensão de rastreamento usuário fornecido com o participante de rastreamento que pode incluir a lógica personalizada para manipular os registros de rastreamento emissores em tempo de execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1c25a-157">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="1c25a-158">Para gravar um participante personalizado de rastreamento, o desenvolvedor deve implementar o método `Track` na classe de <xref:System.Activities.Tracking.TrackingParticipant> .</span><span class="sxs-lookup"><span data-stu-id="1c25a-158">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="1c25a-159">Este método é chamado quando um registro de rastreamento é emitida em tempo de execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1c25a-159">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="1c25a-160">Os participantes de rastreamento derivam da classe de <xref:System.Activities.Tracking.TrackingParticipant> .</span><span class="sxs-lookup"><span data-stu-id="1c25a-160">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="1c25a-161">Sistema forneceu <xref:System.Activities.Tracking.EtwTrackingParticipant> emite-se um rastreamento de evento para o evento do Windows (ETW) para cada registro de rastreamento que é recebido.</span><span class="sxs-lookup"><span data-stu-id="1c25a-161">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="1c25a-162">Para criar um participante personalizado de rastreamento, uma classe é criada que deriva de <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="1c25a-162">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="1c25a-163">Para fornecer a funcionalidade básica de rastreamento, substitua o <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c25a-163">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="1c25a-164">o<xref:System.Activities.Tracking.TrackingParticipant.Track%2A> é chamado quando um registro de rastreamento é enviado em tempo de execução e pode ser processado na forma desejada.</span><span class="sxs-lookup"><span data-stu-id="1c25a-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="1c25a-165">No exemplo a seguir, uma classe personalizada de participante de rastreamento é definida que emite todos os registros de rastreamento para a janela do console.</span><span class="sxs-lookup"><span data-stu-id="1c25a-165">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="1c25a-166">Você também pode implementar um objeto de <xref:System.Activities.Tracking.TrackingParticipant> que processa os registros de rastreamento que usam de forma assíncrona seus métodos de `BeginTrack` e de `EndTrack`</span><span class="sxs-lookup"><span data-stu-id="1c25a-166">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
```csharp  
class ConsoleTrackingParticipant : TrackingParticipant  
{  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        if (record != null)  
        {  
            Console.WriteLine("=================================");  
            Console.WriteLine(record);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="1c25a-167">Para usar um participante específico de rastreamento, registrá-lo com a instância de fluxo de trabalho que você deseja controlar, conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="1c25a-167">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="1c25a-168">No exemplo a seguir, um fluxo de trabalho que consiste uma atividade de <xref:System.Activities.Statements.Sequence> que contém uma atividade de <xref:System.Activities.Statements.WriteLine> é criado.</span><span class="sxs-lookup"><span data-stu-id="1c25a-168">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="1c25a-169">`ConsoleTrackingParticipant` é adicionado para extensões e fluxo de trabalho é chamado.</span><span class="sxs-lookup"><span data-stu-id="1c25a-169">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
```csharp  
Activity activity= new Sequence()  
{  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "Hello World."  
        }  
    }  
};  
  
WorkflowApplication instance = new WorkflowApplication(activity);  
  
instance.Extensions.Add(new ConsoleTrackingParticipant());  
  instance.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
            {  
                Console.WriteLine("workflow instance completed, Id = " + instance.Id);  
                resetEvent.Set();  
            };  
            instance.Run();  
            Console.ReadLine();  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c25a-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c25a-170">See Also</span></span>  
 [<span data-ttu-id="1c25a-171">Monitoramento do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="1c25a-171">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="1c25a-172">Monitoramento de aplicativos com a malha de aplicativos</span><span class="sxs-lookup"><span data-stu-id="1c25a-172">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
