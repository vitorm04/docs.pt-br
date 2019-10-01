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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698160"
---
# <a name="network-settings-schema"></a><span data-ttu-id="5a98e-102">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="5a98e-102">Network Settings Schema</span></span>
<span data-ttu-id="5a98e-103">As configurações de rede especificam como o .NET Framework se conecta à Internet.</span><span class="sxs-lookup"><span data-stu-id="5a98e-103">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="5a98e-104">As configurações do @no__t -0system. net > especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="5a98e-104">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="5a98e-105">A tabela a seguir descreve a função de cada elemento de configuração filho no [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md) [Elemento system.Net> (configurações de rede)].</span><span class="sxs-lookup"><span data-stu-id="5a98e-105">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="5a98e-106">Elemento</span><span class="sxs-lookup"><span data-stu-id="5a98e-106">Element</span></span>|<span data-ttu-id="5a98e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a98e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a98e-108">[\<authenticationModules> Element (Network Settings)](authenticationmodules-element-network-settings.md) [Elemento authenticationModules> (configurações de rede)]</span><span class="sxs-lookup"><span data-stu-id="5a98e-108">[\<authenticationModules> Element (Network Settings)](authenticationmodules-element-network-settings.md)</span></span>|<span data-ttu-id="5a98e-109">Especifica os módulos usados para autenticar solicitações de Internet.</span><span class="sxs-lookup"><span data-stu-id="5a98e-109">Specifies the modules used to authenticate Internet requests.</span></span>|  
|<span data-ttu-id="5a98e-110">[\<connectionManagement> Element (Network Settings)](connectionmanagement-element-network-settings.md) [Elemento connectionManagement> (configurações de rede)]</span><span class="sxs-lookup"><span data-stu-id="5a98e-110">[\<connectionManagement> Element (Network Settings)](connectionmanagement-element-network-settings.md)</span></span>|<span data-ttu-id="5a98e-111">Especifica o número máximo de conexões com host da Internet.</span><span class="sxs-lookup"><span data-stu-id="5a98e-111">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|<span data-ttu-id="5a98e-112">[\<defaultProxy> Element (Network Settings)](defaultproxy-element-network-settings.md) [Elemento defaultProxy> (configurações de rede)]</span><span class="sxs-lookup"><span data-stu-id="5a98e-112">[\<defaultProxy> Element (Network Settings)](defaultproxy-element-network-settings.md)</span></span>|<span data-ttu-id="5a98e-113">Especifica o servidor proxy usado para solicitações HTTP para a Internet.</span><span class="sxs-lookup"><span data-stu-id="5a98e-113">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|<span data-ttu-id="5a98e-114">[\<mailSettings> Element (Network Settings)](mailsettings-element-network-settings.md) [Elemento mailSettings> (configurações de rede)]</span><span class="sxs-lookup"><span data-stu-id="5a98e-114">[\<mailSettings> Element (Network Settings)](mailsettings-element-network-settings.md)</span></span>|<span data-ttu-id="5a98e-115">Contém configurações para opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="5a98e-115">Contains settings for mail sending options.</span></span>|  
|<span data-ttu-id="5a98e-116">[\<requestCaching> Element (Network Settings)](requestcaching-element-network-settings.md) [Elemento requestCaching> (configurações de rede)]</span><span class="sxs-lookup"><span data-stu-id="5a98e-116">[\<requestCaching> Element (Network Settings)](requestcaching-element-network-settings.md)</span></span>|<span data-ttu-id="5a98e-117">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="5a98e-117">Controls the caching mechanism for network requests.</span></span>|  
|<span data-ttu-id="5a98e-118">[\<webRequestModules> Element (Network Settings)](webrequestmodules-element-network-settings.md) [Elemento webRequestModules> (configurações de rede)]</span><span class="sxs-lookup"><span data-stu-id="5a98e-118">[\<webRequestModules> Element (Network Settings)](webrequestmodules-element-network-settings.md)</span></span>|<span data-ttu-id="5a98e-119">Especifica os módulos usados para solicitar informações de hosts da Internet.</span><span class="sxs-lookup"><span data-stu-id="5a98e-119">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="5a98e-120">As configurações de > \<uri especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).</span><span class="sxs-lookup"><span data-stu-id="5a98e-120">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="5a98e-121">A tabela a seguir descreve a função de cada elemento de configuração filho no [elemento \<uri > (configurações de URI)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5a98e-121">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="5a98e-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="5a98e-122">Element</span></span>|<span data-ttu-id="5a98e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a98e-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a98e-124">[\<idn> Element (Uri Settings)](idn-element-uri-settings.md) [Elemento idn> (configurações de URI)]</span><span class="sxs-lookup"><span data-stu-id="5a98e-124">[\<idn> Element (Uri Settings)](idn-element-uri-settings.md)</span></span>|<span data-ttu-id="5a98e-125">Especifica se a análise de IDN (Nome de Domínio Internacionalizado) será aplicada aos nomes de domínio.</span><span class="sxs-lookup"><span data-stu-id="5a98e-125">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|<span data-ttu-id="5a98e-126">[\<iriParsing> Element (Uri Settings)](iriparsing-element-uri-settings.md) [Elemento iriParsing> (configurações de URI)]</span><span class="sxs-lookup"><span data-stu-id="5a98e-126">[\<iriParsing> Element (Uri Settings)](iriparsing-element-uri-settings.md)</span></span>|<span data-ttu-id="5a98e-127">Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="5a98e-127">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|<span data-ttu-id="5a98e-128">[\<schemeSettings> Element (Uri Settings)](schemesettings-element-uri-settings.md) [Elemento schemeSettings> (configurações de URI)]</span><span class="sxs-lookup"><span data-stu-id="5a98e-128">[\<schemeSettings> Element (Uri Settings)](schemesettings-element-uri-settings.md)</span></span>|<span data-ttu-id="5a98e-129">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="5a98e-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a98e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a98e-130">See also</span></span>

- [<span data-ttu-id="5a98e-131">Configurando aplicativos da Internet</span><span class="sxs-lookup"><span data-stu-id="5a98e-131">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="5a98e-132">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="5a98e-132">Configuration File Schema</span></span>](../index.md)
