---
title: Elemento <remove> para bypasslist (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 99c18bd5b779845d52831b4a9591eaf4d5e5530b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920956"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="6108f-102">\<remover o elemento > para BypassList (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="6108f-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="6108f-103">Remove um endereço IP ou nome DNS da lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="6108f-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

<span data-ttu-id="6108f-104">\<> de configuração </span><span class="sxs-lookup"><span data-stu-id="6108f-104">\<configuration></span></span>\
<span data-ttu-id="6108f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="6108f-105">\<system.net></span></span>\
<span data-ttu-id="6108f-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="6108f-106">\<defaultProxy></span></span>\
<span data-ttu-id="6108f-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="6108f-107">\<bypasslist></span></span>\
<span data-ttu-id="6108f-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="6108f-108">\<remove></span></span>

## <a name="syntax"></a><span data-ttu-id="6108f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6108f-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6108f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6108f-110">Attributes and Elements</span></span>

<span data-ttu-id="6108f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6108f-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6108f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="6108f-112">Attributes</span></span>

|<span data-ttu-id="6108f-113">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="6108f-113">**Attribute**</span></span>|<span data-ttu-id="6108f-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="6108f-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="6108f-115">Uma expressão regular que descreve um endereço IP ou nome DNS.</span><span class="sxs-lookup"><span data-stu-id="6108f-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6108f-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6108f-116">Child Elements</span></span>

<span data-ttu-id="6108f-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6108f-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6108f-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6108f-118">Parent Elements</span></span>

|<span data-ttu-id="6108f-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="6108f-119">**Element**</span></span>|<span data-ttu-id="6108f-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="6108f-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="6108f-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="6108f-121">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="6108f-122">Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="6108f-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6108f-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="6108f-123">Remarks</span></span>

<span data-ttu-id="6108f-124">O `remove` elemento remove expressões regulares que descrevem endereços IP ou nomes de servidores DNS da lista de endereços que ignoram um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="6108f-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="6108f-125">Os endereços foram definidos anteriormente no arquivo de configuração ou em um nível superior na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="6108f-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="6108f-126">O valor do `address` atributo deve ser uma expressão regular que descreve um conjunto de endereços IP ou nomes de host.</span><span class="sxs-lookup"><span data-stu-id="6108f-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="6108f-127">Para obter mais informações sobre expressões regulares, consulte. [.NET Framework expressões regulares](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="6108f-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="6108f-128">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="6108f-128">Configuration Files</span></span>

<span data-ttu-id="6108f-129">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="6108f-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="6108f-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6108f-130">Example</span></span>

<span data-ttu-id="6108f-131">O exemplo a seguir remove qualquer definição anterior para o domínio adventure-works.com e, em seguida, adiciona o domínio contoso.com à lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="6108f-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="6108f-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6108f-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="6108f-133">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="6108f-133">Network Settings Schema</span></span>](index.md)
