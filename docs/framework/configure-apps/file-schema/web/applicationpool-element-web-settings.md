---
title: Elemento <applicationPool> (configurações da Web)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 629eb482768e4ed2b3d70ee3d27157b502eeb72b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832717"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="6f841-102">\<applicationPool > (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="6f841-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="6f841-103">Especifica as configurações que são usadas pelo ASP.NET para gerenciar o comportamento de todo o processo quando um aplicativo ASP.NET estiver em execução no modo integrado [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="6f841-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6f841-104">Esse elemento e o recurso ele dá suporte a funcionam apenas se seu aplicativo ASP.NET estiver hospedado em [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="6f841-104">This element and the feature it supports only work if your ASP.NET application is hosted on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions.</span></span>  
  
 <span data-ttu-id="6f841-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6f841-105">\<configuration></span></span>  
<span data-ttu-id="6f841-106">\<System. Web > (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="6f841-106">\<system.web> Element (Web Settings)</span></span>  
<span data-ttu-id="6f841-107">\<applicationPool > (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="6f841-107">\<applicationPool> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f841-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f841-108">Syntax</span></span>  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f841-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6f841-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6f841-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6f841-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f841-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="6f841-111">Attributes</span></span>  
  
|<span data-ttu-id="6f841-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="6f841-112">Attribute</span></span>|<span data-ttu-id="6f841-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f841-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="6f841-114">Especifica a quantidade de solicitações simultâneas por CPU, o ASP.NET permite.</span><span class="sxs-lookup"><span data-stu-id="6f841-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="6f841-115">Especifica quantos threads simultâneos podem estar em execução para um pool de aplicativos para cada CPU.</span><span class="sxs-lookup"><span data-stu-id="6f841-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="6f841-116">Isso fornece uma maneira alternativa para controlar a simultaneidade ASP.NET, porque você pode limitar o número de threads gerenciados que pode ser usado por CPU para atender às solicitações.</span><span class="sxs-lookup"><span data-stu-id="6f841-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="6f841-117">Por padrão, essa configuração é 0, o que significa que o ASP.NET não limita o número de threads que podem ser criados por CPU, embora o pool de threads do CLR também limita o número de threads que podem ser criados.</span><span class="sxs-lookup"><span data-stu-id="6f841-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="6f841-118">Especifica o número máximo de solicitações que podem ser enfileiradas para o ASP.NET em um único processo.</span><span class="sxs-lookup"><span data-stu-id="6f841-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="6f841-119">Quando dois ou mais aplicativos ASP.NET executados em um único pool de aplicativos, o conjunto cumulativo de solicitações sendo feitas para qualquer aplicativo no pool de aplicativos está sujeito a essa configuração.</span><span class="sxs-lookup"><span data-stu-id="6f841-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f841-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6f841-120">Child Elements</span></span>  
 <span data-ttu-id="6f841-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6f841-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f841-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6f841-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6f841-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="6f841-123">Element</span></span>|<span data-ttu-id="6f841-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f841-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f841-125">\<system.web></span><span class="sxs-lookup"><span data-stu-id="6f841-125">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="6f841-126">Contém informações sobre como o ASP.NET interage com um aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="6f841-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f841-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f841-127">Remarks</span></span>  
 <span data-ttu-id="6f841-128">Quando você executa [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou uma versão posterior no modo integrado, essa combinação de elemento permite que você configure como o ASP.NET gerencia solicitações de threads e filas quando o aplicativo é hospedado em um pool de aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="6f841-128">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="6f841-129">Se você executa o IIS 6 ou executar [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] no modo clássico ou no modo ISAPI, essas configurações são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="6f841-129">If you run IIS 6 or you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
 <span data-ttu-id="6f841-130">O `applicationPool` configurações se aplicam a todos os pools de aplicativos que são executados em uma versão específica do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f841-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="6f841-131">As configurações estão contidas em um arquivo ASPNET config.</span><span class="sxs-lookup"><span data-stu-id="6f841-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="6f841-132">Há uma versão desse arquivo para as versões 2.0 e 4.0 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f841-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="6f841-133">(As versões 3.0 e 3.5 do .NET Framework compartilham arquivo ASPNET config com a versão 2.0.)</span><span class="sxs-lookup"><span data-stu-id="6f841-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6f841-134">Se você executar [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] em [!INCLUDE[win7](../../../../../includes/win7-md.md)], você pode configurar um arquivo ASPNET separado para cada pool de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="6f841-134">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] on [!INCLUDE[win7](../../../../../includes/win7-md.md)], you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="6f841-135">Isso lhe permite personalizar o desempenho dos threads para cada pool de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="6f841-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
 <span data-ttu-id="6f841-136">Para o `maxConcurrentRequestsPerCPU` definir, a configuração padrão de "5000" no .NET Framework 4 efetivamente desativa a limitação de solicitação que é controlado pelo ASP.NET, a menos que você realmente tem mais de 5000 solicitações por CPU.</span><span class="sxs-lookup"><span data-stu-id="6f841-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="6f841-137">A configuração padrão em vez disso, depende do pool de threads do CLR para gerenciar automaticamente a simultaneidade por CPU.</span><span class="sxs-lookup"><span data-stu-id="6f841-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="6f841-138">Aplicativos que fazem uso extensivo de processamento assíncrono da solicitação, ou que têm muitas solicitações de longa execução bloqueadas em e/s, de rede serão beneficiados com o limite de aumento padrão no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="6f841-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="6f841-139">Definindo `maxConcurrentRequestsPerCPU` como zero desativa o uso de threads gerenciados para processar solicitações ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6f841-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="6f841-140">Quando um aplicativo é executado em um pool de aplicativos do IIS, fique de solicitações no thread de e/s do IIS e, portanto, a simultaneidade é limitada pelas configurações de thread do IIS.</span><span class="sxs-lookup"><span data-stu-id="6f841-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
 <span data-ttu-id="6f841-141">O `requestQueueLimit` configuração funciona da mesma forma que o `requestQueueLimit` atributo da [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) elemento, que é definido nos arquivos Web. config para aplicativos ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6f841-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="6f841-142">No entanto, o `requestQueueLimit` substituições de configuração em um arquivo ASPNET o `requestQueueLimit` definindo em um arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="6f841-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="6f841-143">Em outras palavras, se ambos os atributos são definidos (por padrão, isso é verdadeiro), o `requestQueueLimit` configuração no arquivo ASPNET config tem precedência.</span><span class="sxs-lookup"><span data-stu-id="6f841-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f841-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f841-144">Example</span></span>  
 <span data-ttu-id="6f841-145">O exemplo a seguir mostra como configurar o comportamento de todo o processo do ASP.NET no arquivo ASPNET config nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="6f841-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="6f841-146">O aplicativo é hospedado em um [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] pool de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="6f841-146">The application is hosted in an [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] application pool.</span></span>  
  
- [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] <span data-ttu-id="6f841-147">está em execução no modo integrado.</span><span class="sxs-lookup"><span data-stu-id="6f841-147">is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="6f841-148">O aplicativo está usando o .NET Framework 3.5 SP1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="6f841-148">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
 <span data-ttu-id="6f841-149">Os valores no exemplo são os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="6f841-149">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="6f841-150">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="6f841-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6f841-151">Namespace</span><span class="sxs-lookup"><span data-stu-id="6f841-151">Namespace</span></span>||  
|<span data-ttu-id="6f841-152">Nome do esquema</span><span class="sxs-lookup"><span data-stu-id="6f841-152">Schema Name</span></span>||  
|<span data-ttu-id="6f841-153">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="6f841-153">Validation File</span></span>||  
|<span data-ttu-id="6f841-154">Pode ser vazio</span><span class="sxs-lookup"><span data-stu-id="6f841-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="6f841-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f841-155">See also</span></span>

- <span data-ttu-id="6f841-156">[\<system.web> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md) [Elemento system.web> (configurações da Web)]</span><span class="sxs-lookup"><span data-stu-id="6f841-156">[\<system.web> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)</span></span>
