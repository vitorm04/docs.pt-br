---
title: Gerando a biblioteca do cliente de serviço de dados (serviços de dados WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: b938e419a5a650fe0e24445c44a67aead13349fa
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348114"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="926f9-102">Gerando a biblioteca do cliente de serviço de dados (serviços de dados WCF)</span><span class="sxs-lookup"><span data-stu-id="926f9-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="926f9-103">Um serviço de dados que implementa o Protocolo Open Data (OData) pode retornar um documento de metadados de serviço que descreve o modelo de dados exposto pelo feed OData.</span><span class="sxs-lookup"><span data-stu-id="926f9-103">A data service that implements the Open Data Protocol (OData) can return a service metadata document that describes the data model exposed by the OData feed.</span></span> <span data-ttu-id="926f9-104">Para obter mais informações, consulte a seção documento de metadados de serviço no artigo [OData: Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) .</span><span class="sxs-lookup"><span data-stu-id="926f9-104">For more information, see the Service Metadata Document section in the [OData: Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) article.</span></span> <span data-ttu-id="926f9-105">Você pode usar a caixa de diálogo **Adicionar referência de serviço** no Visual Studio para adicionar uma referência a um serviço baseado em OData.</span><span class="sxs-lookup"><span data-stu-id="926f9-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an OData-based service.</span></span> <span data-ttu-id="926f9-106">Quando você usa essa ferramenta para adicionar uma referência aos metadados retornados por um feed OData em um projeto cliente, ele executa as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="926f9-106">When you use this tool to add a reference to the metadata returned by an OData feed in a client project, it performs the following actions:</span></span>  
  
- <span data-ttu-id="926f9-107">Solicita o documento de metadados de serviço do serviço de dados e interpreta os metadados retornados.</span><span class="sxs-lookup"><span data-stu-id="926f9-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="926f9-108">Os metadados retornados são armazenados no projeto do cliente como um arquivo. edmx.</span><span class="sxs-lookup"><span data-stu-id="926f9-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="926f9-109">Este arquivo .edmx não pode ser aberto usando o Designer de Modelo de Dados de Entidade porque não tem o mesmo formato que um arquivo .edmx usado pelo Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="926f9-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="926f9-110">Você pode exibir esse arquivo de metadados usando o Editor de XML ou qualquer outro editor de texto.</span><span class="sxs-lookup"><span data-stu-id="926f9-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="926f9-111">Para obter mais informações, consulte [\[MC-EDMX\]: modelo de dados de entidade para o formato de empacotamento de serviços de dados](https://docs.microsoft.com/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16).</span><span class="sxs-lookup"><span data-stu-id="926f9-111">For more information, see [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://docs.microsoft.com/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16).</span></span>
  
- <span data-ttu-id="926f9-112">Gera uma representação do serviço como uma classe do contêiner de entidade que herda de <xref:System.Data.Services.Client.DataServiceContext>.</span><span class="sxs-lookup"><span data-stu-id="926f9-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="926f9-113">Essa classe do contêiner de entidade gerada parece o contêiner de entidade que as ferramentas de Modelo de Dados de Entidade geram.</span><span class="sxs-lookup"><span data-stu-id="926f9-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="926f9-114">Para obter mais informações, consulte [Visão geral dos serviços de objeto (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="926f9-114">For more information, see [Object Services Overview (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span></span>  
  
- <span data-ttu-id="926f9-115">Gera classes de dados para os tipos de modelo de dados que ela descobre nos metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="926f9-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
- <span data-ttu-id="926f9-116">Adiciona uma referência ao assembly do `System.Data.Services.Client` ao projeto.</span><span class="sxs-lookup"><span data-stu-id="926f9-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="926f9-117">Para obter mais informações, consulte [como: adicionar uma referência de serviço de dados](how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="926f9-117">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="926f9-118">As classes de serviço de dados do cliente também podem ser geradas usando a ferramenta [datasvcutil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="926f9-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="926f9-119">Para obter mais informações, consulte [como: gerar manualmente classes de serviço de dados do cliente](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="926f9-119">For more information, see [How to: Manually Generate Client Data Service Classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="926f9-120">Mapeamento de tipo de dados de cliente</span><span class="sxs-lookup"><span data-stu-id="926f9-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="926f9-121">Quando você usa a caixa de diálogo **Adicionar referência de serviço** no Visual Studio ou a ferramenta de `DataSvcUtil.exe` para gerar classes de dados de cliente baseadas em um feed OData, os tipos de dados .NET Framework são mapeados para os tipos primitivos do modelo de dados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="926f9-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an OData feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="926f9-122">Tipo do modelo de dados</span><span class="sxs-lookup"><span data-stu-id="926f9-122">Data model type</span></span>|<span data-ttu-id="926f9-123">Tipo de dados do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="926f9-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="926f9-124"><xref:System.Byte> `[]`</span><span class="sxs-lookup"><span data-stu-id="926f9-124"><xref:System.Byte> `[]`</span></span>|  
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
  
 <span data-ttu-id="926f9-125">Para obter mais informações, consulte a seção tipos de dados primitivos no artigo [OData: Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) .</span><span class="sxs-lookup"><span data-stu-id="926f9-125">For more information, see the Primitive Data Types section in the [OData: Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) article.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="926f9-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="926f9-126">See also</span></span>

- <span data-ttu-id="926f9-127">[WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="926f9-127">[WCF Data Services Client Library](wcf-data-services-client-library.md)</span></span>
- <span data-ttu-id="926f9-128">[Quickstart](quickstart-wcf-data-services.md) (Início rápido)</span><span class="sxs-lookup"><span data-stu-id="926f9-128">[Quickstart](quickstart-wcf-data-services.md)</span></span>
