---
title: Descoberta de WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 63c6589cb2ecff9f0a5e7c8bb61b454f6516c98c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600173"
---
# <a name="wcf-discovery"></a><span data-ttu-id="58c5f-102">Descoberta de WCF</span><span class="sxs-lookup"><span data-stu-id="58c5f-102">WCF Discovery</span></span>
<span data-ttu-id="58c5f-103">O Windows Communication Foundation (WCF) fornece suporte para permitir que os serviços sejam detectáveis em tempo de execução de maneira interoperável usando o protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="58c5f-103">Windows Communication Foundation (WCF) provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> <span data-ttu-id="58c5f-104">Os serviços WCF podem anunciar sua disponibilidade na rede usando uma mensagem multicast ou um servidor proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="58c5f-104">WCF services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="58c5f-105">Os aplicativos cliente podem pesquisar a rede ou um servidor proxy de descoberta para encontrar serviços que atendam a um conjunto de critérios.</span><span class="sxs-lookup"><span data-stu-id="58c5f-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="58c5f-106">Os tópicos nesta seção fornecem uma visão geral e descrevem o modelo de programação para esse recurso em detalhes.</span><span class="sxs-lookup"><span data-stu-id="58c5f-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="58c5f-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="58c5f-107">In This Section</span></span>  
 [<span data-ttu-id="58c5f-108">Visão geral de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="58c5f-108">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)  
 <span data-ttu-id="58c5f-109">Fornece uma visão geral do suporte ao WS-Discovery fornecido pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="58c5f-109">Provides an overview of WS-Discovery support provided by WCF.</span></span>  
  
 [<span data-ttu-id="58c5f-110">Modelo de objeto de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="58c5f-110">WCF Discovery Object Model</span></span>](wcf-discovery-object-model.md)  
 <span data-ttu-id="58c5f-111">Descreve as classes no modelo de objeto e extensibilidade do suporte a WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="58c5f-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="58c5f-112">Como adicionar programaticamente a capacidade de descoberta para um cliente e serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="58c5f-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="58c5f-113">Mostra como tornar um serviço Windows Communication Foundation (WCF) detectável.</span><span class="sxs-lookup"><span data-stu-id="58c5f-113">Shows how to make a Windows Communication Foundation (WCF) service discoverable.</span></span>  
  
 [<span data-ttu-id="58c5f-114">Implementando um proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="58c5f-114">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)  
 <span data-ttu-id="58c5f-115">Descreve as etapas necessárias para implementar um proxy de descoberta, um serviço detectável que registra com o proxy de descoberta e um cliente que usa o proxy de descoberta para encontrar o serviço detectável.</span><span class="sxs-lookup"><span data-stu-id="58c5f-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="58c5f-116">Controle de versão de descoberta</span><span class="sxs-lookup"><span data-stu-id="58c5f-116">Discovery Versioning</span></span>](discovery-versioning.md)  
 <span data-ttu-id="58c5f-117">Fornece uma breve visão geral de uma implementação de protótipo de alguns novos recursos de descoberta.</span><span class="sxs-lookup"><span data-stu-id="58c5f-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="58c5f-118">Ele também fornece uma visão geral de como selecionar a versão de descoberta a ser usada.</span><span class="sxs-lookup"><span data-stu-id="58c5f-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="58c5f-119">Configurando a descoberta em um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="58c5f-119">Configuring Discovery in a Configuration File</span></span>](configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="58c5f-120">Mostra como configurar a descoberta na configuração.</span><span class="sxs-lookup"><span data-stu-id="58c5f-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="58c5f-121">Usando o canal cliente Discovery</span><span class="sxs-lookup"><span data-stu-id="58c5f-121">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)  
 <span data-ttu-id="58c5f-122">Mostra como usar um canal de cliente de descoberta ao gravar um aplicativo cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="58c5f-122">Shows how to use a Discovery Client Channel when writing a WCF client application.</span></span>
