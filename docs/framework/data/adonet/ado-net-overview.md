---
title: Visão geral
description: Leia uma visão geral do ADO.NET em .NET Framework e leia sobre os recursos para obter explicações e exemplos mais detalhados.
ms.date: 03/30/2017
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
ms.openlocfilehash: 459e4a548a4d1358b196dc41ec495921833728d4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153489"
---
# <a name="adonet-overview"></a><span data-ttu-id="15334-103">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15334-103">ADO.NET Overview</span></span>

<span data-ttu-id="15334-104">O ADO.NET fornece acesso consistente a fontes de dados como o SQL Server e o XML, e a fontes de dados expostas através do OLE DB e do ODBC.</span><span class="sxs-lookup"><span data-stu-id="15334-104">ADO.NET provides consistent access to data sources such as SQL Server and XML, and to data sources exposed through OLE DB and ODBC.</span></span> <span data-ttu-id="15334-105">Os aplicativos do consumidor de compartilhamento de dados podem usar o ADO.NET para se conectar a essas fontes de dados, e para recuperar, manipular e atualizar os dados nelas contidos.</span><span class="sxs-lookup"><span data-stu-id="15334-105">Data-sharing consumer applications can use ADO.NET to connect to these data sources and retrieve, handle, and update the data that they contain.</span></span>  
  
 <span data-ttu-id="15334-106">O ADO.NET separa o acesso a dados da manipulação de dados em componentes discretos que podem ser usados separadamente ou em tandem.</span><span class="sxs-lookup"><span data-stu-id="15334-106">ADO.NET separates data access from data manipulation into discrete components that can be used separately or in tandem.</span></span> <span data-ttu-id="15334-107">O ADO.NET inclui os provedores de dados do .NET Framework para se conectar a um banco de dados, executar comandos e recuperar resultados.</span><span class="sxs-lookup"><span data-stu-id="15334-107">ADO.NET includes .NET Framework data providers for connecting to a database, executing commands, and retrieving results.</span></span> <span data-ttu-id="15334-108">Esses resultados são processados diretamente, colocados em um objeto <xref:System.Data.DataSet> do ADO.NET para serem expostos para o usuário ad hoc, combinados com dados de várias fontes ou passados entre as camadas.</span><span class="sxs-lookup"><span data-stu-id="15334-108">Those results are either processed directly, placed in an ADO.NET <xref:System.Data.DataSet> object in order to be exposed to the user in an ad hoc manner, combined with data from multiple sources, or passed between tiers.</span></span> <span data-ttu-id="15334-109">O objeto `DataSet` também pode ser usado independentemente de um provedor de dados .NET Framework para gerenciar o local dos dados para o aplicativo ou originado no XML.</span><span class="sxs-lookup"><span data-stu-id="15334-109">The `DataSet` object can also be used independently of a .NET Framework data provider to manage data local to the application or sourced from XML.</span></span>  
  
 <span data-ttu-id="15334-110">As classes do ADO.NET estão no System.Data.dll e são integradas às classes XML encontradas no System.Xml.dll.</span><span class="sxs-lookup"><span data-stu-id="15334-110">The ADO.NET classes are found in System.Data.dll, and are integrated with the XML classes found in System.Xml.dll.</span></span> <span data-ttu-id="15334-111">Para obter um exemplo de código que se conecta a um banco de dados do, recupera-os e exibe os dados em uma janela de console, consulte [exemplos de código ADO.net](ado-net-code-examples.md).</span><span class="sxs-lookup"><span data-stu-id="15334-111">For sample code that connects to a database, retrieves data from it, and then displays that data in a console window, see [ADO.NET Code Examples](ado-net-code-examples.md).</span></span>  
  
 <span data-ttu-id="15334-112">O ADO.NET fornece a funcionalidade para os desenvolvedores que gravam um código gerenciado semelhante à funcionalidade fornecida aos desenvolvedores COM nativos pelos objetos ActiveX Data Objects (ADO).</span><span class="sxs-lookup"><span data-stu-id="15334-112">ADO.NET provides functionality to developers who write managed code similar to the functionality provided to native component object model (COM) developers by ActiveX Data Objects (ADO).</span></span> <span data-ttu-id="15334-113">É recomendável que você use o ADO.NET, e não o ADO, para acessar dados nos aplicativos .NET.</span><span class="sxs-lookup"><span data-stu-id="15334-113">We recommend that you use ADO.NET, not ADO, for accessing data in your .NET applications.</span></span>  
  
 <span data-ttu-id="15334-114">O ADO.NET fornece o método mais direto de acesso a dados no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15334-114">ADO.NET provides the most direct method of data access within the .NET Framework.</span></span> <span data-ttu-id="15334-115">Para uma abstração de nível superior que permite que os aplicativos funcionem em um modelo conceitual em vez do modelo de armazenamento subjacente, consulte o [Entity Framework ADO.net](./ef/index.md).</span><span class="sxs-lookup"><span data-stu-id="15334-115">For a higher-level abstraction that allows applications to work against a conceptual model instead of the underlying storage model, see the [ADO.NET Entity Framework](./ef/index.md).</span></span>  
  
 <span data-ttu-id="15334-116">**Política de privacidade**: os assemblies System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll e System.Data.DataSetExtensions.dll não fazem distinção entre os dados privados de um usuário e dados não privados.</span><span class="sxs-lookup"><span data-stu-id="15334-116">**Privacy Statement**: The System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll, and System.Data.DataSetExtensions.dll assemblies do not distinguish between a user's private data and non-private data.</span></span>  <span data-ttu-id="15334-117">Esses assemblies não coletam, não armazenam nem transmitem dados privados de nenhum usuário.</span><span class="sxs-lookup"><span data-stu-id="15334-117">These assemblies do not collect, store, or transport any user's private data.</span></span> <span data-ttu-id="15334-118">No entanto, os aplicativos de terceiros podem coletar, armazenar ou transmitir dados privados de um usuário usando esses assemblies.</span><span class="sxs-lookup"><span data-stu-id="15334-118">However, third-party applications might collect, store, or transport a user's private data using these assemblies.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15334-119">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="15334-119">In This Section</span></span>  

 [<span data-ttu-id="15334-120">Arquitetura do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15334-120">ADO.NET Architecture</span></span>](ado-net-architecture.md)  
 <span data-ttu-id="15334-121">Fornece uma visão geral da arquitetura e dos componentes do ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="15334-121">Provides an overview of the architecture and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="15334-122">Opções e diretrizes da tecnologia ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15334-122">ADO.NET Technology Options and Guidelines</span></span>](ado-net-technology-options-and-guidelines.md)  
 <span data-ttu-id="15334-123">Descreve os produtos e as tecnologias incluídos na plataforma de dados de entidade.</span><span class="sxs-lookup"><span data-stu-id="15334-123">Describes the products and technologies included with the Entity Data Platform.</span></span>  
  
 [<span data-ttu-id="15334-124">LINQ e o ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15334-124">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)  
 <span data-ttu-id="15334-125">Descreve como a consulta integrada à linguagem (LINQ) é implementada no ADO.NET e fornece links para tópicos relevantes.</span><span class="sxs-lookup"><span data-stu-id="15334-125">Describes how Language-Integrated Query (LINQ) is implemented in ADO.NET and provides links to relevant topics.</span></span>  
  
 [<span data-ttu-id="15334-126">Provedores de dados .NET Framework</span><span class="sxs-lookup"><span data-stu-id="15334-126">.NET Framework Data Providers</span></span>](data-providers.md)  
 <span data-ttu-id="15334-127">Fornece uma visão geral do design do provedor de dados .NET Framework e dos provedores de dados .NET Framework incluídos no ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="15334-127">Provides an overview of the design of the .NET Framework data provider and of the .NET Framework data providers that are included with ADO.NET.</span></span>  
  
 [<span data-ttu-id="15334-128">DataSets ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15334-128">ADO.NET DataSets</span></span>](ado-net-datasets.md)  
 <span data-ttu-id="15334-129">Fornece uma visão geral do design e dos componentes do `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="15334-129">Provides an overview of the `DataSet` design and components.</span></span>  
  
 [<span data-ttu-id="15334-130">Execução lado a lado no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15334-130">Side-by-Side Execution in ADO.NET</span></span>](side-by-side-execution.md)  
 <span data-ttu-id="15334-131">Aborda as diferenças entre as versões do ADO.NET e seu efeito na execução lado a lado e na compatibilidade entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="15334-131">Discusses differences in ADO.NET versions and their effect on side-by-side execution and application compatibility.</span></span>  
  
 [<span data-ttu-id="15334-132">Exemplos de código do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15334-132">ADO.NET Code Examples</span></span>](ado-net-code-examples.md)  
 <span data-ttu-id="15334-133">Fornece exemplos de código que recuperam dados usando os provedores de dados ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="15334-133">Provides code samples that retrieve data using the ADO.NET data providers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="15334-134">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="15334-134">Related Sections</span></span>  

 [<span data-ttu-id="15334-135">Novidades no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15334-135">What's New in ADO.NET</span></span>](whats-new.md)  
 <span data-ttu-id="15334-136">Apresenta recursos que são novos no ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="15334-136">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="15334-137">Protegendo aplicativos ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15334-137">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="15334-138">Descreve práticas seguras de codificação ao usar o ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="15334-138">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="15334-139">Mapeamentos de tipos de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15334-139">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)  
 <span data-ttu-id="15334-140">Descreve os mapeamentos de tipo de dados entre os tipos de dados do .NET Framework e os provedores de dados .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15334-140">Describes data type mappings between .NET Framework data types and the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="15334-141">Recuperando e modificando dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15334-141">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="15334-142">Descreve como conectar-se a uma fonte de dados, recuperar dados e modificar dados.</span><span class="sxs-lookup"><span data-stu-id="15334-142">Describes how to connect to a data source, retrieve data, and modify data.</span></span> <span data-ttu-id="15334-143">Isso inclui `DataReaders` e `DataAdapters`.</span><span class="sxs-lookup"><span data-stu-id="15334-143">This includes `DataReaders` and `DataAdapters`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15334-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="15334-144">See also</span></span>

- [<span data-ttu-id="15334-145">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15334-145">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="15334-146">Acessando dados no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="15334-146">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
