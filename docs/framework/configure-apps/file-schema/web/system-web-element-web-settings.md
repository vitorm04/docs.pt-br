---
title: Elemento <system.web> (Configurações da Web)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: 5c5c857d4494b6d78b819e56bae4213abc5e2035
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699100"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="72759-102">Elemento de > de \<System. Web (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="72759-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="72759-103">Contém informações sobre como a camada de hospedagem ASP.NET gerencia o comportamento de todo o processo.</span><span class="sxs-lookup"><span data-stu-id="72759-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[<span data-ttu-id="72759-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="72759-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="72759-105">&nbsp;&nbsp; **\<System. web >**</span><span class="sxs-lookup"><span data-stu-id="72759-105">&nbsp;&nbsp;**\<system.web>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72759-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72759-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72759-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="72759-107">Attributes and Elements</span></span>  

<span data-ttu-id="72759-108">As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.</span><span class="sxs-lookup"><span data-stu-id="72759-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72759-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="72759-109">Attributes</span></span>  

<span data-ttu-id="72759-110">None.</span><span class="sxs-lookup"><span data-stu-id="72759-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="72759-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="72759-111">Child Elements</span></span>  
  
|<span data-ttu-id="72759-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="72759-112">Element</span></span>|<span data-ttu-id="72759-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="72759-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72759-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="72759-114">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="72759-115">Especifica as definições de configuração para pools de aplicativos do IIS em um arquivo Aspnet. config.</span><span class="sxs-lookup"><span data-stu-id="72759-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="72759-116">Elementos Pai</span><span class="sxs-lookup"><span data-stu-id="72759-116">Parent Elements</span></span>  
  
|<span data-ttu-id="72759-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="72759-117">Element</span></span>|<span data-ttu-id="72759-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="72759-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72759-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="72759-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="72759-120">Especifica o elemento raiz em cada arquivo de configuração que é usado pelo Common Language Runtime e .NET Framework aplicativos.</span><span class="sxs-lookup"><span data-stu-id="72759-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72759-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="72759-121">Remarks</span></span>  

<span data-ttu-id="72759-122">O elemento `system.web` e seu elemento `applicationPool` filho foram adicionados à .NET Framework a partir do .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="72759-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="72759-123">Quando você executa o IIS 7,0 ou versões posteriores no modo integrado, essa combinação de elementos permite que você configure como o ASP.NET gerencia threads e como ele enfileira solicitações quando o ASP.NET está hospedado em um pool de aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="72759-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="72759-124">Se você executar o IIS 7,0 ou versões posteriores no modo clássico ou ISAPI, essas configurações serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="72759-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72759-125">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="72759-125">Example</span></span>  

<span data-ttu-id="72759-126">O exemplo a seguir mostra como configurar o comportamento do ASP.NET em todo o processo no arquivo Aspnet. config quando o ASP.NET está hospedado em um pool de aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="72759-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="72759-127">O exemplo supõe que o IIS está sendo executado no modo integrado e que o aplicativo está usando o .NET Framework 3,5 SP1 ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="72759-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="72759-128">Esse comportamento não ocorre em versões do .NET Framework anteriores ao .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="72759-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="72759-129">Os valores no exemplo são os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="72759-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="72759-130">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="72759-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="72759-131">{1&gt;Namespace&lt;1}</span><span class="sxs-lookup"><span data-stu-id="72759-131">Namespace</span></span>||  
|<span data-ttu-id="72759-132">Schema Name</span><span class="sxs-lookup"><span data-stu-id="72759-132">Schema Name</span></span>||  
|<span data-ttu-id="72759-133">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="72759-133">Validation File</span></span>||  
|<span data-ttu-id="72759-134">Pode estar vazio</span><span class="sxs-lookup"><span data-stu-id="72759-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="72759-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72759-135">See also</span></span>

- <span data-ttu-id="72759-136">[\<applicationPool> Element (Web Settings)](applicationpool-element-web-settings.md) [Elemento applicationPool> (configurações da Web)]</span><span class="sxs-lookup"><span data-stu-id="72759-136">[\<applicationPool> Element (Web Settings)](applicationpool-element-web-settings.md)</span></span>
