---
title: Tipos definido pelo usuário CLR
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: b946a87e49d8bf496fb215eb95f9db9cb453c13c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878092"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="5c3db-102">Tipos definido pelo usuário CLR</span><span class="sxs-lookup"><span data-stu-id="5c3db-102">CLR User-Defined Types</span></span>
<span data-ttu-id="5c3db-103">O Microsoft SQL Server oferece suporte a tipos definidos pelo usuário (UDTs) implementados com o CLR do Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5c3db-103">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="5c3db-104">O CLR é integrado no SQL Server e esse mecanismo permite estender o sistema de tipos do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="5c3db-104">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="5c3db-105">Os UDTs oferecem extensibilidade do usuário do sistema de tipo de dados do SQL Server, além da capacidade de definir tipos estruturados complexos.</span><span class="sxs-lookup"><span data-stu-id="5c3db-105">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="5c3db-106">Os UDTs podem fornecer dois principais benefícios de uma perspectiva da arquitetura de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="5c3db-106">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
-   <span data-ttu-id="5c3db-107">Encapsulamento forte (no cliente e no servidor) entre o estado interno e os comportamentos externos.</span><span class="sxs-lookup"><span data-stu-id="5c3db-107">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
-   <span data-ttu-id="5c3db-108">Integração profunda com outros recursos relacionados ao servidor.</span><span class="sxs-lookup"><span data-stu-id="5c3db-108">Deep integration with other related server features.</span></span> <span data-ttu-id="5c3db-109">Depois de definir seu próprio UDT, você poderá usá-lo em todos os contextos em que você pode usar um tipo de sistema no SQL Server, inclusive definições de coluna, e como variáveis, parâmetros, resultados de função, cursores, gatilhos e replicação.</span><span class="sxs-lookup"><span data-stu-id="5c3db-109">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="5c3db-110">Para obter mais informações, consulte o [documentação do SQL Server](/sql) para a versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="5c3db-110">For more detailed information, see the [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="5c3db-111">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="5c3db-111">**SQL Server documentation**</span></span>
  
1. [<span data-ttu-id="5c3db-112">Tipos CLR definidos pelo usuário</span><span class="sxs-lookup"><span data-stu-id="5c3db-112">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="see-also"></a><span data-ttu-id="5c3db-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c3db-113">See also</span></span>

- <span data-ttu-id="5c3db-114">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="5c3db-114">[ADO.NET Overview](../ado-net-overview.md)</span></span>
