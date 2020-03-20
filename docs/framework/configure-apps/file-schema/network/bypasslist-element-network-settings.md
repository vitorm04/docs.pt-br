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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154940"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="22519-102">\<elemento> de bypasslist (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="22519-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="22519-103">Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="22519-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

<span data-ttu-id="22519-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="22519-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="22519-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="22519-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="22519-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de proxy padrão**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="22519-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="22519-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de bypasslist**</span><span class="sxs-lookup"><span data-stu-id="22519-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>

## <a name="syntax"></a><span data-ttu-id="22519-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22519-108">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22519-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="22519-109">Attributes and Elements</span></span>  
 <span data-ttu-id="22519-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="22519-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22519-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="22519-111">Attributes</span></span>  
 <span data-ttu-id="22519-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="22519-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="22519-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="22519-113">Child Elements</span></span>  
  
|<span data-ttu-id="22519-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="22519-114">**Element**</span></span>|<span data-ttu-id="22519-115">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="22519-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="22519-116">adicionar</span><span class="sxs-lookup"><span data-stu-id="22519-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="22519-117">Adiciona um endereço IP ou nome DNS à lista de desvio proxy.</span><span class="sxs-lookup"><span data-stu-id="22519-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="22519-118">Claro</span><span class="sxs-lookup"><span data-stu-id="22519-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="22519-119">Limpa a lista de desvios.</span><span class="sxs-lookup"><span data-stu-id="22519-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="22519-120">remover</span><span class="sxs-lookup"><span data-stu-id="22519-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="22519-121">Remove um endereço IP ou nome DNS da lista de desvio proxy.</span><span class="sxs-lookup"><span data-stu-id="22519-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="22519-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="22519-122">Parent Elements</span></span>  
  
|<span data-ttu-id="22519-123">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="22519-123">**Element**</span></span>|<span data-ttu-id="22519-124">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="22519-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="22519-125">Defaultproxy</span><span class="sxs-lookup"><span data-stu-id="22519-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="22519-126">Configura o servidor proxy Hypertext Transfer Protocol (HTTP).</span><span class="sxs-lookup"><span data-stu-id="22519-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22519-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="22519-127">Remarks</span></span>  
 <span data-ttu-id="22519-128">A lista de bypass contém expressões <xref:System.Net.WebRequest> regulares que descrevem URIs que as instâncias acessam diretamente em vez de através do servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="22519-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="22519-129">Você deve ter cuidado ao especificar uma expressão regular para este elemento.</span><span class="sxs-lookup"><span data-stu-id="22519-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="22519-130">A expressão regular\\"[a-z]+\\.contoso .com" corresponde a qualquer host no domínio contoso.com, mas também corresponde a qualquer host no domínio contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="22519-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="22519-131">Para combinar apenas um host no domínio contoso.com, use uma âncora ("$"): "[a-z]+\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="22519-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="22519-132">Para obter mais informações sobre expressões regulares, consulte . [.NET Framework Expressões Regulares](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="22519-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="22519-133">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="22519-133">Configuration Files</span></span>  
 <span data-ttu-id="22519-134">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="22519-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22519-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22519-135">Example</span></span>  
 <span data-ttu-id="22519-136">O exemplo a seguir adiciona dois endereços à lista de desvios.</span><span class="sxs-lookup"><span data-stu-id="22519-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="22519-137">O primeiro ignora o proxy para todos os servidores do domínio contoso.com; o segundo ignora o proxy para todos os servidores cujos endereços IP começam com 192.168.</span><span class="sxs-lookup"><span data-stu-id="22519-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22519-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="22519-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="22519-139">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="22519-139">Network Settings Schema</span></span>](index.md)
