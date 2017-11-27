---
title: "Dados de valor grande e binários do servidor SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9065f467cd353c17471db2c0d67001a188459819
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="1ce50-102">Dados de valor grande e binários do servidor SQL</span><span class="sxs-lookup"><span data-stu-id="1ce50-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="1ce50-103">O SQL Server fornece a `max` especificador, que se expande a capacidade de armazenamento do `varchar`, `nvarchar`, e `varbinary` tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="1ce50-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="1ce50-104">`varchar(max)`, `nvarchar(max)`, e `varbinary(max)` são coletivamente chamados de *tipos de dados de valor grande*.</span><span class="sxs-lookup"><span data-stu-id="1ce50-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="1ce50-105">Você pode usar os tipos de dados de valor grande para armazenar até 2 ^ 31-1 bytes de dados.</span><span class="sxs-lookup"><span data-stu-id="1ce50-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="1ce50-106">SQL Server 2008 apresenta o atributo FILESTREAM, que não é um tipo de dados, mas em vez disso, um atributo que pode ser definido em uma coluna, permitindo que os dados de valor grande ser armazenado no sistema de arquivos em vez de no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1ce50-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ce50-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1ce50-107">In This Section</span></span>  
 [<span data-ttu-id="1ce50-108">Modificando dados de valor grande (max) no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1ce50-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 <span data-ttu-id="1ce50-109">Descreve como trabalhar com os tipos de dados de valor grande.</span><span class="sxs-lookup"><span data-stu-id="1ce50-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="1ce50-110">Dados FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="1ce50-110">FILESTREAM Data</span></span>](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 <span data-ttu-id="1ce50-111">Descreve como trabalhar com dados de valor grande armazenados no SQL Server 2008 com o atributo FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="1ce50-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce50-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ce50-112">See Also</span></span>  
 <span data-ttu-id="1ce50-113">[SQL Server Data Types and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1ce50-113">[SQL Server Data Types and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)</span></span>  
 <span data-ttu-id="1ce50-114">[SQL Server Data Operations in ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md) (Operações de dados do SQL Server no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1ce50-114">[SQL Server Data Operations in ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)</span></span>  
 <span data-ttu-id="1ce50-115">[Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1ce50-115">[Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>  
 <span data-ttu-id="1ce50-116">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1ce50-116">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
