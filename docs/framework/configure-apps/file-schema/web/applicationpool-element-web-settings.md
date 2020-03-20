---
title: Elemento <applicationPool> (configurações da Web)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152848"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="c34ad-102">\<applicationPool> Element (Web Settings) [Elemento applicationPool> (configurações da Web)]</span><span class="sxs-lookup"><span data-stu-id="c34ad-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="c34ad-103">Especifica as configurações usadas por ASP.NET para gerenciar o comportamento em todo o processo quando um aplicativo ASP.NET está sendo executado no modo Integrado no IIS 7.0 ou em uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="c34ad-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on IIS 7.0 or a later version.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c34ad-104">Esse elemento e o recurso que ele suporta só funcionam se o aplicativo ASP.NET estiver hospedado nas versões IIS 7.0 ou posteriores.</span><span class="sxs-lookup"><span data-stu-id="c34ad-104">This element and the feature it supports only work if your ASP.NET application is hosted on IIS 7.0 or later versions.</span></span>  
  
[<span data-ttu-id="c34ad-105">**\<>de configuração**</span><span class="sxs-lookup"><span data-stu-id="c34ad-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="c34ad-106">&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c34ad-106">&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)</span></span>  
<span data-ttu-id="c34ad-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<>de pool de aplicativos**</span><span class="sxs-lookup"><span data-stu-id="c34ad-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c34ad-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c34ad-108">Syntax</span></span>  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c34ad-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c34ad-109">Attributes and Elements</span></span>  

<span data-ttu-id="c34ad-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c34ad-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c34ad-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="c34ad-111">Attributes</span></span>  
  
|<span data-ttu-id="c34ad-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="c34ad-112">Attribute</span></span>|<span data-ttu-id="c34ad-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c34ad-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="c34ad-114">Especifica quantas solicitações simultâneas ASP.NET permite por CPU.</span><span class="sxs-lookup"><span data-stu-id="c34ad-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="c34ad-115">Especifica quantos threads simultâneos podem ser executados para um pool de aplicativos para cada CPU.</span><span class="sxs-lookup"><span data-stu-id="c34ad-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="c34ad-116">Isso fornece uma maneira alternativa de controlar ASP.NET simultâneo, porque você pode limitar o número de threads gerenciados que podem ser usados por CPU para atender solicitações.</span><span class="sxs-lookup"><span data-stu-id="c34ad-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="c34ad-117">Por padrão, essa configuração é 0, o que significa que ASP.NET não limita o número de threads que podem ser criados por CPU, embora o pool de threads CLR também limite o número de threads que podem ser criados.</span><span class="sxs-lookup"><span data-stu-id="c34ad-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="c34ad-118">Especifica o número máximo de solicitações que podem ser enfileiradas para ASP.NET em um único processo.</span><span class="sxs-lookup"><span data-stu-id="c34ad-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="c34ad-119">Quando dois ou mais aplicativos ASP.NET são executados em um único pool de aplicativos, o conjunto cumulativo de solicitações que estão sendo feitas a qualquer aplicativo no pool de aplicativos está sujeito a essa configuração.</span><span class="sxs-lookup"><span data-stu-id="c34ad-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c34ad-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c34ad-120">Child Elements</span></span>  
 <span data-ttu-id="c34ad-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c34ad-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c34ad-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c34ad-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c34ad-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="c34ad-123">Element</span></span>|<span data-ttu-id="c34ad-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="c34ad-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c34ad-125">\<system.web></span><span class="sxs-lookup"><span data-stu-id="c34ad-125">\<system.web></span></span>](system-web-element-web-settings.md)|<span data-ttu-id="c34ad-126">Contém informações sobre como ASP.NET interage com um aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="c34ad-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c34ad-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="c34ad-127">Remarks</span></span>  

<span data-ttu-id="c34ad-128">Quando você executa o IIS 7.0 ou uma versão posterior no modo Integrado, essa combinação de elementos permite configurar como ASP.NET gerencia threads e filas de solicitações quando o aplicativo está hospedado em um pool de aplicativos IIS.</span><span class="sxs-lookup"><span data-stu-id="c34ad-128">When you run IIS 7.0 or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="c34ad-129">Se você executar o IIS 6 ou executar o IIS 7.0 no modo Classic ou no modo ISAPI, essas configurações serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="c34ad-129">If you run IIS 6 or you run IIS 7.0 in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
<span data-ttu-id="c34ad-130">As `applicationPool` configurações se aplicam a todos os pools de aplicativos executados em uma versão específica do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c34ad-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="c34ad-131">As configurações estão contidas em um arquivo aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="c34ad-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="c34ad-132">Há uma versão deste arquivo para as versões 2.0 e 4.0 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c34ad-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="c34ad-133">(As versões 3.0 e 3.5 do .NET Framework compartilham o arquivo aspnet.config com a versão 2.0.)</span><span class="sxs-lookup"><span data-stu-id="c34ad-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c34ad-134">Se você executar o IIS 7.0 no Windows 7, você poderá configurar um arquivo aspnet.config separado para cada pool de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c34ad-134">If you run IIS 7.0 on Windows 7, you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="c34ad-135">Isso permite que você adapte o desempenho dos threads para cada pool de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c34ad-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
<span data-ttu-id="c34ad-136">Para `maxConcurrentRequestsPerCPU` a configuração, a configuração padrão de "5000" no Quadro .NET 4 efetivamente desliga o estrangulamento da solicitação que é controlada por ASP.NET, a menos que você realmente tenha 5000 ou mais solicitações por CPU.</span><span class="sxs-lookup"><span data-stu-id="c34ad-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="c34ad-137">A configuração padrão depende, em vez disso, do pool de threads CLR para gerenciar automaticamente a concorrência por CPU.</span><span class="sxs-lookup"><span data-stu-id="c34ad-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="c34ad-138">Os aplicativos que fazem uso extensivo do processamento de solicitações assíncronas, ou que têm muitas solicitações de longo prazo bloqueadas na I/O da rede, se beneficiarão do limite de inadimplência aumentado no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="c34ad-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="c34ad-139">A `maxConcurrentRequestsPerCPU` configuração para zero desliga o uso de threads gerenciados para processar ASP.NET solicitações.</span><span class="sxs-lookup"><span data-stu-id="c34ad-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="c34ad-140">Quando um aplicativo é executado em um pool de aplicativos IIS, as solicitações permanecem no segmento IIS I/O e, portanto, a concorrência é estrangulada pelas configurações de rosca do IIS.</span><span class="sxs-lookup"><span data-stu-id="c34ad-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
<span data-ttu-id="c34ad-141">A `requestQueueLimit` configuração funciona da `requestQueueLimit` mesma forma que o atributo do elemento [processModel,](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) que é definido nos arquivos Web.config para aplicativos ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c34ad-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="c34ad-142">No entanto, a `requestQueueLimit` configuração em um arquivo `requestQueueLimit` aspnet.config substitui a configuração em um arquivo Web.config.</span><span class="sxs-lookup"><span data-stu-id="c34ad-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="c34ad-143">Em outras palavras, se ambos os atributos forem definidos (por padrão, isso é verdade), a `requestQueueLimit` configuração no arquivo aspnet.config tem precedência.</span><span class="sxs-lookup"><span data-stu-id="c34ad-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c34ad-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c34ad-144">Example</span></span>  

<span data-ttu-id="c34ad-145">O exemplo a seguir mostra como configurar ASP.NET comportamento em todo o processo no arquivo aspnet.config nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="c34ad-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="c34ad-146">O aplicativo está hospedado em um pool de aplicativos IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="c34ad-146">The application is hosted in an IIS 7.0 application pool.</span></span>  
  
- <span data-ttu-id="c34ad-147">O IIS 7.0 está sendo executado no modo Integrado.</span><span class="sxs-lookup"><span data-stu-id="c34ad-147">IIS 7.0 is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="c34ad-148">O aplicativo está usando o .NET Framework 3.5 SP1 ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="c34ad-148">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
<span data-ttu-id="c34ad-149">Os valores no exemplo são os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="c34ad-149">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="c34ad-150">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="c34ad-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c34ad-151">Namespace</span><span class="sxs-lookup"><span data-stu-id="c34ad-151">Namespace</span></span>||  
|<span data-ttu-id="c34ad-152">Nome do Esquema</span><span class="sxs-lookup"><span data-stu-id="c34ad-152">Schema Name</span></span>||  
|<span data-ttu-id="c34ad-153">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="c34ad-153">Validation File</span></span>||  
|<span data-ttu-id="c34ad-154">Pode ser vazio</span><span class="sxs-lookup"><span data-stu-id="c34ad-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="c34ad-155">Confira também</span><span class="sxs-lookup"><span data-stu-id="c34ad-155">See also</span></span>

- [<span data-ttu-id="c34ad-156">\<system.web> Element (Configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="c34ad-156">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)
