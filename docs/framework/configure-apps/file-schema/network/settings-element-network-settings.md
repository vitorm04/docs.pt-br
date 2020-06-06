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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089112"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="afbdc-102">Elemento \<settings> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="afbdc-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="afbdc-103">Configura as opções de rede básicaspara o namespace <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="afbdc-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="afbdc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="afbdc-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afbdc-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="afbdc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="afbdc-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="afbdc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afbdc-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="afbdc-107">Attributes</span></span>  
 <span data-ttu-id="afbdc-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="afbdc-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="afbdc-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="afbdc-109">Child Elements</span></span>  
  
|<span data-ttu-id="afbdc-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="afbdc-110">Element</span></span>|<span data-ttu-id="afbdc-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="afbdc-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afbdc-112">httpListener</span><span class="sxs-lookup"><span data-stu-id="afbdc-112">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="afbdc-113">Personaliza os parâmetros usados pela <xref:System.Net.HttpListener> classe.</span><span class="sxs-lookup"><span data-stu-id="afbdc-113">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="afbdc-114">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="afbdc-114">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="afbdc-115">Personaliza os parâmetros de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="afbdc-115">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="afbdc-116">protocolo</span><span class="sxs-lookup"><span data-stu-id="afbdc-116">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="afbdc-117">Habilita o suporte a IPv6 (protocolo IP versão 6).</span><span class="sxs-lookup"><span data-stu-id="afbdc-117">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="afbdc-118">\<performanceCounter>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="afbdc-118">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="afbdc-119">Habilita contadores de desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="afbdc-119">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="afbdc-120">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="afbdc-120">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="afbdc-121">Configura conexões com recursos de rede.</span><span class="sxs-lookup"><span data-stu-id="afbdc-121">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="afbdc-122">SSA</span><span class="sxs-lookup"><span data-stu-id="afbdc-122">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="afbdc-123">Especifica se as operações de soquete usam portas de conclusão.</span><span class="sxs-lookup"><span data-stu-id="afbdc-123">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="afbdc-124">\<webProxyScript>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="afbdc-124">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="afbdc-125">Configura as características do script usado para descobrir proxies da Web.</span><span class="sxs-lookup"><span data-stu-id="afbdc-125">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afbdc-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="afbdc-126">Parent Elements</span></span>  
  
|<span data-ttu-id="afbdc-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="afbdc-127">Element</span></span>|<span data-ttu-id="afbdc-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="afbdc-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afbdc-129">system.net</span><span class="sxs-lookup"><span data-stu-id="afbdc-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="afbdc-130">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="afbdc-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afbdc-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="afbdc-131">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="afbdc-132">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="afbdc-132">Configuration Files</span></span>  
 <span data-ttu-id="afbdc-133">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="afbdc-133">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afbdc-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="afbdc-134">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="afbdc-135">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="afbdc-135">Network Settings Schema</span></span>](index.md)
