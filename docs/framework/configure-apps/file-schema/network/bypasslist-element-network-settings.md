---
title: Elemento <bypasslist> (Configurações de Rede)
description: O <bypasslist> elemento de configurações de rede fornece um conjunto de expressões regulares que descrevem os endereços que não usam um proxy no .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 58cdcf046b2a5a292493c5704739b22aa4ec4f17
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178405"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="fe6fa-103">Elemento \<bypasslist> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="fe6fa-103">\<bypasslist> Element (Network Settings)</span></span>

<span data-ttu-id="fe6fa-104">Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="fe6fa-104">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a><span data-ttu-id="fe6fa-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe6fa-105">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe6fa-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fe6fa-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fe6fa-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fe6fa-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe6fa-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="fe6fa-108">Attributes</span></span>  

 <span data-ttu-id="fe6fa-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fe6fa-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fe6fa-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fe6fa-110">Child Elements</span></span>  
  
|<span data-ttu-id="fe6fa-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="fe6fa-111">**Element**</span></span>|<span data-ttu-id="fe6fa-112">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="fe6fa-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fe6fa-113">add</span><span class="sxs-lookup"><span data-stu-id="fe6fa-113">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="fe6fa-114">Adiciona um endereço IP ou nome DNS à lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="fe6fa-114">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="fe6fa-115">clear</span><span class="sxs-lookup"><span data-stu-id="fe6fa-115">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="fe6fa-116">Limpa a lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="fe6fa-116">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="fe6fa-117">remove</span><span class="sxs-lookup"><span data-stu-id="fe6fa-117">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="fe6fa-118">Remove um endereço IP ou nome DNS da lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="fe6fa-118">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe6fa-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fe6fa-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fe6fa-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="fe6fa-120">**Element**</span></span>|<span data-ttu-id="fe6fa-121">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="fe6fa-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fe6fa-122">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="fe6fa-122">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="fe6fa-123">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="fe6fa-123">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe6fa-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe6fa-124">Remarks</span></span>  

 <span data-ttu-id="fe6fa-125">A lista de bypass contém expressões regulares que descrevem URIs que as <xref:System.Net.WebRequest> instâncias acessam diretamente em vez de por meio do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="fe6fa-125">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="fe6fa-126">Tome cuidado ao especificar uma expressão regular para este elemento.</span><span class="sxs-lookup"><span data-stu-id="fe6fa-126">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="fe6fa-127">A expressão regular "[a-z] + \\ . contoso \\ . com" corresponde a qualquer host no domínio contoso.com, mas também corresponde a qualquer host no domínio contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="fe6fa-127">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="fe6fa-128">Para corresponder apenas a um host no domínio contoso.com, use uma âncora ("$"): "[a-z] + \\ . contoso \\ . com $".</span><span class="sxs-lookup"><span data-stu-id="fe6fa-128">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="fe6fa-129">Para obter mais informações sobre expressões regulares, consulte. [.NET Framework expressões regulares](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="fe6fa-129">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fe6fa-130">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="fe6fa-130">Configuration Files</span></span>  

 <span data-ttu-id="fe6fa-131">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="fe6fa-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe6fa-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fe6fa-132">Example</span></span>  

 <span data-ttu-id="fe6fa-133">O exemplo a seguir adiciona dois endereços à lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="fe6fa-133">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="fe6fa-134">O primeiro ignora o proxy para todos os servidores no domínio contoso.com; o segundo ignora o proxy para todos os servidores cujos endereços IP começam com 192,168.</span><span class="sxs-lookup"><span data-stu-id="fe6fa-134">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe6fa-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="fe6fa-135">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="fe6fa-136">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="fe6fa-136">Network Settings Schema</span></span>](index.md)
