---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: d12656b77fa219080382603fd04a542d2fa9064a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399083"
---
# <a name="workflowruntime"></a><span data-ttu-id="a3d6c-101">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="a3d6c-101">\<workflowRuntime></span></span>
<span data-ttu-id="a3d6c-102">Especifica as configurações para uma instância <xref:System.Workflow.Runtime.WorkflowRuntime> do para hospedar serviços de Windows Communication Foundation baseado em fluxo de trabalho (WCF).</span><span class="sxs-lookup"><span data-stu-id="a3d6c-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
<span data-ttu-id="a3d6c-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a3d6c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a3d6c-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a3d6c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a3d6c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a3d6c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a3d6c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a3d6c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="a3d6c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a3d6c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="a3d6c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de workflowRuntime**</span><span class="sxs-lookup"><span data-stu-id="a3d6c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3d6c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3d6c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3d6c-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a3d6c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a3d6c-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3d6c-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a3d6c-112">Attributes</span></span>  
  
|<span data-ttu-id="a3d6c-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a3d6c-113">Attribute</span></span>|<span data-ttu-id="a3d6c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3d6c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3d6c-115">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="a3d6c-115">cachedInstanceExpiration</span></span>|<span data-ttu-id="a3d6c-116">Um valor <xref:System.TimeSpan> opcional que especifica a duração máxima em que uma instância de fluxo de trabalho pode permanecer na memória no estado ocioso antes de ser descarregada ou anulada de modo forçado.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-116">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="a3d6c-117">Se o WorkflowRuntime tiver `PersistenceService` que executar UnloadOnIdle, esse atributo será ignorado.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-117">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="a3d6c-118">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="a3d6c-118">enablePerformanceCounters</span></span>|<span data-ttu-id="a3d6c-119">Um valor booliano opcional que especifica se os contadores de desempenho estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-119">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="a3d6c-120">Os contadores de desempenho fornecem informações sobre várias estatísticas relacionadas ao fluxo de trabalho, mas causam uma penalidade de desempenho quando o mecanismo de tempo de execução do fluxo de trabalho é iniciado e quando as instâncias de fluxo de trabalho estão em execução.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-120">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="a3d6c-121">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-121">The default value is `true`.</span></span>|  
|<span data-ttu-id="a3d6c-122">name</span><span class="sxs-lookup"><span data-stu-id="a3d6c-122">name</span></span>|<span data-ttu-id="a3d6c-123">Uma cadeia de caracteres que contém o nome do mecanismo de tempo de execução do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-123">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="a3d6c-124">O nome é usado na saída para distinguir esse tempo de execução de outros tempos de execução que podem estar em execução no sistema, por exemplo, em contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-124">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="a3d6c-125">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-125">The default is an empty string.</span></span>|  
|<span data-ttu-id="a3d6c-126">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="a3d6c-126">validateOnCreate</span></span>|<span data-ttu-id="a3d6c-127">Um valor booliano opcional que especifica se a validação da definição de fluxo de trabalho ocorrerá quando o WorkflowServiceHost for aberto.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-127">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="a3d6c-128">Quando esse atributo é definido como `true`, a validação do fluxo de trabalho é `WorkflowServiceHost.Open` executada toda vez que é chamada.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-128">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="a3d6c-129">Se forem encontrados erros de validação, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-129">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="a3d6c-130">Quando essa propriedade é definida como `false`, nenhuma validação de definição de fluxo de trabalho ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-130">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="a3d6c-131">O valor padrão para essa propriedade é `true`.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-131">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3d6c-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a3d6c-132">Child Elements</span></span>  
  
|<span data-ttu-id="a3d6c-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="a3d6c-133">Element</span></span>|<span data-ttu-id="a3d6c-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3d6c-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3d6c-135">commonParameters</span><span class="sxs-lookup"><span data-stu-id="a3d6c-135">commonParameters</span></span>|<span data-ttu-id="a3d6c-136">Uma coleção de parâmetros comuns usados por serviços.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-136">A collection of common parameters used by services.</span></span> <span data-ttu-id="a3d6c-137">Normalmente, essa coleção inclui a cadeia de conexão do banco de dados que pode ser compartilhada por serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-137">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="a3d6c-138">serviços</span><span class="sxs-lookup"><span data-stu-id="a3d6c-138">services</span></span>|<span data-ttu-id="a3d6c-139">Uma coleção de serviços que serão adicionados ao <xref:System.Workflow.Runtime.WorkflowRuntime> mecanismo.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-139">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="a3d6c-140">Os elementos são do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-140">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="a3d6c-141">Os serviços especificados na coleção serão inicializados pelo mecanismo de tempo de execução do fluxo de trabalho e adicionados aos seus <xref:System.Workflow.Runtime.WorkflowRuntime> serviços quando o construtor apropriado for chamado.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-141">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="a3d6c-142">Portanto, os serviços especificados na coleção devem seguir determinadas regras sobre as assinaturas de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-142">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="a3d6c-143">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-143">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3d6c-144">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a3d6c-144">Parent Elements</span></span>  
  
|<span data-ttu-id="a3d6c-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="a3d6c-145">Element</span></span>|<span data-ttu-id="a3d6c-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3d6c-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3d6c-147">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="a3d6c-147">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a3d6c-148">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="a3d6c-148">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3d6c-149">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3d6c-149">Remarks</span></span>  
 <span data-ttu-id="a3d6c-150">Para obter mais informações sobre como usar um arquivo de configuração para controlar o <xref:System.Workflow.Runtime.WorkflowRuntime> comportamento de um objeto de um aplicativo host Windows Workflow Foundation, consulte [arquivos de configuração de fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a3d6c-150">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3d6c-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a3d6c-151">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3d6c-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3d6c-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="a3d6c-153">[Arquivos de configuração de fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a3d6c-153">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
