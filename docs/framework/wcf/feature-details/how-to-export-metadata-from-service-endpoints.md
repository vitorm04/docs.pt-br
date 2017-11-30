---
title: "Como exportar metadados para pontos de extremidade de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d076878f31d162713feaecc0a92c2f6f534897b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-export-metadata-from-service-endpoints"></a><span data-ttu-id="efbce-102">Como exportar metadados para pontos de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="efbce-102">How to: Export Metadata from Service Endpoints</span></span>
<span data-ttu-id="efbce-103">Este tópico explica como exportar metadados de pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="efbce-103">This topic explains how to export metadata from service endpoints.</span></span>  
  
### <a name="to-export-metadata-from-service-endpoints"></a><span data-ttu-id="efbce-104">Para exportar metadados de pontos de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="efbce-104">To export metadata from service endpoints</span></span>  
  
1.  <span data-ttu-id="efbce-105">Crie um projeto de aplicativo de Console novo de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="efbce-105">Create a new Visual Studio Console App Project.</span></span> <span data-ttu-id="efbce-106">Adicione o código mostrado nas etapas a seguir no arquivo Program.cs gerado no método Main ().</span><span class="sxs-lookup"><span data-stu-id="efbce-106">Add the code shown in the following steps in the generated Program.cs file within the main() method.</span></span>  
  
2.  <span data-ttu-id="efbce-107">Criará um <xref:System.ServiceModel.Description.WsdlExporter>.</span><span class="sxs-lookup"><span data-stu-id="efbce-107">Create a <xref:System.ServiceModel.Description.WsdlExporter>.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3.  <span data-ttu-id="efbce-108">Definir o <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> um dos valores de propriedade a <xref:System.ServiceModel.Description.PolicyVersion> enumeração.</span><span class="sxs-lookup"><span data-stu-id="efbce-108">Set the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to one of the values from the <xref:System.ServiceModel.Description.PolicyVersion> enumeration.</span></span> <span data-ttu-id="efbce-109">Este exemplo define o valor como <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> que corresponde ao WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="efbce-109">This sample sets the value to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> which corresponds to WS-Policy 1.5.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4.  <span data-ttu-id="efbce-110">Crie uma matriz de <xref:System.ServiceModel.Description.ServiceEndpoint> objetos.</span><span class="sxs-lookup"><span data-stu-id="efbce-110">Create an array of <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5.  <span data-ttu-id="efbce-111">Exportação de metadados para cada ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="efbce-111">Export metadata for each service endpoint.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6.  <span data-ttu-id="efbce-112">Verifique para certificar-se de que nenhum erro ocorreu durante o processo de exportação e recuperar os metadados.</span><span class="sxs-lookup"><span data-stu-id="efbce-112">Check to make sure no errors occurred during the export process and retrieve the metadata.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7.  <span data-ttu-id="efbce-113">Agora você pode usar os metadados, como gravá-la em um arquivo chamando o <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> método.</span><span class="sxs-lookup"><span data-stu-id="efbce-113">You can now use the metadata, such as write it to a file by calling the <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efbce-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="efbce-114">Example</span></span>  
 <span data-ttu-id="efbce-115">A seguir está a listagem completa de códigos deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="efbce-115">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="efbce-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="efbce-116">Compiling the Code</span></span>  
 <span data-ttu-id="efbce-117">Ao compilar referência Program.cs System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="efbce-117">When compiling Program.cs reference System.ServiceModel.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efbce-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="efbce-118">See Also</span></span>  
 [<span data-ttu-id="efbce-119">Visão geral da arquitetura de metadados</span><span class="sxs-lookup"><span data-stu-id="efbce-119">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [<span data-ttu-id="efbce-120">Uso de metadados</span><span class="sxs-lookup"><span data-stu-id="efbce-120">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [<span data-ttu-id="efbce-121">Pontos de extremidade: Endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="efbce-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
