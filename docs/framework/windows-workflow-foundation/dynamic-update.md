---
title: Atualização dinâmica
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: a1d5337bf69cb87d790ce4074cde4c18c989a4d8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724458"
---
# <a name="dynamic-update"></a><span data-ttu-id="7437e-102">Atualização dinâmica</span><span class="sxs-lookup"><span data-stu-id="7437e-102">Dynamic Update</span></span>

<span data-ttu-id="7437e-103">A atualização dinâmica fornece um mecanismo para que os desenvolvedores de aplicativos de fluxo de trabalho atualizem a definição de fluxo de trabalho de uma instância do fluxo de trabalho persistida.</span><span class="sxs-lookup"><span data-stu-id="7437e-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="7437e-104">Isso pode ser implementar uma correção de bug, novos requisitos ou acomodar alterações inesperadas.</span><span class="sxs-lookup"><span data-stu-id="7437e-104">This can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="7437e-105">Este tópico fornece uma visão geral da funcionalidade de atualização dinâmica introduzida no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7437e-105">This topic provides an overview of the dynamic update functionality introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>

## <a name="dynamic-update"></a><span data-ttu-id="7437e-106">Atualização dinâmica</span><span class="sxs-lookup"><span data-stu-id="7437e-106">Dynamic Update</span></span>

<span data-ttu-id="7437e-107">Para aplicar as atualizações dinâmicas em uma instância fluxo de trabalho persistida, um <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> é criado que contém instruções para o tempo de execução que descreve como modificar a instância de fluxo de trabalho persistida para refletir as alterações desejadas.</span><span class="sxs-lookup"><span data-stu-id="7437e-107">To apply dynamic updates to a persisted workflow instance, a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> is created that contains instructions for the runtime that describe how to modify the persisted workflow instance to reflect the desired changes.</span></span> <span data-ttu-id="7437e-108">Assim que o mapa de atualização é criado, ele é aplicado às instâncias desejadas do fluxo de trabalho persistido.</span><span class="sxs-lookup"><span data-stu-id="7437e-108">Once the update map is created, it is applied to the desired persisted workflow instances.</span></span> <span data-ttu-id="7437e-109">Assim que a atualização dinâmica é aplicada, a instância do fluxo de trabalho pode ser retomada usando a nova definição do fluxo de trabalho atualizado.</span><span class="sxs-lookup"><span data-stu-id="7437e-109">Once the dynamic update is applied, the workflow instance may be resumed using the new updated workflow definition.</span></span> <span data-ttu-id="7437e-110">Há quatro etapas necessárias para criar e aplicar um mapa de atualização.</span><span class="sxs-lookup"><span data-stu-id="7437e-110">There are four steps required to create and apply an update map.</span></span>

1. [<span data-ttu-id="7437e-111">Preparar a definição de fluxo de trabalho para atualização dinâmica</span><span class="sxs-lookup"><span data-stu-id="7437e-111">Prepare the workflow definition for dynamic update</span></span>](dynamic-update.md#Prepare)

2. [<span data-ttu-id="7437e-112">Atualize a definição de fluxo de trabalho para refletir as alterações desejadas</span><span class="sxs-lookup"><span data-stu-id="7437e-112">Update the workflow definition to reflect the desired changes</span></span>](dynamic-update.md#Update)

3. [<span data-ttu-id="7437e-113">Criar o mapa de atualização</span><span class="sxs-lookup"><span data-stu-id="7437e-113">Create the update map</span></span>](dynamic-update.md#Create)

4. [<span data-ttu-id="7437e-114">Aplicar o mapa de atualização para as instâncias de fluxo de trabalho persistidas desejado</span><span class="sxs-lookup"><span data-stu-id="7437e-114">Apply the update map to the desired persisted workflow instances</span></span>](dynamic-update.md#Apply)

> [!NOTE]
> <span data-ttu-id="7437e-115">Observe que as etapas de 1 a 3, que abrangem a criação do mapa de atualização, podem ser executadas de maneira independente de aplicar a atualização.</span><span class="sxs-lookup"><span data-stu-id="7437e-115">Note that steps 1 through 3, which cover the creation of the update map, may be performed independently of applying the update.</span></span> <span data-ttu-id="7437e-116">Um cenário comum que o desenvolvedor de fluxo de trabalho criará o mapa de atualização offline e, em seguida, um administrador aplicará a atualização em um momento posterior.</span><span class="sxs-lookup"><span data-stu-id="7437e-116">A common scenario that the workflow developer will create the update map offline, and then an administrator will apply the update at a later time.</span></span>

<span data-ttu-id="7437e-117">Este tópico fornece uma visão geral do processo de atualização dinâmica de adicionar uma nova atividade a uma instância persistida de um fluxo de trabalho Xaml compilado.</span><span class="sxs-lookup"><span data-stu-id="7437e-117">This topic provides an overview of the dynamic update process of adding a new activity to a persisted instance of a compiled Xaml workflow.</span></span>

### <a name="Prepare"></a> <span data-ttu-id="7437e-118">Preparar a definição de fluxo de trabalho para atualização dinâmica</span><span class="sxs-lookup"><span data-stu-id="7437e-118">Prepare the workflow definition for dynamic update</span></span>

<span data-ttu-id="7437e-119">A primeira etapa do processo de atualização dinâmica é preparar a definição desejada do fluxo de trabalho para atualização.</span><span class="sxs-lookup"><span data-stu-id="7437e-119">The first step in the dynamic update process is to prepare the desired workflow definition for update.</span></span> <span data-ttu-id="7437e-120">Isso é feito chamando o método <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> e transmitindo na definição de fluxo de trabalho para ser modificado.</span><span class="sxs-lookup"><span data-stu-id="7437e-120">This is done by calling the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method and passing in the workflow definition to modify.</span></span> <span data-ttu-id="7437e-121">Esse método valida e percorre a árvore de fluxo de trabalho para identificar todos os objetos, como atividades públicas e variáveis que precisam ser marcadas para que possam ser comparadas posteriormente com a definição do fluxo de trabalho alterado.</span><span class="sxs-lookup"><span data-stu-id="7437e-121">This method validates and then walks the workflow tree to identify all of the objects such as public activities and variables that need to be tagged so they can be compared later with the modified workflow definition.</span></span> <span data-ttu-id="7437e-122">Quando isso estiver concluído, a árvore de fluxo de trabalho será clonada e anexada à definição original do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7437e-122">When this is complete, the workflow tree is cloned and attached to the original workflow definition.</span></span> <span data-ttu-id="7437e-123">Quando o mapa de atualização é criado, a versão atualizada da definição de fluxo de trabalho é comparada com a definição original de fluxo de trabalho e o mapa de atualização é gerado com base nas diferenças.</span><span class="sxs-lookup"><span data-stu-id="7437e-123">When the update map is created, the updated version of the workflow definition is compared with the original workflow definition and the update map is generated based on the differences.</span></span>

<span data-ttu-id="7437e-124">Para preparar um fluxo de trabalho do Xaml para atualização dinâmica, ele pode ser carregado em um <xref:System.Activities.ActivityBuilder> e, em seguida, o <xref:System.Activities.ActivityBuilder> é passado em <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7437e-124">To prepare a Xaml workflow for dynamic update it may be loaded into an <xref:System.Activities.ActivityBuilder>, and then the <xref:System.Activities.ActivityBuilder> is passed into <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="7437e-125">Para obter mais informações sobre como trabalhar com fluxos de trabalho serializados e <xref:System.Activities.ActivityBuilder>, consulte [serializar fluxos de trabalho e atividades de XAML e](serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="7437e-125">For more information about working with serialized workflows and <xref:System.Activities.ActivityBuilder>, see [Serializing Workflows and Activities to and from XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

<span data-ttu-id="7437e-126">No exemplo a seguir, uma definição de `MortgageWorkflow` (que consiste em um <xref:System.Activities.Statements.Sequence> com várias atividades filhos) é carregada em um <xref:System.Activities.ActivityBuilder> e, em seguida, é preparada para atualização dinâmica.</span><span class="sxs-lookup"><span data-stu-id="7437e-126">In the following example, a `MortgageWorkflow` definition (that consists of a <xref:System.Activities.Statements.Sequence> with several child activities) is loaded into an <xref:System.Activities.ActivityBuilder>, and then prepared for dynamic update.</span></span> <span data-ttu-id="7437e-127">Depois que o método retorna, o <xref:System.Activities.ActivityBuilder> contém a definição original de fluxo de trabalho assim como uma cópia.</span><span class="sxs-lookup"><span data-stu-id="7437e-127">After the method returns, the <xref:System.Activities.ActivityBuilder> contains the original workflow definition as well as a copy.</span></span>

```csharp
// Load the MortgageWorkflow definition from Xaml into
// an ActivityBuilder.
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
{
    LocalAssembly = Assembly.GetExecutingAssembly()
};

XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefinitions\MortgageWorkflow.xaml",
    readerSettings);

ActivityBuilder ab = XamlServices.Load(
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;

// Prepare the workflow definition for dynamic update.
DynamicUpdateServices.PrepareForUpdate(ab);
```

> [!NOTE]
> <span data-ttu-id="7437e-128">Para baixar o código de exemplo que acompanha este tópico, consulte [código de exemplo de atualização dinâmica](https://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="7437e-128">To download the sample code that accompanies this topic, see [Dynamic Update sample code](https://go.microsoft.com/fwlink/?LinkId=227905).</span></span>

### <a name="Update"></a> <span data-ttu-id="7437e-129">Atualize a definição de fluxo de trabalho para refletir as alterações desejadas</span><span class="sxs-lookup"><span data-stu-id="7437e-129">Update the workflow definition to reflect the desired changes</span></span>

<span data-ttu-id="7437e-130">Quando a definição de fluxo de trabalho tiver sido preparada para atualização, as alterações desejadas poderão ser feitas.</span><span class="sxs-lookup"><span data-stu-id="7437e-130">Once the workflow definition has been prepared for updating, the desired changes can be made.</span></span> <span data-ttu-id="7437e-131">Você pode adicionar ou remover atividades, adicionar, mover ou excluir variáveis públicas, adicionar ou remover argumentos, e fazer alterações na assinatura de representantes da atividade.</span><span class="sxs-lookup"><span data-stu-id="7437e-131">You can add or remove activities, add, move or delete public variables, add or remove arguments, and make changes to the signature of activity delegates.</span></span> <span data-ttu-id="7437e-132">Você não pode remover uma atividade em execução ou modificar a assinatura de um representante em execução.</span><span class="sxs-lookup"><span data-stu-id="7437e-132">You cannot remove a running activity or change the signature of a running delegate.</span></span> <span data-ttu-id="7437e-133">Essas alterações podem ser feitas com o uso de código ou em um designer de fluxo de trabalho hospedado novamente.</span><span class="sxs-lookup"><span data-stu-id="7437e-133">These changes may be made using code, or in a re-hosted workflow designer.</span></span> <span data-ttu-id="7437e-134">No exemplo a seguir, uma atividade `VerifyAppraisal` personalizada é adicionada à sequência que compõe o corpo do `MortgageWorkflow` do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="7437e-134">In the following example, a custom `VerifyAppraisal` activity is added to the Sequence that makes up the body of the `MortgageWorkflow` from the previous example.</span></span>

```csharp
// Make desired changes to the definition. In this example, we are
// inserting a new VerifyAppraisal activity as the 3rd child of the root Sequence.
VerifyAppraisal va = new VerifyAppraisal
{
    Result = new VisualBasicReference<bool>("LoanCriteria")
};

// Get the Sequence that makes up the body of the workflow.
Sequence s = ab.Implementation as Sequence;

// Insert the new activity into the Sequence.
s.Activities.Insert(2, va);
```

### <a name="Create"></a> <span data-ttu-id="7437e-135">Criar o mapa de atualização</span><span class="sxs-lookup"><span data-stu-id="7437e-135">Create the update map</span></span>

<span data-ttu-id="7437e-136">Assim que a definição de fluxo de trabalho que foi preparada para atualização tiver sido modificada, o mapa de atualização poderá ser criado.</span><span class="sxs-lookup"><span data-stu-id="7437e-136">Once the workflow definition that was prepared for update has been modified, the update map can be created.</span></span> <span data-ttu-id="7437e-137">Para criar um mapa de atualização dinâmica, o método <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> será chamado.</span><span class="sxs-lookup"><span data-stu-id="7437e-137">To create a dynamic update map, the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> method is invoked.</span></span> <span data-ttu-id="7437e-138">Isso retorna um <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> que contém as informações que o tempo de execução precisa para modificar uma instância do fluxo de trabalho persistido de forma que pode ser carregado e retomado com a nova definição de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7437e-138">This returns a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> that contains the information the runtime needs to modify a persisted workflow instance so that it may be loaded and resumed with the new workflow definition.</span></span> <span data-ttu-id="7437e-139">No exemplo a seguir, um mapa dinâmico é criado para a definição alterada de `MortgageWorkflow` do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="7437e-139">In the following example, a dynamic map is created for the modified `MortgageWorkflow` definition from the previous example.</span></span>

```csharp
// Create the update map.
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);
```

<span data-ttu-id="7437e-140">Esse mapa de atualização pode ser usado imediatamente para modificar as instâncias de fluxo de trabalho, ou normalmente pode ser salvo e as atualizações aplicadas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="7437e-140">This update map can immediately be used to modify persisted workflow instances, or more typically it can be saved and the updates applied later.</span></span> <span data-ttu-id="7437e-141">Uma maneira de salvar o mapa de atualização é serializá-lo em um arquivo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7437e-141">One way to save the update map is to serialize it to a file, as shown in the following example.</span></span>

```csharp
// Serialize the update map to a file.
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Create))
{
    serializer.WriteObject(fs, map);
}
```

<span data-ttu-id="7437e-142">Quando o <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> retornar, a definição clonada de fluxo de trabalho e outras informações de atualização dinâmica que foram adicionadas na chamada para o <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> serão removidas e a definição modificada do fluxo de trabalho estará pronta para ser salva para ser usada posteriormente ao retomar as instâncias de fluxo de trabalho atualizado.</span><span class="sxs-lookup"><span data-stu-id="7437e-142">When <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> returns, the cloned workflow definition and other dynamic update information that was added in the call to <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> is removed, and the modified workflow definition is ready to be saved so that it can be used later when resuming updated workflow instances.</span></span> <span data-ttu-id="7437e-143">No exemplo a seguir, a definição modificada do fluxo de trabalho é salva em `MortgageWorkflow_v2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="7437e-143">In the following example, the modified workflow definition is saved to `MortgageWorkflow_v2.xaml`.</span></span>

```csharp
// Save the modified workflow definition.
StreamWriter sw = File.CreateText(@"C:\WorkflowDefinitions\MortgageWorkflow_v1.1.xaml");
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
sw.Close();
```

### <a name="Apply"></a> <span data-ttu-id="7437e-144">Aplicar o mapa de atualização para as instâncias de fluxo de trabalho persistidas desejado</span><span class="sxs-lookup"><span data-stu-id="7437e-144">Apply the update map to the desired persisted workflow instances</span></span>

<span data-ttu-id="7437e-145">Aplicar o mapa da atualização pode ser feito a qualquer momento após criá-lo.</span><span class="sxs-lookup"><span data-stu-id="7437e-145">Applying the update map can be done at any time after creating it.</span></span> <span data-ttu-id="7437e-146">Pode ser feito imediatamente usando a instância do <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> que foi retornada pelo <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> ou pode ser feito posteriormente usando uma cópia salva do mapa da atualização.</span><span class="sxs-lookup"><span data-stu-id="7437e-146">It can be done right away using the <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance that was returned by <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, or it can be done later using a saved copy of the update map.</span></span> <span data-ttu-id="7437e-147">Para atualizar uma instância de fluxo de trabalho, carregue-a em um <xref:System.Activities.WorkflowApplicationInstance> usando <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7437e-147">To update a workflow instance, load it into a <xref:System.Activities.WorkflowApplicationInstance> using <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7437e-148">Em seguida, crie uma <xref:System.Activities.WorkflowApplication> usando a definição de fluxo de trabalho atualizado e os detalhes desejados <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="7437e-148">Next, create a <xref:System.Activities.WorkflowApplication> using the updated workflow definition, and the desired <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="7437e-149">Este <xref:System.Activities.WorkflowIdentity> pode ser diferente do que foi usado para persistir o fluxo de trabalho original, e é normalmente para refletir que a instância persistida foi modificada.</span><span class="sxs-lookup"><span data-stu-id="7437e-149">This <xref:System.Activities.WorkflowIdentity> may be different than the one that was used to persist the original workflow, and typically is in order to reflect that the persisted instance has been modified.</span></span> <span data-ttu-id="7437e-150">Quando o <xref:System.Activities.WorkflowApplication> é criado, ele é carregado usando a sobrecarga de <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> que usa um <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> e, em seguida, descarregado com uma chamada para <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7437e-150">Once the <xref:System.Activities.WorkflowApplication> is created, it is loaded using the overload of <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> that takes a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, and then unloaded with a call to <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7437e-151">Isso aplica a atualização dinâmica e persiste a instância atualizada do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7437e-151">This applies the dynamic update and persists the updated workflow instance.</span></span>

```csharp
// Load the serialized update map.
DynamicUpdateMap map;
using (FileStream fs = File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Open))
{
    DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
    object updateMap = serializer.ReadObject(fs);
    if (updateMap == null)
    {
        throw new ApplicationException("DynamicUpdateMap is null.");
    }

    map = (DynamicUpdateMap)updateMap;
}

// Retrieve a list of workflow instance ids that corresponds to the
// workflow instances to update. This step is the responsibility of
// the application developer.
List<Guid> ids = GetPersistedWorkflowIds();
foreach (Guid id in ids)
{
    // Get a proxy to the persisted workflow instance.
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(id, store);

    // If desired, you can inspect the WorkflowIdentity of the instance
    // using the DefinitionIdentity property to determine whether to apply
    // the update.
    Console.WriteLine(instance.DefinitionIdentity);

    // Create a workflow application. You must specify the updated workflow definition, and
    // you may provide an updated WorkflowIdentity if desired to reflect the update.
    WorkflowIdentity identity = new WorkflowIdentity
    {
        Name = "MortgageWorkflow v1.1",
        Version = new Version(1, 1, 0, 0)
    };

    // Load the persisted workflow instance using the updated workflow definition
    // and with an updated WorkflowIdentity. In this example the MortgageWorkflow class
    // contains the updated definition.
    WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

    // Apply the dynamic update on the loaded instance.
    wfApp.Load(instance, map);

    // Unload the updated instance.
    wfApp.Unload();
}
```

### <a name="resuming-an-updated-workflow-instance"></a><span data-ttu-id="7437e-152">Retomando uma instância atualizada do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7437e-152">Resuming an Updated Workflow Instance</span></span>

<span data-ttu-id="7437e-153">Assim que a atualização dinâmica tiver sido aplicada, a instância do fluxo de trabalho poderá ser retomada.</span><span class="sxs-lookup"><span data-stu-id="7437e-153">Once dynamic update has been applied, the workflow instance may be resumed.</span></span> <span data-ttu-id="7437e-154">Observe que a nova definição atualizada e o <xref:System.Activities.WorkflowIdentity> devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="7437e-154">Note that the new updated definition and <xref:System.Activities.WorkflowIdentity> must be used.</span></span>

> [!NOTE]
> <span data-ttu-id="7437e-155">Para obter mais informações sobre como trabalhar com <xref:System.Activities.WorkflowApplication> e <xref:System.Activities.WorkflowIdentity>, consulte [usando WorkflowIdentity e controle de versão](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="7437e-155">For more information about working with <xref:System.Activities.WorkflowApplication> and <xref:System.Activities.WorkflowIdentity>, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

<span data-ttu-id="7437e-156">No exemplo a seguir, o fluxo de trabalho do `MortgageWorkflow_v1.1.xaml` do exemplo anterior foi compilado, e foi carregado e retomado usando a definição atualizada do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7437e-156">In the following example, the `MortgageWorkflow_v1.1.xaml` workflow from the previous example has been compiled, and is loaded and resumed using the updated workflow definition.</span></span>

```csharp
// Load the persisted workflow instance using the updated workflow definition
// and updated WorkflowIdentity.
WorkflowIdentity identity = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1.1",
    Version = new Version(1, 1, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure persistence and desired workflow event handlers.
// (Omitted for brevity.)
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(InstanceId);

// Resume the workflow.
// wfApp.ResumeBookmark(...);
```

> [!NOTE]
> <span data-ttu-id="7437e-157">Para baixar o código de exemplo que acompanha este tópico, consulte [código de exemplo de atualização dinâmica](https://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="7437e-157">To download the sample code that accompanies this topic, see [Dynamic Update sample code](https://go.microsoft.com/fwlink/?LinkId=227905).</span></span>
