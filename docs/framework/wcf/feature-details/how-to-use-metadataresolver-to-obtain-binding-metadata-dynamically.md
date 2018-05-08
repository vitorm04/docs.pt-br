---
title: Como utilizar o MetadataResolver para obter metadados de associação dinamicamente
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: cffe47f301c1943a0d97e3a95a5b7c24979b4f69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Como utilizar o MetadataResolver para obter metadados de associação dinamicamente
Este tópico mostra como usar o <xref:System.ServiceModel.Description.MetadataResolver> classe dinamicamente obter metadados de associação.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Para obter o metadados de associação dinamicamente  
  
1.  Criar um <xref:System.ServiceModel.EndpointAddress> objeto com o endereço do ponto de extremidade de metadados.  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  Chamar <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, que passa o tipo de serviço e o endereço de ponto de extremidade de metadados. Isso retorna uma coleção de pontos de extremidade que implementam o contrato especificado. Somente as informações de associação são importadas de metadados; informações de contrato não serão importadas. O contrato fornecido será usado.  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  Em seguida, você pode iterar através da coleção de pontos de extremidade de serviço para extrair as informações de associação que você precisa. O código a seguir itera por meio de pontos de extremidade, cria um objeto de cliente de serviço que passa a associação e o endereço associado ao ponto de extremidade atual e, em seguida, chama um método no serviço.  
  
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
 [Metadados](../../../../docs/framework/wcf/feature-details/metadata.md)
