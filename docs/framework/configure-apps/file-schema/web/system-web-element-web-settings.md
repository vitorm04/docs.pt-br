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
ms.openlocfilehash: b9a43c5f5141e364ab9aac1cfdff577a8fb8a161
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486672"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="256b0-102">\<System. Web > (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="256b0-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="256b0-103">Contém informações sobre como a camada de hospedagem do ASP.NET gerencia o comportamento de todo o processo.</span><span class="sxs-lookup"><span data-stu-id="256b0-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="256b0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="256b0-104">\<configuration></span></span>  
<span data-ttu-id="256b0-105">\<System. Web > (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="256b0-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="256b0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="256b0-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="256b0-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="256b0-107">Attributes and Elements</span></span>  
 <span data-ttu-id="256b0-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="256b0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="256b0-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="256b0-109">Attributes</span></span>  
 <span data-ttu-id="256b0-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="256b0-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="256b0-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="256b0-111">Child Elements</span></span>  
  
|<span data-ttu-id="256b0-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="256b0-112">Element</span></span>|<span data-ttu-id="256b0-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="256b0-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="256b0-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="256b0-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="256b0-115">Especifica as configurações para pools de aplicativos do IIS em um arquivo ASPNET config.</span><span class="sxs-lookup"><span data-stu-id="256b0-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="256b0-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="256b0-116">Parent Elements</span></span>  
  
|<span data-ttu-id="256b0-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="256b0-117">Element</span></span>|<span data-ttu-id="256b0-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="256b0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="256b0-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="256b0-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="256b0-120">Especifica o elemento raiz em cada arquivo de configuração que é usado pelo common language runtime e aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="256b0-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="256b0-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="256b0-121">Remarks</span></span>  
 <span data-ttu-id="256b0-122">O `system.web` elemento e seu filho `applicationPool` elemento foram adicionados ao .NET Framework a partir do .NET Framework 3.5 SP1.</span><span class="sxs-lookup"><span data-stu-id="256b0-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="256b0-123">Quando você executa o IIS 7.0 ou versões posteriores no modo integrado, essa combinação de elemento lhe permite configurar como o ASP.NET gerencia os threads e como ele enfileira as solicitações quando o ASP.NET está hospedado em um pool de aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="256b0-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="256b0-124">Se você executar o IIS 7.0 ou versões posteriores no modo clássico ou ISAPI, essas configurações serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="256b0-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="256b0-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="256b0-125">Example</span></span>  
 <span data-ttu-id="256b0-126">O exemplo a seguir mostra como configurar o comportamento de todo o processo do ASP.NET no arquivo ASPNET config quando o ASP.NET está hospedado em um pool de aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="256b0-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="256b0-127">O exemplo supõe que o IIS está em execução no integrado modo e que o aplicativo está usando o .NET Framework 3.5 SP1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="256b0-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="256b0-128">Esse comportamento não ocorre nas versões do .NET Framework anteriores ao .NET Framework 3.5 SP1.</span><span class="sxs-lookup"><span data-stu-id="256b0-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="256b0-129">Os valores no exemplo são os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="256b0-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="256b0-130">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="256b0-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="256b0-131">Namespace</span><span class="sxs-lookup"><span data-stu-id="256b0-131">Namespace</span></span>||  
|<span data-ttu-id="256b0-132">Nome do esquema</span><span class="sxs-lookup"><span data-stu-id="256b0-132">Schema Name</span></span>||  
|<span data-ttu-id="256b0-133">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="256b0-133">Validation File</span></span>||  
|<span data-ttu-id="256b0-134">Pode ser vazio</span><span class="sxs-lookup"><span data-stu-id="256b0-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="256b0-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="256b0-135">See also</span></span>

- <span data-ttu-id="256b0-136">[\<applicationPool> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md) [Elemento applicationPool> (configurações da Web)]</span><span class="sxs-lookup"><span data-stu-id="256b0-136">[\<applicationPool> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)</span></span>
