---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 43cdec2403e8d80256279388a1adf7cf3cedbb73
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558778"
---
# \<workflowRuntime>
<span data-ttu-id="68b01-101">Especifica as configurações para uma instância do <xref:System.Workflow.Runtime.WorkflowRuntime> para hospedar serviços de Windows Communication Foundation baseado em fluxo de trabalho (WCF).</span><span class="sxs-lookup"><span data-stu-id="68b01-101">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**  
  
## <a name="syntax"></a><span data-ttu-id="68b01-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="68b01-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68b01-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="68b01-103">Attributes and Elements</span></span>  
 <span data-ttu-id="68b01-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="68b01-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68b01-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="68b01-105">Attributes</span></span>  
  
|<span data-ttu-id="68b01-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="68b01-106">Attribute</span></span>|<span data-ttu-id="68b01-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="68b01-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68b01-108">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="68b01-108">cachedInstanceExpiration</span></span>|<span data-ttu-id="68b01-109">Um <xref:System.TimeSpan> valor opcional que especifica a duração máxima em que uma instância de fluxo de trabalho pode permanecer na memória no estado ocioso antes de ser descarregada ou anulada de modo forçado.</span><span class="sxs-lookup"><span data-stu-id="68b01-109">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="68b01-110">Se o WorkflowRuntime tiver `PersistenceService` que executar UnloadOnIdle, esse atributo será ignorado.</span><span class="sxs-lookup"><span data-stu-id="68b01-110">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="68b01-111">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="68b01-111">enablePerformanceCounters</span></span>|<span data-ttu-id="68b01-112">Um valor booliano opcional que especifica se os contadores de desempenho estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="68b01-112">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="68b01-113">Os contadores de desempenho fornecem informações sobre várias estatísticas relacionadas ao fluxo de trabalho, mas causam uma penalidade de desempenho quando o mecanismo de tempo de execução do fluxo de trabalho é iniciado e quando as instâncias de fluxo de trabalho estão em execução.</span><span class="sxs-lookup"><span data-stu-id="68b01-113">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="68b01-114">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="68b01-114">The default value is `true`.</span></span>|  
|<span data-ttu-id="68b01-115">name</span><span class="sxs-lookup"><span data-stu-id="68b01-115">name</span></span>|<span data-ttu-id="68b01-116">Uma cadeia de caracteres que contém o nome do mecanismo de tempo de execução do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="68b01-116">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="68b01-117">O nome é usado na saída para distinguir esse tempo de execução de outros tempos de execução que podem estar em execução no sistema, por exemplo, em contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="68b01-117">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="68b01-118">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="68b01-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="68b01-119">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="68b01-119">validateOnCreate</span></span>|<span data-ttu-id="68b01-120">Um valor booliano opcional que especifica se a validação da definição de fluxo de trabalho ocorrerá quando o WorkflowServiceHost for aberto.</span><span class="sxs-lookup"><span data-stu-id="68b01-120">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="68b01-121">Quando esse atributo é definido como `true` , a validação do fluxo de trabalho é executada toda vez que `WorkflowServiceHost.Open` é chamada.</span><span class="sxs-lookup"><span data-stu-id="68b01-121">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="68b01-122">Se forem encontrados erros de validação, um <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="68b01-122">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="68b01-123">Quando essa propriedade é definida como `false` , nenhuma validação de definição de fluxo de trabalho ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="68b01-123">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="68b01-124">O valor padrão para essa propriedade é `true`.</span><span class="sxs-lookup"><span data-stu-id="68b01-124">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68b01-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="68b01-125">Child Elements</span></span>  
  
|<span data-ttu-id="68b01-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="68b01-126">Element</span></span>|<span data-ttu-id="68b01-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="68b01-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68b01-128">commonParameters</span><span class="sxs-lookup"><span data-stu-id="68b01-128">commonParameters</span></span>|<span data-ttu-id="68b01-129">Uma coleção de parâmetros comuns usados por serviços.</span><span class="sxs-lookup"><span data-stu-id="68b01-129">A collection of common parameters used by services.</span></span> <span data-ttu-id="68b01-130">Normalmente, essa coleção inclui a cadeia de conexão do banco de dados que pode ser compartilhada por serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="68b01-130">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="68b01-131">services</span><span class="sxs-lookup"><span data-stu-id="68b01-131">services</span></span>|<span data-ttu-id="68b01-132">Uma coleção de serviços que serão adicionados ao <xref:System.Workflow.Runtime.WorkflowRuntime> mecanismo.</span><span class="sxs-lookup"><span data-stu-id="68b01-132">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="68b01-133">Os elementos são do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="68b01-133">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="68b01-134">Os serviços especificados na coleção serão inicializados pelo mecanismo de tempo de execução do fluxo de trabalho e adicionados aos seus serviços quando o <xref:System.Workflow.Runtime.WorkflowRuntime> construtor apropriado for chamado.</span><span class="sxs-lookup"><span data-stu-id="68b01-134">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="68b01-135">Portanto, os serviços especificados na coleção devem seguir determinadas regras sobre as assinaturas de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="68b01-135">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="68b01-136">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="68b01-136">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68b01-137">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="68b01-137">Parent Elements</span></span>  
  
|<span data-ttu-id="68b01-138">Elemento</span><span class="sxs-lookup"><span data-stu-id="68b01-138">Element</span></span>|<span data-ttu-id="68b01-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="68b01-139">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="68b01-140">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="68b01-140">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68b01-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="68b01-141">Remarks</span></span>  
 <span data-ttu-id="68b01-142">Para obter mais informações sobre como usar um arquivo de configuração para controlar o comportamento de um <xref:System.Workflow.Runtime.WorkflowRuntime> objeto de um aplicativo host Windows Workflow Foundation, consulte [arquivos de configuração de fluxo de trabalho](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="68b01-142">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68b01-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68b01-143">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="68b01-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="68b01-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="68b01-145">[Arquivos de configuração de fluxo de trabalho](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="68b01-145">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
