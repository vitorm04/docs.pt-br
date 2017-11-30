---
title: Usando os comandos para modificar dados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 853f8e4e75df3fffad4a2d5ecd4f7ae21b5d674f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="57358-102">Usando os comandos para modificar dados</span><span class="sxs-lookup"><span data-stu-id="57358-102">Using Commands to Modify Data</span></span>
<span data-ttu-id="57358-103">Usando um provedor de dados do .NET Framework, você pode executar os procedimentos armazenados ou instruções definição de dados idioma (por exemplo, CREATE TABLE e ALTER COLUMN) para executar a manipulação de esquema em um banco de dados ou catálogo.</span><span class="sxs-lookup"><span data-stu-id="57358-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="57358-104">Esses comandos não retornam linhas como uma consulta, portanto, o **comando** objeto fornece um **ExecuteNonQuery** para processá-las.</span><span class="sxs-lookup"><span data-stu-id="57358-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="57358-105">Além de usar **ExecuteNonQuery** para modificar o esquema, você também pode usar esse método para instruções SQL de processo que modificam dados, mas que não retornam linhas, como INSERT, UPDATE e excluir.</span><span class="sxs-lookup"><span data-stu-id="57358-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="57358-106">Embora linhas não são retornadas pelo **ExecuteNonQuery** parâmetros de método de entrada e saída e valores de retorno podem ser passados e retornados por meio de **parâmetros** coleção do **comando**  objeto.</span><span class="sxs-lookup"><span data-stu-id="57358-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57358-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="57358-107">In This Section</span></span>  
 [<span data-ttu-id="57358-108">Atualizando dados em uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="57358-108">Updating Data in a Data Source</span></span>](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 <span data-ttu-id="57358-109">Descreve como executar comandos ou procedimentos armazenados que modificam dados em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="57358-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="57358-110">Executando operações de catálogo</span><span class="sxs-lookup"><span data-stu-id="57358-110">Performing Catalog Operations</span></span>](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 <span data-ttu-id="57358-111">Descreve como executar comandos que modificam o esquema de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="57358-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57358-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57358-112">See Also</span></span>  
 <span data-ttu-id="57358-113">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="57358-113">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>  
 [<span data-ttu-id="57358-114">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="57358-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 <span data-ttu-id="57358-115">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="57358-115">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
