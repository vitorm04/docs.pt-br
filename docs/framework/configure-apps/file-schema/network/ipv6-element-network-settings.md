---
title: '&lt;IPv6&gt; (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: 1ca1bb6a0b1a9c3deab9cb3ba15e9b3b2c29f1f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531883"
---
# <a name="ltipv6gt-element-network-settings"></a><span data-ttu-id="45a33-102">&lt;IPv6&gt; (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="45a33-102">&lt;ipv6&gt; Element (Network Settings)</span></span>
<span data-ttu-id="45a33-103">Permite que o protocolo IP versão 6 (IPv6) respostas de membros obsoletos do <xref:System.Net.Dns> classe.</span><span class="sxs-lookup"><span data-stu-id="45a33-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="45a33-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="45a33-104">\<configuration></span></span>  
<span data-ttu-id="45a33-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="45a33-105">\<system.net></span></span>  
<span data-ttu-id="45a33-106">\<Configurações ></span><span class="sxs-lookup"><span data-stu-id="45a33-106">\<settings></span></span>  
<span data-ttu-id="45a33-107">\<ipv6></span><span class="sxs-lookup"><span data-stu-id="45a33-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45a33-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45a33-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45a33-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="45a33-109">Attributes and Elements</span></span>  
 <span data-ttu-id="45a33-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="45a33-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45a33-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="45a33-111">Attributes</span></span>  
  
|<span data-ttu-id="45a33-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="45a33-112">**Attribute**</span></span>|<span data-ttu-id="45a33-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="45a33-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="45a33-114">Especifica se os membros de <xref:System.Net.Dns> classe retornar o protocolo IP versão 6 (IPv6) endereços.</span><span class="sxs-lookup"><span data-stu-id="45a33-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="45a33-115">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="45a33-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45a33-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="45a33-116">Child Elements</span></span>  
 <span data-ttu-id="45a33-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="45a33-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45a33-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="45a33-118">Parent Elements</span></span>  
  
|<span data-ttu-id="45a33-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="45a33-119">**Element**</span></span>|<span data-ttu-id="45a33-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="45a33-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="45a33-121">settings</span><span class="sxs-lookup"><span data-stu-id="45a33-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="45a33-122">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="45a33-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45a33-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="45a33-123">Remarks</span></span>  
 <span data-ttu-id="45a33-124">Essa configuração habilita o suporte a IPv6 para os membros obsoletos do <xref:System.Net.Dns> classe: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, e <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="45a33-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="45a33-125">Para outros membros do <xref:System.Net?displayProperty=nameWithType> namespace, os endereços IPv6 podem ser retornados se IPv6 estiver habilitado no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="45a33-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="45a33-126">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="45a33-126">Configuration Files</span></span>  
 <span data-ttu-id="45a33-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="45a33-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="45a33-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45a33-128">Example</span></span>  
 <span data-ttu-id="45a33-129">O exemplo a seguir mostra como habilitar o suporte a IPv6 para o <xref:System.Net.Dns> classe.</span><span class="sxs-lookup"><span data-stu-id="45a33-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45a33-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45a33-130">See also</span></span>
- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="45a33-131">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="45a33-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
