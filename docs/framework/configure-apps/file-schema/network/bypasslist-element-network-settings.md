---
title: "&lt;bypasslist&gt; elemento (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 20e3676e69357dc73433876275cb2737ee235552
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbypasslistgt-element-network-settings"></a><span data-ttu-id="aeec7-102">&lt;bypasslist&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="aeec7-102">&lt;bypasslist&gt; Element (Network Settings)</span></span>
<span data-ttu-id="aeec7-103">Fornece um conjunto de expressões regulares que descrevem os endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="aeec7-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
 <span data-ttu-id="aeec7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="aeec7-104">\<configuration></span></span>  
<span data-ttu-id="aeec7-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="aeec7-105">\<system.net></span></span>  
<span data-ttu-id="aeec7-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="aeec7-106">\<defaultProxy></span></span>  
<span data-ttu-id="aeec7-107">\<bypasslist ></span><span class="sxs-lookup"><span data-stu-id="aeec7-107">\<bypasslist></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeec7-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aeec7-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aeec7-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="aeec7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="aeec7-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="aeec7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aeec7-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="aeec7-111">Attributes</span></span>  
 <span data-ttu-id="aeec7-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="aeec7-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aeec7-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="aeec7-113">Child Elements</span></span>  
  
|<span data-ttu-id="aeec7-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="aeec7-114">**Element**</span></span>|<span data-ttu-id="aeec7-115">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="aeec7-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="aeec7-116">add</span><span class="sxs-lookup"><span data-stu-id="aeec7-116">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="aeec7-117">Adiciona um endereço IP ou nome DNS para a lista de proxies.</span><span class="sxs-lookup"><span data-stu-id="aeec7-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="aeec7-118">clear</span><span class="sxs-lookup"><span data-stu-id="aeec7-118">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="aeec7-119">Limpa a lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="aeec7-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="aeec7-120">remove</span><span class="sxs-lookup"><span data-stu-id="aeec7-120">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="aeec7-121">Remove a lista de proxies um endereço IP ou nome DNS.</span><span class="sxs-lookup"><span data-stu-id="aeec7-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aeec7-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="aeec7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="aeec7-123">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="aeec7-123">**Element**</span></span>|<span data-ttu-id="aeec7-124">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="aeec7-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="aeec7-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="aeec7-125">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="aeec7-126">Configura o servidor de proxy do protocolo HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="aeec7-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeec7-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="aeec7-127">Remarks</span></span>  
 <span data-ttu-id="aeec7-128">A lista de bypass contém expressões regulares que descrevem os URIs que <xref:System.Net.WebRequest> instâncias acessar diretamente em vez de por meio do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="aeec7-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="aeec7-129">Você deve ter cuidado ao especificar uma expressão regular para este elemento.</span><span class="sxs-lookup"><span data-stu-id="aeec7-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="aeec7-130">A expressão regular "[a-z] +\\.contoso\\.com" corresponde a qualquer host no domínio contoso.com, mas também corresponde a qualquer host no domínio contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="aeec7-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="aeec7-131">Para corresponder a um host no domínio contoso.com, use uma âncora ("$"): "[a-z] +\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="aeec7-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="aeec7-132">Para obter mais informações sobre expressões regulares, consulte. [Expressões regulares do .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="aeec7-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="aeec7-133">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="aeec7-133">Configuration Files</span></span>  
 <span data-ttu-id="aeec7-134">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="aeec7-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeec7-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aeec7-135">Example</span></span>  
 <span data-ttu-id="aeec7-136">O exemplo a seguir adiciona dois endereços à lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="aeec7-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="aeec7-137">O primeiro ignora o proxy para todos os servidores no domínio contoso.com; o segundo ignora o proxy para todos os servidores cujos endereços IP começam com 192.168.</span><span class="sxs-lookup"><span data-stu-id="aeec7-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aeec7-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aeec7-138">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="aeec7-139">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="aeec7-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
