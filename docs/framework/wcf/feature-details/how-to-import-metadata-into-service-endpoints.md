---
title: 'Como: importar metadados para pontos de extremidade de serviço'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: dce65c31134c211c134cbae2b9bd8296f74b1627
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930723"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>Como: importar metadados para pontos de extremidade de serviço
Este tópico explica como importar metadados para uma coleção de pontos de extremidade de serviço e usar o serviço definido no [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). Este tópico mostra como criar um aplicativo cliente que importa os metadados do serviço e, em seguida, `Add` chama o método no serviço.  
  
### <a name="to-import-metadata-into-service-endpoints"></a>Para importar metadados em pontos de extremidade de serviço  
  
1. Declare um <xref:System.ServiceModel.EndpointAddress> objeto e inicialize-o com o Uniform Resource Identifier (URI) para o endereço de intercâmbio de metadados (MEX) do serviço.  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. Crie um <xref:System.ServiceModel.Description.MetadataExchangeClient>, passando o endereço MEX e chame <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>. Isso recupera os metadados do serviço.  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. Crie um <xref:System.ServiceModel.Description.WsdlImporter>, passando os metadados recuperados anteriormente e chame <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>. Isso gera uma coleção de <xref:System.ServiceModel.Description.ContractDescription> objetos. Você também pode chamar <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> ou <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, dependendo das suas necessidades.  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > Depois de importar os metadados, você não poderá criar um canal de cliente nem exportar os metadados. Isso ocorre porque nenhuma informação de tipo está disponível neste ponto. As informações de tipo são necessárias para realmente interagir com o serviço ou exportar metadados. Para gerar as informações de tipo, você precisa gerar o código, mostrado nas etapas 4 e 5. Como alternativa, você pode usar a <xref:System.ServiceModel.Description.MetadataResolver> classe auxiliar. Para obter mais informações, confira [Como: Use MetadataResolver para obter metadados de associação](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)dinamicamente.  
  
4. Gerar informações de tipo para cada contrato.  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. Agora você pode usar essas informações. O exemplo a seguir C# gera código-fonte.  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>Consulte também

- [Metadados](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md)
