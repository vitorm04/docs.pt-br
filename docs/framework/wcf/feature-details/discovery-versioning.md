---
title: "Controle de versão de descoberta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df5a15f740e9db4eb58ec4e410db9ef5e014fe0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="discovery-versioning"></a><span data-ttu-id="f67c6-102">Controle de versão de descoberta</span><span class="sxs-lookup"><span data-stu-id="f67c6-102">Discovery Versioning</span></span>
<span data-ttu-id="f67c6-103">Este tópico fornece uma visão geral da implementação de alguns novos recursos de descoberta.</span><span class="sxs-lookup"><span data-stu-id="f67c6-103">This topic provides a brief overview of the implementation of some new discovery features.</span></span> <span data-ttu-id="f67c6-104">Ele também fornece uma visão geral sobre como selecionar a versão de descoberta para usar.</span><span class="sxs-lookup"><span data-stu-id="f67c6-104">It also gives an overview on how to select the discovery version to use.</span></span>  
  
## <a name="discovery-versioning"></a><span data-ttu-id="f67c6-105">Controle de versão de descoberta</span><span class="sxs-lookup"><span data-stu-id="f67c6-105">Discovery Versioning</span></span>  
 <span data-ttu-id="f67c6-106">O recurso de descoberta inclui suporte para três versões do protocolo WS_Discovery.</span><span class="sxs-lookup"><span data-stu-id="f67c6-106">The discovery feature includes support for three versions of the WS_Discovery protocol.</span></span> <span data-ttu-id="f67c6-107">A descoberta de APIs permitem que você selecione qual versão do protocolo que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="f67c6-107">The discovery APIs allow you to select which version of the protocol you want to use.</span></span> <span data-ttu-id="f67c6-108">Este documento descreve brevemente as configurações relacionadas ao controle de versão.</span><span class="sxs-lookup"><span data-stu-id="f67c6-108">This document briefly describes the versioning-related settings.</span></span>  
  
 <span data-ttu-id="f67c6-109">As classes de descoberta a seguir agora têm um <xref:System.ServiceModel.Discovery.DiscoveryVersion> propriedade e execute um <xref:System.ServiceModel.Discovery.DiscoveryVersion> argumento em seus construtores:</span><span class="sxs-lookup"><span data-stu-id="f67c6-109">The following Discovery classes now have a <xref:System.ServiceModel.Discovery.DiscoveryVersion> property and take a <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument in their constructors:</span></span>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
### <a name="discoveryversionwsdiscoveryapril2005"></a><span data-ttu-id="f67c6-110">DiscoveryVersion.WSDiscoveryApril2005</span><span class="sxs-lookup"><span data-stu-id="f67c6-110">DiscoveryVersion.WSDiscoveryApril2005</span></span>  
 <span data-ttu-id="f67c6-111">Fornecendo <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> como um construtor parâmetro faz com que a implementação de usar a versão April2005 do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="f67c6-111">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> as a constructor parameter makes the implementation use the April2005 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="f67c6-112">Esta versão corresponde à versão publicada da especificação do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="f67c6-112">This version corresponds to the published version of the WS-Discovery protocol specification.</span></span> <span data-ttu-id="f67c6-113">Esta versão deve ser usada para interoperar com o aplicativo herdado utilizando a versão April2005 do WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="f67c6-113">This version should be used to interoperate with legacy application utilizing the April2005 version of WS-Discovery.</span></span>  
  
### <a name="discoveryversionwsdiscovery11"></a><span data-ttu-id="f67c6-114">DiscoveryVersion.WSDiscovery11</span><span class="sxs-lookup"><span data-stu-id="f67c6-114">DiscoveryVersion.WSDiscovery11</span></span>  
 <span data-ttu-id="f67c6-115">É a versão de descoberta padrão usada pelas APIs <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span><span class="sxs-lookup"><span data-stu-id="f67c6-115">The default discovery version used by the APIs is <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span></span> <span data-ttu-id="f67c6-116">Essa é a versão atual padronizado do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="f67c6-116">This is the current standardized version of the WS-Discovery protocol.</span></span>  
  
## <a name="discoveryversionwsdiscoverycd1"></a><span data-ttu-id="f67c6-117">DiscoveryVersion.WSDiscoveryCD1</span><span class="sxs-lookup"><span data-stu-id="f67c6-117">DiscoveryVersion.WSDiscoveryCD1</span></span>  
 <span data-ttu-id="f67c6-118">Fornecendo <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> como um parâmetro de construtor utiliza a implementação do Comitê de rascunho 1 versão do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="f67c6-118">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> as a constructor parameter makes the implementation use the committee draft 1 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="f67c6-119">Esta versão do protocolo deve ser usado para interoperar com implementações executando a versão do CD 1 do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="f67c6-119">This version of the protocol should be used to interoperate with implementations running the CD1 version of the WS-Discovery protocol.</span></span>  
  
## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a><span data-ttu-id="f67c6-120">O suporte a vários pontos de extremidade de descoberta UDP para versões diferentes de descoberta em um Host de serviço único</span><span class="sxs-lookup"><span data-stu-id="f67c6-120">Supporting Multiple UDP Discovery Endpoints for Different Discovery Versions on a Single Service Host</span></span>  
 <span data-ttu-id="f67c6-121">Você talvez queira expor vários descoberta de pontos de extremidade UDP para versões diferentes de descoberta em um host de serviço único.</span><span class="sxs-lookup"><span data-stu-id="f67c6-121">You may want to expose multiple UDP Discovery Endpoints for different discovery versions on a single service host.</span></span> <span data-ttu-id="f67c6-122">Para fazer isso, você deve especificar um endereço exclusivo para cada ponto de extremidade de descoberta UDP.</span><span class="sxs-lookup"><span data-stu-id="f67c6-122">To do this you must specify a unique address for each UDP discovery endpoint.</span></span> <span data-ttu-id="f67c6-123">O exemplo a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="f67c6-123">The following example shows how to do this.</span></span>  
  
```  
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);  
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
  
newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");  
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionAril2005");  
  
serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);  
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);  
```
