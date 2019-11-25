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
ms.openlocfilehash: d510c445c585a36005ed415b14188efc4be03984
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089112"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="8a4fd-102">\<configurações de > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="8a4fd-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="8a4fd-103">Configura as opções de rede básicaspara o namespace <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8a4fd-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

<span data-ttu-id="8a4fd-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8a4fd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8a4fd-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8a4fd-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="8a4fd-106">&nbsp;&nbsp;&nbsp;&nbsp;**configurações**\<</span><span class="sxs-lookup"><span data-stu-id="8a4fd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8a4fd-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a4fd-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a4fd-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8a4fd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8a4fd-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8a4fd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a4fd-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8a4fd-110">Attributes</span></span>  
 <span data-ttu-id="8a4fd-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8a4fd-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8a4fd-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8a4fd-112">Child Elements</span></span>  
  
|<span data-ttu-id="8a4fd-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="8a4fd-113">Element</span></span>|<span data-ttu-id="8a4fd-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a4fd-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a4fd-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="8a4fd-115">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="8a4fd-116">Personaliza os parâmetros usados pela classe <xref:System.Net.HttpListener>.</span><span class="sxs-lookup"><span data-stu-id="8a4fd-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="8a4fd-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="8a4fd-117">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="8a4fd-118">Personaliza os parâmetros de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="8a4fd-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="8a4fd-119">protocolo</span><span class="sxs-lookup"><span data-stu-id="8a4fd-119">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="8a4fd-120">Habilita o suporte a IPv6 (protocolo IP versão 6).</span><span class="sxs-lookup"><span data-stu-id="8a4fd-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="8a4fd-121">Elemento \<performanceCounter > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="8a4fd-121">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="8a4fd-122">Habilita contadores de desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="8a4fd-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="8a4fd-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="8a4fd-123">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="8a4fd-124">Configura conexões com recursos de rede.</span><span class="sxs-lookup"><span data-stu-id="8a4fd-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="8a4fd-125">SSA</span><span class="sxs-lookup"><span data-stu-id="8a4fd-125">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="8a4fd-126">Especifica se as operações de soquete usam portas de conclusão.</span><span class="sxs-lookup"><span data-stu-id="8a4fd-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="8a4fd-127">\<elemento de > webProxyScript (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="8a4fd-127">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="8a4fd-128">Configura as características do script usado para descobrir proxies da Web.</span><span class="sxs-lookup"><span data-stu-id="8a4fd-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8a4fd-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8a4fd-129">Parent Elements</span></span>  
  
|<span data-ttu-id="8a4fd-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="8a4fd-130">Element</span></span>|<span data-ttu-id="8a4fd-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a4fd-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a4fd-132">system.net</span><span class="sxs-lookup"><span data-stu-id="8a4fd-132">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="8a4fd-133">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="8a4fd-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a4fd-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a4fd-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8a4fd-135">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="8a4fd-135">Configuration Files</span></span>  
 <span data-ttu-id="8a4fd-136">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8a4fd-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a4fd-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a4fd-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="8a4fd-138">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="8a4fd-138">Network Settings Schema</span></span>](index.md)
