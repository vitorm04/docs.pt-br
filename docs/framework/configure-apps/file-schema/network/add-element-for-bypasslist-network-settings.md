---
title: '&lt;Adicionar&gt; elemento para bypasslist (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 3be617d53ba87c35ae44f143da15a6b647eaa0d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680774"
---
# <a name="ltaddgt-element-for-bypasslist-network-settings"></a><span data-ttu-id="00cd5-102">&lt;Adicionar&gt; elemento para bypasslist (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="00cd5-102">&lt;add&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="00cd5-103">Adiciona um endereço IP ou nome DNS à lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="00cd5-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
 <span data-ttu-id="00cd5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="00cd5-104">\<configuration></span></span>  
<span data-ttu-id="00cd5-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="00cd5-105">\<system.net></span></span>  
<span data-ttu-id="00cd5-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="00cd5-106">\<defaultProxy></span></span>  
<span data-ttu-id="00cd5-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="00cd5-107">\<bypasslist></span></span>  
<span data-ttu-id="00cd5-108">\<add></span><span class="sxs-lookup"><span data-stu-id="00cd5-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00cd5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00cd5-109">Syntax</span></span>  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00cd5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="00cd5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="00cd5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="00cd5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00cd5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="00cd5-112">Attributes</span></span>  
  
|<span data-ttu-id="00cd5-113">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="00cd5-113">**Attribute**</span></span>|<span data-ttu-id="00cd5-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="00cd5-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="00cd5-115">**address**</span><span class="sxs-lookup"><span data-stu-id="00cd5-115">**address**</span></span>|<span data-ttu-id="00cd5-116">Uma expressão regular que descreve um endereço IP ou nome DNS.</span><span class="sxs-lookup"><span data-stu-id="00cd5-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00cd5-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="00cd5-117">Child Elements</span></span>  
 <span data-ttu-id="00cd5-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="00cd5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00cd5-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="00cd5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="00cd5-120">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="00cd5-120">**Element**</span></span>|<span data-ttu-id="00cd5-121">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="00cd5-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="00cd5-122">bypasslist</span><span class="sxs-lookup"><span data-stu-id="00cd5-122">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="00cd5-123">Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="00cd5-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00cd5-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="00cd5-124">Remarks</span></span>  
 <span data-ttu-id="00cd5-125">O `add` elemento insere expressões regulares que descrevem endereços IP ou nomes de servidores DNS à lista de endereços que ignora um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="00cd5-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="00cd5-126">O valor da `address` atributo deve ser uma expressão regular que descreve um conjunto de endereços IP ou nomes de host.</span><span class="sxs-lookup"><span data-stu-id="00cd5-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="00cd5-127">Você deve usar o cuidado ao especificar uma expressão regular para este elemento.</span><span class="sxs-lookup"><span data-stu-id="00cd5-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="00cd5-128">A expressão regular "[a-z] +\\.contoso\\.com" corresponde a qualquer host no domínio contoso.com, mas também corresponde a qualquer host no domínio contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="00cd5-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="00cd5-129">Para corresponder a um host no domínio contoso.com, use uma âncora ("$"): "[a-z] +\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="00cd5-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="00cd5-130">Para obter mais informações sobre expressões regulares, consulte. [Expressões regulares do .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="00cd5-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="00cd5-131">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="00cd5-131">Configuration Files</span></span>  
 <span data-ttu-id="00cd5-132">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="00cd5-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="00cd5-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00cd5-133">Example</span></span>  
 <span data-ttu-id="00cd5-134">O exemplo a seguir adiciona dois endereços à lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="00cd5-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="00cd5-135">A primeira ignora o proxy para todos os servidores no domínio contoso.com; o segundo ignora o proxy para todos os servidores cujo endereço IP começa com 192.168.</span><span class="sxs-lookup"><span data-stu-id="00cd5-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="00cd5-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00cd5-136">See also</span></span>
- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="00cd5-137">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="00cd5-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
