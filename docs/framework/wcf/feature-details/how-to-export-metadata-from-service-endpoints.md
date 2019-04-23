---
title: 'Como: exportar metadados para pontos de extremidade de serviço'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: 6bf2eb3d295f9cbf6a7e13a612d5846ceaa75ab4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345502"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a><span data-ttu-id="aafe3-102">Como: exportar metadados para pontos de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="aafe3-102">How to: Export Metadata from Service Endpoints</span></span>
<span data-ttu-id="aafe3-103">Este tópico explica como exportar metadados de pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="aafe3-103">This topic explains how to export metadata from service endpoints.</span></span>  
  
### <a name="to-export-metadata-from-service-endpoints"></a><span data-ttu-id="aafe3-104">Para exportar metadados de pontos de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="aafe3-104">To export metadata from service endpoints</span></span>  
  
1. <span data-ttu-id="aafe3-105">Crie um projeto de aplicativo de Console novo de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aafe3-105">Create a new Visual Studio Console App Project.</span></span> <span data-ttu-id="aafe3-106">Adicione o código mostrado nas etapas a seguir no arquivo Program.cs gerado dentro do método Main ().</span><span class="sxs-lookup"><span data-stu-id="aafe3-106">Add the code shown in the following steps in the generated Program.cs file within the main() method.</span></span>  
  
2. <span data-ttu-id="aafe3-107">Criará um <xref:System.ServiceModel.Description.WsdlExporter>.</span><span class="sxs-lookup"><span data-stu-id="aafe3-107">Create a <xref:System.ServiceModel.Description.WsdlExporter>.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3. <span data-ttu-id="aafe3-108">Defina a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> propriedade para um dos valores da <xref:System.ServiceModel.Description.PolicyVersion> enumeração.</span><span class="sxs-lookup"><span data-stu-id="aafe3-108">Set the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to one of the values from the <xref:System.ServiceModel.Description.PolicyVersion> enumeration.</span></span> <span data-ttu-id="aafe3-109">Este exemplo define o valor como <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> que corresponde ao WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="aafe3-109">This sample sets the value to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> which corresponds to WS-Policy 1.5.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4. <span data-ttu-id="aafe3-110">Criar uma matriz de <xref:System.ServiceModel.Description.ServiceEndpoint> objetos.</span><span class="sxs-lookup"><span data-stu-id="aafe3-110">Create an array of <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5. <span data-ttu-id="aafe3-111">Exporte os metadados para cada ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="aafe3-111">Export metadata for each service endpoint.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6. <span data-ttu-id="aafe3-112">Verifique para certificar-se de que nenhum erro ocorreu durante o processo de exportação e recuperar os metadados.</span><span class="sxs-lookup"><span data-stu-id="aafe3-112">Check to make sure no errors occurred during the export process and retrieve the metadata.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7. <span data-ttu-id="aafe3-113">Agora você pode usar os metadados, tais como gravá-lo em um arquivo chamando o <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> método.</span><span class="sxs-lookup"><span data-stu-id="aafe3-113">You can now use the metadata, such as write it to a file by calling the <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aafe3-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aafe3-114">Example</span></span>  
 <span data-ttu-id="aafe3-115">A seguir está a listagem completa de códigos deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="aafe3-115">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aafe3-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="aafe3-116">Compiling the Code</span></span>  
 <span data-ttu-id="aafe3-117">Ao compilar referência Program.cs ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="aafe3-117">When compiling Program.cs reference System.ServiceModel.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aafe3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aafe3-118">See also</span></span>

- [<span data-ttu-id="aafe3-119">Visão geral da arquitetura de metadados</span><span class="sxs-lookup"><span data-stu-id="aafe3-119">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="aafe3-120">Usando metadados</span><span class="sxs-lookup"><span data-stu-id="aafe3-120">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="aafe3-121">Pontos de extremidade: Endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="aafe3-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
