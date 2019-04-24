---
title: Protocolo IP versão 6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: 135d87f126dcdb9689c23adbaaa4786bc69a3e09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182319"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="cc6ec-102">Protocolo IP versão 6</span><span class="sxs-lookup"><span data-stu-id="cc6ec-102">Internet Protocol Version 6</span></span>
<span data-ttu-id="cc6ec-103">O protocolo IP versão 6 (IPv6) é um novo pacote de protocolos padrão para a camada de rede da Internet.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-103">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="cc6ec-104">O IPv6 foi projetado para resolver muitos dos problemas da versão atual do pacote de protocolos IP (conhecido como IPv4) relacionados ao o esgotamento de endereços, a segurança, a configuração automática, a necessidade de extensibilidade e outros.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-104">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="cc6ec-105">O IPv6 expande os recursos da Internet para habilitar novos tipos de aplicativos, inclusive aplicativos móveis e de ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-105">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="cc6ec-106">Estes são os principais problemas do protocolo IPv4 atual:</span><span class="sxs-lookup"><span data-stu-id="cc6ec-106">The following are the main issues of the current IPv4 protocol:</span></span>  
  
-   <span data-ttu-id="cc6ec-107">Rápido esgotamento do espaço de endereço.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-107">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="cc6ec-108">Isso levou ao uso de conversores de endereço de rede (NATs) que mapeiam vários endereços particulares para um único endereço IP público.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-108">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="cc6ec-109">Os principais problemas criados por esse mecanismo são a sobrecarga de processamento e a falta de conectividade de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-109">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
-   <span data-ttu-id="cc6ec-110">Falta de suporte a hierarquia.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-110">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="cc6ec-111">Por causa de sua organização de classe predefinida inerente, IPv4 não tem um verdadeiro suporte hierárquico.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-111">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="cc6ec-112">É impossível estruturar os endereços IP de uma forma que realmente mapeie a topologia de rede.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-112">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="cc6ec-113">Essa falha de design crucial cria a necessidade de grandes tabelas de roteamento para entregar pacotes IPv4 em qualquer local na Internet.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-113">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
-   <span data-ttu-id="cc6ec-114">Configuração de rede complexa.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-114">Complex network configuration.</span></span>  
  
     <span data-ttu-id="cc6ec-115">Com o IPv4, os endereços devem ser atribuídos estaticamente ou usando um protocolo de configuração, como o DHCP.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-115">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="cc6ec-116">Em uma situação ideal, hosts não precisariam depender da administração de uma infraestrutura DHCP.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-116">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="cc6ec-117">Em vez disso, eles poderiam configurar a si mesmos com base no segmento de rede no qual estivessem localizados.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-117">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
-   <span data-ttu-id="cc6ec-118">Falta de autenticação interna e de confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-118">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="cc6ec-119">O IPv4 não requer suporte para nenhum outro mecanismo que fornece autenticação ou criptografia dos dados transmitidos.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-119">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="cc6ec-120">Isso muda com o IPv6.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-120">This changes with IPv6.</span></span> <span data-ttu-id="cc6ec-121">O protocolo IPsec é um requisito de suporte a IPv6.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-121">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="cc6ec-122">Um novo pacote de protocolos deve atender aos seguintes requisitos básicos:</span><span class="sxs-lookup"><span data-stu-id="cc6ec-122">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
-   <span data-ttu-id="cc6ec-123">Roteamento em larga escala e endereçamento com pouca sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-123">Large-scale routing and addressing with low overhead.</span></span>  
  
-   <span data-ttu-id="cc6ec-124">Configuração automática para situações de conexão diversas.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-124">Auto-configuration for various connecting situations.</span></span>  
  
-   <span data-ttu-id="cc6ec-125">Autenticação interna e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-125">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="cc6ec-126">Para obter mais informações, confira [Endereçamento IPv6](../../../docs/framework/network-programming/ipv6-addressing.md), [Roteamento IPv6](../../../docs/framework/network-programming/ipv6-routing.md), [Configuração automática do IPv6](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Habilitando e desabilitando o IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md) e [Como: Modificar o arquivo de configuração do computador para habilitar o suporte ao IPv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="cc6ec-126">For more information, see [IPv6 Addressing](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 Auto-Configuration](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Enabling and Disabling IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="cc6ec-127">Referências</span><span class="sxs-lookup"><span data-stu-id="cc6ec-127">References</span></span>  
 <span data-ttu-id="cc6ec-128">Veja a seguir documentos do RFC selecionados que podem ser encontrados no site da [IETF (Internet Engineering Task Force)](https://www.ietf.org/):</span><span class="sxs-lookup"><span data-stu-id="cc6ec-128">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
-   <span data-ttu-id="cc6ec-129">RFC 1287, voltado a arquitetura de Internet futura.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-129">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
-   <span data-ttu-id="cc6ec-130">RFC 1454, comparação de propostas para a próxima versão do IP.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-130">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
-   <span data-ttu-id="cc6ec-131">RFC 2373, arquitetura de endereçamento do IP versão 6.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-131">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
-   <span data-ttu-id="cc6ec-132">RFC 2374, um formato de endereço unicast global agregável IPv6.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-132">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="cc6ec-133">Você também pode encontrar informações relacionadas ao IPv6 em [Versão 6 do IP (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span><span class="sxs-lookup"><span data-stu-id="cc6ec-133">You can also find IPv6-related information on the [IP Version 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc6ec-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc6ec-134">See also</span></span>

- [<span data-ttu-id="cc6ec-135">Amostra de soquetes IPv6</span><span class="sxs-lookup"><span data-stu-id="cc6ec-135">IPv6 Sockets Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [<span data-ttu-id="cc6ec-136">Amostras de programação de rede</span><span class="sxs-lookup"><span data-stu-id="cc6ec-136">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
- [<span data-ttu-id="cc6ec-137">Soquetes</span><span class="sxs-lookup"><span data-stu-id="cc6ec-137">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
