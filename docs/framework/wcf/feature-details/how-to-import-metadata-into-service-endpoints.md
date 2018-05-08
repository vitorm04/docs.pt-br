---
title: Como importar metadados para pontos de extremidade de serviço
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: 88b48b95a62c000d88b302589ebc489089e77602
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>Como importar metadados para pontos de extremidade de serviço
Este tópico explica como importar metadados para uma coleção de pontos de extremidade de serviço e usar o serviço definido no [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). Neste tópico mostram como criar um aplicativo cliente que importa os metadados de serviço e, em seguida, chama o `Add` método no serviço.  
  
### <a name="to-import-metadata-into-service-endpoints"></a>Para importar metadados para pontos de extremidade de serviço  
  
1.  Declarar uma <xref:System.ServiceModel.EndpointAddress> objeto e inicializá-lo com o URI Uniform Resource Identifier () para o endereço do exchange (MEX) de metadados do serviço.  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2.  Criar um <xref:System.ServiceModel.Description.MetadataExchangeClient>, passando o endereço MEX e chamar <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>. Isso recupera os metadados do serviço.  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3.  Criar um <xref:System.ServiceModel.Description.WsdlImporter>, passando os metadados recuperados anteriormente e chame <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>. Isso gera uma coleção de <xref:System.ServiceModel.Description.ContractDescription> objetos. Você também pode chamar <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> ou <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, dependendo das suas necessidades.  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  Depois de importar os metadados, você não poderá criar um canal do cliente ou exportar os metadados. Isso ocorre porque nenhuma informação de tipo está disponível neste momento. Informações de tipo são necessárias para interagir com o serviço, na verdade, ou exportar metadados. Para gerar as informações de tipo, você precisa gerar código, como mostrado nas etapas 4 e 5. Como alternativa, você pode usar o <xref:System.ServiceModel.Description.MetadataResolver> classe auxiliar. Para obter mais informações, consulte [como: Use o MetadataResolver para obter dinamicamente metadados associação](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).  
  
4.  Gere informações de tipo para cada contrato.  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5.  Agora você pode usar essas informações. O exemplo a seguir gera o código-fonte c#.  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>Consulte também  
 [Metadados](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md)
