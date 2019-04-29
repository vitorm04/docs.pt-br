---
title: Oracle e ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: ce92705d22edfc832e894dd2feaafcd11088bf26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772015"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="aef32-102">Oracle e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="aef32-102">Oracle and ADO.NET</span></span>
> [!NOTE]
>  <span data-ttu-id="aef32-103">Os tipos em <xref:System.Data.OracleClient> são preteridos.</span><span class="sxs-lookup"><span data-stu-id="aef32-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="aef32-104">Os tipos permanecem com suporte na versão atual do .NET Framework, mas serão removidos em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="aef32-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="aef32-105">A Microsoft recomenda que você use um provedor Oracle de terceiros.</span><span class="sxs-lookup"><span data-stu-id="aef32-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="aef32-106">Esta seção descreve os recursos e os comportamentos que são específicos ao Provedor de Dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para Oracle.</span><span class="sxs-lookup"><span data-stu-id="aef32-106">This section describes features and behaviors that are specific to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="aef32-107">O Provedor de Dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para Oracle fornece acesso a um banco de dados Oracle usando a interface OCI (Oracle Call Interface), fornecida pelo software cliente Oracle.</span><span class="sxs-lookup"><span data-stu-id="aef32-107">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="aef32-108">A funcionalidade do provedor de dados foi projetada para ser semelhante do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedores de dados do SQL Server, OLE DB e ODBC.</span><span class="sxs-lookup"><span data-stu-id="aef32-108">The functionality of the data provider is designed to be similar to that of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="aef32-109">Para usar o Provedor de Dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para Oracle, um aplicativo deve fazer referência ao namespace <xref:System.Data.OracleClient> como a seguir:</span><span class="sxs-lookup"><span data-stu-id="aef32-109">To use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="aef32-110">Você também deve incluir uma referência à DLL ao compilar seu código.</span><span class="sxs-lookup"><span data-stu-id="aef32-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="aef32-111">Por exemplo, se você estiver criando um programa C#, sua linha de comando deverá incluir:</span><span class="sxs-lookup"><span data-stu-id="aef32-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="aef32-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="aef32-112">In This Section</span></span>  
 [<span data-ttu-id="aef32-113">Requisitos do sistema</span><span class="sxs-lookup"><span data-stu-id="aef32-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="aef32-114">Descreve requisitos de uso do Provedor de Dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para Oracle, além de uma série de questões a serem consideradas ao usá-lo.</span><span class="sxs-lookup"><span data-stu-id="aef32-114">Describes requirements for using the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="aef32-115">Oracle BFILEs</span><span class="sxs-lookup"><span data-stu-id="aef32-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="aef32-116">Descreve a classe <xref:System.Data.OracleClient.OracleBFile>, que é usada no trabalho com o tipo de dados Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="aef32-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="aef32-117">LOBs do Oracle</span><span class="sxs-lookup"><span data-stu-id="aef32-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="aef32-118">Descreve a classe <xref:System.Data.OracleClient.OracleLob>, que é usada para no trabalho com tipos de dados Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="aef32-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="aef32-119">REF CURSORs do Oracle</span><span class="sxs-lookup"><span data-stu-id="aef32-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="aef32-120">Descreve o suporte para o tipo de dados REF CURSOR Oracle.</span><span class="sxs-lookup"><span data-stu-id="aef32-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="aef32-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="aef32-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="aef32-122">Descreve estruturas que você pode usar para trabalhar com tipos de dados Oracle, incluindo <xref:System.Data.OracleClient.OracleNumber> e <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="aef32-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="aef32-123">Sequências da Oracle</span><span class="sxs-lookup"><span data-stu-id="aef32-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="aef32-124">Descreve o suporte para recuperar os principais valores de sequência Oracle gerados pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="aef32-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="aef32-125">Mapeamentos de tipo de dados Oracle</span><span class="sxs-lookup"><span data-stu-id="aef32-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="aef32-126">Lista tipos de dados Oracle e seus mapeamentos para <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="aef32-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="aef32-127">Transações distribuídas do Oracle</span><span class="sxs-lookup"><span data-stu-id="aef32-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="aef32-128">Descreve como o objeto <xref:System.Data.OracleClient.OracleConnection> automaticamente se inscreve em uma transação distribuída existente caso determine que uma transação está ativa.</span><span class="sxs-lookup"><span data-stu-id="aef32-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aef32-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="aef32-129">Related Sections</span></span>  
 <span data-ttu-id="aef32-130">[Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="aef32-130">[Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)</span></span>  
 <span data-ttu-id="aef32-131">Descreve práticas seguras de codificação ao usar o [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aef32-131">Describes secure coding practices when using [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 <span data-ttu-id="aef32-132">[DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="aef32-132">[DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="aef32-133">Descreve como criar e usar `DataSets`, `DataSets` tipados, `DataTables` e `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="aef32-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 <span data-ttu-id="aef32-134">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="aef32-134">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>  
 <span data-ttu-id="aef32-135">Descreve como trabalhar com dados no ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="aef32-135">Describes how to work with data in ADO.NET.</span></span>  
  
 <span data-ttu-id="aef32-136">[SQL Server and ADO.NET](../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="aef32-136">[SQL Server and ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)</span></span>  
 <span data-ttu-id="aef32-137">Descreve como trabalhar com recursos e funcionalidades que são específicos ao SQL Server.</span><span class="sxs-lookup"><span data-stu-id="aef32-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="aef32-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="aef32-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="aef32-139">Descreve as classes genéricas que permitem que você grave código independente de provedor no [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aef32-139">Describes generic classes that allow you to write provider-independent code in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef32-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aef32-140">See also</span></span>

- [<span data-ttu-id="aef32-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="aef32-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- <span data-ttu-id="aef32-142">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="aef32-142">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
