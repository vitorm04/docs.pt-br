---
title: Pontos de extremidade do Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4ac3d1f16d860ea01217d0d1d35d0588da0c8d87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="f7de1-102">Pontos de extremidade do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f7de1-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="f7de1-103">Toda a comunicação com um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] serviço ocorre por meio de *pontos de extremidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="f7de1-103">All communication with a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="f7de1-104">Pontos de extremidade fornecem acesso de clientes para a funcionalidade que um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ofertas de serviço.</span><span class="sxs-lookup"><span data-stu-id="f7de1-104">Endpoints provide clients access to the functionality that a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service offers.</span></span>  
  
 <span data-ttu-id="f7de1-105">Para obter uma visão geral sobre como criar um ponto de extremidade, consulte [visão geral de criação de ponto de extremidade](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f7de1-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="f7de1-106">Cada ponto de extremidade contém:</span><span class="sxs-lookup"><span data-stu-id="f7de1-106">Each endpoint contains:</span></span>  
  
-   <span data-ttu-id="f7de1-107">Um endereço que indica onde encontrar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f7de1-107">An address that indicates where to find the endpoint.</span></span>  
  
-   <span data-ttu-id="f7de1-108">Uma associação que especifica como um cliente pode se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f7de1-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="f7de1-109">Um contrato que identifica os métodos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="f7de1-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="f7de1-110">Para obter descrições sobre como especificar essas partes individuais de um ponto de extremidade, consulte:</span><span class="sxs-lookup"><span data-stu-id="f7de1-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
-   <span data-ttu-id="f7de1-111">[Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md) (Especificando um endereço do ponto de extremidade)</span><span class="sxs-lookup"><span data-stu-id="f7de1-111">[Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md)</span></span>  
  
-   <span data-ttu-id="f7de1-112">[Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md) (Usando associações para configurar serviços e clientes)</span><span class="sxs-lookup"><span data-stu-id="f7de1-112">[Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)</span></span>  
  
-   <span data-ttu-id="f7de1-113">[Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md) (Serviços de design e implantação)</span><span class="sxs-lookup"><span data-stu-id="f7de1-113">[Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7de1-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f7de1-114">In This Section</span></span>  
 <span data-ttu-id="f7de1-115">[Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md) (Visão geral de criação de ponto de extremidade)</span><span class="sxs-lookup"><span data-stu-id="f7de1-115">[Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md)</span></span>  
 <span data-ttu-id="f7de1-116">Descreve a estrutura de um ponto de extremidade e descreve como definir um ponto de extremidade na configuração e no código, bem como usar os pontos de extremidade padrão, associações e comportamentos fornecido pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f7de1-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 <span data-ttu-id="f7de1-117">[Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md) (Especificando um endereço do ponto de extremidade)</span><span class="sxs-lookup"><span data-stu-id="f7de1-117">[Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md)</span></span>  
 <span data-ttu-id="f7de1-118">Descreve como a comunicação com um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço ocorre por meio de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f7de1-118">Describes how communication with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="f7de1-119">Como: criar um ponto de extremidade de serviço na configuração</span><span class="sxs-lookup"><span data-stu-id="f7de1-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="f7de1-120">Demonstra como criar um ponto de extremidade de serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="f7de1-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="f7de1-121">Como: criar um ponto de extremidade de serviço em código</span><span class="sxs-lookup"><span data-stu-id="f7de1-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="f7de1-122">Demonstra como criar um ponto de extremidade de serviço em código.</span><span class="sxs-lookup"><span data-stu-id="f7de1-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 <span data-ttu-id="f7de1-123">[Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md) (Publicando pontos de extremidade de metadados)</span><span class="sxs-lookup"><span data-stu-id="f7de1-123">[Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md)</span></span>  
 <span data-ttu-id="f7de1-124">Demonstra como publicar metadados, publicar pontos de extremidade de metadados na configuração e no código.</span><span class="sxs-lookup"><span data-stu-id="f7de1-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f7de1-125">Referência</span><span class="sxs-lookup"><span data-stu-id="f7de1-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="f7de1-126">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="f7de1-126">Related Sections</span></span>  
 <span data-ttu-id="f7de1-127">[Basic Programming Lifecycle](../../../docs/framework/wcf/basic-programming-lifecycle.md) (Ciclo de vida de programação básica)</span><span class="sxs-lookup"><span data-stu-id="f7de1-127">[Basic Programming Lifecycle](../../../docs/framework/wcf/basic-programming-lifecycle.md)</span></span>
