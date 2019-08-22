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
ms.openlocfilehash: 449146612938700f59f5e2ec761526d1dc66a3fc
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663950"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="670c1-102">\<Elemento system.Net> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="670c1-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="670c1-103">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="670c1-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="670c1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="670c1-104">\<configuration></span></span>  
<span data-ttu-id="670c1-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="670c1-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="670c1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="670c1-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="670c1-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="670c1-107">Attributes and Elements</span></span>  
 <span data-ttu-id="670c1-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="670c1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="670c1-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="670c1-109">Attributes</span></span>  
 <span data-ttu-id="670c1-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="670c1-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="670c1-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="670c1-111">Child Elements</span></span>  
  
|<span data-ttu-id="670c1-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="670c1-112">**Element**</span></span>|<span data-ttu-id="670c1-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="670c1-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="670c1-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="670c1-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="670c1-115">Especifica os módulos usados para autenticar solicitações da Internet.</span><span class="sxs-lookup"><span data-stu-id="670c1-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="670c1-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="670c1-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="670c1-117">Especifica o número máximo de conexões com um host de Internet.</span><span class="sxs-lookup"><span data-stu-id="670c1-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="670c1-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="670c1-118">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="670c1-119">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="670c1-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="670c1-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="670c1-120">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="670c1-121">Configura as opções de envio de email do protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="670c1-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="670c1-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="670c1-122">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="670c1-123">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="670c1-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="670c1-124">settings</span><span class="sxs-lookup"><span data-stu-id="670c1-124">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="670c1-125">Configura as opções básicas de rede para classes nos <xref:System.Net> namespaces filho relacionados.</span><span class="sxs-lookup"><span data-stu-id="670c1-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="670c1-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="670c1-126">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="670c1-127">Especifica os módulos a serem usados para solicitar informações de hosts da Internet.</span><span class="sxs-lookup"><span data-stu-id="670c1-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="670c1-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="670c1-128">Parent Elements</span></span>  
  
|<span data-ttu-id="670c1-129">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="670c1-129">**Element**</span></span>|<span data-ttu-id="670c1-130">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="670c1-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="670c1-131">configuração</span><span class="sxs-lookup"><span data-stu-id="670c1-131">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="670c1-132">Contém configurações para todos os namespaces.</span><span class="sxs-lookup"><span data-stu-id="670c1-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="670c1-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="670c1-133">Remarks</span></span>  
 <span data-ttu-id="670c1-134"><xref:System.Net> O [ \<elemento System. net >](system-net-element-network-settings.md) contém configurações para classes nos namespaces filho relacionados.</span><span class="sxs-lookup"><span data-stu-id="670c1-134">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="670c1-135">As configurações definem módulos de autenticação, gerenciamento de conexão, configurações de email, o servidor proxy e os módulos de solicitação da Internet para receber informações de hosts da Internet.</span><span class="sxs-lookup"><span data-stu-id="670c1-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="670c1-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="670c1-136">Example</span></span>  
 <span data-ttu-id="670c1-137">O exemplo a seguir mostra uma configuração típica usada <xref:System.Net> por classes.</span><span class="sxs-lookup"><span data-stu-id="670c1-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="670c1-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="670c1-138">See also</span></span>

- [<span data-ttu-id="670c1-139">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="670c1-139">Network Settings Schema</span></span>](index.md)
