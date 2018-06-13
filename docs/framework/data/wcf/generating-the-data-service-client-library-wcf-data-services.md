---
title: Gerando a biblioteca do cliente de serviço de dados (serviços de dados WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 999cbaa98c26d2d00b7e8f319ee87f8b07d7f5c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357745"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="e5df6-102">Gerando a biblioteca do cliente de serviço de dados (serviços de dados WCF)</span><span class="sxs-lookup"><span data-stu-id="e5df6-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="e5df6-103">Um serviço de dados que implementa o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] pode retornar um documento de metadados de serviço que descreve o modelo de dados exposto pelo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span><span class="sxs-lookup"><span data-stu-id="e5df6-103">A data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] can return a service metadata document that describes the data model exposed by the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="e5df6-104">Para obter mais informações, consulte [OData: documento de metadados de serviço](http://go.microsoft.com/fwlink/?LinkId=186070).</span><span class="sxs-lookup"><span data-stu-id="e5df6-104">For more information, see [OData: Service Metadata Document](http://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="e5df6-105">Você pode usar o **adicionar referência de serviço** caixa de diálogo no Visual Studio para adicionar uma referência a um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-com base em serviço.</span><span class="sxs-lookup"><span data-stu-id="e5df6-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service.</span></span> <span data-ttu-id="e5df6-106">Quando você usar essa ferramenta para adicionar uma referência para os metadados retornados por uma [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed em um projeto de cliente, ele executa as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="e5df6-106">When you use this tool to add a reference to the metadata returned by an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in a client project, it performs the following actions:</span></span>  
  
-   <span data-ttu-id="e5df6-107">Solicita o documento de metadados de serviço do serviço de dados e interpreta os metadados retornados.</span><span class="sxs-lookup"><span data-stu-id="e5df6-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e5df6-108">Os metadados retornados são armazenados no projeto do cliente como um arquivo. edmx.</span><span class="sxs-lookup"><span data-stu-id="e5df6-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="e5df6-109">Este arquivo .edmx não pode ser aberto usando o Designer de Modelo de Dados de Entidade porque não tem o mesmo formato que um arquivo .edmx usado pelo Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="e5df6-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="e5df6-110">Você pode exibir esse arquivo de metadados usando o Editor de XML ou qualquer outro editor de texto.</span><span class="sxs-lookup"><span data-stu-id="e5df6-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="e5df6-111">Para obter mais informações, consulte o [ \[MC EDMX\]: modelo de dados de entidade para formato de empacotamento de serviços de dados](http://go.microsoft.com/fwlink/?LinkID=178833) especificação</span><span class="sxs-lookup"><span data-stu-id="e5df6-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](http://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
-   <span data-ttu-id="e5df6-112">Gera uma representação do serviço como uma classe do contêiner de entidade que herda de <xref:System.Data.Services.Client.DataServiceContext>.</span><span class="sxs-lookup"><span data-stu-id="e5df6-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="e5df6-113">Essa classe do contêiner de entidade gerada parece o contêiner de entidade que as ferramentas de Modelo de Dados de Entidade geram.</span><span class="sxs-lookup"><span data-stu-id="e5df6-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="e5df6-114">Para obter mais informações, consulte [Visão geral dos serviços de objeto (Entity Framework)](http://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).</span><span class="sxs-lookup"><span data-stu-id="e5df6-114">For more information, see [Object Services Overview (Entity Framework)](http://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).</span></span>  
  
-   <span data-ttu-id="e5df6-115">Gera classes de dados para os tipos de modelo de dados que ela descobre nos metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="e5df6-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
-   <span data-ttu-id="e5df6-116">Adiciona uma referência ao assembly do `System.Data.Services.Client` ao projeto.</span><span class="sxs-lookup"><span data-stu-id="e5df6-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="e5df6-117">Para obter mais informações, consulte [como: adicionar uma referência de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e5df6-117">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="e5df6-118">As classes de serviço de dados do cliente também podem ser geradas usando o [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) ferramenta de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e5df6-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="e5df6-119">Para obter mais informações, consulte [como: manualmente gerar cliente dados Classes de serviço](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e5df6-119">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="e5df6-120">Mapeamento de tipo de dados de cliente</span><span class="sxs-lookup"><span data-stu-id="e5df6-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="e5df6-121">Quando você usa o **adicionar referência de serviço** diálogo no Visual Studio ou o `DataSvcUtil.exe` ferramenta para gerar classes de dados do cliente com base em um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, os tipos de dados do .NET Framework são mapeados para os tipos primitivos das modelo de dados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e5df6-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="e5df6-122">Tipo do modelo de dados</span><span class="sxs-lookup"><span data-stu-id="e5df6-122">Data model type</span></span>|<span data-ttu-id="e5df6-123">Tipo de dados do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e5df6-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="e5df6-124"><xref:System.Byte> `[]`</span><span class="sxs-lookup"><span data-stu-id="e5df6-124"><xref:System.Byte> `[]`</span></span>|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 <span data-ttu-id="e5df6-125">Para obter mais informações, consulte [OData: tipos de dados primitivos](http://go.microsoft.com/fwlink/?LinkId=186072).</span><span class="sxs-lookup"><span data-stu-id="e5df6-125">For more information, see [OData: Primitive Data Types](http://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5df6-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5df6-126">See Also</span></span>  
 <span data-ttu-id="e5df6-127">[WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="e5df6-127">[WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)</span></span>  
 <span data-ttu-id="e5df6-128">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)</span><span class="sxs-lookup"><span data-stu-id="e5df6-128">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)</span></span>
