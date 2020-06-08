---
title: Esquema de configurações de rede
description: Saiba mais sobre o esquema para as configurações de rede que especificam como o .NET Framework se conecta à Internet e manipula URIs.
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 6a22d7f1608db2e8909d0ead11e9110ec8a8a2c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504570"
---
# <a name="network-settings-schema"></a><span data-ttu-id="32276-103">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="32276-103">Network Settings Schema</span></span>
<span data-ttu-id="32276-104">As configurações de rede especificam como o .NET Framework se conecta à Internet.</span><span class="sxs-lookup"><span data-stu-id="32276-104">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="32276-105">As \<system.net> configurações especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="32276-105">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="32276-106">A tabela a seguir descreve a função de cada elemento de configuração filho no [ \<system.Net> elemento (configurações de rede)](system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="32276-106">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="32276-107">Elemento</span><span class="sxs-lookup"><span data-stu-id="32276-107">Element</span></span>|<span data-ttu-id="32276-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="32276-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32276-109">\<authenticationModules>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="32276-109">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="32276-110">Especifica os módulos usados para autenticar solicitações de Internet.</span><span class="sxs-lookup"><span data-stu-id="32276-110">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="32276-111">\<connectionManagement>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="32276-111">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="32276-112">Especifica o número máximo de conexões com host da Internet.</span><span class="sxs-lookup"><span data-stu-id="32276-112">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="32276-113">\<defaultProxy>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="32276-113">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="32276-114">Especifica o servidor proxy usado para solicitações HTTP para a Internet.</span><span class="sxs-lookup"><span data-stu-id="32276-114">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="32276-115">\<mailSettings>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="32276-115">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="32276-116">Contém configurações para opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="32276-116">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="32276-117">\<requestCaching>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="32276-117">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="32276-118">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="32276-118">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="32276-119">\<webRequestModules>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="32276-119">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="32276-120">Especifica os módulos usados para solicitar informações de hosts da Internet.</span><span class="sxs-lookup"><span data-stu-id="32276-120">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="32276-121">As \<uri> configurações especificam como o .NET Framework trata os endereços da Web expressos usando URIs (Uniform Resource Identifiers).</span><span class="sxs-lookup"><span data-stu-id="32276-121">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="32276-122">A tabela a seguir descreve a função de cada elemento de configuração filho no [ \<uri> elemento (configurações de URI)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="32276-122">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="32276-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="32276-123">Element</span></span>|<span data-ttu-id="32276-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="32276-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32276-125">\<idn>Elemento (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="32276-125">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="32276-126">Especifica se a análise de IDN (Nome de Domínio Internacionalizado) será aplicada aos nomes de domínio.</span><span class="sxs-lookup"><span data-stu-id="32276-126">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="32276-127">\<iriParsing>Elemento (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="32276-127">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="32276-128">Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="32276-128">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="32276-129">\<schemeSettings>Elemento (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="32276-129">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="32276-130">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="32276-130">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32276-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="32276-131">See also</span></span>

- <span data-ttu-id="32276-132">[Configuring Internet Applications](../../../network-programming/configuring-internet-applications.md) (Configurando aplicativos da Internet)</span><span class="sxs-lookup"><span data-stu-id="32276-132">[Configuring Internet Applications](../../../network-programming/configuring-internet-applications.md)</span></span>
- [<span data-ttu-id="32276-133">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="32276-133">Configuration File Schema</span></span>](../index.md)
