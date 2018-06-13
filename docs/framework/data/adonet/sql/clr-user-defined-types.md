---
title: Tipos definido pelo usuário CLR
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: 344245ea7c67d7b5363c17bb42e2606ca11142bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357576"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="c7185-102">Tipos definido pelo usuário CLR</span><span class="sxs-lookup"><span data-stu-id="c7185-102">CLR User-Defined Types</span></span>
<span data-ttu-id="c7185-103">O Microsoft SQL Server oferece suporte a tipos definidos pelo usuário (UDTs) implementados com o CLR do Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c7185-103">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="c7185-104">O CLR é integrado no SQL Server e esse mecanismo permite estender o sistema de tipos do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c7185-104">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="c7185-105">Os UDTs oferecem extensibilidade do usuário do sistema de tipo de dados do SQL Server, além da capacidade de definir tipos estruturados complexos.</span><span class="sxs-lookup"><span data-stu-id="c7185-105">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="c7185-106">Os UDTs podem fornecer dois principais benefícios de uma perspectiva da arquitetura de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="c7185-106">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
-   <span data-ttu-id="c7185-107">Encapsulamento forte (no cliente e no servidor) entre o estado interno e os comportamentos externos.</span><span class="sxs-lookup"><span data-stu-id="c7185-107">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
-   <span data-ttu-id="c7185-108">Integração profunda com outros recursos relacionados ao servidor.</span><span class="sxs-lookup"><span data-stu-id="c7185-108">Deep integration with other related server features.</span></span> <span data-ttu-id="c7185-109">Depois de definir seu próprio UDT, você poderá usá-lo em todos os contextos em que você pode usar um tipo de sistema no SQL Server, inclusive definições de coluna, e como variáveis, parâmetros, resultados de função, cursores, gatilhos e replicação.</span><span class="sxs-lookup"><span data-stu-id="c7185-109">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="c7185-110">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="c7185-110">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="c7185-111">**SQL Server Books Online** (Guias online do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c7185-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="c7185-112">Tipos CLR definidos pelo usuário</span><span class="sxs-lookup"><span data-stu-id="c7185-112">CLR User-Defined Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="see-also"></a><span data-ttu-id="c7185-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7185-113">See Also</span></span>  
 [<span data-ttu-id="c7185-114">Criando objetos do SQL Server 2005 em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="c7185-114">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 <span data-ttu-id="c7185-115">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c7185-115">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
