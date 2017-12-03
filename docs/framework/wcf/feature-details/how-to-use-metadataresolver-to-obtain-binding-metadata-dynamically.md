---
title: "Como utilizar o MetadataResolver para obter metadados de associação dinamicamente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8f3d8245b9d5bf05297b4d1edfba1926d2104ce
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
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
