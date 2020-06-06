---
title: Elemento <applicationPool> (configurações da Web)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152848"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="9111c-102">Elemento \<applicationPool> (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="9111c-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="9111c-103">Especifica as definições de configuração que são usadas pelo ASP.NET para gerenciar o comportamento de todo o processo quando um aplicativo ASP.NET está sendo executado no modo integrado no IIS 7,0 ou em uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="9111c-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on IIS 7.0 or a later version.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9111c-104">Esse elemento e o recurso que ele dá suporte só funcionarão se o aplicativo ASP.NET estiver hospedado no IIS 7,0 ou em versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="9111c-104">This element and the feature it supports only work if your ASP.NET application is hosted on IIS 7.0 or later versions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**  
  
## <a name="syntax"></a><span data-ttu-id="9111c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9111c-105">Syntax</span></span>  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9111c-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9111c-106">Attributes and Elements</span></span>  

<span data-ttu-id="9111c-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9111c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9111c-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="9111c-108">Attributes</span></span>  
  
|<span data-ttu-id="9111c-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="9111c-109">Attribute</span></span>|<span data-ttu-id="9111c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="9111c-110">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="9111c-111">Especifica quantas solicitações simultâneas o ASP.NET permite por CPU.</span><span class="sxs-lookup"><span data-stu-id="9111c-111">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="9111c-112">Especifica quantos threads simultâneos podem ser executados para um pool de aplicativos para cada CPU.</span><span class="sxs-lookup"><span data-stu-id="9111c-112">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="9111c-113">Isso fornece uma maneira alternativa de controlar a simultaneidade ASP.NET, pois você pode limitar o número de threads gerenciados que podem ser usados por CPU para atender a solicitações.</span><span class="sxs-lookup"><span data-stu-id="9111c-113">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="9111c-114">Por padrão, essa configuração é 0, o que significa que o ASP.NET não limita o número de threads que podem ser criados por CPU, embora o pool de threads do CLR também limite o número de threads que podem ser criados.</span><span class="sxs-lookup"><span data-stu-id="9111c-114">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="9111c-115">Especifica o número máximo de solicitações que podem ser enfileiradas para ASP.NET em um único processo.</span><span class="sxs-lookup"><span data-stu-id="9111c-115">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="9111c-116">Quando dois ou mais aplicativos ASP.NET são executados em um único pool de aplicativos, o conjunto cumulativo de solicitações que estão sendo feitas a qualquer aplicativo no pool de aplicativos está sujeito a essa configuração.</span><span class="sxs-lookup"><span data-stu-id="9111c-116">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9111c-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9111c-117">Child Elements</span></span>  
 <span data-ttu-id="9111c-118">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9111c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9111c-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9111c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9111c-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="9111c-120">Element</span></span>|<span data-ttu-id="9111c-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="9111c-121">Description</span></span>|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|<span data-ttu-id="9111c-122">Contém informações sobre como o ASP.NET interage com um aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="9111c-122">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9111c-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="9111c-123">Remarks</span></span>  

<span data-ttu-id="9111c-124">Quando você executa o IIS 7,0 ou uma versão posterior no modo integrado, essa combinação de elementos permite que você configure como o ASP.NET gerencia as solicitações de threads e filas quando o aplicativo é hospedado em um pool de aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="9111c-124">When you run IIS 7.0 or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="9111c-125">Se você executar o IIS 6 ou executar o IIS 7,0 no modo clássico ou no modo ISAPI, essas configurações serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="9111c-125">If you run IIS 6 or you run IIS 7.0 in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
<span data-ttu-id="9111c-126">As `applicationPool` configurações se aplicam a todos os pools de aplicativos executados em uma versão específica do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9111c-126">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="9111c-127">As configurações estão contidas em um arquivo Aspnet. config.</span><span class="sxs-lookup"><span data-stu-id="9111c-127">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="9111c-128">Há uma versão desse arquivo para as versões 2,0 e 4,0 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9111c-128">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="9111c-129">(As versões 3,0 e 3,5 do .NET Framework compartilham o arquivo Aspnet. config com a versão 2,0.)</span><span class="sxs-lookup"><span data-stu-id="9111c-129">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9111c-130">Se você executar o IIS 7,0 no Windows 7, poderá configurar um arquivo Aspnet. config separado para cada pool de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9111c-130">If you run IIS 7.0 on Windows 7, you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="9111c-131">Isso permite que você personalize o desempenho dos threads para cada pool de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9111c-131">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
<span data-ttu-id="9111c-132">Para a `maxConcurrentRequestsPerCPU` configuração, a configuração padrão de "5000" no .NET Framework 4 desativa efetivamente a limitação de solicitação controlada pelo ASP.net, a menos que você realmente tenha 5000 ou mais solicitações por CPU.</span><span class="sxs-lookup"><span data-stu-id="9111c-132">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="9111c-133">A configuração padrão depende, em vez disso, do pool de threads CLR para gerenciar automaticamente a simultaneidade por CPU.</span><span class="sxs-lookup"><span data-stu-id="9111c-133">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="9111c-134">Os aplicativos que fazem uso extensivo do processamento assíncrono de solicitações ou que têm muitas solicitações de execução longa bloqueadas na e/s de rede, se beneficiarão do maior limite padrão no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9111c-134">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="9111c-135">`maxConcurrentRequestsPerCPU`A configuração para zero desativa o uso de threads gerenciados para processar solicitações ASP.net.</span><span class="sxs-lookup"><span data-stu-id="9111c-135">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="9111c-136">Quando um aplicativo é executado em um pool de aplicativos do IIS, as solicitações permanecem no thread de e/s do IIS e, portanto, a simultaneidade é limitada pelas configurações de thread do IIS.</span><span class="sxs-lookup"><span data-stu-id="9111c-136">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
<span data-ttu-id="9111c-137">A `requestQueueLimit` configuração funciona da mesma maneira que o `requestQueueLimit` atributo do elemento [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) , que é definido nos arquivos Web. config para aplicativos ASP.net.</span><span class="sxs-lookup"><span data-stu-id="9111c-137">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="9111c-138">No entanto, a `requestQueueLimit` configuração em um arquivo Aspnet. config substitui a `requestQueueLimit` configuração em um arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="9111c-138">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="9111c-139">Em outras palavras, se ambos os atributos forem definidos (por padrão, isso é verdadeiro), a `requestQueueLimit` configuração no arquivo Aspnet. config terá precedência.</span><span class="sxs-lookup"><span data-stu-id="9111c-139">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9111c-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9111c-140">Example</span></span>  

<span data-ttu-id="9111c-141">O exemplo a seguir mostra como configurar o comportamento do ASP.NET em todo o processo no arquivo Aspnet. config nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="9111c-141">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="9111c-142">O aplicativo é hospedado em um pool de aplicativos do IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="9111c-142">The application is hosted in an IIS 7.0 application pool.</span></span>  
  
- <span data-ttu-id="9111c-143">O IIS 7,0 está sendo executado no modo integrado.</span><span class="sxs-lookup"><span data-stu-id="9111c-143">IIS 7.0 is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="9111c-144">O aplicativo está usando o .NET Framework 3,5 SP1 ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="9111c-144">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
<span data-ttu-id="9111c-145">Os valores no exemplo são os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="9111c-145">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="9111c-146">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="9111c-146">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9111c-147">Namespace</span><span class="sxs-lookup"><span data-stu-id="9111c-147">Namespace</span></span>||  
|<span data-ttu-id="9111c-148">Nome do Esquema</span><span class="sxs-lookup"><span data-stu-id="9111c-148">Schema Name</span></span>||  
|<span data-ttu-id="9111c-149">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="9111c-149">Validation File</span></span>||  
|<span data-ttu-id="9111c-150">Pode estar vazio</span><span class="sxs-lookup"><span data-stu-id="9111c-150">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="9111c-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="9111c-151">See also</span></span>

- [<span data-ttu-id="9111c-152">\<system.web>Elemento (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="9111c-152">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)
