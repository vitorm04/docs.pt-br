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
ms.openlocfilehash: 44ef0b8e1b6dc6ad0efde6b26ad7d4700e06f2c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178327"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="cf8c8-102">Elemento \<ipv6> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="cf8c8-102">\<ipv6> Element (Network Settings)</span></span>

<span data-ttu-id="cf8c8-103">Habilita respostas de IPv6 (protocolo IP versão 6) de membros obsoletos da <xref:System.Net.Dns> classe.</span><span class="sxs-lookup"><span data-stu-id="cf8c8-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**

## <a name="syntax"></a><span data-ttu-id="cf8c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf8c8-104">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf8c8-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cf8c8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cf8c8-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cf8c8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf8c8-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="cf8c8-107">Attributes</span></span>  
  
|<span data-ttu-id="cf8c8-108">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="cf8c8-108">**Attribute**</span></span>|<span data-ttu-id="cf8c8-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="cf8c8-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="cf8c8-110">Especifica se os membros da <xref:System.Net.Dns> classe retornam endereços IPv6 (protocolo IP versão 6).</span><span class="sxs-lookup"><span data-stu-id="cf8c8-110">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="cf8c8-111">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="cf8c8-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf8c8-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cf8c8-112">Child Elements</span></span>  

 <span data-ttu-id="cf8c8-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cf8c8-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf8c8-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cf8c8-114">Parent Elements</span></span>  
  
|<span data-ttu-id="cf8c8-115">**Element**</span><span class="sxs-lookup"><span data-stu-id="cf8c8-115">**Element**</span></span>|<span data-ttu-id="cf8c8-116">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="cf8c8-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cf8c8-117">configurações</span><span class="sxs-lookup"><span data-stu-id="cf8c8-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="cf8c8-118">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="cf8c8-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf8c8-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf8c8-119">Remarks</span></span>  

 <span data-ttu-id="cf8c8-120">Essa configuração habilita o suporte a IPv6 para os membros obsoletos da classe:,,,,, <xref:System.Net.Dns> <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Net.Dns.BeginResolve%2A> <xref:System.Net.Dns.EndGetHostByName%2A> <xref:System.Net.Dns.EndResolve%2A> <xref:System.Net.Dns.GetHostByAddress%2A> <xref:System.Net.Dns.GetHostByName%2A> e <xref:System.Net.Dns.Resolve%2A> .</span><span class="sxs-lookup"><span data-stu-id="cf8c8-120">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="cf8c8-121">Para outros membros do <xref:System.Net?displayProperty=nameWithType> namespace, os endereços IPv6 podem ser retornados se o IPv6 estiver habilitado no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="cf8c8-121">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cf8c8-122">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="cf8c8-122">Configuration Files</span></span>  

 <span data-ttu-id="cf8c8-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="cf8c8-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf8c8-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf8c8-124">Example</span></span>  

 <span data-ttu-id="cf8c8-125">O exemplo a seguir mostra como habilitar o suporte a IPv6 para a <xref:System.Net.Dns> classe.</span><span class="sxs-lookup"><span data-stu-id="cf8c8-125">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf8c8-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="cf8c8-126">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cf8c8-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="cf8c8-127">Network Settings Schema</span></span>](index.md)
