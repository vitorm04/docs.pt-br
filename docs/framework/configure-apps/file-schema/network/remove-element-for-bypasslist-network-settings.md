---
title: Elemento <remove> para bypasslist (configurações de rede)
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
ms.openlocfilehash: a04cca3e57af5cc422776c5b2444a140e86f98b9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354252"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="eb35a-102">\<Remover > elemento para bypasslist (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="eb35a-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="eb35a-103">Remove um endereço IP ou nome DNS da lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="eb35a-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

<span data-ttu-id="eb35a-104">\<configuration>\\</span><span class="sxs-lookup"><span data-stu-id="eb35a-104">\<configuration>\\</span></span>
<span data-ttu-id="eb35a-105">\<system.net>\\</span><span class="sxs-lookup"><span data-stu-id="eb35a-105">\<system.net>\\</span></span>
<span data-ttu-id="eb35a-106">\<defaultProxy>\\</span><span class="sxs-lookup"><span data-stu-id="eb35a-106">\<defaultProxy>\\</span></span>
<span data-ttu-id="eb35a-107">\<bypasslist>\\</span><span class="sxs-lookup"><span data-stu-id="eb35a-107">\<bypasslist>\\</span></span>
<span data-ttu-id="eb35a-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="eb35a-108">\<remove></span></span>

## <a name="syntax"></a><span data-ttu-id="eb35a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb35a-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eb35a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eb35a-110">Attributes and Elements</span></span>

<span data-ttu-id="eb35a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="eb35a-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="eb35a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="eb35a-112">Attributes</span></span>

|<span data-ttu-id="eb35a-113">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="eb35a-113">**Attribute**</span></span>|<span data-ttu-id="eb35a-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="eb35a-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="eb35a-115">Uma expressão regular que descreve um endereço IP ou nome DNS.</span><span class="sxs-lookup"><span data-stu-id="eb35a-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="eb35a-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eb35a-116">Child Elements</span></span>

<span data-ttu-id="eb35a-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="eb35a-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="eb35a-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eb35a-118">Parent Elements</span></span>

|<span data-ttu-id="eb35a-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="eb35a-119">**Element**</span></span>|<span data-ttu-id="eb35a-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="eb35a-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="eb35a-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="eb35a-121">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="eb35a-122">Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="eb35a-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eb35a-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb35a-123">Remarks</span></span>

<span data-ttu-id="eb35a-124">O `remove` elemento remove as expressões regulares que descrevem endereços IP ou nomes de servidores DNS da lista de endereços que ignora um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="eb35a-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="eb35a-125">Os endereços foram definidos anteriormente no arquivo de configuração ou em um nível mais alto na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="eb35a-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="eb35a-126">O valor para o `address` atributo deve ser uma expressão regular que descreve um conjunto de endereços IP ou nomes de host.</span><span class="sxs-lookup"><span data-stu-id="eb35a-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="eb35a-127">Para obter mais informações sobre expressões regulares, consulte. [Expressões regulares do .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="eb35a-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="eb35a-128">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="eb35a-128">Configuration Files</span></span>

<span data-ttu-id="eb35a-129">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="eb35a-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="eb35a-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb35a-130">Example</span></span>

<span data-ttu-id="eb35a-131">O exemplo a seguir remove qualquer definição anterior para o domínio adventure-works.com e, em seguida, adiciona o domínio contoso.com à lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="eb35a-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eb35a-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb35a-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="eb35a-133">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="eb35a-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
