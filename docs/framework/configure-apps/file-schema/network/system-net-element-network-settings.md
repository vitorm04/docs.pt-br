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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154550"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="07a3e-102">Elemento \<system.Net> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="07a3e-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="07a3e-103">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="07a3e-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a><span data-ttu-id="07a3e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07a3e-104">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07a3e-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="07a3e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="07a3e-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="07a3e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07a3e-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="07a3e-107">Attributes</span></span>  
 <span data-ttu-id="07a3e-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="07a3e-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="07a3e-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="07a3e-109">Child Elements</span></span>  
  
|<span data-ttu-id="07a3e-110">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="07a3e-110">**Element**</span></span>|<span data-ttu-id="07a3e-111">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="07a3e-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="07a3e-112">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="07a3e-112">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="07a3e-113">Especifica os módulos usados para autenticar solicitações da Internet.</span><span class="sxs-lookup"><span data-stu-id="07a3e-113">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="07a3e-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="07a3e-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="07a3e-115">Especifica o número máximo de conexões com um host de Internet.</span><span class="sxs-lookup"><span data-stu-id="07a3e-115">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="07a3e-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="07a3e-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="07a3e-117">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="07a3e-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="07a3e-118">mailSettings</span><span class="sxs-lookup"><span data-stu-id="07a3e-118">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="07a3e-119">Configura as opções de envio de email do protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="07a3e-119">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="07a3e-120">requestCaching</span><span class="sxs-lookup"><span data-stu-id="07a3e-120">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="07a3e-121">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="07a3e-121">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="07a3e-122">configurações</span><span class="sxs-lookup"><span data-stu-id="07a3e-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="07a3e-123">Configura as opções básicas de rede para classes nos <xref:System.Net> namespaces filho relacionados.</span><span class="sxs-lookup"><span data-stu-id="07a3e-123">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="07a3e-124">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="07a3e-124">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="07a3e-125">Especifica os módulos a serem usados para solicitar informações de hosts da Internet.</span><span class="sxs-lookup"><span data-stu-id="07a3e-125">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="07a3e-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="07a3e-126">Parent Elements</span></span>  
  
|<span data-ttu-id="07a3e-127">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="07a3e-127">**Element**</span></span>|<span data-ttu-id="07a3e-128">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="07a3e-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="07a3e-129">configuração</span><span class="sxs-lookup"><span data-stu-id="07a3e-129">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="07a3e-130">Contém configurações para todos os namespaces.</span><span class="sxs-lookup"><span data-stu-id="07a3e-130">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07a3e-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="07a3e-131">Remarks</span></span>  
 <span data-ttu-id="07a3e-132">O [\<system.net>](system-net-element-network-settings.md) elemento contém configurações para classes nos <xref:System.Net> namespaces filho relacionados.</span><span class="sxs-lookup"><span data-stu-id="07a3e-132">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="07a3e-133">As configurações definem módulos de autenticação, gerenciamento de conexão, configurações de email, o servidor proxy e os módulos de solicitação da Internet para receber informações de hosts da Internet.</span><span class="sxs-lookup"><span data-stu-id="07a3e-133">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07a3e-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07a3e-134">Example</span></span>  
 <span data-ttu-id="07a3e-135">O exemplo a seguir mostra uma configuração típica usada por <xref:System.Net> classes.</span><span class="sxs-lookup"><span data-stu-id="07a3e-135">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07a3e-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="07a3e-136">See also</span></span>

- [<span data-ttu-id="07a3e-137">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="07a3e-137">Network Settings Schema</span></span>](index.md)
