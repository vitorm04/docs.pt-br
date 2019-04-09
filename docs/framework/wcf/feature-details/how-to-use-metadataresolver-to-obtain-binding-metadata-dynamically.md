---
title: 'Como: usar MetadataResolver para obter metadados de associação dinamicamente'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: d8efe2522d17829cc42d8ed1304983f6da46fb58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111196"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Como: usar MetadataResolver para obter metadados de associação dinamicamente
Este tópico mostra como usar o <xref:System.ServiceModel.Description.MetadataResolver> classe dinamicamente obter metadados de associação.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Para obter dinamicamente a associação de metadados  
  
1.  Criar um <xref:System.ServiceModel.EndpointAddress> objeto com o endereço do ponto de extremidade de metadados.  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  Chamar <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, que passa o tipo de serviço e o endereço do ponto de extremidade de metadados. Isso retorna uma coleção de pontos de extremidade que implementam o contrato especificado. Somente as informações de associação são importadas de metadados; informações de contrato não serão importadas. O contrato fornecido será usado.  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  Em seguida, você pode iterar por meio da coleção de pontos de extremidade de serviço para extrair as informações de associação que você precisa. O código a seguir itera por meio de pontos de extremidade, cria um objeto de cliente de serviço que passa a associação e o endereço associado com o ponto de extremidade atual e, em seguida, chama um método no serviço.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Metadados](../../../../docs/framework/wcf/feature-details/metadata.md)
