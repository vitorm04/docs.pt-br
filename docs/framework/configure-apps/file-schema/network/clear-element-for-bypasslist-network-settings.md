---
title: Elemento <clear> para bypasslist (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: 2ad6b16370f600299439d2e810dfefa1b5fa3c06
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087540"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="1bc6f-102">\<limpar > elemento para BypassList (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="1bc6f-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="1bc6f-103">Limpa a lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="1bc6f-103">Clears the proxy bypass list.</span></span>  
  
<span data-ttu-id="1bc6f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1bc6f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1bc6f-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1bc6f-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="1bc6f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1bc6f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="1bc6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bypasslist >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1bc6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>\
<span data-ttu-id="1bc6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<desmarque >**</span><span class="sxs-lookup"><span data-stu-id="1bc6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1bc6f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1bc6f-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bc6f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1bc6f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1bc6f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1bc6f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bc6f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="1bc6f-112">Attributes</span></span>  
 <span data-ttu-id="1bc6f-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1bc6f-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1bc6f-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1bc6f-114">Child Elements</span></span>  
 <span data-ttu-id="1bc6f-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1bc6f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1bc6f-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1bc6f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1bc6f-117">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="1bc6f-117">**Element**</span></span>|<span data-ttu-id="1bc6f-118">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="1bc6f-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1bc6f-119">BypassList</span><span class="sxs-lookup"><span data-stu-id="1bc6f-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="1bc6f-120">Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="1bc6f-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bc6f-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="1bc6f-121">Remarks</span></span>  
 <span data-ttu-id="1bc6f-122">O elemento `clear` limpa todas as entradas da lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="1bc6f-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1bc6f-123">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="1bc6f-123">Configuration Files</span></span>  
 <span data-ttu-id="1bc6f-124">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="1bc6f-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bc6f-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1bc6f-125">Example</span></span>  
 <span data-ttu-id="1bc6f-126">O exemplo a seguir limpa a lista de bypass e, em seguida, adiciona dois endereços à lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="1bc6f-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="1bc6f-127">O primeiro ignora o proxy para todos os servidores no domínio contoso.com; o segundo ignora o proxy para todos os servidores cujo endereço IP começa com 192,168.</span><span class="sxs-lookup"><span data-stu-id="1bc6f-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="1bc6f-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bc6f-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="1bc6f-129">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="1bc6f-129">Network Settings Schema</span></span>](index.md)
