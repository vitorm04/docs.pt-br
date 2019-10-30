---
title: Oracle e ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: a49634f712e32f873df8e47fbcb0c91dbe33fa94
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039833"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="8585a-102">Oracle e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8585a-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="8585a-103">Os tipos em <xref:System.Data.OracleClient> são preteridos.</span><span class="sxs-lookup"><span data-stu-id="8585a-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="8585a-104">Os tipos permanecem com suporte na versão atual do .NET Framework, mas serão removidos em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="8585a-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="8585a-105">A Microsoft recomenda que você use um provedor Oracle de terceiros.</span><span class="sxs-lookup"><span data-stu-id="8585a-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="8585a-106">Esta seção descreve os recursos e comportamentos específicos para o .NET Framework Provedor de Dados para Oracle.</span><span class="sxs-lookup"><span data-stu-id="8585a-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="8585a-107">O .NET Framework Provedor de Dados para Oracle fornece acesso a um banco de dados Oracle usando a interface de chamada Oracle (OCI), conforme fornecido pelo software cliente Oracle.</span><span class="sxs-lookup"><span data-stu-id="8585a-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="8585a-108">A funcionalidade do provedor de dados foi projetada para ser semelhante à do .NET Framework provedores de dados para SQL Server, OLE DB e ODBC.</span><span class="sxs-lookup"><span data-stu-id="8585a-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="8585a-109">Para usar o .NET Framework Provedor de Dados para Oracle, um aplicativo deve fazer referência ao namespace <xref:System.Data.OracleClient> da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8585a-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="8585a-110">Você também deve incluir uma referência à DLL ao compilar seu código.</span><span class="sxs-lookup"><span data-stu-id="8585a-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="8585a-111">Por exemplo, se você estiver criando um programa C#, sua linha de comando deverá incluir:</span><span class="sxs-lookup"><span data-stu-id="8585a-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="8585a-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8585a-112">In This Section</span></span>  
 [<span data-ttu-id="8585a-113">Requisitos do sistema</span><span class="sxs-lookup"><span data-stu-id="8585a-113">System Requirements</span></span>](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="8585a-114">Descreve os requisitos para usar o .NET Framework Provedor de Dados para Oracle e descreve uma série de problemas que você deve saber ao usá-lo.</span><span class="sxs-lookup"><span data-stu-id="8585a-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="8585a-115">Oracle BFILEs</span><span class="sxs-lookup"><span data-stu-id="8585a-115">Oracle BFILEs</span></span>](oracle-bfiles.md)  
 <span data-ttu-id="8585a-116">Descreve a classe <xref:System.Data.OracleClient.OracleBFile>, que é usada no trabalho com o tipo de dados Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="8585a-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="8585a-117">LOBs do Oracle</span><span class="sxs-lookup"><span data-stu-id="8585a-117">Oracle LOBs</span></span>](oracle-lobs.md)  
 <span data-ttu-id="8585a-118">Descreve a classe <xref:System.Data.OracleClient.OracleLob>, que é usada para no trabalho com tipos de dados Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="8585a-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="8585a-119">REF CURSORs do Oracle</span><span class="sxs-lookup"><span data-stu-id="8585a-119">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)  
 <span data-ttu-id="8585a-120">Descreve o suporte para o tipo de dados REF CURSOR Oracle.</span><span class="sxs-lookup"><span data-stu-id="8585a-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="8585a-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="8585a-121">OracleTypes</span></span>](oracletypes.md)  
 <span data-ttu-id="8585a-122">Descreve estruturas que você pode usar para trabalhar com tipos de dados Oracle, incluindo <xref:System.Data.OracleClient.OracleNumber> e <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="8585a-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="8585a-123">Sequências da Oracle</span><span class="sxs-lookup"><span data-stu-id="8585a-123">Oracle Sequences</span></span>](oracle-sequences.md)  
 <span data-ttu-id="8585a-124">Descreve o suporte para recuperar os principais valores de sequência Oracle gerados pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="8585a-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="8585a-125">Mapeamentos de tipo de dados Oracle</span><span class="sxs-lookup"><span data-stu-id="8585a-125">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="8585a-126">Lista tipos de dados Oracle e seus mapeamentos para <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8585a-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="8585a-127">Transações distribuídas do Oracle</span><span class="sxs-lookup"><span data-stu-id="8585a-127">Oracle Distributed Transactions</span></span>](oracle-distributed-transactions.md)  
 <span data-ttu-id="8585a-128">Descreve como o objeto <xref:System.Data.OracleClient.OracleConnection> automaticamente se inscreve em uma transação distribuída existente caso determine que uma transação está ativa.</span><span class="sxs-lookup"><span data-stu-id="8585a-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8585a-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="8585a-129">Related Sections</span></span>  
 <span data-ttu-id="8585a-130">[Securing ADO.NET Applications](securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8585a-130">[Securing ADO.NET Applications](securing-ado-net-applications.md)</span></span>  
 <span data-ttu-id="8585a-131">Descreve práticas seguras de codificação ao usar o ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8585a-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 <span data-ttu-id="8585a-132">[DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="8585a-132">[DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="8585a-133">Descreve como criar e usar `DataSets`, `DataSets` tipados, `DataTables` e `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="8585a-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 <span data-ttu-id="8585a-134">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8585a-134">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md)</span></span>  
 <span data-ttu-id="8585a-135">Descreve como trabalhar com dados no ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8585a-135">Describes how to work with data in ADO.NET.</span></span>  
  
 <span data-ttu-id="8585a-136">[SQL Server and ADO.NET](./sql/index.md) (SQL Server e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8585a-136">[SQL Server and ADO.NET](./sql/index.md)</span></span>  
 <span data-ttu-id="8585a-137">Descreve como trabalhar com recursos e funcionalidades que são específicos ao SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8585a-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="8585a-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="8585a-138">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="8585a-139">Descreve classes genéricas que permitem que você grave código independente de provedor em ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8585a-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8585a-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8585a-140">See also</span></span>

- [<span data-ttu-id="8585a-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8585a-141">ADO.NET</span></span>](index.md)
- <span data-ttu-id="8585a-142">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8585a-142">[ADO.NET Overview](ado-net-overview.md)</span></span>
