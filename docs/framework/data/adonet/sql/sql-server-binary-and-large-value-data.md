---
title: Dados binários e de valor grande do SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4d941ad6b7865112b45fd8c20ad89e9236e17b9d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791677"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="de1b2-102">Dados binários e de valor grande do SQL Server</span><span class="sxs-lookup"><span data-stu-id="de1b2-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="de1b2-103">SQL Server fornece o `max` especificador, que expande a capacidade `varchar`de armazenamento dos `nvarchar`tipos de `varbinary` dados, e.</span><span class="sxs-lookup"><span data-stu-id="de1b2-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="de1b2-104">`varchar(max)`, `nvarchar(max)` e`varbinary(max)` são chamados coletivamente *de tipos de dados de valor grande*.</span><span class="sxs-lookup"><span data-stu-id="de1b2-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="de1b2-105">Você pode usar os tipos de dados de valor grande para armazenar até 2 ^ 31-1 bytes de dados.</span><span class="sxs-lookup"><span data-stu-id="de1b2-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="de1b2-106">SQL Server 2008 apresenta o atributo FILESTREAM, que não é um tipo de dados, mas um atributo que pode ser definido em uma coluna, permitindo que dados de valor grande sejam armazenados no sistema de arquivos, e não no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="de1b2-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="de1b2-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="de1b2-107">In This Section</span></span>  
 [<span data-ttu-id="de1b2-108">Modificando dados de valor grande (max) no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="de1b2-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](modifying-large-value-max-data.md)  
 <span data-ttu-id="de1b2-109">Descreve como trabalhar com os tipos de dados de valor grande.</span><span class="sxs-lookup"><span data-stu-id="de1b2-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="de1b2-110">Dados FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="de1b2-110">FILESTREAM Data</span></span>](filestream-data.md)  
 <span data-ttu-id="de1b2-111">Descreve como trabalhar com dados de valor grande armazenados no SQL Server 2008 com o atributo FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="de1b2-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de1b2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de1b2-112">See also</span></span>

- <span data-ttu-id="de1b2-113">[SQL Server Data Types and ADO.NET](sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="de1b2-113">[SQL Server Data Types and ADO.NET](sql-server-data-types.md)</span></span>
- <span data-ttu-id="de1b2-114">[SQL Server Data Operations in ADO.NET](sql-server-data-operations.md) (Operações de dados do SQL Server no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="de1b2-114">[SQL Server Data Operations in ADO.NET](sql-server-data-operations.md)</span></span>
- <span data-ttu-id="de1b2-115">[Retrieving and Modifying Data in ADO.NET](../retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="de1b2-115">[Retrieving and Modifying Data in ADO.NET](../retrieving-and-modifying-data.md)</span></span>
- <span data-ttu-id="de1b2-116">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="de1b2-116">[ADO.NET Overview](../ado-net-overview.md)</span></span>
