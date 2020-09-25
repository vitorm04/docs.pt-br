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
ms.openlocfilehash: c5fe0b9eccd1c429c0041fcfab06b0cc20a20aa2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167269"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="239b8-102">Elemento \<settings> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="239b8-102">\<settings> Element (Network Settings)</span></span>

<span data-ttu-id="239b8-103">Configura as opções de rede básicaspara o namespace <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="239b8-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="239b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="239b8-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="239b8-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="239b8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="239b8-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="239b8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="239b8-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="239b8-107">Attributes</span></span>  

 <span data-ttu-id="239b8-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="239b8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="239b8-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="239b8-109">Child Elements</span></span>  
  
|<span data-ttu-id="239b8-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="239b8-110">Element</span></span>|<span data-ttu-id="239b8-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="239b8-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="239b8-112">httpListener</span><span class="sxs-lookup"><span data-stu-id="239b8-112">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="239b8-113">Personaliza os parâmetros usados pela <xref:System.Net.HttpListener> classe.</span><span class="sxs-lookup"><span data-stu-id="239b8-113">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="239b8-114">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="239b8-114">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="239b8-115">Personaliza os parâmetros de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="239b8-115">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="239b8-116">protocolo</span><span class="sxs-lookup"><span data-stu-id="239b8-116">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="239b8-117">Habilita o suporte a IPv6 (protocolo IP versão 6).</span><span class="sxs-lookup"><span data-stu-id="239b8-117">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="239b8-118">\<performanceCounter> Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="239b8-118">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="239b8-119">Habilita contadores de desempenho de rede.</span><span class="sxs-lookup"><span data-stu-id="239b8-119">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="239b8-120">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="239b8-120">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="239b8-121">Configura conexões com recursos de rede.</span><span class="sxs-lookup"><span data-stu-id="239b8-121">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="239b8-122">SSA</span><span class="sxs-lookup"><span data-stu-id="239b8-122">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="239b8-123">Especifica se as operações de soquete usam portas de conclusão.</span><span class="sxs-lookup"><span data-stu-id="239b8-123">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="239b8-124">\<webProxyScript> Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="239b8-124">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="239b8-125">Configura as características do script usado para descobrir proxies da Web.</span><span class="sxs-lookup"><span data-stu-id="239b8-125">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="239b8-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="239b8-126">Parent Elements</span></span>  
  
|<span data-ttu-id="239b8-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="239b8-127">Element</span></span>|<span data-ttu-id="239b8-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="239b8-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="239b8-129">system.net</span><span class="sxs-lookup"><span data-stu-id="239b8-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="239b8-130">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="239b8-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="239b8-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="239b8-131">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="239b8-132">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="239b8-132">Configuration Files</span></span>  

 <span data-ttu-id="239b8-133">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="239b8-133">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239b8-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="239b8-134">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="239b8-135">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="239b8-135">Network Settings Schema</span></span>](index.md)
