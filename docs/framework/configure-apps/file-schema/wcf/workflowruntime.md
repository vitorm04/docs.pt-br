---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: db5e1083c07d4e204eb19eaae9257ed44439132e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206558"
---
# <a name="workflowruntime"></a><span data-ttu-id="68a76-101">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="68a76-101">\<workflowRuntime></span></span>
<span data-ttu-id="68a76-102">Especifica configurações para uma instância de <xref:System.Workflow.Runtime.WorkflowRuntime> para hospedar os serviços do Windows Communication Foundation (WCF) baseados em fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="68a76-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
 <span data-ttu-id="68a76-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="68a76-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="68a76-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="68a76-104">\<behaviors></span></span>  
<span data-ttu-id="68a76-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="68a76-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="68a76-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="68a76-106">\<behavior></span></span>  
<span data-ttu-id="68a76-107">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="68a76-107">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68a76-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68a76-108">Syntax</span></span>  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68a76-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="68a76-109">Attributes and Elements</span></span>  
 <span data-ttu-id="68a76-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="68a76-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68a76-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="68a76-111">Attributes</span></span>  
  
|<span data-ttu-id="68a76-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="68a76-112">Attribute</span></span>|<span data-ttu-id="68a76-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="68a76-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68a76-114">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="68a76-114">cachedInstanceExpiration</span></span>|<span data-ttu-id="68a76-115">Um recurso opcional <xref:System.TimeSpan> valor que especifica a duração máxima que uma instância de fluxo de trabalho pode permanecer na memória no estado ocioso antes de modo forçado é descarregado ou anulada.</span><span class="sxs-lookup"><span data-stu-id="68a76-115">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="68a76-116">Se tiver o workflowruntime `PersistenceService` que executa unloadOnIdle, esse atributo é ignorado.</span><span class="sxs-lookup"><span data-stu-id="68a76-116">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="68a76-117">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="68a76-117">enablePerformanceCounters</span></span>|<span data-ttu-id="68a76-118">Um valor booleano opcional que especifica se contadores de desempenho estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="68a76-118">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="68a76-119">Contadores de desempenho fornecem informações sobre várias estatísticas relacionadas ao fluxo de trabalho, mas eles causam uma penalidade de desempenho quando o mecanismo de tempo de execução do fluxo de trabalho é iniciado e quando as instâncias de fluxo de trabalho estão em execução.</span><span class="sxs-lookup"><span data-stu-id="68a76-119">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="68a76-120">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="68a76-120">The default value is `true`.</span></span>|  
|<span data-ttu-id="68a76-121">name</span><span class="sxs-lookup"><span data-stu-id="68a76-121">name</span></span>|<span data-ttu-id="68a76-122">Uma cadeia de caracteres que contém o nome do mecanismo de tempo de execução do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="68a76-122">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="68a76-123">O nome é usado na saída para distinguir esse tempo de execução de outros tempos de execução podem estar em execução no sistema, por exemplo, nos contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="68a76-123">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="68a76-124">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="68a76-124">The default is an empty string.</span></span>|  
|<span data-ttu-id="68a76-125">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="68a76-125">validateOnCreate</span></span>|<span data-ttu-id="68a76-126">Um valor booleano opcional que especifica se a validação da definição de fluxo de trabalho ocorrerá quando o WorkflowServiceHost for aberto.</span><span class="sxs-lookup"><span data-stu-id="68a76-126">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="68a76-127">Quando esse atributo é definido como `true`, a validação do fluxo de trabalho é executada sempre que `WorkflowServiceHost.Open` é chamado.</span><span class="sxs-lookup"><span data-stu-id="68a76-127">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="68a76-128">Se forem encontrados erros de validação, um <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="68a76-128">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="68a76-129">Quando essa propriedade é definida como `false`, nenhuma validação de definição de fluxo de trabalho acontecerá.</span><span class="sxs-lookup"><span data-stu-id="68a76-129">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="68a76-130">O valor padrão desta propriedade é `true`.</span><span class="sxs-lookup"><span data-stu-id="68a76-130">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68a76-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="68a76-131">Child Elements</span></span>  
  
|<span data-ttu-id="68a76-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="68a76-132">Element</span></span>|<span data-ttu-id="68a76-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="68a76-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68a76-134">commonParameters</span><span class="sxs-lookup"><span data-stu-id="68a76-134">commonParameters</span></span>|<span data-ttu-id="68a76-135">Uma coleção de parâmetros comuns usados pelos serviços.</span><span class="sxs-lookup"><span data-stu-id="68a76-135">A collection of common parameters used by services.</span></span> <span data-ttu-id="68a76-136">Esta coleção normalmente incluirão a cadeia de caracteres de conexão de banco de dados que pode ser compartilhada por serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="68a76-136">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="68a76-137">serviços</span><span class="sxs-lookup"><span data-stu-id="68a76-137">services</span></span>|<span data-ttu-id="68a76-138">Uma coleção de serviços que serão adicionados para o <xref:System.Workflow.Runtime.WorkflowRuntime> mecanismo.</span><span class="sxs-lookup"><span data-stu-id="68a76-138">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="68a76-139">Os elementos são do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="68a76-139">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="68a76-140">Os serviços especificados na coleção serão inicializados pelo mecanismo de tempo de execução de fluxo de trabalho e adicionados a seus serviços quando apropriado <xref:System.Workflow.Runtime.WorkflowRuntime> construtor é chamado.</span><span class="sxs-lookup"><span data-stu-id="68a76-140">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="68a76-141">Portanto, os serviços especificados na coleção devem seguir determinadas regras sobre as assinaturas de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="68a76-141">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="68a76-142">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="68a76-142">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68a76-143">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="68a76-143">Parent Elements</span></span>  
  
|<span data-ttu-id="68a76-144">Elemento</span><span class="sxs-lookup"><span data-stu-id="68a76-144">Element</span></span>|<span data-ttu-id="68a76-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="68a76-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68a76-146">\<behavior></span><span class="sxs-lookup"><span data-stu-id="68a76-146">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="68a76-147">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="68a76-147">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68a76-148">Comentários</span><span class="sxs-lookup"><span data-stu-id="68a76-148">Remarks</span></span>  
 <span data-ttu-id="68a76-149">Para obter mais informações sobre como usar um arquivo de configuração para controlar o comportamento de um <xref:System.Workflow.Runtime.WorkflowRuntime> objeto de um aplicativo de host do Windows Workflow Foundation, consulte [arquivos de configuração do fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="68a76-149">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68a76-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68a76-150">Example</span></span>  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="68a76-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68a76-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- [<span data-ttu-id="68a76-152">Arquivos de configuração do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="68a76-152">Workflow Configuration Files</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
