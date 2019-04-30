---
title: Publicando pontos de extremidade de metadados
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 143a46ce18a0d9dee89bbbffac9be9a467e951df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955149"
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="de2c8-102">Publicando pontos de extremidade de metadados</span><span class="sxs-lookup"><span data-stu-id="de2c8-102">Publishing Metadata Endpoints</span></span>
<span data-ttu-id="de2c8-103">Serviços Windows Communication Foundation (WCF) publicam metadados, um ou mais pontos de extremidade de metadados de publicação.</span><span class="sxs-lookup"><span data-stu-id="de2c8-103">Windows Communication Foundation (WCF) services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="de2c8-104">Publicação de metadados de serviço disponibiliza os metadados usando protocolos padronizados, como solicitações de WS-MetadataExchange (MEX) e HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="de2c8-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="de2c8-105">Pontos de extremidade de metadados são semelhantes aos outros pontos de extremidade de serviço que têm um endereço, uma ligação e um contrato, e eles podem ser adicionados a um host de serviço por meio da configuração ou no código.</span><span class="sxs-lookup"><span data-stu-id="de2c8-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="de2c8-106">Para habilitar a publicação pontos de extremidade de metadados, você deve adicionar o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportamento para o serviço de serviço.</span><span class="sxs-lookup"><span data-stu-id="de2c8-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="de2c8-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="de2c8-107">In This Section</span></span>  
 [<span data-ttu-id="de2c8-108">Como: Publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="de2c8-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="de2c8-109">Demonstra como configurar um serviço WCF para publicar metadados para que os clientes podem recuperar os metadados usando um WS-MetadataExchange ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="de2c8-109">Demonstrates how to configure a WCF service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="de2c8-110">Como: Publicar metadados para um serviço usando código</span><span class="sxs-lookup"><span data-stu-id="de2c8-110">How to: Publish Metadata for a Service Using Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="de2c8-111">Demonstra como habilitar a publicação de metadados para um serviço WCF em código para que os clientes podem recuperar os metadados usando um WS-MetadataExchange ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="de2c8-111">Demonstrates how to enable metadata publishing for a WCF service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de2c8-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de2c8-112">See also</span></span>

- [<span data-ttu-id="de2c8-113">Publicando metadados</span><span class="sxs-lookup"><span data-stu-id="de2c8-113">Publishing Metadata</span></span>](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
