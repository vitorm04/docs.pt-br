---
title: Elemento <system.Net> (configurações de rede)
description: O elemento de configurações de rede <system.Net> contém configurações que especificam como o .NET Framework se conecta às opções de rede no .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 9f18c7a3586948c03391d609f437e216a91bc27f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504479"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="d31ea-103">Elemento \<system.Net> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="d31ea-103">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="d31ea-104">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="d31ea-104">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a><span data-ttu-id="d31ea-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d31ea-105">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d31ea-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d31ea-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d31ea-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d31ea-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d31ea-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="d31ea-108">Attributes</span></span>  
 <span data-ttu-id="d31ea-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d31ea-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d31ea-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d31ea-110">Child Elements</span></span>  
  
|<span data-ttu-id="d31ea-111">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="d31ea-111">**Element**</span></span>|<span data-ttu-id="d31ea-112">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d31ea-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d31ea-113">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="d31ea-113">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="d31ea-114">Especifica os módulos usados para autenticar solicitações da Internet.</span><span class="sxs-lookup"><span data-stu-id="d31ea-114">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="d31ea-115">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="d31ea-115">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="d31ea-116">Especifica o número máximo de conexões com um host de Internet.</span><span class="sxs-lookup"><span data-stu-id="d31ea-116">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="d31ea-117">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="d31ea-117">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="d31ea-118">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="d31ea-118">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="d31ea-119">mailSettings</span><span class="sxs-lookup"><span data-stu-id="d31ea-119">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="d31ea-120">Configura as opções de envio de email do protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="d31ea-120">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="d31ea-121">requestCaching</span><span class="sxs-lookup"><span data-stu-id="d31ea-121">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="d31ea-122">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="d31ea-122">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="d31ea-123">configurações</span><span class="sxs-lookup"><span data-stu-id="d31ea-123">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="d31ea-124">Configura as opções básicas de rede para classes nos <xref:System.Net> namespaces filho relacionados.</span><span class="sxs-lookup"><span data-stu-id="d31ea-124">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="d31ea-125">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="d31ea-125">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="d31ea-126">Especifica os módulos a serem usados para solicitar informações de hosts da Internet.</span><span class="sxs-lookup"><span data-stu-id="d31ea-126">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d31ea-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d31ea-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d31ea-128">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="d31ea-128">**Element**</span></span>|<span data-ttu-id="d31ea-129">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d31ea-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d31ea-130">configuração</span><span class="sxs-lookup"><span data-stu-id="d31ea-130">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="d31ea-131">Contém configurações para todos os namespaces.</span><span class="sxs-lookup"><span data-stu-id="d31ea-131">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d31ea-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="d31ea-132">Remarks</span></span>  
 <span data-ttu-id="d31ea-133">O [\<system.net>](system-net-element-network-settings.md) elemento contém configurações para classes nos <xref:System.Net> namespaces filho relacionados.</span><span class="sxs-lookup"><span data-stu-id="d31ea-133">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="d31ea-134">As configurações definem módulos de autenticação, gerenciamento de conexão, configurações de email, o servidor proxy e os módulos de solicitação da Internet para receber informações de hosts da Internet.</span><span class="sxs-lookup"><span data-stu-id="d31ea-134">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d31ea-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d31ea-135">Example</span></span>  
 <span data-ttu-id="d31ea-136">O exemplo a seguir mostra uma configuração típica usada por <xref:System.Net> classes.</span><span class="sxs-lookup"><span data-stu-id="d31ea-136">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d31ea-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="d31ea-137">See also</span></span>

- [<span data-ttu-id="d31ea-138">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="d31ea-138">Network Settings Schema</span></span>](index.md)
