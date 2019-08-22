---
title: Elemento <ipv6> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: d89c2e2c6943aca38f8a71092ba3121447a77574
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664092"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="e7f90-102">\<Elemento ipv6> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="e7f90-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="e7f90-103">Habilita respostas de IPv6 (protocolo IP versão 6) de membros obsoletos <xref:System.Net.Dns> da classe.</span><span class="sxs-lookup"><span data-stu-id="e7f90-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="e7f90-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e7f90-104">\<configuration></span></span>  
<span data-ttu-id="e7f90-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e7f90-105">\<system.net></span></span>  
<span data-ttu-id="e7f90-106">\<> de configurações</span><span class="sxs-lookup"><span data-stu-id="e7f90-106">\<settings></span></span>  
<span data-ttu-id="e7f90-107">\<ipv6></span><span class="sxs-lookup"><span data-stu-id="e7f90-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7f90-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7f90-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7f90-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e7f90-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e7f90-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e7f90-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7f90-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="e7f90-111">Attributes</span></span>  
  
|<span data-ttu-id="e7f90-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="e7f90-112">**Attribute**</span></span>|<span data-ttu-id="e7f90-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e7f90-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="e7f90-114">Especifica se os membros da <xref:System.Net.Dns> classe retornam endereços IPv6 (protocolo IP versão 6).</span><span class="sxs-lookup"><span data-stu-id="e7f90-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="e7f90-115">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="e7f90-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7f90-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e7f90-116">Child Elements</span></span>  
 <span data-ttu-id="e7f90-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e7f90-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7f90-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e7f90-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e7f90-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e7f90-119">**Element**</span></span>|<span data-ttu-id="e7f90-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e7f90-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e7f90-121">settings</span><span class="sxs-lookup"><span data-stu-id="e7f90-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="e7f90-122">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="e7f90-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7f90-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7f90-123">Remarks</span></span>  
 <span data-ttu-id="e7f90-124">Essa configuração habilita <xref:System.Net.Dns> o suporte a IPv6 para os membros obsoletos da classe <xref:System.Net.Dns.BeginResolve%2A>: <xref:System.Net.Dns.EndGetHostByName%2A> <xref:System.Net.Dns.GetHostByName%2A> <xref:System.Net.Dns.GetHostByAddress%2A> <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>,,,, <xref:System.Net.Dns.Resolve%2A>e.</span><span class="sxs-lookup"><span data-stu-id="e7f90-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="e7f90-125">Para outros membros do <xref:System.Net?displayProperty=nameWithType> namespace, os endereços IPv6 podem ser retornados se o IPv6 estiver habilitado no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="e7f90-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e7f90-126">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="e7f90-126">Configuration Files</span></span>  
 <span data-ttu-id="e7f90-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e7f90-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7f90-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7f90-128">Example</span></span>  
 <span data-ttu-id="e7f90-129">O exemplo a seguir mostra como habilitar o suporte a IPv6 <xref:System.Net.Dns> para a classe.</span><span class="sxs-lookup"><span data-stu-id="e7f90-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7f90-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7f90-130">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e7f90-131">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="e7f90-131">Network Settings Schema</span></span>](index.md)
