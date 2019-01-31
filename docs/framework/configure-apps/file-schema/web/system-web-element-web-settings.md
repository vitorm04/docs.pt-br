---
title: Elemento < System. Web > (configurações da Web)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: a8d0905dc64ae3e3c4977639ccf881a677de73a9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272806"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="54dd2-102">\<System. Web > (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="54dd2-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="54dd2-103">Contém informações sobre como a camada de hospedagem do ASP.NET gerencia o comportamento de todo o processo.</span><span class="sxs-lookup"><span data-stu-id="54dd2-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="54dd2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="54dd2-104">\<configuration></span></span>  
<span data-ttu-id="54dd2-105">\<System. Web > (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="54dd2-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54dd2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54dd2-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54dd2-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="54dd2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="54dd2-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="54dd2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54dd2-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="54dd2-109">Attributes</span></span>  
 <span data-ttu-id="54dd2-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="54dd2-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="54dd2-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="54dd2-111">Child Elements</span></span>  
  
|<span data-ttu-id="54dd2-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="54dd2-112">Element</span></span>|<span data-ttu-id="54dd2-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="54dd2-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54dd2-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="54dd2-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="54dd2-115">Especifica as configurações para pools de aplicativos do IIS em um arquivo ASPNET config.</span><span class="sxs-lookup"><span data-stu-id="54dd2-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54dd2-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="54dd2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="54dd2-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="54dd2-117">Element</span></span>|<span data-ttu-id="54dd2-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="54dd2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54dd2-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="54dd2-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="54dd2-120">Especifica o elemento raiz em cada arquivo de configuração que é usado pelo common language runtime e [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="54dd2-120">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54dd2-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="54dd2-121">Remarks</span></span>  
 <span data-ttu-id="54dd2-122">O `system.web` elemento e seus filhos `applicationPool` elemento foram adicionados para o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] partir do [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54dd2-122">The `system.web` element and its child `applicationPool` element were added to the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] as of [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="54dd2-123">Quando você executa [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versões posteriores no modo integrado, essa combinação de elemento permite que você configure como o ASP.NET gerencia os threads e como ele enfileira as solicitações quando o ASP.NET está hospedado em um pool de aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="54dd2-123">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="54dd2-124">Se você executar [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versões posteriores no modo clássico ou ISAPI, essas configurações são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="54dd2-124">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54dd2-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54dd2-125">Example</span></span>  
 <span data-ttu-id="54dd2-126">O exemplo a seguir mostra como configurar o comportamento de todo o processo do ASP.NET no arquivo ASPNET config quando o ASP.NET está hospedado em um pool de aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="54dd2-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="54dd2-127">O exemplo supõe que o IIS está em execução no integrado modo e que o aplicativo está usando o [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="54dd2-127">The example assumes that IIS is running in Integrated mode and that the application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span> <span data-ttu-id="54dd2-128">Esse comportamento não ocorre nas versões dos [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] anteriores a [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54dd2-128">This behavior does not occur in versions of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] earlier than the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="54dd2-129">Os valores no exemplo são os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="54dd2-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="54dd2-130">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="54dd2-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="54dd2-131">Namespace</span><span class="sxs-lookup"><span data-stu-id="54dd2-131">Namespace</span></span>||  
|<span data-ttu-id="54dd2-132">Nome do esquema</span><span class="sxs-lookup"><span data-stu-id="54dd2-132">Schema Name</span></span>||  
|<span data-ttu-id="54dd2-133">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="54dd2-133">Validation File</span></span>||  
|<span data-ttu-id="54dd2-134">Pode ser vazio</span><span class="sxs-lookup"><span data-stu-id="54dd2-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="54dd2-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54dd2-135">See also</span></span>
- <span data-ttu-id="54dd2-136">[\<applicationPool> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md) [Elemento applicationPool> (configurações da Web)]</span><span class="sxs-lookup"><span data-stu-id="54dd2-136">[\<applicationPool> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)</span></span>
