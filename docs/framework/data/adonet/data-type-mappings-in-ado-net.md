---
title: Mapeamentos de tipos de dados no ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b30f4e36ffd98289bb971e04b55b0249138e0efd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="data-type-mappings-in-adonet"></a><span data-ttu-id="8d6eb-102">Mapeamentos de tipos de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8d6eb-102">Data Type Mappings in ADO.NET</span></span>
<span data-ttu-id="8d6eb-103">O .NET Framework é baseado no Common Type System, que define como os tipos são declarados, usados e gerenciados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-103">The .NET Framework is based on the common type system, which defines how types are declared, used, and managed in the runtime.</span></span> <span data-ttu-id="8d6eb-104">Consiste nos tipos de valor e nos tipos de referência, que derivam do tipo de base <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-104">It consists of both value types and reference types, which all derive from the <xref:System.Object> base type.</span></span> <span data-ttu-id="8d6eb-105">Ao trabalhar com uma fonte de dados, o tipo de dados será inferido no provedor de dados se não for especificado explicitamente.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-105">When working with a data source, the data type is inferred from the data provider if it is not explicitly specified.</span></span> <span data-ttu-id="8d6eb-106">Por exemplo, um objeto <xref:System.Data.DataSet> é independente de qualquer fonte de dados específica.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-106">For example, a <xref:System.Data.DataSet> object is independent of any specific data source.</span></span> <span data-ttu-id="8d6eb-107">Os dados de um `DataSet` são recuperados de uma fonte de dados, e as alterações são persistidas de volta para a fonte de dados usando o `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-107">Data in a `DataSet` is retrieved from a data source, and changes are persisted back to the data source by using a `DataAdapter`.</span></span> <span data-ttu-id="8d6eb-108">Isso significa que quando o `DataAdapter` preenche um <xref:System.Data.DataTable> em um `DataSet` com valores de uma fonte de dados, os tipos de dados resultantes das colunas no `DataTable` são tipos [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], em vez de tipos específicos ao provedor de dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], que é usado para conectar a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-108">This means that when a `DataAdapter` fills a <xref:System.Data.DataTable> in a `DataSet` with values from a data source, the resulting data types of the columns in the `DataTable` are [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types, instead of types specific to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider that is used to connect to the data source.</span></span>  
  
 <span data-ttu-id="8d6eb-109">Da mesma forma, quando um `DataReader` retorna um valor de uma fonte de dados, o valor resultante é armazenado em uma variável local que tenha um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipo.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-109">Likewise, when a `DataReader` returns a value from a data source, the resulting value is stored in a local variable that has a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type.</span></span> <span data-ttu-id="8d6eb-110">Para ambos os `Fill` operações do `DataAdapter` e o `Get` métodos do `DataReader`, o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipo é inferido do valor retornado do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-110">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type is inferred from the value returned from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span>  
  
 <span data-ttu-id="8d6eb-111">Em vez de depender do tipo de dados inferido, você pode usar os métodos acessadores tipados do `DataReader` quando souber o tipo específico do valor que está sendo retornado.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-111">Instead of relying on the inferred data type, you can use the typed accessor methods of the `DataReader` when you know the specific type of the value being returned.</span></span> <span data-ttu-id="8d6eb-112">Os métodos acessadores tipados oferecem melhor desempenho devolvendo um valor como um tipo [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] específico, que elimina a necessidade de conversão de tipos adicionais.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-112">Typed accessor methods give you better performance by returning a value as a specific [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type, which eliminates the need for additional type conversion.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d6eb-113">Valores nulos para tipos de dados do provedor de dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] são representados por `DBNull.Value`.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-113">Null values for [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider data types are represented by `DBNull.Value`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8d6eb-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8d6eb-114">In This Section</span></span>  
 [<span data-ttu-id="8d6eb-115">Mapeamentos de tipo de dados do SQL Server</span><span class="sxs-lookup"><span data-stu-id="8d6eb-115">SQL Server Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 <span data-ttu-id="8d6eb-116">As listas inferiram mapeamentos de tipos de dados e de métodos de acessador de dados para <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-116">Lists inferred data type mappings and data accessor methods for <xref:System.Data.SqlClient>.</span></span>  
  
 [<span data-ttu-id="8d6eb-117">Mapeamentos de tipo de dados do OLE DB</span><span class="sxs-lookup"><span data-stu-id="8d6eb-117">OLE DB Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 <span data-ttu-id="8d6eb-118">As listas inferiram mapeamentos de tipos de dados e de métodos de acessador de dados para <xref:System.Data.OleDb>.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-118">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OleDb>.</span></span>  
  
 [<span data-ttu-id="8d6eb-119">Mapeamentos de tipo de dados ODBC</span><span class="sxs-lookup"><span data-stu-id="8d6eb-119">ODBC Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 <span data-ttu-id="8d6eb-120">As listas inferiram mapeamentos de tipos de dados e de métodos de acessador de dados para <xref:System.Data.Odbc>.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-120">Lists inferred data type mappings and data accessor methods for <xref:System.Data.Odbc>.</span></span>  
  
 [<span data-ttu-id="8d6eb-121">Mapeamentos de tipo de dados Oracle</span><span class="sxs-lookup"><span data-stu-id="8d6eb-121">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="8d6eb-122">As listas inferiram mapeamentos de tipos de dados e de métodos de acessador de dados para <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-122">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OracleClient>.</span></span>  
  
 [<span data-ttu-id="8d6eb-123">Números de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="8d6eb-123">Floating-Point Numbers</span></span>](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 <span data-ttu-id="8d6eb-124">Descreve os problemas que os desenvolvedores geralmente encontram ao trabalhar com números de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="8d6eb-124">Describes issues that developers frequently encounter when working with floating-point numbers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6eb-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d6eb-125">See Also</span></span>  
 <span data-ttu-id="8d6eb-126">[SQL Server Data Types and ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8d6eb-126">[SQL Server Data Types and ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)</span></span>  
 [<span data-ttu-id="8d6eb-127">Configurando parâmetros e tipos de dados de parâmetro</span><span class="sxs-lookup"><span data-stu-id="8d6eb-127">Configuring Parameters and Parameter Data Types</span></span>](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="8d6eb-128">Recuperando informações de esquema de banco de dados</span><span class="sxs-lookup"><span data-stu-id="8d6eb-128">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="8d6eb-129">Common Type System</span><span class="sxs-lookup"><span data-stu-id="8d6eb-129">Common Type System</span></span>](../../../../docs/standard/base-types/common-type-system.md)  
 [<span data-ttu-id="8d6eb-130">Convertendo tipos</span><span class="sxs-lookup"><span data-stu-id="8d6eb-130">Converting Types</span></span>](http://msdn.microsoft.com/en-us/6038316e-bdaf-4f55-8006-407f591ce156)  
 <span data-ttu-id="8d6eb-131">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8d6eb-131">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
