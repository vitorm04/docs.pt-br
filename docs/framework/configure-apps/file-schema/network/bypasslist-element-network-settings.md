---
title: Elemento <bypasslist> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 7a6c1282c9ca8381d2dbb21ffdc82f95732c42b3
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087517"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="6859f-102">\<elemento de > BypassList (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="6859f-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="6859f-103">Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="6859f-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

<span data-ttu-id="6859f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6859f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6859f-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6859f-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="6859f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6859f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="6859f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bypasslist >**</span><span class="sxs-lookup"><span data-stu-id="6859f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6859f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6859f-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6859f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6859f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6859f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6859f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6859f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="6859f-111">Attributes</span></span>  
 <span data-ttu-id="6859f-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6859f-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6859f-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6859f-113">Child Elements</span></span>  
  
|<span data-ttu-id="6859f-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="6859f-114">**Element**</span></span>|<span data-ttu-id="6859f-115">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="6859f-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6859f-116">add</span><span class="sxs-lookup"><span data-stu-id="6859f-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="6859f-117">Adiciona um endereço IP ou nome DNS à lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="6859f-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="6859f-118">clear</span><span class="sxs-lookup"><span data-stu-id="6859f-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="6859f-119">Limpa a lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="6859f-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="6859f-120">remove</span><span class="sxs-lookup"><span data-stu-id="6859f-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="6859f-121">Remove um endereço IP ou nome DNS da lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="6859f-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6859f-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6859f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6859f-123">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="6859f-123">**Element**</span></span>|<span data-ttu-id="6859f-124">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="6859f-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6859f-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="6859f-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="6859f-126">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="6859f-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6859f-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="6859f-127">Remarks</span></span>  
 <span data-ttu-id="6859f-128">A lista de bypass contém expressões regulares que descrevem URIs que <xref:System.Net.WebRequest> instâncias acessam diretamente em vez de por meio do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="6859f-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="6859f-129">Tome cuidado ao especificar uma expressão regular para este elemento.</span><span class="sxs-lookup"><span data-stu-id="6859f-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="6859f-130">A expressão regular "[a-z] +\\. contoso\\. com" corresponde a qualquer host no domínio contoso.com, mas também corresponde a qualquer host no domínio contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="6859f-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="6859f-131">Para corresponder apenas a um host no domínio contoso.com, use uma âncora ("$"): "[a-z] +\\. contoso\\. com $".</span><span class="sxs-lookup"><span data-stu-id="6859f-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="6859f-132">Para obter mais informações sobre expressões regulares, consulte. [.NET Framework expressões regulares](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="6859f-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6859f-133">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="6859f-133">Configuration Files</span></span>  
 <span data-ttu-id="6859f-134">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="6859f-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6859f-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6859f-135">Example</span></span>  
 <span data-ttu-id="6859f-136">O exemplo a seguir adiciona dois endereços à lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="6859f-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="6859f-137">O primeiro ignora o proxy para todos os servidores no domínio contoso.com; o segundo ignora o proxy para todos os servidores cujos endereços IP começam com 192,168.</span><span class="sxs-lookup"><span data-stu-id="6859f-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6859f-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6859f-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="6859f-139">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="6859f-139">Network Settings Schema</span></span>](index.md)
