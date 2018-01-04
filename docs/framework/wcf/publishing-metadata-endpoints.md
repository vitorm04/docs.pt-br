---
title: Publicando pontos de extremidade de metadados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f4d7d99304df1622f482a827d67d389760bf76d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="f638e-102">Publicando pontos de extremidade de metadados</span><span class="sxs-lookup"><span data-stu-id="f638e-102">Publishing Metadata Endpoints</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="f638e-103">Serviços de publicar metadados por um ou mais pontos de extremidade de metadados de publicação.</span><span class="sxs-lookup"><span data-stu-id="f638e-103"> services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="f638e-104">Metadados de serviço de publicação disponibiliza os metadados usando protocolos padronizados, como solicitações de WS-MetadataExchange (MEX) e HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="f638e-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="f638e-105">Pontos de extremidade de metadados são semelhantes aos outros pontos de extremidade de serviço que têm um endereço, uma ligação e um contrato e podem ser adicionadas a um host de serviço por meio de configuração ou em código.</span><span class="sxs-lookup"><span data-stu-id="f638e-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="f638e-106">Para habilitar a publicação pontos de extremidade de metadados, você deve adicionar o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportamento para o serviço de serviço.</span><span class="sxs-lookup"><span data-stu-id="f638e-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f638e-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f638e-107">In This Section</span></span>  
 [<span data-ttu-id="f638e-108">Como publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="f638e-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="f638e-109">Demonstra como configurar um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço para publicar metadados, de forma que os clientes podem recuperar os metadados usando um WS-MetadataExchange ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="f638e-109">Demonstrates how to configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="f638e-110">Como publicar metadados para um serviço utilizando código</span><span class="sxs-lookup"><span data-stu-id="f638e-110">How to: Publish Metadata for a Service Using Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="f638e-111">Demonstra como habilitar a publicação de metadados para um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] no código de serviço para que os clientes podem recuperar os metadados usando um WS-MetadataExchange ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="f638e-111">Demonstrates how to enable metadata publishing for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f638e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f638e-112">See Also</span></span>  
 [<span data-ttu-id="f638e-113">Publicando metadados</span><span class="sxs-lookup"><span data-stu-id="f638e-113">Publishing Metadata</span></span>](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
