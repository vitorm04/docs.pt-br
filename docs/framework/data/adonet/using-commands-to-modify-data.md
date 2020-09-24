---
title: Usar os comandos para modificar dados
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: e2f61dbf74f28d026ae91a2bc8f5bb78530ffeac
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177248"
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="f332c-102">Usar os comandos para modificar dados</span><span class="sxs-lookup"><span data-stu-id="f332c-102">Using Commands to Modify Data</span></span>

<span data-ttu-id="f332c-103">Usando um provedor de dados .NET Framework, você pode executar procedimentos armazenados ou instruções de linguagem de definição de dados (por exemplo, CREATE TABLE e alterar coluna) para executar a manipulação de esquema em um banco de dados ou catálogo.</span><span class="sxs-lookup"><span data-stu-id="f332c-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="f332c-104">Esses comandos não retornam linhas como uma consulta, portanto, o objeto **Command** fornece um **ExecuteNonQuery** para processá-los.</span><span class="sxs-lookup"><span data-stu-id="f332c-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="f332c-105">Além de usar o **ExecuteNonQuery** para modificar o esquema, você também pode usar esse método para processar instruções SQL que modificam dados, mas que não retornam linhas, como INSERT, Update e Delete.</span><span class="sxs-lookup"><span data-stu-id="f332c-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="f332c-106">Embora as linhas não sejam retornadas pelo método **ExecuteNonQuery** , os parâmetros de entrada e saída e os valores de retorno podem ser passados e retornados por meio da coleção de **parâmetros** do objeto de **comando** .</span><span class="sxs-lookup"><span data-stu-id="f332c-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f332c-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f332c-107">In This Section</span></span>  

 [<span data-ttu-id="f332c-108">Atualizando dados em uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="f332c-108">Updating Data in a Data Source</span></span>](updating-data-in-a-data-source.md)  
 <span data-ttu-id="f332c-109">Descreve como executar comandos ou procedimentos armazenados que modificam dados em um banco de dado.</span><span class="sxs-lookup"><span data-stu-id="f332c-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="f332c-110">Executar operações de catálogo</span><span class="sxs-lookup"><span data-stu-id="f332c-110">Performing Catalog Operations</span></span>](performing-catalog-operations.md)  
 <span data-ttu-id="f332c-111">Descreve como executar comandos que modificam o esquema de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f332c-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f332c-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="f332c-112">See also</span></span>

- [<span data-ttu-id="f332c-113">Recuperando e modificando dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f332c-113">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="f332c-114">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="f332c-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="f332c-115">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f332c-115">ADO.NET Overview</span></span>](ado-net-overview.md)
