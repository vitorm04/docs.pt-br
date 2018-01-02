---
title: "&lt;System. Web&gt; elemento (configurações da Web)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 59899178fd9fc8da2334883ed62d9f8655eb335b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemwebgt-element-web-settings"></a><span data-ttu-id="0b89d-102">&lt;System. Web&gt; elemento (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="0b89d-102">&lt;system.web&gt; Element (Web Settings)</span></span>
<span data-ttu-id="0b89d-103">Contém informações sobre como a camada de hospedagem ASP.NET gerencia o comportamento de todo o processo.</span><span class="sxs-lookup"><span data-stu-id="0b89d-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="0b89d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0b89d-104">\<configuration></span></span>  
<span data-ttu-id="0b89d-105">\<System. Web > elemento (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="0b89d-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b89d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b89d-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b89d-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0b89d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0b89d-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0b89d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b89d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="0b89d-109">Attributes</span></span>  
 <span data-ttu-id="0b89d-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0b89d-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0b89d-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0b89d-111">Child Elements</span></span>  
  
|<span data-ttu-id="0b89d-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b89d-112">Element</span></span>|<span data-ttu-id="0b89d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b89d-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b89d-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="0b89d-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="0b89d-115">Especifica as configurações para pools de aplicativos do IIS em um arquivo ASPNET config.</span><span class="sxs-lookup"><span data-stu-id="0b89d-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0b89d-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0b89d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0b89d-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b89d-117">Element</span></span>|<span data-ttu-id="0b89d-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b89d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b89d-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0b89d-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="0b89d-120">Especifica o elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="0b89d-120">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b89d-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b89d-121">Remarks</span></span>  
 <span data-ttu-id="0b89d-122">O `system.web` elemento e seus filhos `applicationPool` elemento foram adicionados para o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] do [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b89d-122">The `system.web` element and its child `applicationPool` element were added to the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] as of [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="0b89d-123">Quando você executa [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versões posteriores no modo integrado, essa combinação de elemento permite que você configure como o ASP.NET gerencia threads e como ele enfileira as solicitações ao ASP.NET hospedado em um pool de aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="0b89d-123">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="0b89d-124">Se você executar [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versões posteriores no modo clássico ou ISAPI, essas configurações são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="0b89d-124">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b89d-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b89d-125">Example</span></span>  
 <span data-ttu-id="0b89d-126">O exemplo a seguir mostra como configurar o comportamento de todo o processo ASP.NET no arquivo ASPNET ao ASP.NET hospedado em um pool de aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="0b89d-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="0b89d-127">O exemplo supõe que o IIS está em execução no integrado modo e que o aplicativo está usando o [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="0b89d-127">The example assumes that IIS is running in Integrated mode and that the application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span> <span data-ttu-id="0b89d-128">Esse comportamento não ocorre nas versões do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] anteriores a [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b89d-128">This behavior does not occur in versions of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] earlier than the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="0b89d-129">Os valores de exemplo são os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="0b89d-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="0b89d-130">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="0b89d-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0b89d-131">Namespace</span><span class="sxs-lookup"><span data-stu-id="0b89d-131">Namespace</span></span>||  
|<span data-ttu-id="0b89d-132">Nome do esquema</span><span class="sxs-lookup"><span data-stu-id="0b89d-132">Schema Name</span></span>||  
|<span data-ttu-id="0b89d-133">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="0b89d-133">Validation File</span></span>||  
|<span data-ttu-id="0b89d-134">Pode ser vazio</span><span class="sxs-lookup"><span data-stu-id="0b89d-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="0b89d-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b89d-135">See Also</span></span>  
 <span data-ttu-id="0b89d-136">[\<applicationPool> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md) [Elemento applicationPool> (configurações da Web)]</span><span class="sxs-lookup"><span data-stu-id="0b89d-136">[\<applicationPool> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)</span></span>
