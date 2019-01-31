---
title: Elemento < system.Net > (configurações de rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: f9fbf48325c7cb5216d16041543bc53c00584ea3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257866"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="52aab-102">\<system.Net > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="52aab-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="52aab-103">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="52aab-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="52aab-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="52aab-104">\<configuration></span></span>  
<span data-ttu-id="52aab-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="52aab-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52aab-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52aab-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52aab-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="52aab-107">Attributes and Elements</span></span>  
 <span data-ttu-id="52aab-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="52aab-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52aab-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="52aab-109">Attributes</span></span>  
 <span data-ttu-id="52aab-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="52aab-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="52aab-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="52aab-111">Child Elements</span></span>  
  
|<span data-ttu-id="52aab-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="52aab-112">**Element**</span></span>|<span data-ttu-id="52aab-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="52aab-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="52aab-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="52aab-114">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="52aab-115">Especifica os módulos usados para autenticar solicitações de Internet.</span><span class="sxs-lookup"><span data-stu-id="52aab-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="52aab-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="52aab-116">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="52aab-117">Especifica o número máximo de conexões para um host da Internet.</span><span class="sxs-lookup"><span data-stu-id="52aab-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="52aab-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="52aab-118">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="52aab-119">Configura o servidor de proxy de protocolo HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="52aab-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="52aab-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="52aab-120">mailSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="52aab-121">Configura as opções de envio de mensagens de transporte protocolo SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="52aab-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="52aab-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="52aab-122">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="52aab-123">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="52aab-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="52aab-124">settings</span><span class="sxs-lookup"><span data-stu-id="52aab-124">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="52aab-125">Configura as opções de rede básica para classes no <xref:System.Net> e namespaces filho relacionados.</span><span class="sxs-lookup"><span data-stu-id="52aab-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="52aab-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="52aab-126">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="52aab-127">Especifica os módulos para usá-lo para solicitar informações de hosts da Internet.</span><span class="sxs-lookup"><span data-stu-id="52aab-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="52aab-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="52aab-128">Parent Elements</span></span>  
  
|<span data-ttu-id="52aab-129">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="52aab-129">**Element**</span></span>|<span data-ttu-id="52aab-130">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="52aab-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="52aab-131">configuration</span><span class="sxs-lookup"><span data-stu-id="52aab-131">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="52aab-132">Contém configurações para todos os namespaces.</span><span class="sxs-lookup"><span data-stu-id="52aab-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52aab-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="52aab-133">Remarks</span></span>  
 <span data-ttu-id="52aab-134">O [ \<system.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) elemento contém definições de classes no <xref:System.Net> e namespaces filho relacionados.</span><span class="sxs-lookup"><span data-stu-id="52aab-134">The [\<system.net>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="52aab-135">As configurações de configuram os módulos de autenticação, gerenciamento de conexão, configurações de email, o servidor proxy e módulos de solicitação de Internet para receber informações de hosts da Internet.</span><span class="sxs-lookup"><span data-stu-id="52aab-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52aab-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52aab-136">Example</span></span>  
 <span data-ttu-id="52aab-137">O exemplo a seguir mostra uma configuração típica usada pelo <xref:System.Net> classes.</span><span class="sxs-lookup"><span data-stu-id="52aab-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="52aab-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52aab-138">See also</span></span>
- [<span data-ttu-id="52aab-139">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="52aab-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
