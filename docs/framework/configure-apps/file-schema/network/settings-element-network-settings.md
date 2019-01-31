---
title: Elemento <settings> (configurações de rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: 839907d9339d459070fff12dbca22d3c2df5b020
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260613"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="59cad-102">\<Configurações > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="59cad-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="59cad-103">Configura as opções de rede básicaspara o namespace <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59cad-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="59cad-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="59cad-104">\<configuration></span></span>  
<span data-ttu-id="59cad-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="59cad-105">\<system.net></span></span>  
<span data-ttu-id="59cad-106">\<Configurações ></span><span class="sxs-lookup"><span data-stu-id="59cad-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59cad-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59cad-107">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59cad-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="59cad-108">Attributes and Elements</span></span>  
 <span data-ttu-id="59cad-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="59cad-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59cad-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="59cad-110">Attributes</span></span>  
 <span data-ttu-id="59cad-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="59cad-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="59cad-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="59cad-112">Child Elements</span></span>  
  
|<span data-ttu-id="59cad-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="59cad-113">Element</span></span>|<span data-ttu-id="59cad-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="59cad-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59cad-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="59cad-115">httpListener</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|<span data-ttu-id="59cad-116">Personaliza os parâmetros usados pelo <xref:System.Net.HttpListener> classe.</span><span class="sxs-lookup"><span data-stu-id="59cad-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="59cad-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="59cad-117">httpWebRequest</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|<span data-ttu-id="59cad-118">Personaliza os parâmetros de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="59cad-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="59cad-119">ipv6</span><span class="sxs-lookup"><span data-stu-id="59cad-119">ipv6</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|<span data-ttu-id="59cad-120">Permite que o protocolo IP versão 6 (IPv6) dão suporte.</span><span class="sxs-lookup"><span data-stu-id="59cad-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="59cad-121">\<performanceCounter > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="59cad-121">\<performanceCounter> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|<span data-ttu-id="59cad-122">Permite que os contadores de desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="59cad-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="59cad-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="59cad-123">servicePointManager</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|<span data-ttu-id="59cad-124">Configura as conexões aos recursos da rede.</span><span class="sxs-lookup"><span data-stu-id="59cad-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="59cad-125">socket</span><span class="sxs-lookup"><span data-stu-id="59cad-125">socket</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|<span data-ttu-id="59cad-126">Especifica se as operações de soquete usam portas de conclusão.</span><span class="sxs-lookup"><span data-stu-id="59cad-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="59cad-127">\<webProxyScript > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="59cad-127">\<webProxyScript> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|<span data-ttu-id="59cad-128">Configura as características do script usado para descobrir os proxies da Web.</span><span class="sxs-lookup"><span data-stu-id="59cad-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59cad-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="59cad-129">Parent Elements</span></span>  
  
|<span data-ttu-id="59cad-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="59cad-130">Element</span></span>|<span data-ttu-id="59cad-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="59cad-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59cad-132">system.net</span><span class="sxs-lookup"><span data-stu-id="59cad-132">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="59cad-133">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="59cad-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59cad-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="59cad-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="59cad-135">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="59cad-135">Configuration Files</span></span>  
 <span data-ttu-id="59cad-136">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="59cad-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59cad-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59cad-137">See also</span></span>
- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="59cad-138">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="59cad-138">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
