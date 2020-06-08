---
title: Protocolo PNRP
description: Saiba mais sobre o PNRP (Peer Name Resolution Protocol), um protocolo de registro de nome seguro, escalonável e dinâmico e resolução de nomes.
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: 72eb63c2c90f398c515d77cd2b2d693237e533a5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502217"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="c4d99-103">Protocolo PNRP</span><span class="sxs-lookup"><span data-stu-id="c4d99-103">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="c4d99-104">Em ambientes de ponto a ponto, pares usam sistemas de resolução de nome específicos para resolver os locais de rede (endereços, protocolos e portas) uns dos outros, com base em nomes ou outros tipos de identificadores.</span><span class="sxs-lookup"><span data-stu-id="c4d99-104">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="c4d99-105">No passado, a resolução de nome de par foi complicada devido à conectividade inerentemente transitória, bem como outras falhas dentro do sistema DNS (Sistema de Nomes de Domínio).</span><span class="sxs-lookup"><span data-stu-id="c4d99-105">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="c4d99-106">A plataforma de rede ponto a ponto do Microsoft® Windows® resolve esse problema com o protocolo PNRP, um protocolo de registro de nomes e de resolução de nomes seguro, escalonável e dinâmico desenvolvido primeiro para o Windows XP e depois atualizado para o Windows Vista™.</span><span class="sxs-lookup"><span data-stu-id="c4d99-106">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="c4d99-107">O PNRP funciona de forma muito diferente dos sistemas de resolução de nome tradicionais, abrindo incríveis novas possibilidades para desenvolvedores de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c4d99-107">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="c4d99-108">Com o PNRP, nomes de par podem ser aplicados ao computador ou a serviços ou aplicativos individuais no computador.</span><span class="sxs-lookup"><span data-stu-id="c4d99-108">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="c4d99-109">Uma resolução de nome de par inclui um endereço, porta e possivelmente uma carga estendida.</span><span class="sxs-lookup"><span data-stu-id="c4d99-109">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="c4d99-110">Os benefícios do sistema incluem a tolerância a falhas, nenhum gargalo e também resoluções de nome que nunca retornarão endereços obsoletos, o que torna o protocolo de uma solução excelente para localizar usuários móveis.</span><span class="sxs-lookup"><span data-stu-id="c4d99-110">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="c4d99-111">Em termos de segurança, os nomes de par podem ser publicados como seguros (protegidos) ou não seguros (desprotegidos).</span><span class="sxs-lookup"><span data-stu-id="c4d99-111">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="c4d99-112">O PNRP usa criptografia de chave pública para proteger os nomes de par segura contra falsificação; tanto computadores quanto serviços podem ser nomeados com PNRP.</span><span class="sxs-lookup"><span data-stu-id="c4d99-112">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="c4d99-113">O protocolo PNRP demonstra as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c4d99-113">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
- <span data-ttu-id="c4d99-114">Distribuído e quase que totalmente sem servidor.</span><span class="sxs-lookup"><span data-stu-id="c4d99-114">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="c4d99-115">Servidores só são necessários para o processo de inicialização.</span><span class="sxs-lookup"><span data-stu-id="c4d99-115">Servers are only required for the bootstrapping process.</span></span>  
  
- <span data-ttu-id="c4d99-116">Publicação de nome segura sem o envolvimento de terceiros.</span><span class="sxs-lookup"><span data-stu-id="c4d99-116">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="c4d99-117">Ao contrário da publicação de nome DNS, a publicação de nome PNRP é instantânea e sem custos financeiros.</span><span class="sxs-lookup"><span data-stu-id="c4d99-117">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
- <span data-ttu-id="c4d99-118">O PNRP é atualizado em tempo real, o que impede a resolução de endereços obsoletos.</span><span class="sxs-lookup"><span data-stu-id="c4d99-118">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
- <span data-ttu-id="c4d99-119">A resolução de nomes por meio de PNRP vai além de computadores, permitindo também a resolução de nomes de serviços.</span><span class="sxs-lookup"><span data-stu-id="c4d99-119">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="c4d99-120">O namespace System.Net.PeerToPeer</span><span class="sxs-lookup"><span data-stu-id="c4d99-120">The System.Net.PeerToPeer namespace</span></span>  
  
- <span data-ttu-id="c4d99-121">A funcionalidade do protocolo PNRP é definida pelo namespace <xref:System.Net.PeerToPeer> dentro do .NET Framework versão 3.5.</span><span class="sxs-lookup"><span data-stu-id="c4d99-121">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="c4d99-122">Ele fornece um conjunto de tipos que podem ser usados para registrar e resolver os nomes de ponto a ponto com um serviço PNRP disponível.</span><span class="sxs-lookup"><span data-stu-id="c4d99-122">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
- <span data-ttu-id="c4d99-123">(PNRP e resolvedores de par personalizados podem ser criados e instanciados usando os tipos fornecidos no namespace <xref:System.ServiceModel.PeerResolvers>.)</span><span class="sxs-lookup"><span data-stu-id="c4d99-123">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
- <span data-ttu-id="c4d99-124">Os tipos básicos usados para registrar e resolver os nomes com um serviço PNRP disponível são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="c4d99-124">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
- <span data-ttu-id="c4d99-125"><xref:System.Net.PeerToPeer.Cloud>: define as informações que descrevem uma nuvem PNRP disponíveis, incluindo o escopo dela.</span><span class="sxs-lookup"><span data-stu-id="c4d99-125"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
- <span data-ttu-id="c4d99-126"><xref:System.Net.PeerToPeer.PeerName>: define um nome de par que pode ser usado para registrar e subsequentemente resolver um par em uma nuvem.</span><span class="sxs-lookup"><span data-stu-id="c4d99-126"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
- <span data-ttu-id="c4d99-127"><xref:System.Net.PeerToPeer.PeerNameRecord>: Define o registro na nuvem PNRP que contém as informações de registro para um par, o que inclui os pontos de extremidade de rede em que o par pode ser contatado.</span><span class="sxs-lookup"><span data-stu-id="c4d99-127"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
- <span data-ttu-id="c4d99-128"><xref:System.Net.PeerToPeer.PeerNameRegistration>: define o processo de registro para um nome de par, incluindo métodos para iniciar e parar o registro de nome de par.</span><span class="sxs-lookup"><span data-stu-id="c4d99-128"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
- <span data-ttu-id="c4d99-129"><xref:System.Net.PeerToPeer.PeerNameResolver>: Define o processo de resolução de um nome de par para o respectivo ponto de extremidade da rede, incluindo métodos síncronos e assíncronos para a resolução.</span><span class="sxs-lookup"><span data-stu-id="c4d99-129"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d99-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="c4d99-130">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="c4d99-131">Amostras de programação de rede</span><span class="sxs-lookup"><span data-stu-id="c4d99-131">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
