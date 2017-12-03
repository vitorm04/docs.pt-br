---
title: "Como importar metadados para pontos de extremidade de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: afc08d08a8843460972daf259027475cbbc10b66
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="b4ac7-102">Como importar metadados para pontos de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="b4ac7-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="b4ac7-103">Este tópico explica como importar metadados para uma coleção de pontos de extremidade de serviço e usar o serviço definido no [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b4ac7-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="b4ac7-104">Neste tópico mostram como criar um aplicativo cliente que importa os metadados de serviço e, em seguida, chama o `Add` método no serviço.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="b4ac7-105">Para importar metadados para pontos de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="b4ac7-105">To import metadata into service endpoints</span></span>  
  
1.  <span data-ttu-id="b4ac7-106">Declarar uma <xref:System.ServiceModel.EndpointAddress> objeto e inicializá-lo com o URI Uniform Resource Identifier () para o endereço do exchange (MEX) de metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2.  <span data-ttu-id="b4ac7-107">Criar um <xref:System.ServiceModel.Description.MetadataExchangeClient>, passando o endereço MEX e chamar <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="b4ac7-108">Isso recupera os metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3.  <span data-ttu-id="b4ac7-109">Criar um <xref:System.ServiceModel.Description.WsdlImporter>, passando os metadados recuperados anteriormente e chame <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="b4ac7-110">Isso gera uma coleção de <xref:System.ServiceModel.Description.ContractDescription> objetos.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="b4ac7-111">Você também pode chamar <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> ou <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, dependendo das suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  <span data-ttu-id="b4ac7-112">Depois de importar os metadados, você não poderá criar um canal do cliente ou exportar os metadados.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="b4ac7-113">Isso ocorre porque nenhuma informação de tipo está disponível neste momento.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="b4ac7-114">Informações de tipo são necessárias para interagir com o serviço, na verdade, ou exportar metadados.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="b4ac7-115">Para gerar as informações de tipo, você precisa gerar código, como mostrado nas etapas 4 e 5.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="b4ac7-116">Como alternativa, você pode usar o <xref:System.ServiceModel.Description.MetadataResolver> classe auxiliar.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b4ac7-117">[Como: usar o MetadataResolver para obter metadados de associação dinamicamente](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="b4ac7-117"> [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4.  <span data-ttu-id="b4ac7-118">Gere informações de tipo para cada contrato.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5.  <span data-ttu-id="b4ac7-119">Agora você pode usar essas informações.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-119">Now you can use this information.</span></span> <span data-ttu-id="b4ac7-120">O exemplo a seguir gera o código-fonte c#.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b4ac7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4ac7-121">See Also</span></span>  
 [<span data-ttu-id="b4ac7-122">Metadados</span><span class="sxs-lookup"><span data-stu-id="b4ac7-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="b4ac7-123">Introdução</span><span class="sxs-lookup"><span data-stu-id="b4ac7-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
