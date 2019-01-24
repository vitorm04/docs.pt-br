---
title: '&lt;Limpar&gt; elemento para bypasslist (configurações de rede)'
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
ms.openlocfilehash: 840833f2752115cb5f5639a25daf05bcbff3d452
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720909"
---
# <a name="ltcleargt-element-for-bypasslist-network-settings"></a><span data-ttu-id="9eda5-102">&lt;Limpar&gt; elemento para bypasslist (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="9eda5-102">&lt;clear&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="9eda5-103">Limpa a lista de bypass de proxy.</span><span class="sxs-lookup"><span data-stu-id="9eda5-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="9eda5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9eda5-104">\<configuration></span></span>  
<span data-ttu-id="9eda5-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="9eda5-105">\<system.net></span></span>  
<span data-ttu-id="9eda5-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="9eda5-106">\<defaultProxy></span></span>  
<span data-ttu-id="9eda5-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="9eda5-107">\<bypasslist></span></span>  
<span data-ttu-id="9eda5-108">\<clear></span><span class="sxs-lookup"><span data-stu-id="9eda5-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eda5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9eda5-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9eda5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9eda5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9eda5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9eda5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9eda5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9eda5-112">Attributes</span></span>  
 <span data-ttu-id="9eda5-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9eda5-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9eda5-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9eda5-114">Child Elements</span></span>  
 <span data-ttu-id="9eda5-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9eda5-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9eda5-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9eda5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9eda5-117">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="9eda5-117">**Element**</span></span>|<span data-ttu-id="9eda5-118">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="9eda5-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9eda5-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="9eda5-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="9eda5-120">Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.</span><span class="sxs-lookup"><span data-stu-id="9eda5-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eda5-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="9eda5-121">Remarks</span></span>  
 <span data-ttu-id="9eda5-122">O `clear` elemento limpa todas as entradas da lista de ignoráveis.</span><span class="sxs-lookup"><span data-stu-id="9eda5-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9eda5-123">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="9eda5-123">Configuration Files</span></span>  
 <span data-ttu-id="9eda5-124">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="9eda5-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eda5-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9eda5-125">Example</span></span>  
 <span data-ttu-id="9eda5-126">O exemplo a seguir limpa a lista de bypass e, em seguida, adiciona dois endereços à lista de bypass.</span><span class="sxs-lookup"><span data-stu-id="9eda5-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="9eda5-127">A primeira ignora o proxy para todos os servidores no domínio contoso.com; o segundo ignora o proxy para todos os servidores cujo endereço IP começa com 192.168.</span><span class="sxs-lookup"><span data-stu-id="9eda5-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9eda5-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9eda5-128">See also</span></span>
- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="9eda5-129">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="9eda5-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
