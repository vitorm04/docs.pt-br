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
ms.openlocfilehash: 96cef2dff3156e49a93be818230c83370dab5264
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185855"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="d7b45-102">Elemento \<clear> para bypasslist (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="d7b45-102">\<clear> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="d7b45-103">Limpa a lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="d7b45-103">Clears the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="d7b45-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7b45-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7b45-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d7b45-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d7b45-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d7b45-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7b45-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d7b45-107">Attributes</span></span>  

 <span data-ttu-id="d7b45-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d7b45-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d7b45-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d7b45-109">Child Elements</span></span>  

 <span data-ttu-id="d7b45-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d7b45-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7b45-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d7b45-111">Parent Elements</span></span>  
  
|<span data-ttu-id="d7b45-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="d7b45-112">**Element**</span></span>|<span data-ttu-id="d7b45-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d7b45-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d7b45-114">bypasslist</span><span class="sxs-lookup"><span data-stu-id="d7b45-114">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="d7b45-115">Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="d7b45-115">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7b45-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7b45-116">Remarks</span></span>  

 <span data-ttu-id="d7b45-117">O `clear` elemento limpa todas as entradas da lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="d7b45-117">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d7b45-118">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="d7b45-118">Configuration Files</span></span>  

 <span data-ttu-id="d7b45-119">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d7b45-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7b45-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d7b45-120">Example</span></span>  

 <span data-ttu-id="d7b45-121">O exemplo a seguir limpa a lista de bypass e, em seguida, adiciona dois endereços à lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="d7b45-121">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="d7b45-122">O primeiro ignora o proxy para todos os servidores no domínio contoso.com; o segundo ignora o proxy para todos os servidores cujo endereço IP começa com 192,168.</span><span class="sxs-lookup"><span data-stu-id="d7b45-122">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d7b45-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="d7b45-123">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="d7b45-124">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="d7b45-124">Network Settings Schema</span></span>](index.md)
