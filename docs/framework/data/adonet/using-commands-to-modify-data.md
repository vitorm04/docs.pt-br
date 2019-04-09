---
title: Usar os comandos para modificar dados
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: f2e3d162bfbdcb79cfecefa4ddc8e6a0dc46ee3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102447"
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="439fa-102">Usar os comandos para modificar dados</span><span class="sxs-lookup"><span data-stu-id="439fa-102">Using Commands to Modify Data</span></span>
<span data-ttu-id="439fa-103">Usando um provedor de dados .NET Framework, você pode executar os procedimentos armazenados ou dados instruções linguagem de definição (por exemplo, CREATE TABLE e ALTER COLUMN) para executar a manipulação de esquema em um banco de dados ou o catálogo.</span><span class="sxs-lookup"><span data-stu-id="439fa-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="439fa-104">Esses comandos não retornam linhas, como faria com uma consulta, portanto, o **comando** objeto fornece um **ExecuteNonQuery** para processá-las.</span><span class="sxs-lookup"><span data-stu-id="439fa-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="439fa-105">Além de usar **ExecuteNonQuery** para modificar o esquema, você também pode usar esse método para instruções SQL de processo que modificam dados, mas que não retornam linhas, como INSERT, UPDATE e excluir.</span><span class="sxs-lookup"><span data-stu-id="439fa-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="439fa-106">Embora linhas não são retornadas pelo **ExecuteNonQuery** parâmetros de método, entrada e saída e valores retornados podem ser passados e retornados por meio de **parâmetros** coleção do **comando**  objeto.</span><span class="sxs-lookup"><span data-stu-id="439fa-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="439fa-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="439fa-107">In This Section</span></span>  
 [<span data-ttu-id="439fa-108">Atualizando dados em uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="439fa-108">Updating Data in a Data Source</span></span>](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 <span data-ttu-id="439fa-109">Descreve como executar comandos ou procedimentos armazenados que modificam dados em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="439fa-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="439fa-110">Executar operações de catálogo</span><span class="sxs-lookup"><span data-stu-id="439fa-110">Performing Catalog Operations</span></span>](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 <span data-ttu-id="439fa-111">Descreve como executar comandos que modificam o esquema de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="439fa-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="439fa-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="439fa-112">See also</span></span>

- [<span data-ttu-id="439fa-113">Recuperando e modificando dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="439fa-113">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="439fa-114">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="439fa-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="439fa-115">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="439fa-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
