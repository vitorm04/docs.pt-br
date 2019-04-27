---
title: Pontos de extremidade do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: b55abe937701f8708643efa2ea4cb62514b3521b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923182"
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="83804-102">Pontos de extremidade do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="83804-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="83804-103">Toda a comunicação com um serviço do Windows Communication Foundation (WCF) ocorre por meio de *pontos de extremidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="83804-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="83804-104">Pontos de extremidade de fornecem aos clientes acesso à funcionalidade que oferece um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="83804-104">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="83804-105">Para obter uma visão geral sobre como criar um ponto de extremidade, consulte [visão geral de criação de ponto de extremidade](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="83804-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="83804-106">Cada ponto de extremidade contém:</span><span class="sxs-lookup"><span data-stu-id="83804-106">Each endpoint contains:</span></span>  
  
-   <span data-ttu-id="83804-107">Um endereço que indica onde encontrar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="83804-107">An address that indicates where to find the endpoint.</span></span>  
  
-   <span data-ttu-id="83804-108">Uma associação que especifica como um cliente pode se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="83804-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="83804-109">Um contrato que identifica os métodos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="83804-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="83804-110">Para obter descrições sobre como especificar essas partes individuais de um ponto de extremidade, consulte:</span><span class="sxs-lookup"><span data-stu-id="83804-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
-   [<span data-ttu-id="83804-111">Especificando um endereço do ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="83804-111">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
-   [<span data-ttu-id="83804-112">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="83804-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
-   [<span data-ttu-id="83804-113">Serviços de design e implantação</span><span class="sxs-lookup"><span data-stu-id="83804-113">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="83804-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="83804-114">In This Section</span></span>  
 [<span data-ttu-id="83804-115">Visão geral de criação de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="83804-115">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 <span data-ttu-id="83804-116">Descreve a estrutura de um ponto de extremidade e descreve como definir um ponto de extremidade na configuração e no código, bem como usar os pontos de extremidade padrão, associações e comportamentos fornecidos pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="83804-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="83804-117">Especificando um endereço do ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="83804-117">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 <span data-ttu-id="83804-118">Descreve como a comunicação com um serviço WCF ocorre por meio de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="83804-118">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="83804-119">Como: Criar um ponto de extremidade de serviço na configuração</span><span class="sxs-lookup"><span data-stu-id="83804-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="83804-120">Demonstra como criar um ponto de extremidade de serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="83804-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="83804-121">Como: Criar um ponto de extremidade de serviço no código</span><span class="sxs-lookup"><span data-stu-id="83804-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="83804-122">Demonstra como criar um ponto de extremidade de serviço no código.</span><span class="sxs-lookup"><span data-stu-id="83804-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="83804-123">Publicando pontos de extremidade de metadados</span><span class="sxs-lookup"><span data-stu-id="83804-123">Publishing Metadata Endpoints</span></span>](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 <span data-ttu-id="83804-124">Demonstra como publicar metadados ao publicar pontos de extremidade de metadados na configuração e no código.</span><span class="sxs-lookup"><span data-stu-id="83804-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="83804-125">Referência</span><span class="sxs-lookup"><span data-stu-id="83804-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="83804-126">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="83804-126">Related Sections</span></span>  
 [<span data-ttu-id="83804-127">Ciclo de vida de programação básica</span><span class="sxs-lookup"><span data-stu-id="83804-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)
