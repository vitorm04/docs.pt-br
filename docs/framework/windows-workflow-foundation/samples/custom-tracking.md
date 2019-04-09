---
title: Rastreamento personalizada
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: ca53d74f31059532118f3b5d96760a25ed72b3d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161839"
---
# <a name="custom-tracking"></a><span data-ttu-id="7a600-102">Rastreamento personalizada</span><span class="sxs-lookup"><span data-stu-id="7a600-102">Custom Tracking</span></span>
<span data-ttu-id="7a600-103">Este exemplo demonstra como criar um participante personalizado de rastreamento e gravar o conteúdo dos dados de acompanhamento no console.</span><span class="sxs-lookup"><span data-stu-id="7a600-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="7a600-104">Além disso, o exemplo demonstra como emitir os objetos de <xref:System.Activities.Tracking.CustomTrackingRecord> preenchido com dados definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7a600-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="7a600-105">O participante controlando console- base filtra os objetos de <xref:System.Activities.Tracking.TrackingRecord> emissores pelo fluxo de trabalho usando um objeto de perfil de rastreamento criado em código.</span><span class="sxs-lookup"><span data-stu-id="7a600-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>

## <a name="sample-details"></a><span data-ttu-id="7a600-106">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="7a600-106">Sample Details</span></span>
 <span data-ttu-id="7a600-107">Windows Workflow Foundation (WF) fornece uma infraestrutura de acompanhamento para controlar a execução de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7a600-107">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="7a600-108">O tempo de execução de rastreamento implementa uma instância de fluxo de trabalho para emitir os eventos relacionados ao ciclo de vida de fluxo de trabalho, os eventos de atividades de fluxo de trabalho e eventos personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="7a600-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="7a600-109">A tabela a seguir detalha os componentes principais de infraestrutura de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="7a600-109">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="7a600-110">Componente</span><span class="sxs-lookup"><span data-stu-id="7a600-110">Component</span></span>|<span data-ttu-id="7a600-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a600-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="7a600-112">Tempo de execução de rastreamento</span><span class="sxs-lookup"><span data-stu-id="7a600-112">Tracking runtime</span></span>|<span data-ttu-id="7a600-113">Fornece a infraestrutura para emitir registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="7a600-113">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="7a600-114">Participantes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="7a600-114">Tracking participants</span></span>|<span data-ttu-id="7a600-115">Consome os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="7a600-115">Consumes the tracking records.</span></span> [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] <span data-ttu-id="7a600-116">é fornecido com um participante de rastreamento que grava registros de rastreamento como eventos do Event Tracing for Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="7a600-116">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="7a600-117">Controlando o perfil</span><span class="sxs-lookup"><span data-stu-id="7a600-117">Tracking profile</span></span>|<span data-ttu-id="7a600-118">Um mecanismo de filtragem que permite que um participante de rastreamento assine para um subconjunto de registros de rastreamento emissores de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7a600-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="7a600-119">A tabela a seguir detalha os registros de rastreamento que o tempo de execução de fluxo de trabalho se emite.</span><span class="sxs-lookup"><span data-stu-id="7a600-119">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="7a600-120">Registro de Rastreamento</span><span class="sxs-lookup"><span data-stu-id="7a600-120">Tracking Record</span></span>|<span data-ttu-id="7a600-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a600-121">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="7a600-122">Registros de rastreamento de instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7a600-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="7a600-123">Descreve o ciclo de vida de instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7a600-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="7a600-124">Por exemplo, um registro de instância é emitida quando o fluxo de trabalho inicia ou termina.</span><span class="sxs-lookup"><span data-stu-id="7a600-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="7a600-125">Estado da atividade que acompanha registros.</span><span class="sxs-lookup"><span data-stu-id="7a600-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="7a600-126">Detalha a execução da atividade.</span><span class="sxs-lookup"><span data-stu-id="7a600-126">Details activity execution.</span></span> <span data-ttu-id="7a600-127">Esses registros indicam o estado de uma atividade de fluxo de trabalho como quando uma atividade é agendada ou quando a atividade completa ou quando uma falha é lançada.</span><span class="sxs-lookup"><span data-stu-id="7a600-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="7a600-128">Registro de ressunção do indexador.</span><span class="sxs-lookup"><span data-stu-id="7a600-128">Bookmark resumption record.</span></span>|<span data-ttu-id="7a600-129">Emitido sempre que um marcador em uma instância de fluxo de trabalho que é.</span><span class="sxs-lookup"><span data-stu-id="7a600-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="7a600-130">Registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="7a600-130">Custom Tracking Records.</span></span>|<span data-ttu-id="7a600-131">Um autor de fluxo de trabalho pode criar registros personalizados de rastreamento e emitir os dentro da atividade personalizado.</span><span class="sxs-lookup"><span data-stu-id="7a600-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|

 <span data-ttu-id="7a600-132">O participante de rastreamento assinatura para um subconjunto dos objetos emissores de <xref:System.Activities.Tracking.TrackingRecord> usando perfis de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="7a600-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="7a600-133">Um perfil de rastreamento contém consultas de rastreamento que permitem assinar para um tipo de registro específico de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="7a600-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="7a600-134">Controlar perfis pode ser especificado no código ou na configuração.</span><span class="sxs-lookup"><span data-stu-id="7a600-134">Tracking profiles can be specified in code or in configuration.</span></span>

### <a name="custom-tracking-participant"></a><span data-ttu-id="7a600-135">Participante de rastreamento personalizada</span><span class="sxs-lookup"><span data-stu-id="7a600-135">Custom Tracking Participant</span></span>
 <span data-ttu-id="7a600-136">O participante API de rastreamento permite a extensão de rastreamento com um usuário fornecido pelo participante que pode incluir a lógica personalizada para manipular os objetos de <xref:System.Activities.Tracking.TrackingRecord> emissores em tempo de execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7a600-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>

 <span data-ttu-id="7a600-137">Para gravar um participante de rastreamento o usuário deve implementar <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="7a600-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="7a600-138">Especificamente, o método de <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> precisa ser implementado por participante personalizado.</span><span class="sxs-lookup"><span data-stu-id="7a600-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="7a600-139">Este método é chamado quando <xref:System.Activities.Tracking.TrackingRecord> é emitida em tempo de execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7a600-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 <span data-ttu-id="7a600-140">O participante completo de rastreamento é implementado no arquivo de ConsoleTrackingParticipant.cs. O exemplo de código é o método de <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> para o participante personalizado de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="7a600-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>

```csharp
protected override void Track(TrackingRecord record, TimeSpan timeout)
{
    ...
    WorkflowInstanceRecord workflowInstanceRecord = record as WorkflowInstanceRecord;
    if (workflowInstanceRecord != null)
    {
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,
            " Workflow InstanceID: {0} Workflow instance state: {1}",
            record.InstanceId, workflowInstanceRecord.State));
    }

    ActivityStateRecord activityStateRecord = record as ActivityStateRecord;
    if (activityStateRecord != null)
    {
        IDictionary<String, object> variables = activityStateRecord.Variables;
        StringBuilder vars = new StringBuilder();

        if (variables.Count > 0)
        {
            vars.AppendLine("\n\tVariables:");
            foreach (KeyValuePair<string, object> variable in variables)
            {
                vars.AppendLine(String.Format(
                    "\t\tName: {0} Value: {1}", variable.Key, variable.Value));
            }
        }
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,
            " :Activity DisplayName: {0} :ActivityInstanceState: {1} {2}",
                activityStateRecord.Activity.Name, activityStateRecord.State,
            ((variables.Count > 0) ? vars.ToString() : String.Empty)));
    }

    CustomTrackingRecord customTrackingRecord = record as CustomTrackingRecord;

    if ((customTrackingRecord != null) && (customTrackingRecord.Data.Count > 0))
    {
        ...
    }
    Console.WriteLine();

}
```

 <span data-ttu-id="7a600-141">O exemplo de código a seguir adiciona o participante de console para o solicitante de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7a600-141">The following code example adds the console participant to the workflow invoker.</span></span>

```csharp
ConsoleTrackingParticipant customTrackingParticipant = new ConsoleTrackingParticipant()
{
    ...
    // The tracking profile is set here, refer to Program.CS
...
}

WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
```

### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="7a600-142">Emitindo registros de rastreamento personalizadas</span><span class="sxs-lookup"><span data-stu-id="7a600-142">Emitting Custom Tracking Records</span></span>
 <span data-ttu-id="7a600-143">Este exemplo também demonstra a capacidade de emitir objetos de <xref:System.Activities.Tracking.CustomTrackingRecord> de uma atividade personalizado de fluxo de trabalho:</span><span class="sxs-lookup"><span data-stu-id="7a600-143">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>

-   <span data-ttu-id="7a600-144">Os objetos de <xref:System.Activities.Tracking.CustomTrackingRecord> são criados e preenchido com dados definidos pelo usuário que são desejados ser emitidos com o registro.</span><span class="sxs-lookup"><span data-stu-id="7a600-144">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>

-   <span data-ttu-id="7a600-145">O <xref:System.Activities.Tracking.CustomTrackingRecord> é emitida chamando o método de controle do <xref:System.Activities.ActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="7a600-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>

 <span data-ttu-id="7a600-146">O exemplo a seguir demonstra como emitir objetos de <xref:System.Activities.Tracking.CustomTrackingRecord> dentro de uma atividade personalizado.</span><span class="sxs-lookup"><span data-stu-id="7a600-146">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>

```csharp
// Create the Custom Tracking Record
CustomTrackingRecord customRecord = new CustomTrackingRecord("OrderIn")
{
    Data =
    {
        {"OrderId", 200},
        {"OrderDate", "20 Aug 2001"}
    }
};

// Emit custom tracking record
context.Track(customRecord);
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="7a600-147">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="7a600-147">To use this sample</span></span>

1.  <span data-ttu-id="7a600-148">Usando o Visual Studio 2010, abra o arquivo de solução de Customtrackingsample.</span><span class="sxs-lookup"><span data-stu-id="7a600-148">Using Visual Studio 2010, open the CustomTrackingSample.sln solution file.</span></span>

2.  <span data-ttu-id="7a600-149">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="7a600-149">To build the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="7a600-150">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="7a600-150">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="7a600-151">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7a600-151">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7a600-152">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7a600-152">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7a600-153">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="7a600-153">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7a600-154">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="7a600-154">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="7a600-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a600-155">See also</span></span>

- [<span data-ttu-id="7a600-156">AppFabric que monitora Exemplos</span><span class="sxs-lookup"><span data-stu-id="7a600-156">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
