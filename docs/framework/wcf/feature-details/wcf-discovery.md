---
title: Descoberta de WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fda50f14d9003b81f93840571b8b27f874f7730b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-discovery"></a><span data-ttu-id="dfc52-102">Descoberta de WCF</span><span class="sxs-lookup"><span data-stu-id="dfc52-102">WCF Discovery</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="dfc52-103">fornece suporte para habilitar o serviço seja detectável em tempo de execução de uma maneira interoperável usando o protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="dfc52-103"> provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc52-104">serviços podem anunciar a disponibilidade de rede usando uma mensagem de multicast ou em um servidor de proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="dfc52-104"> services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="dfc52-105">Aplicativos cliente podem pesquisar a rede ou um servidor de proxy de descoberta para localizar os serviços que atendem a um conjunto de critérios.</span><span class="sxs-lookup"><span data-stu-id="dfc52-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="dfc52-106">Os tópicos nesta seção fornecem uma visão geral e descrevem o modelo de programação para esse recurso em detalhes.</span><span class="sxs-lookup"><span data-stu-id="dfc52-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dfc52-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="dfc52-107">In This Section</span></span>  
 [<span data-ttu-id="dfc52-108">Visão geral de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="dfc52-108">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 <span data-ttu-id="dfc52-109">Fornece uma visão geral do suporte do WS-Discovery fornecido por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dfc52-109">Provides an overview of WS-Discovery support provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="dfc52-110">Modelo de objeto de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="dfc52-110">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)  
 <span data-ttu-id="dfc52-111">Descreve as classes no modelo de objeto de extensibilidade de suporte do WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="dfc52-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="dfc52-112">Como: adicionar programaticamente a capacidade de descoberta para um cliente e de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="dfc52-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="dfc52-113">Mostra como fazer um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço detectável.</span><span class="sxs-lookup"><span data-stu-id="dfc52-113">Shows how to make a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service discoverable.</span></span>  
  
 [<span data-ttu-id="dfc52-114">Implementando um Proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="dfc52-114">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 <span data-ttu-id="dfc52-115">Descreve as etapas necessárias para implementar um proxy de descoberta, um serviço de descoberta que registra com o proxy de descoberta e um cliente que usa o proxy de descoberta para localizar o serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="dfc52-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="dfc52-116">Controle de versão de descoberta</span><span class="sxs-lookup"><span data-stu-id="dfc52-116">Discovery Versioning</span></span>](../../../../docs/framework/wcf/feature-details/discovery-versioning.md)  
 <span data-ttu-id="dfc52-117">Fornece uma visão geral de uma implementação de protótipo de alguns novos recursos de descoberta.</span><span class="sxs-lookup"><span data-stu-id="dfc52-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="dfc52-118">Ele também fornece uma visão geral sobre como selecionar a versão de descoberta para usar.</span><span class="sxs-lookup"><span data-stu-id="dfc52-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="dfc52-119">Configurando a descoberta em um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="dfc52-119">Configuring Discovery in a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="dfc52-120">Mostra como configurar a descoberta na configuração.</span><span class="sxs-lookup"><span data-stu-id="dfc52-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="dfc52-121">Usando o canal cliente Discovery</span><span class="sxs-lookup"><span data-stu-id="dfc52-121">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 <span data-ttu-id="dfc52-122">Mostra como usar um canal de cliente de descoberta ao escrever um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="dfc52-122">Shows how to use a Discovery Client Channel when writing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span>
