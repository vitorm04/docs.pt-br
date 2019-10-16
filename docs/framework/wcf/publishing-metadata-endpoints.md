---
title: Publicando pontos de extremidade de metadados
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 4c6ac81f0c97415dc21ff3346178dd1e9936b7a5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319903"
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="11998-102">Publicando pontos de extremidade de metadados</span><span class="sxs-lookup"><span data-stu-id="11998-102">Publishing Metadata Endpoints</span></span>
<span data-ttu-id="11998-103">Os serviços Windows Communication Foundation (WCF) publicam metadados publicando um ou mais pontos de extremidade de metadados.</span><span class="sxs-lookup"><span data-stu-id="11998-103">Windows Communication Foundation (WCF) services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="11998-104">A publicação de metadados de serviço torna os metadados disponíveis usando protocolos padronizados, como WS-MetadataExchange (MEX) e solicitações HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="11998-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="11998-105">Os pontos de extremidade de metadados são semelhantes a outros pontos de extremidade de serviço, pois têm um endereço, uma associação e um contrato, e podem ser adicionados a um host de serviço por meio da configuração ou no código.</span><span class="sxs-lookup"><span data-stu-id="11998-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="11998-106">Para habilitar a publicação de pontos de extremidade de metadados, você deve adicionar o comportamento de serviço <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ao serviço.</span><span class="sxs-lookup"><span data-stu-id="11998-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11998-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="11998-107">In This Section</span></span>  
 [<span data-ttu-id="11998-108">Como publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="11998-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="11998-109">Demonstra como configurar um serviço WCF para publicar metadados para que os clientes possam recuperar os metadados usando uma solicitação WS-MetadataExchange ou HTTP/GET usando a cadeia de caracteres de consulta `?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="11998-109">Demonstrates how to configure a WCF service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="11998-110">Como publicar metadados para um serviço utilizando código</span><span class="sxs-lookup"><span data-stu-id="11998-110">How to: Publish Metadata for a Service Using Code</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="11998-111">Demonstra como habilitar a publicação de metadados para um serviço WCF no código para que os clientes possam recuperar os metadados usando uma solicitação WS-MetadataExchange ou HTTP/GET usando a cadeia de caracteres de consulta `?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="11998-111">Demonstrates how to enable metadata publishing for a WCF service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11998-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11998-112">See also</span></span>

- [<span data-ttu-id="11998-113">Publicando metadados</span><span class="sxs-lookup"><span data-stu-id="11998-113">Publishing Metadata</span></span>](./feature-details/publishing-metadata.md)
