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
ms.openlocfilehash: 97b49a8a520d6a4f72945366874991d2deb18710
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697900"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="0a7ce-102">Elemento \<remove> para bypasslist (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="0a7ce-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="0a7ce-103">Remove um endereço IP ou nome DNS da lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="0a7ce-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  

## <a name="syntax"></a><span data-ttu-id="0a7ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a7ce-104">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0a7ce-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0a7ce-105">Attributes and Elements</span></span>

<span data-ttu-id="0a7ce-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0a7ce-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0a7ce-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="0a7ce-107">Attributes</span></span>

|<span data-ttu-id="0a7ce-108">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="0a7ce-108">**Attribute**</span></span>|<span data-ttu-id="0a7ce-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="0a7ce-109">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="0a7ce-110">Uma expressão regular que descreve um endereço IP ou nome DNS.</span><span class="sxs-lookup"><span data-stu-id="0a7ce-110">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0a7ce-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0a7ce-111">Child Elements</span></span>

<span data-ttu-id="0a7ce-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0a7ce-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0a7ce-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0a7ce-113">Parent Elements</span></span>

|<span data-ttu-id="0a7ce-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="0a7ce-114">**Element**</span></span>|<span data-ttu-id="0a7ce-115">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="0a7ce-115">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="0a7ce-116">bypasslist</span><span class="sxs-lookup"><span data-stu-id="0a7ce-116">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="0a7ce-117">Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="0a7ce-117">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0a7ce-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="0a7ce-118">Remarks</span></span>

<span data-ttu-id="0a7ce-119">O `remove` elemento remove expressões regulares que descrevem endereços IP ou nomes de servidores DNS da lista de endereços que ignoram um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="0a7ce-119">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="0a7ce-120">Os endereços foram definidos anteriormente no arquivo de configuração ou em um nível superior na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="0a7ce-120">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="0a7ce-121">O valor do `address` atributo deve ser uma expressão regular que descreve um conjunto de endereços IP ou nomes de host.</span><span class="sxs-lookup"><span data-stu-id="0a7ce-121">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="0a7ce-122">Para obter mais informações sobre expressões regulares, consulte. [.NET Framework expressões regulares](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0a7ce-122">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="0a7ce-123">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="0a7ce-123">Configuration Files</span></span>

<span data-ttu-id="0a7ce-124">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="0a7ce-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="0a7ce-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0a7ce-125">Example</span></span>

<span data-ttu-id="0a7ce-126">O exemplo a seguir remove qualquer definição anterior para o domínio adventure-works.com e, em seguida, adiciona o domínio contoso.com à lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="0a7ce-126">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0a7ce-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="0a7ce-127">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="0a7ce-128">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="0a7ce-128">Network Settings Schema</span></span>](index.md)
