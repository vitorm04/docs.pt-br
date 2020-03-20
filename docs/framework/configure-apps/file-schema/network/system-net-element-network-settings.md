---
title: Elemento <system.Net> (configurações de rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154550"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="dcd39-102">\<Elemento system.Net> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="dcd39-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="dcd39-103">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="dcd39-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[<span data-ttu-id="dcd39-104">**\<>de configuração**</span><span class="sxs-lookup"><span data-stu-id="dcd39-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="dcd39-105">&nbsp;&nbsp;**\<system.net>**</span><span class="sxs-lookup"><span data-stu-id="dcd39-105">&nbsp;&nbsp;**\<system.net>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcd39-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dcd39-106">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcd39-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dcd39-107">Attributes and Elements</span></span>  
 <span data-ttu-id="dcd39-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dcd39-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcd39-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="dcd39-109">Attributes</span></span>  
 <span data-ttu-id="dcd39-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dcd39-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dcd39-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dcd39-111">Child Elements</span></span>  
  
|<span data-ttu-id="dcd39-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="dcd39-112">**Element**</span></span>|<span data-ttu-id="dcd39-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="dcd39-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dcd39-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="dcd39-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="dcd39-115">Especifica módulos usados para autenticar solicitações da Internet.</span><span class="sxs-lookup"><span data-stu-id="dcd39-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="dcd39-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="dcd39-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="dcd39-117">Especifica o número máximo de conexões a um host da Internet.</span><span class="sxs-lookup"><span data-stu-id="dcd39-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="dcd39-118">Defaultproxy</span><span class="sxs-lookup"><span data-stu-id="dcd39-118">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="dcd39-119">Configura o servidor proxy Hypertext Transfer Protocol (HTTP).</span><span class="sxs-lookup"><span data-stu-id="dcd39-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="dcd39-120">Mailsettings</span><span class="sxs-lookup"><span data-stu-id="dcd39-120">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="dcd39-121">Configura opções de envio de e-mails do Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="dcd39-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="dcd39-122">solicitaçãoCaching</span><span class="sxs-lookup"><span data-stu-id="dcd39-122">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="dcd39-123">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="dcd39-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="dcd39-124">configurações</span><span class="sxs-lookup"><span data-stu-id="dcd39-124">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="dcd39-125">Configura opções básicas de <xref:System.Net> rede para classes nos espaços de nome de crianças relacionados.</span><span class="sxs-lookup"><span data-stu-id="dcd39-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="dcd39-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="dcd39-126">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="dcd39-127">Especifica módulos a serem usados para solicitar informações de hosts da Internet.</span><span class="sxs-lookup"><span data-stu-id="dcd39-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dcd39-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dcd39-128">Parent Elements</span></span>  
  
|<span data-ttu-id="dcd39-129">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="dcd39-129">**Element**</span></span>|<span data-ttu-id="dcd39-130">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="dcd39-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dcd39-131">configuração</span><span class="sxs-lookup"><span data-stu-id="dcd39-131">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="dcd39-132">Contém configurações para todos os namespaces.</span><span class="sxs-lookup"><span data-stu-id="dcd39-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcd39-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="dcd39-133">Remarks</span></span>  
 <span data-ttu-id="dcd39-134">O [ \<elemento>system.net](system-net-element-network-settings.md) contém configurações para classes nos <xref:System.Net> espaços de nome de crianças e filhos relacionados.</span><span class="sxs-lookup"><span data-stu-id="dcd39-134">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="dcd39-135">As configurações configuram módulos de autenticação, gerenciamento de conexão, configurações de e-mail, servidor proxy e módulos de solicitação da Internet para receber informações de hosts da Internet.</span><span class="sxs-lookup"><span data-stu-id="dcd39-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcd39-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dcd39-136">Example</span></span>  
 <span data-ttu-id="dcd39-137">O exemplo a seguir mostra <xref:System.Net> uma configuração típica usada pelas classes.</span><span class="sxs-lookup"><span data-stu-id="dcd39-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dcd39-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="dcd39-138">See also</span></span>

- [<span data-ttu-id="dcd39-139">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="dcd39-139">Network Settings Schema</span></span>](index.md)
