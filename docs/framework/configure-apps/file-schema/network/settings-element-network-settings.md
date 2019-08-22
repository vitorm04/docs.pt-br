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
ms.openlocfilehash: 12797e2f06d03aacd81700eae57d5776c1a6f354
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663988"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="8d04d-102">\<Elemento > Settings (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="8d04d-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="8d04d-103">Configura as opções de rede básicaspara o namespace <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8d04d-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="8d04d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8d04d-104">\<configuration></span></span>  
<span data-ttu-id="8d04d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="8d04d-105">\<system.net></span></span>  
<span data-ttu-id="8d04d-106">\<> de configurações</span><span class="sxs-lookup"><span data-stu-id="8d04d-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d04d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d04d-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d04d-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8d04d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8d04d-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8d04d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d04d-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8d04d-110">Attributes</span></span>  
 <span data-ttu-id="8d04d-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8d04d-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d04d-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8d04d-112">Child Elements</span></span>  
  
|<span data-ttu-id="8d04d-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d04d-113">Element</span></span>|<span data-ttu-id="8d04d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d04d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d04d-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="8d04d-115">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="8d04d-116">Personaliza os <xref:System.Net.HttpListener> parâmetros usados pela classe.</span><span class="sxs-lookup"><span data-stu-id="8d04d-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="8d04d-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="8d04d-117">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="8d04d-118">Personaliza os parâmetros de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="8d04d-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="8d04d-119">ipv6</span><span class="sxs-lookup"><span data-stu-id="8d04d-119">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="8d04d-120">Habilita o suporte a IPv6 (protocolo IP versão 6).</span><span class="sxs-lookup"><span data-stu-id="8d04d-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="8d04d-121">\<performanceCounter > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="8d04d-121">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="8d04d-122">Habilita contadores de desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="8d04d-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="8d04d-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="8d04d-123">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="8d04d-124">Configura conexões com recursos de rede.</span><span class="sxs-lookup"><span data-stu-id="8d04d-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="8d04d-125">socket</span><span class="sxs-lookup"><span data-stu-id="8d04d-125">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="8d04d-126">Especifica se as operações de soquete usam portas de conclusão.</span><span class="sxs-lookup"><span data-stu-id="8d04d-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="8d04d-127">\<Elemento de > webProxyScript (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="8d04d-127">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="8d04d-128">Configura as características do script usado para descobrir proxies da Web.</span><span class="sxs-lookup"><span data-stu-id="8d04d-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d04d-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8d04d-129">Parent Elements</span></span>  
  
|<span data-ttu-id="8d04d-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d04d-130">Element</span></span>|<span data-ttu-id="8d04d-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d04d-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d04d-132">system.net</span><span class="sxs-lookup"><span data-stu-id="8d04d-132">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="8d04d-133">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="8d04d-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d04d-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d04d-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8d04d-135">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="8d04d-135">Configuration Files</span></span>  
 <span data-ttu-id="8d04d-136">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8d04d-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d04d-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d04d-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="8d04d-138">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="8d04d-138">Network Settings Schema</span></span>](index.md)
