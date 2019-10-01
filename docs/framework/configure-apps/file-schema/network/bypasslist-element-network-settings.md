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
ms.openlocfilehash: 1dda43be8c0e0c94bdf7b57b67aa4d403b547f97
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699551"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="1438e-102">\<bypasslist > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="1438e-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="1438e-103">Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="1438e-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
[<span data-ttu-id="1438e-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="1438e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="1438e-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1438e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="1438e-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1438e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="1438e-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<bypasslist >**</span><span class="sxs-lookup"><span data-stu-id="1438e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1438e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1438e-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1438e-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1438e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1438e-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1438e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1438e-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="1438e-111">Attributes</span></span>  
 <span data-ttu-id="1438e-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1438e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1438e-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1438e-113">Child Elements</span></span>  
  
|<span data-ttu-id="1438e-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="1438e-114">**Element**</span></span>|<span data-ttu-id="1438e-115">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="1438e-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1438e-116">add</span><span class="sxs-lookup"><span data-stu-id="1438e-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="1438e-117">Adiciona um endereço IP ou nome DNS à lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="1438e-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="1438e-118">clear</span><span class="sxs-lookup"><span data-stu-id="1438e-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="1438e-119">Limpa a lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="1438e-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="1438e-120">remove</span><span class="sxs-lookup"><span data-stu-id="1438e-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="1438e-121">Remove um endereço IP ou nome DNS da lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="1438e-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1438e-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1438e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1438e-123">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="1438e-123">**Element**</span></span>|<span data-ttu-id="1438e-124">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="1438e-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1438e-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="1438e-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="1438e-126">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="1438e-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1438e-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="1438e-127">Remarks</span></span>  
 <span data-ttu-id="1438e-128">A lista de bypass contém expressões regulares que descrevem URIs que <xref:System.Net.WebRequest> acessam diretamente em vez de por meio do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="1438e-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="1438e-129">Tome cuidado ao especificar uma expressão regular para este elemento.</span><span class="sxs-lookup"><span data-stu-id="1438e-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="1438e-130">A expressão regular "[a-z] + @no__t -0.contoso\\.com" corresponde a qualquer host no domínio contoso.com, mas também corresponde a qualquer host no domínio contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="1438e-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="1438e-131">Para corresponder apenas a um host no domínio contoso.com, use uma âncora ("$"): "[a-z] + @no__t -0.contoso\\.com $".</span><span class="sxs-lookup"><span data-stu-id="1438e-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="1438e-132">Para obter mais informações sobre expressões regulares, consulte. [.NET Framework expressões regulares](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1438e-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1438e-133">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="1438e-133">Configuration Files</span></span>  
 <span data-ttu-id="1438e-134">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="1438e-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1438e-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1438e-135">Example</span></span>  
 <span data-ttu-id="1438e-136">O exemplo a seguir adiciona dois endereços à lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="1438e-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="1438e-137">O primeiro ignora o proxy para todos os servidores no domínio contoso.com; o segundo ignora o proxy para todos os servidores cujos endereços IP começam com 192,168.</span><span class="sxs-lookup"><span data-stu-id="1438e-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1438e-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1438e-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="1438e-139">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="1438e-139">Network Settings Schema</span></span>](index.md)
