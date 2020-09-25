---
title: Dados binários e de valor grande do SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: a9296e83b0f4e4352423470433670bb2cbe5a248
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183033"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="906f8-102">Dados binários e de valor grande do SQL Server</span><span class="sxs-lookup"><span data-stu-id="906f8-102">SQL Server Binary and Large-Value Data</span></span>

<span data-ttu-id="906f8-103">O SQL Server fornece o especificador `max`, que expande a capacidade de armazenamento dos tipos de dados `varchar`, `nvarchar` e `varbinary`.</span><span class="sxs-lookup"><span data-stu-id="906f8-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="906f8-104">`varchar(max)`, `nvarchar(max)` e `varbinary(max)` são coletivamente chamados de *tipos de dados do valor grande*.</span><span class="sxs-lookup"><span data-stu-id="906f8-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="906f8-105">Você pode usar os tipos de dados de valor grande para armazenar até 2^31-1 bytes de dados.</span><span class="sxs-lookup"><span data-stu-id="906f8-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="906f8-106">O SQL Server 2008 introduz o atributo FILESTREAM, que não é um tipo de dados, mas um atributo que pode ser definido em uma coluna, permitindo que dados de valor grande sejam armazenados no sistema de arquivos em vez de no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="906f8-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="906f8-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="906f8-107">In This Section</span></span>  

 [<span data-ttu-id="906f8-108">Modificando dados de valor grande (max) em ADO.NET</span><span class="sxs-lookup"><span data-stu-id="906f8-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](modifying-large-value-max-data.md)  
 <span data-ttu-id="906f8-109">Descreve como trabalhar com tipos de dados de valores grandes.</span><span class="sxs-lookup"><span data-stu-id="906f8-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="906f8-110">Dados FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="906f8-110">FILESTREAM Data</span></span>](filestream-data.md)  
 <span data-ttu-id="906f8-111">Descreve como trabalhar usando dados de valor grande armazenados no SQL Server 2008 com o atributo FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="906f8-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906f8-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="906f8-112">See also</span></span>

- [<span data-ttu-id="906f8-113">Tipos de dados do SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="906f8-113">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="906f8-114">SQL Server operações de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="906f8-114">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="906f8-115">Recuperando e modificando dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="906f8-115">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="906f8-116">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="906f8-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
