---
title: Oracle e ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 5683f2b4ba57021ff6dda3a51baca016f886b605
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980074"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="c591e-102">Oracle e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c591e-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="c591e-103">Os tipos em <xref:System.Data.OracleClient> são preteridos.</span><span class="sxs-lookup"><span data-stu-id="c591e-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="c591e-104">Os tipos permanecem com suporte na versão atual do .NET Framework, mas serão removidos em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="c591e-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="c591e-105">A Microsoft recomenda que você use um provedor Oracle de terceiros.</span><span class="sxs-lookup"><span data-stu-id="c591e-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="c591e-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span><span class="sxs-lookup"><span data-stu-id="c591e-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="c591e-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span><span class="sxs-lookup"><span data-stu-id="c591e-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="c591e-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span><span class="sxs-lookup"><span data-stu-id="c591e-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="c591e-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span><span class="sxs-lookup"><span data-stu-id="c591e-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="c591e-110">Você também deve incluir uma referência à DLL ao compilar seu código.</span><span class="sxs-lookup"><span data-stu-id="c591e-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="c591e-111">Por exemplo, se você estiver criando um programa C#, sua linha de comando deverá incluir:</span><span class="sxs-lookup"><span data-stu-id="c591e-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="c591e-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c591e-112">In This Section</span></span>  
 [<span data-ttu-id="c591e-113">Requisitos do sistema</span><span class="sxs-lookup"><span data-stu-id="c591e-113">System Requirements</span></span>](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="c591e-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span><span class="sxs-lookup"><span data-stu-id="c591e-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="c591e-115">Oracle BFILEs</span><span class="sxs-lookup"><span data-stu-id="c591e-115">Oracle BFILEs</span></span>](oracle-bfiles.md)  
 <span data-ttu-id="c591e-116">Descreve a classe <xref:System.Data.OracleClient.OracleBFile>, que é usada no trabalho com o tipo de dados Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="c591e-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="c591e-117">LOBs do Oracle</span><span class="sxs-lookup"><span data-stu-id="c591e-117">Oracle LOBs</span></span>](oracle-lobs.md)  
 <span data-ttu-id="c591e-118">Descreve a classe <xref:System.Data.OracleClient.OracleLob>, que é usada para no trabalho com tipos de dados Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="c591e-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="c591e-119">REF CURSORs do Oracle</span><span class="sxs-lookup"><span data-stu-id="c591e-119">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)  
 <span data-ttu-id="c591e-120">Descreve o suporte para o tipo de dados REF CURSOR Oracle.</span><span class="sxs-lookup"><span data-stu-id="c591e-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="c591e-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="c591e-121">OracleTypes</span></span>](oracletypes.md)  
 <span data-ttu-id="c591e-122">Descreve estruturas que você pode usar para trabalhar com tipos de dados Oracle, incluindo <xref:System.Data.OracleClient.OracleNumber> e <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="c591e-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="c591e-123">Sequências da Oracle</span><span class="sxs-lookup"><span data-stu-id="c591e-123">Oracle Sequences</span></span>](oracle-sequences.md)  
 <span data-ttu-id="c591e-124">Descreve o suporte para recuperar os principais valores de sequência Oracle gerados pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="c591e-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="c591e-125">Mapeamentos de tipo de dados Oracle</span><span class="sxs-lookup"><span data-stu-id="c591e-125">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="c591e-126">Lista tipos de dados Oracle e seus mapeamentos para <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="c591e-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="c591e-127">Transações distribuídas do Oracle</span><span class="sxs-lookup"><span data-stu-id="c591e-127">Oracle Distributed Transactions</span></span>](oracle-distributed-transactions.md)  
 <span data-ttu-id="c591e-128">Descreve como o objeto <xref:System.Data.OracleClient.OracleConnection> automaticamente se inscreve em uma transação distribuída existente caso determine que uma transação está ativa.</span><span class="sxs-lookup"><span data-stu-id="c591e-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c591e-129">Seções Relacionadas</span><span class="sxs-lookup"><span data-stu-id="c591e-129">Related Sections</span></span>  
 <span data-ttu-id="c591e-130">[Securing ADO.NET Applications](securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c591e-130">[Securing ADO.NET Applications](securing-ado-net-applications.md)</span></span>  
 <span data-ttu-id="c591e-131">Descreve práticas seguras de codificação ao usar o ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c591e-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 <span data-ttu-id="c591e-132">[DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="c591e-132">[DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="c591e-133">Descreve como criar e usar `DataSets`, `DataSets` tipados, `DataTables` e `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="c591e-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 <span data-ttu-id="c591e-134">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c591e-134">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md)</span></span>  
 <span data-ttu-id="c591e-135">Descreve como trabalhar com dados no ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c591e-135">Describes how to work with data in ADO.NET.</span></span>  
  
 <span data-ttu-id="c591e-136">[SQL Server and ADO.NET](./sql/index.md) (SQL Server e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c591e-136">[SQL Server and ADO.NET](./sql/index.md)</span></span>  
 <span data-ttu-id="c591e-137">Descreve como trabalhar com recursos e funcionalidades que são específicos ao SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c591e-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="c591e-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="c591e-138">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="c591e-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c591e-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c591e-140">Veja também</span><span class="sxs-lookup"><span data-stu-id="c591e-140">See also</span></span>

- [<span data-ttu-id="c591e-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c591e-141">ADO.NET</span></span>](index.md)
- <span data-ttu-id="c591e-142">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c591e-142">[ADO.NET Overview](ado-net-overview.md)</span></span>
