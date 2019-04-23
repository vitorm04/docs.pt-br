---
title: Elemento <settings> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: a1733803d1f5a5bf64aeb69d0360cef3de3b3a69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096921"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="f8a91-102">\<Configurações > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="f8a91-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="f8a91-103">Configura as opções de rede básicaspara o namespace <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f8a91-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="f8a91-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f8a91-104">\<configuration></span></span>  
<span data-ttu-id="f8a91-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f8a91-105">\<system.net></span></span>  
<span data-ttu-id="f8a91-106">\<Configurações ></span><span class="sxs-lookup"><span data-stu-id="f8a91-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8a91-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8a91-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8a91-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f8a91-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f8a91-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f8a91-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8a91-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="f8a91-110">Attributes</span></span>  
 <span data-ttu-id="f8a91-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f8a91-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f8a91-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f8a91-112">Child Elements</span></span>  
  
|<span data-ttu-id="f8a91-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f8a91-113">Element</span></span>|<span data-ttu-id="f8a91-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8a91-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8a91-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="f8a91-115">httpListener</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|<span data-ttu-id="f8a91-116">Personaliza os parâmetros usados pelo <xref:System.Net.HttpListener> classe.</span><span class="sxs-lookup"><span data-stu-id="f8a91-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="f8a91-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="f8a91-117">httpWebRequest</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|<span data-ttu-id="f8a91-118">Personaliza os parâmetros de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="f8a91-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="f8a91-119">ipv6</span><span class="sxs-lookup"><span data-stu-id="f8a91-119">ipv6</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|<span data-ttu-id="f8a91-120">Permite que o protocolo IP versão 6 (IPv6) dão suporte.</span><span class="sxs-lookup"><span data-stu-id="f8a91-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="f8a91-121">\<performanceCounter > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="f8a91-121">\<performanceCounter> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|<span data-ttu-id="f8a91-122">Permite que os contadores de desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="f8a91-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="f8a91-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="f8a91-123">servicePointManager</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|<span data-ttu-id="f8a91-124">Configura as conexões aos recursos da rede.</span><span class="sxs-lookup"><span data-stu-id="f8a91-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="f8a91-125">socket</span><span class="sxs-lookup"><span data-stu-id="f8a91-125">socket</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|<span data-ttu-id="f8a91-126">Especifica se as operações de soquete usam portas de conclusão.</span><span class="sxs-lookup"><span data-stu-id="f8a91-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="f8a91-127">\<webProxyScript > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="f8a91-127">\<webProxyScript> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|<span data-ttu-id="f8a91-128">Configura as características do script usado para descobrir os proxies da Web.</span><span class="sxs-lookup"><span data-stu-id="f8a91-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f8a91-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f8a91-129">Parent Elements</span></span>  
  
|<span data-ttu-id="f8a91-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="f8a91-130">Element</span></span>|<span data-ttu-id="f8a91-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8a91-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8a91-132">system.net</span><span class="sxs-lookup"><span data-stu-id="f8a91-132">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="f8a91-133">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="f8a91-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8a91-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8a91-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f8a91-135">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="f8a91-135">Configuration Files</span></span>  
 <span data-ttu-id="f8a91-136">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f8a91-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8a91-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8a91-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="f8a91-138">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="f8a91-138">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
