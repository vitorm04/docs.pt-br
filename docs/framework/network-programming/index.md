---
title: Programação de rede no .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
ms.openlocfilehash: 1e7f0123ab07fd4e83eea957b72bf79eeeecef2b
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204688"
---
# <a name="network-programming-in-the-net-framework"></a><span data-ttu-id="faf6e-102">Programação de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="faf6e-102">Network Programming in the .NET Framework</span></span>
<span data-ttu-id="faf6e-103">O Microsoft .NET Framework fornece uma implementação dos serviços de Internet em camadas, extensível e gerenciada que pode ser rápida e facilmente integrada aos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="faf6e-103">The Microsoft .NET Framework provides a layered, extensible, and managed implementation of Internet services that can be quickly and easily integrated into your applications.</span></span> <span data-ttu-id="faf6e-104">Os aplicativos de rede podem compilar em protocolos conectáveis para usufruir automaticamente de novos protocolos da Internet ou podem usar uma implementação gerenciada da interface de soquete do Windows para trabalhar com a rede a nível de soquete.</span><span class="sxs-lookup"><span data-stu-id="faf6e-104">Your network applications can build on pluggable protocols to automatically take advantage of new Internet protocols, or they can use a managed implementation of the Windows socket interface to work with the network on the socket level.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="faf6e-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="faf6e-105">In This Section</span></span>  

 [<span data-ttu-id="faf6e-106">Apresentando protocolos conectáveis</span><span class="sxs-lookup"><span data-stu-id="faf6e-106">Introducing Pluggable Protocols</span></span>](introducing-pluggable-protocols.md)  
 <span data-ttu-id="faf6e-107">Descreve como acessar um recurso da Internet sem considerar o protocolo de acesso necessário.</span><span class="sxs-lookup"><span data-stu-id="faf6e-107">Describes how to access an Internet resource without regard to the access protocol that it requires.</span></span>  
  
 [<span data-ttu-id="faf6e-108">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="faf6e-108">Requesting Data</span></span>](requesting-data.md)  
 <span data-ttu-id="faf6e-109">Explica como usar protocolos conectáveis para carregar e baixar dados dos recursos da Internet.</span><span class="sxs-lookup"><span data-stu-id="faf6e-109">Explains how to use pluggable protocols to upload and download data from Internet resources.</span></span>  
  
 [<span data-ttu-id="faf6e-110">Programando protocolos conectáveis</span><span class="sxs-lookup"><span data-stu-id="faf6e-110">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)  
 <span data-ttu-id="faf6e-111">Explica como derivar classes específicas de protocolo para implementar protocolos conectáveis.</span><span class="sxs-lookup"><span data-stu-id="faf6e-111">Explains how to derive protocol-specific classes to implement pluggable protocols.</span></span>  
  
 [<span data-ttu-id="faf6e-112">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="faf6e-112">Using Application Protocols</span></span>](using-application-protocols.md)  
 <span data-ttu-id="faf6e-113">Descreve aplicativos de programação que se beneficiam de protocolos de rede como o TCP, UDP e HTTP.</span><span class="sxs-lookup"><span data-stu-id="faf6e-113">Describes programming applications that take advantage of network protocols such as TCP, UDP, and HTTP.</span></span>  
  
 [<span data-ttu-id="faf6e-114">Protocolo da Internet Versão 6</span><span class="sxs-lookup"><span data-stu-id="faf6e-114">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)  
 <span data-ttu-id="faf6e-115">Descreve as vantagens do Protocolo de Internet versão 6 (IPv6) sob a versão atual do pacote do Protocolo de Internet (IPv4), descreve o endereçamento do IPv6, o roteamento e a configuração automática e também como habilitar e desabilitar o IPv6.</span><span class="sxs-lookup"><span data-stu-id="faf6e-115">Describes the advantages of Internet Protocol version 6 (IPv6) over the current version of the Internet Protocol suite (IPv4), describes IPv6 addressing, routing and auto-configuration, and how to enable and disable IPv6.</span></span>  
  
 [<span data-ttu-id="faf6e-116">Configurando aplicativos da Internet</span><span class="sxs-lookup"><span data-stu-id="faf6e-116">Configuring Internet Applications</span></span>](configuring-internet-applications.md)  
 <span data-ttu-id="faf6e-117">Explica como usar os arquivos de configuração do .NET Framework para configurar aplicativos da Internet.</span><span class="sxs-lookup"><span data-stu-id="faf6e-117">Explains how to use the .NET Framework configuration files to configure Internet applications.</span></span>  
  
 [<span data-ttu-id="faf6e-118">Rastreamento de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="faf6e-118">Network Tracing in the .NET Framework</span></span>](network-tracing.md)  
 <span data-ttu-id="faf6e-119">Explica como usar o rastreamento de rede para obter informações sobre invocações de método e tráfego de rede geradas por um aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="faf6e-119">Explains how to use network tracing to get information about method invocations and network traffic generated by a managed application.</span></span>  
  
 [<span data-ttu-id="faf6e-120">Gerenciamento de cache para aplicativos de rede</span><span class="sxs-lookup"><span data-stu-id="faf6e-120">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)  
 <span data-ttu-id="faf6e-121">Descreve como usar o cachê para aplicativos que usam as classes <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType> e <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="faf6e-121">Describes how to use caching for applications that use the <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType>, and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.</span></span>  
  
 [<span data-ttu-id="faf6e-122">Segurança na programação de rede</span><span class="sxs-lookup"><span data-stu-id="faf6e-122">Security in Network Programming</span></span>](security-in-network-programming.md)  
 <span data-ttu-id="faf6e-123">Descreve como usar técnicas padrão de segurança e autenticação da Internet.</span><span class="sxs-lookup"><span data-stu-id="faf6e-123">Describes how to use standard Internet security and authentication techniques.</span></span>  
  
 [<span data-ttu-id="faf6e-124">Melhores práticas para classes System.Net</span><span class="sxs-lookup"><span data-stu-id="faf6e-124">Best Practices for System.Net Classes</span></span>](best-practices-for-system-net-classes.md)  
 <span data-ttu-id="faf6e-125">Fornece dicas e truques para obter o máximo dos aplicativos da Internet.</span><span class="sxs-lookup"><span data-stu-id="faf6e-125">Provides tips and tricks for getting the most out of your Internet applications.</span></span>  
  
 [<span data-ttu-id="faf6e-126">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="faf6e-126">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)  
 <span data-ttu-id="faf6e-127">Descreve como configurar proxies.</span><span class="sxs-lookup"><span data-stu-id="faf6e-127">Describes how to configure proxies.</span></span>  
  
 [<span data-ttu-id="faf6e-128">NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="faf6e-128">NetworkInformation</span></span>](networkinformation.md)  
 <span data-ttu-id="faf6e-129">Descreve como coletar informações sobre eventos, alterações, estatísticas e propriedades de rede e também explica como determinar se um host remoto é acessível usando a classe <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="faf6e-129">Describes how to gather information about network events, changes, statistics, and properties and also explains how to determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
 [<span data-ttu-id="faf6e-130">Alterações no namespace System.Uri na versão 2.0</span><span class="sxs-lookup"><span data-stu-id="faf6e-130">Changes to the System.Uri namespace in Version 2.0</span></span>](changes-to-the-system-uri-namespace-in-version-2-0.md)  
 <span data-ttu-id="faf6e-131">Descreve várias alterações feitas na classe <xref:System.Uri?displayProperty=nameWithType> na versão 2.0 para comportamento fixo incorreto; aprimora a usabilidade e a segurança.</span><span class="sxs-lookup"><span data-stu-id="faf6e-131">Describes several changes made to the <xref:System.Uri?displayProperty=nameWithType> class in Version 2.0 to fixed incorrect behavior, enhance usability, and enhance security.</span></span>  
  
 [<span data-ttu-id="faf6e-132">Suporte ao International Resource Identifier em System.Uri</span><span class="sxs-lookup"><span data-stu-id="faf6e-132">International Resource Identifier Support in System.Uri</span></span>](international-resource-identifier-support-in-system-uri.md)  
 <span data-ttu-id="faf6e-133">Descreve aprimoramentos na classe <xref:System.Uri?displayProperty=nameWithType> na versão 3.5, 3.0 SP1 e 2.0 SP1 para o Identificador Internacional de Recursos (IRI) e o suporte de Nome de Domínio Internacionalizado (IDN).</span><span class="sxs-lookup"><span data-stu-id="faf6e-133">Describes enhancements to the <xref:System.Uri?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 for International Resource Identifier (IRI) and Internationalized Domain Name (IDN) support.</span></span>  
  
 [<span data-ttu-id="faf6e-134">Melhorias do desempenho de soquete na versão 3.5</span><span class="sxs-lookup"><span data-stu-id="faf6e-134">Socket Performance Enhancements in Version 3.5</span></span>](socket-performance-enhancements-in-version-3-5.md)  
 <span data-ttu-id="faf6e-135">Descreve um conjunto de aprimoramentos na classe <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> na versão 3.5, 3.0 SP1 e 2.0 SP1, que fornece um padrão assíncrono alternativo, o qual pode ser usado por aplicativos de alto desempenho especializados em soquete.</span><span class="sxs-lookup"><span data-stu-id="faf6e-135">Describes a set of enhancements to the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 that provide an alternative asynchronous pattern that can be used by specialized high-performance socket applications.</span></span>  
  
 [<span data-ttu-id="faf6e-136">Protocolo PNRP</span><span class="sxs-lookup"><span data-stu-id="faf6e-136">Peer Name Resolution Protocol</span></span>](peer-name-resolution-protocol.md)  
 <span data-ttu-id="faf6e-137">Descreve o suporte adicionado à versão 3.5 para oferecer suporte ao protocolo PNRP, um protocolo de resolução de nome e um registro de nome dinâmico sem servidor.</span><span class="sxs-lookup"><span data-stu-id="faf6e-137">Describes support added in Version 3.5 to support the Peer Name Resolution Protocol (PNRP), a serverless and dynamic name registration and name resolution protocol.</span></span> <span data-ttu-id="faf6e-138">Esses novos recursos têm suporte pelo namespace <xref:System.Net.PeerToPeer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="faf6e-138">These new features are supported by the <xref:System.Net.PeerToPeer?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="faf6e-139">Colaboração ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="faf6e-139">Peer-to-Peer Collaboration</span></span>](peer-to-peer-collaboration.md)  
 <span data-ttu-id="faf6e-140">Descreve o suporte adicionado à versão 3.5 para dar suporte à Colaboração Ponto a Ponto que compila no PNRP.</span><span class="sxs-lookup"><span data-stu-id="faf6e-140">Describes support added in Version 3.5 to support the Peer-to-Peer Collaboration that builds on PNRP.</span></span> <span data-ttu-id="faf6e-141">Esses novos recursos têm suporte pelo namespace <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="faf6e-141">These new features are supported by the <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="faf6e-142">Alterações na autenticação NTLM para HttpWebRequest na versão 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="faf6e-142">Changes to NTLM authentication for HttpWebRequest in Version 3.5 SP1</span></span>](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 <span data-ttu-id="faf6e-143">Descreve as alterações de segurança feitas na versão 3.5 SP1 que afetam a maneira como a autenticação integrada do Windows é controlada por <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType> e por classes relacionadas no namespace do System.Net.</span><span class="sxs-lookup"><span data-stu-id="faf6e-143">Describes security changes made in Version 3.5 SP1 that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the System.Net namespace.</span></span>  
  
 [<span data-ttu-id="faf6e-144">Autenticação Integrada do Windows com proteção estendida</span><span class="sxs-lookup"><span data-stu-id="faf6e-144">Integrated Windows Authentication with Extended Protection</span></span>](integrated-windows-authentication-with-extended-protection.md)  
 <span data-ttu-id="faf6e-145">Descreve aprimoramentos para a proteção estendida que afetam a maneira como a autenticação integrada do Windows é controlada por <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType> e por classes relacionadas no <xref:System.Net?displayProperty=nameWithType> e por namespaces relacionados.</span><span class="sxs-lookup"><span data-stu-id="faf6e-145">Describes enhancements for extended protection that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the <xref:System.Net?displayProperty=nameWithType> and related namespaces.</span></span>  
  
 [<span data-ttu-id="faf6e-146">Passagem de NAT usando IPv6 e Teredo</span><span class="sxs-lookup"><span data-stu-id="faf6e-146">NAT Traversal using IPv6 and Teredo</span></span>](nat-traversal-using-ipv6-and-teredo.md)  
 <span data-ttu-id="faf6e-147">Descreve os aprimoramentos adicionados ao <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType> e namespaces <xref:System.Net.Sockets?displayProperty=nameWithType> para oferecer suporte à NAT transversal usando o IPv6 e o Teredo.</span><span class="sxs-lookup"><span data-stu-id="faf6e-147">Describes enhancements added to the <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType>, and <xref:System.Net.Sockets?displayProperty=nameWithType> namespaces to support NAT traversal using IPv6 and Teredo.</span></span>  
  
 [<span data-ttu-id="faf6e-148">Isolamento de rede para Aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="faf6e-148">Network Isolation for Windows Store Apps</span></span>](network-isolation-for-windows-store-apps.md)  
 <span data-ttu-id="faf6e-149">Descreve o impacto do isolamento de rede quando as classes nos namespaces <xref:System.Net>, <xref:System.Net.Http>e <xref:System.Net.Http.Headers> são usadas em aplicativos da loja do Windows 8. x.</span><span class="sxs-lookup"><span data-stu-id="faf6e-149">Describes the impact of network isolation when classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces are used in Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="faf6e-150">Amostras de programação de rede</span><span class="sxs-lookup"><span data-stu-id="faf6e-150">Network Programming Samples</span></span>](network-programming-samples.md)  
 <span data-ttu-id="faf6e-151">Vincula-se a amostras para download de programação de rede que usam classes nos namespaces <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets>.</span><span class="sxs-lookup"><span data-stu-id="faf6e-151">Links to downloadable network programming samples that use classes in the <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> namespaces.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="faf6e-152">Referência</span><span class="sxs-lookup"><span data-stu-id="faf6e-152">Reference</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-153">{1&gt;Fornece uma interface de programação simples para muitos dos protocolos usados nas redes de hoje.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="faf6e-153">Provides a simple programming interface for many of the protocols used on networks today.</span></span> <span data-ttu-id="faf6e-154">As classes <xref:System.Net.WebRequest?displayProperty=nameWithType> e <xref:System.Net.WebResponse?displayProperty=nameWithType> nesse namespace são a base para protocolos conectáveis.</span><span class="sxs-lookup"><span data-stu-id="faf6e-154">The <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.WebResponse?displayProperty=nameWithType> classes in this namespace are the basis for pluggable protocols.</span></span>  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-155">Define tipos e enumerações usados para definir políticas de cache para os recursos obtidos usando as classes <xref:System.Net.WebRequest?displayProperty=nameWithType> e <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="faf6e-155">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.</span></span>  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-156">Classes que os aplicativos usam para acessar e atualizar programaticamente definições de configuração dos namespaces do System.Net.</span><span class="sxs-lookup"><span data-stu-id="faf6e-156">Classes that applications use to programmatically access and update configuration settings for the System.Net namespaces.</span></span>  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-157">Classes que fornecem uma interface de programação para aplicativos HTTP modernos.</span><span class="sxs-lookup"><span data-stu-id="faf6e-157">Classes that provides a programming interface for modern HTTP applications.</span></span>  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-158">Fornece suporte para coleções de cabeçalhos HTTP usados pelo namespace <xref:System.Net.Http?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="faf6e-158">Provides support for collections of HTTP headers used by the <xref:System.Net.Http?displayProperty=nameWithType> namespace</span></span>  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-159">Classes para compor e enviar email usando o protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="faf6e-159">Classes to compose and send mail using the SMTP protocol.</span></span>  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-160">Define os tipos usados para representar os cabeçalhos MIME (Multipurpose Internet Mail Exchange) usado por classes no namespace <xref:System.Net.Mail?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="faf6e-160">Defines types that are used to represent Multipurpose Internet Mail Exchange (MIME) headers used by classes in the <xref:System.Net.Mail?displayProperty=nameWithType> namespace.</span></span>  
  
 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-161">Classes para coletar programaticamente informações sobre eventos, alterações, estatísticas e propriedades de rede.</span><span class="sxs-lookup"><span data-stu-id="faf6e-161">Classes to programmatically gather information about network events, changes, statistics, and properties.</span></span>  
  
 <xref:System.Net.PeerToPeer?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-162">Fornece uma implementação gerenciada do protocolo PNRP para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="faf6e-162">Provides a managed implementation of the Peer Name Resolution Protocol (PNRP) for developers.</span></span>  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-163">Fornece uma implementação gerenciada da interface de Colaboração Ponto a Ponto para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="faf6e-163">Provides a managed implementation of the Peer-to-Peer Collaboration interface for developers.</span></span>  
  
 <xref:System.Net.Security?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-164">Classes para fornecer fluxos de rede para proteger comunicações entre hosts.</span><span class="sxs-lookup"><span data-stu-id="faf6e-164">Classes to provide network streams for secure communications between hosts.</span></span>  
  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-165">Fornece uma implementação gerenciada da interface dos Soquetes do Windows (Winsock) para desenvolvedores que precisam ajudar a controlar o acesso à rede.</span><span class="sxs-lookup"><span data-stu-id="faf6e-165">Provides a managed implementation of the Windows Sockets (Winsock) interface for developers who need to help control access to the network.</span></span>  
  
 <xref:System.Net.WebSockets?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-166">Fornece uma implementação gerenciada da interface de WebSocket para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="faf6e-166">Provides a managed implementation of the WebSocket interface for developers.</span></span>  
  
 <xref:System.Uri?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-167">Fornece uma representação de objeto de um URI (Uniform Resource Identifier) e acesso fácil às partes do URI.</span><span class="sxs-lookup"><span data-stu-id="faf6e-167">Provides an object representation of a uniform resource identifier (URI) and easy access to the parts of the URI.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-168">Fornece suporte à autenticação usando proteção estendida para aplicativos.</span><span class="sxs-lookup"><span data-stu-id="faf6e-168">Provides support for authentication using extended protection for applications.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="faf6e-169">Fornece suporte à configuração da autenticação usando proteção estendida para aplicativos.</span><span class="sxs-lookup"><span data-stu-id="faf6e-169">Provides support for configuration of authentication using extended protection for applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf6e-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="faf6e-170">See also</span></span>

- [<span data-ttu-id="faf6e-171">Práticas recomendadas do protocolo TLS com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="faf6e-171">Transport Layer Security (TLS) best practices with .NET Framework</span></span>](tls.md)
- [<span data-ttu-id="faf6e-172">Tópicos de instruções de programação de rede</span><span class="sxs-lookup"><span data-stu-id="faf6e-172">Network Programming How-to Topics</span></span>](network-programming-how-to-topics.md)
- [<span data-ttu-id="faf6e-173">Amostras de programação de rede</span><span class="sxs-lookup"><span data-stu-id="faf6e-173">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="faf6e-174">Amostra de HttpClient</span><span class="sxs-lookup"><span data-stu-id="faf6e-174">HttpClient Sample</span></span>](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
