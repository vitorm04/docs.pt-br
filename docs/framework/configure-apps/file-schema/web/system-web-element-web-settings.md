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
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152835"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="b2d3c-102">Elemento \<system.web> (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="b2d3c-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="b2d3c-103">Contém informações sobre como a camada de hospedagem ASP.NET gerencia o comportamento de todo o processo.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a><span data-ttu-id="b2d3c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2d3c-104">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2d3c-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b2d3c-105">Attributes and Elements</span></span>  

<span data-ttu-id="b2d3c-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2d3c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="b2d3c-107">Attributes</span></span>  

<span data-ttu-id="b2d3c-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b2d3c-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b2d3c-109">Child Elements</span></span>  
  
|<span data-ttu-id="b2d3c-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="b2d3c-110">Element</span></span>|<span data-ttu-id="b2d3c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2d3c-111">Description</span></span>|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="b2d3c-112">Especifica as definições de configuração para pools de aplicativos do IIS em um arquivo Aspnet. config.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-112">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2d3c-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b2d3c-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b2d3c-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="b2d3c-114">Element</span></span>|<span data-ttu-id="b2d3c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2d3c-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="b2d3c-116">Especifica o elemento raiz em cada arquivo de configuração que é usado pelo Common Language Runtime e .NET Framework aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-116">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2d3c-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2d3c-117">Remarks</span></span>  

<span data-ttu-id="b2d3c-118">O `system.web` elemento e seu `applicationPool` elemento filho foram adicionados à .NET Framework a partir de .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-118">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="b2d3c-119">Quando você executa o IIS 7,0 ou versões posteriores no modo integrado, essa combinação de elementos permite que você configure como o ASP.NET gerencia threads e como ele enfileira solicitações quando o ASP.NET está hospedado em um pool de aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-119">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="b2d3c-120">Se você executar o IIS 7,0 ou versões posteriores no modo clássico ou ISAPI, essas configurações serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-120">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2d3c-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b2d3c-121">Example</span></span>  

<span data-ttu-id="b2d3c-122">O exemplo a seguir mostra como configurar o comportamento do ASP.NET em todo o processo no arquivo Aspnet. config quando o ASP.NET está hospedado em um pool de aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-122">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="b2d3c-123">O exemplo supõe que o IIS está sendo executado no modo integrado e que o aplicativo está usando o .NET Framework 3,5 SP1 ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-123">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="b2d3c-124">Esse comportamento não ocorre em versões do .NET Framework anteriores ao .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-124">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="b2d3c-125">Os valores no exemplo são os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-125">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="b2d3c-126">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="b2d3c-126">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2d3c-127">Namespace</span><span class="sxs-lookup"><span data-stu-id="b2d3c-127">Namespace</span></span>||  
|<span data-ttu-id="b2d3c-128">Nome do Esquema</span><span class="sxs-lookup"><span data-stu-id="b2d3c-128">Schema Name</span></span>||  
|<span data-ttu-id="b2d3c-129">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="b2d3c-129">Validation File</span></span>||  
|<span data-ttu-id="b2d3c-130">Pode estar vazio</span><span class="sxs-lookup"><span data-stu-id="b2d3c-130">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="b2d3c-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="b2d3c-131">See also</span></span>

- [<span data-ttu-id="b2d3c-132">\<applicationPool>Elemento (configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="b2d3c-132">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
