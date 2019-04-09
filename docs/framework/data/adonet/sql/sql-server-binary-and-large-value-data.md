---
title: Dados binários e de valor grande do SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4b7a3f16726d6363cd702fb912bb7be281a25000
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192960"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="d12e2-102">Dados binários e de valor grande do SQL Server</span><span class="sxs-lookup"><span data-stu-id="d12e2-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="d12e2-103">O SQL Server fornece as `max` especificador, que expande a capacidade de armazenamento do `varchar`, `nvarchar`, e `varbinary` tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="d12e2-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> `varchar(max)`<span data-ttu-id="d12e2-104">, `nvarchar(max)`, e `varbinary(max)` são coletivamente chamados *tipos de dados de valor grande*.</span><span class="sxs-lookup"><span data-stu-id="d12e2-104">, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="d12e2-105">Você pode usar os tipos de dados de valor grande para armazenar até 2 ^ 31-1 bytes de dados.</span><span class="sxs-lookup"><span data-stu-id="d12e2-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="d12e2-106">SQL Server 2008 apresenta o atributo FILESTREAM, que é não um tipo de dados, mas em vez disso, um atributo que pode ser definido em uma coluna, permitindo que os dados de valor grande ser armazenado no sistema de arquivos em vez de no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d12e2-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d12e2-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d12e2-107">In This Section</span></span>  
 [<span data-ttu-id="d12e2-108">Modificando dados de valores grandes (max) no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d12e2-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 <span data-ttu-id="d12e2-109">Descreve como trabalhar com os tipos de dados de valor grande.</span><span class="sxs-lookup"><span data-stu-id="d12e2-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="d12e2-110">Dados FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="d12e2-110">FILESTREAM Data</span></span>](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 <span data-ttu-id="d12e2-111">Descreve como trabalhar com dados de valor grande armazenados no SQL Server 2008 com o atributo FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="d12e2-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d12e2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d12e2-112">See also</span></span>

- [<span data-ttu-id="d12e2-113">Tipos de dados do SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d12e2-113">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [<span data-ttu-id="d12e2-114">Operações de dados do SQL Server no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d12e2-114">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [<span data-ttu-id="d12e2-115">Recuperando e modificando dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d12e2-115">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="d12e2-116">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="d12e2-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
