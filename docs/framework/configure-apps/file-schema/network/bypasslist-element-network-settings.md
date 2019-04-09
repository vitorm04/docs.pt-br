---
title: <bypasslist> (Configurações de rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: d3d986dae478f49504dae21b9f39574b7887b4d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202216"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="4edd3-102">\<bypasslist > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="4edd3-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="4edd3-103">Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="4edd3-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
 <span data-ttu-id="4edd3-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4edd3-104">\<configuration></span></span>  
<span data-ttu-id="4edd3-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4edd3-105">\<system.net></span></span>  
<span data-ttu-id="4edd3-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="4edd3-106">\<defaultProxy></span></span>  
<span data-ttu-id="4edd3-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="4edd3-107">\<bypasslist></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4edd3-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4edd3-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4edd3-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4edd3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4edd3-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4edd3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4edd3-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="4edd3-111">Attributes</span></span>  
 <span data-ttu-id="4edd3-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4edd3-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4edd3-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4edd3-113">Child Elements</span></span>  
  
|**<span data-ttu-id="4edd3-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="4edd3-114">Element</span></span>**|**<span data-ttu-id="4edd3-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="4edd3-115">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="4edd3-116">adicionar</span><span class="sxs-lookup"><span data-stu-id="4edd3-116">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="4edd3-117">Adiciona um endereço IP ou nome DNS à lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="4edd3-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="4edd3-118">clear</span><span class="sxs-lookup"><span data-stu-id="4edd3-118">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="4edd3-119">Limpa a lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="4edd3-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="4edd3-120">remove</span><span class="sxs-lookup"><span data-stu-id="4edd3-120">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="4edd3-121">Remove um endereço IP ou nome DNS da lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="4edd3-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4edd3-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4edd3-122">Parent Elements</span></span>  
  
|**<span data-ttu-id="4edd3-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="4edd3-123">Element</span></span>**|**<span data-ttu-id="4edd3-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="4edd3-124">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="4edd3-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="4edd3-125">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="4edd3-126">Configura o servidor de proxy de protocolo HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="4edd3-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4edd3-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="4edd3-127">Remarks</span></span>  
 <span data-ttu-id="4edd3-128">A lista de bypass contém expressões regulares que descrevem os URIs que <xref:System.Net.WebRequest> instâncias acessar diretamente em vez de por meio do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="4edd3-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="4edd3-129">Você deve usar o cuidado ao especificar uma expressão regular para este elemento.</span><span class="sxs-lookup"><span data-stu-id="4edd3-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="4edd3-130">A expressão regular "[a-z] +\\.contoso\\.com" corresponde a qualquer host no domínio contoso.com, mas também corresponde a qualquer host no domínio contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="4edd3-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="4edd3-131">Para corresponder a um host no domínio contoso.com, use uma âncora ("$"): "[a-z] +\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="4edd3-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="4edd3-132">Para obter mais informações sobre expressões regulares, consulte. [Expressões regulares do .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4edd3-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4edd3-133">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="4edd3-133">Configuration Files</span></span>  
 <span data-ttu-id="4edd3-134">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="4edd3-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4edd3-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4edd3-135">Example</span></span>  
 <span data-ttu-id="4edd3-136">O exemplo a seguir adiciona dois endereços à lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="4edd3-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="4edd3-137">A primeira ignora o proxy para todos os servidores no domínio contoso.com; o segundo ignora o proxy para todos os servidores cujos endereços IP começam com 192.168.</span><span class="sxs-lookup"><span data-stu-id="4edd3-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4edd3-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4edd3-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="4edd3-139">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="4edd3-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
