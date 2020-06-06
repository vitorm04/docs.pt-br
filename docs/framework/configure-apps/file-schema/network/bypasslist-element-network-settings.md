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
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154940"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="c5c9d-102">Elemento \<bypasslist> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="c5c9d-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="c5c9d-103">Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="c5c9d-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a><span data-ttu-id="c5c9d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5c9d-104">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5c9d-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c5c9d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c5c9d-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c5c9d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5c9d-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c5c9d-107">Attributes</span></span>  
 <span data-ttu-id="c5c9d-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c5c9d-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c5c9d-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c5c9d-109">Child Elements</span></span>  
  
|<span data-ttu-id="c5c9d-110">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="c5c9d-110">**Element**</span></span>|<span data-ttu-id="c5c9d-111">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c5c9d-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c5c9d-112">adicionar</span><span class="sxs-lookup"><span data-stu-id="c5c9d-112">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="c5c9d-113">Adiciona um endereço IP ou nome DNS à lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="c5c9d-113">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="c5c9d-114">formatação</span><span class="sxs-lookup"><span data-stu-id="c5c9d-114">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="c5c9d-115">Limpa a lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="c5c9d-115">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="c5c9d-116">remove</span><span class="sxs-lookup"><span data-stu-id="c5c9d-116">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="c5c9d-117">Remove um endereço IP ou nome DNS da lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="c5c9d-117">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5c9d-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c5c9d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c5c9d-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="c5c9d-119">**Element**</span></span>|<span data-ttu-id="c5c9d-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c5c9d-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c5c9d-121">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="c5c9d-121">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="c5c9d-122">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="c5c9d-122">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5c9d-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5c9d-123">Remarks</span></span>  
 <span data-ttu-id="c5c9d-124">A lista de bypass contém expressões regulares que descrevem URIs que as <xref:System.Net.WebRequest> instâncias acessam diretamente em vez de por meio do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="c5c9d-124">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="c5c9d-125">Tome cuidado ao especificar uma expressão regular para este elemento.</span><span class="sxs-lookup"><span data-stu-id="c5c9d-125">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="c5c9d-126">A expressão regular "[a-z] + \\ . contoso \\ . com" corresponde a qualquer host no domínio contoso.com, mas também corresponde a qualquer host no domínio contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="c5c9d-126">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="c5c9d-127">Para corresponder apenas a um host no domínio contoso.com, use uma âncora ("$"): "[a-z] + \\ . contoso \\ . com $".</span><span class="sxs-lookup"><span data-stu-id="c5c9d-127">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="c5c9d-128">Para obter mais informações sobre expressões regulares, consulte. [.NET Framework expressões regulares](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c5c9d-128">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c5c9d-129">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="c5c9d-129">Configuration Files</span></span>  
 <span data-ttu-id="c5c9d-130">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="c5c9d-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5c9d-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5c9d-131">Example</span></span>  
 <span data-ttu-id="c5c9d-132">O exemplo a seguir adiciona dois endereços à lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="c5c9d-132">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="c5c9d-133">O primeiro ignora o proxy para todos os servidores no domínio contoso.com; o segundo ignora o proxy para todos os servidores cujos endereços IP começam com 192,168.</span><span class="sxs-lookup"><span data-stu-id="c5c9d-133">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5c9d-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="c5c9d-134">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="c5c9d-135">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="c5c9d-135">Network Settings Schema</span></span>](index.md)
