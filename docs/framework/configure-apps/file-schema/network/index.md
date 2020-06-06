---
title: Esquema de configurações de rede
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
ms.openlocfilehash: 5e3bd1b1734fc7fba50b72785531a8b001d6d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698160"
---
# <a name="network-settings-schema"></a><span data-ttu-id="4baea-102">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="4baea-102">Network Settings Schema</span></span>
<span data-ttu-id="4baea-103">As configurações de rede especificam como o .NET Framework se conecta à Internet.</span><span class="sxs-lookup"><span data-stu-id="4baea-103">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="4baea-104">As \<system.net> configurações especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="4baea-104">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="4baea-105">A tabela a seguir descreve a função de cada elemento de configuração filho no [ \<system.Net> elemento (configurações de rede)](system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="4baea-105">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="4baea-106">Elemento</span><span class="sxs-lookup"><span data-stu-id="4baea-106">Element</span></span>|<span data-ttu-id="4baea-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4baea-107">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4baea-108">\<authenticationModules>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="4baea-108">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="4baea-109">Especifica os módulos usados para autenticar solicitações de Internet.</span><span class="sxs-lookup"><span data-stu-id="4baea-109">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="4baea-110">\<connectionManagement>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="4baea-110">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="4baea-111">Especifica o número máximo de conexões com host da Internet.</span><span class="sxs-lookup"><span data-stu-id="4baea-111">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="4baea-112">\<defaultProxy>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="4baea-112">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="4baea-113">Especifica o servidor proxy usado para solicitações HTTP para a Internet.</span><span class="sxs-lookup"><span data-stu-id="4baea-113">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="4baea-114">\<mailSettings>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="4baea-114">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="4baea-115">Contém configurações para opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="4baea-115">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="4baea-116">\<requestCaching>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="4baea-116">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="4baea-117">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="4baea-117">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="4baea-118">\<webRequestModules>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="4baea-118">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="4baea-119">Especifica os módulos usados para solicitar informações de hosts da Internet.</span><span class="sxs-lookup"><span data-stu-id="4baea-119">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="4baea-120">As \<uri> configurações especificam como o .NET Framework trata os endereços da Web expressos usando URIs (Uniform Resource Identifiers).</span><span class="sxs-lookup"><span data-stu-id="4baea-120">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="4baea-121">A tabela a seguir descreve a função de cada elemento de configuração filho no [ \<uri> elemento (configurações de URI)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="4baea-121">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="4baea-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="4baea-122">Element</span></span>|<span data-ttu-id="4baea-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="4baea-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4baea-124">\<idn>Elemento (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="4baea-124">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="4baea-125">Especifica se a análise de IDN (Nome de Domínio Internacionalizado) será aplicada aos nomes de domínio.</span><span class="sxs-lookup"><span data-stu-id="4baea-125">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="4baea-126">\<iriParsing>Elemento (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="4baea-126">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="4baea-127">Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="4baea-127">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="4baea-128">\<schemeSettings>Elemento (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="4baea-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="4baea-129">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="4baea-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4baea-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="4baea-130">See also</span></span>

- <span data-ttu-id="4baea-131">[Configuring Internet Applications](../../../network-programming/configuring-internet-applications.md) (Configurando aplicativos da Internet)</span><span class="sxs-lookup"><span data-stu-id="4baea-131">[Configuring Internet Applications](../../../network-programming/configuring-internet-applications.md)</span></span>
- [<span data-ttu-id="4baea-132">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="4baea-132">Configuration File Schema</span></span>](../index.md)
