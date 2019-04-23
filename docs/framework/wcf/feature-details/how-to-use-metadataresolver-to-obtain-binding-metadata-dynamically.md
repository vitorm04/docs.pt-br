---
title: 'Como: usar MetadataResolver para obter metadados de associação dinamicamente'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 3fe09699304de42ed00312f50f3b9e0edb20615d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298923"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="2d4af-102">Como: usar MetadataResolver para obter metadados de associação dinamicamente</span><span class="sxs-lookup"><span data-stu-id="2d4af-102">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>
<span data-ttu-id="2d4af-103">Este tópico mostra como usar o <xref:System.ServiceModel.Description.MetadataResolver> classe dinamicamente obter metadados de associação.</span><span class="sxs-lookup"><span data-stu-id="2d4af-103">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="2d4af-104">Para obter dinamicamente a associação de metadados</span><span class="sxs-lookup"><span data-stu-id="2d4af-104">To dynamically obtain binding metadata</span></span>  
  
1. <span data-ttu-id="2d4af-105">Criar um <xref:System.ServiceModel.EndpointAddress> objeto com o endereço do ponto de extremidade de metadados.</span><span class="sxs-lookup"><span data-stu-id="2d4af-105">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. <span data-ttu-id="2d4af-106">Chamar <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, que passa o tipo de serviço e o endereço do ponto de extremidade de metadados.</span><span class="sxs-lookup"><span data-stu-id="2d4af-106">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="2d4af-107">Isso retorna uma coleção de pontos de extremidade que implementam o contrato especificado.</span><span class="sxs-lookup"><span data-stu-id="2d4af-107">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="2d4af-108">Somente as informações de associação são importadas de metadados; informações de contrato não serão importadas.</span><span class="sxs-lookup"><span data-stu-id="2d4af-108">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="2d4af-109">O contrato fornecido será usado.</span><span class="sxs-lookup"><span data-stu-id="2d4af-109">The supplied contract is used instead.</span></span>  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. <span data-ttu-id="2d4af-110">Em seguida, você pode iterar por meio da coleção de pontos de extremidade de serviço para extrair as informações de associação que você precisa.</span><span class="sxs-lookup"><span data-stu-id="2d4af-110">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="2d4af-111">O código a seguir itera por meio de pontos de extremidade, cria um objeto de cliente de serviço que passa a associação e o endereço associado com o ponto de extremidade atual e, em seguida, chama um método no serviço.</span><span class="sxs-lookup"><span data-stu-id="2d4af-111">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
    ```  
    foreach (ServiceEndpoint point in endpoints)  
    {  
       if (point != null)  
       {  
          // Create a new wcfClient using retrieved endpoints.  
          using (wcfClient = new SampleServiceClient(point.Binding, point.Address))  
          {  
             Console.WriteLine(  
               wcfClient.SampleMethod("Client used the "  
               + point.Address.ToString() + " address."));  
          }  
      }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2d4af-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d4af-112">See also</span></span>

- [<span data-ttu-id="2d4af-113">Metadados</span><span class="sxs-lookup"><span data-stu-id="2d4af-113">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
