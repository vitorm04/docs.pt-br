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
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="a0a68-102">Como: importar metadados para pontos de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="a0a68-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="a0a68-103">Este tópico explica como importar metadados para uma coleção de pontos de extremidade de serviço e usar o serviço definido no [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a0a68-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="a0a68-104">Este tópico mostra como criar um aplicativo cliente que importa os metadados do serviço e, em seguida, `Add` chama o método no serviço.</span><span class="sxs-lookup"><span data-stu-id="a0a68-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="a0a68-105">Para importar metadados em pontos de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="a0a68-105">To import metadata into service endpoints</span></span>  
  
1. <span data-ttu-id="a0a68-106">Declare um <xref:System.ServiceModel.EndpointAddress> objeto e inicialize-o com o Uniform Resource Identifier (URI) para o endereço de intercâmbio de metadados (MEX) do serviço.</span><span class="sxs-lookup"><span data-stu-id="a0a68-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. <span data-ttu-id="a0a68-107">Crie um <xref:System.ServiceModel.Description.MetadataExchangeClient>, passando o endereço MEX e chame <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0a68-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="a0a68-108">Isso recupera os metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="a0a68-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. <span data-ttu-id="a0a68-109">Crie um <xref:System.ServiceModel.Description.WsdlImporter>, passando os metadados recuperados anteriormente e chame <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0a68-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="a0a68-110">Isso gera uma coleção de <xref:System.ServiceModel.Description.ContractDescription> objetos.</span><span class="sxs-lookup"><span data-stu-id="a0a68-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="a0a68-111">Você também pode chamar <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> ou <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, dependendo das suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="a0a68-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="a0a68-112">Depois de importar os metadados, você não poderá criar um canal de cliente nem exportar os metadados.</span><span class="sxs-lookup"><span data-stu-id="a0a68-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="a0a68-113">Isso ocorre porque nenhuma informação de tipo está disponível neste ponto.</span><span class="sxs-lookup"><span data-stu-id="a0a68-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="a0a68-114">As informações de tipo são necessárias para realmente interagir com o serviço ou exportar metadados.</span><span class="sxs-lookup"><span data-stu-id="a0a68-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="a0a68-115">Para gerar as informações de tipo, você precisa gerar o código, mostrado nas etapas 4 e 5.</span><span class="sxs-lookup"><span data-stu-id="a0a68-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="a0a68-116">Como alternativa, você pode usar a <xref:System.ServiceModel.Description.MetadataResolver> classe auxiliar.</span><span class="sxs-lookup"><span data-stu-id="a0a68-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="a0a68-117">Para obter mais informações, confira [Como: Use MetadataResolver para obter metadados de associação](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="a0a68-117">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4. <span data-ttu-id="a0a68-118">Gerar informações de tipo para cada contrato.</span><span class="sxs-lookup"><span data-stu-id="a0a68-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. <span data-ttu-id="a0a68-119">Agora você pode usar essas informações.</span><span class="sxs-lookup"><span data-stu-id="a0a68-119">Now you can use this information.</span></span> <span data-ttu-id="a0a68-120">O exemplo a seguir C# gera código-fonte.</span><span class="sxs-lookup"><span data-stu-id="a0a68-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a0a68-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0a68-121">See also</span></span>

- [<span data-ttu-id="a0a68-122">Metadados</span><span class="sxs-lookup"><span data-stu-id="a0a68-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="a0a68-123">Introdução</span><span class="sxs-lookup"><span data-stu-id="a0a68-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
