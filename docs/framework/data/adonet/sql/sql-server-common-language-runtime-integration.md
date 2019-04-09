---
title: Integração do Common Language Runtime do SQL
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: d87f2b89583747b80ef103f419bd9bd2e3b1e0da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089829"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="7d90a-102">Integração do Common Language Runtime do SQL</span><span class="sxs-lookup"><span data-stu-id="7d90a-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="7d90a-103">O SQL Server 2005 introduziu a integração do componente CLR do .NET Framework para Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="7d90a-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="7d90a-104">Isso significa que você pode gravar procedimentos armazenados, gatilhos, tipos definidos pelo usuário, funções definidas pelo usuário, agregações definidas pelo usuário e funções de streaming com valor de tabela, usando qualquer linguagem do .NET Framework, incluindo o Microsoft Visual Basic .NET e o Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="7d90a-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="7d90a-105">O namespace <xref:Microsoft.SqlServer.Server> contém um conjunto de APIs de modo que o código gerenciado possa interagir com o ambiente do Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7d90a-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="7d90a-106">Esta seção descreve os recursos e os comportamentos específicos para a integração de CLR e as extensões específicas no processo do SQL Server para o ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="7d90a-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="7d90a-107">Esta seção é destinada para fornecer somente as informações suficientes para começar a programar com a integração de CLR do SQL Server, e não para ser abrangente.</span><span class="sxs-lookup"><span data-stu-id="7d90a-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="7d90a-108">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="7d90a-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 **<span data-ttu-id="7d90a-109">Manuais Online do SQL Server</span><span class="sxs-lookup"><span data-stu-id="7d90a-109">SQL Server Books Online</span></span>**  
  
1.  [<span data-ttu-id="7d90a-110">Conceitos de programação da integração do CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="7d90a-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a><span data-ttu-id="7d90a-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="7d90a-111">In This Section</span></span>  
 [<span data-ttu-id="7d90a-112">Introdução à Integração do SQL Server CLR</span><span class="sxs-lookup"><span data-stu-id="7d90a-112">Introduction to SQL Server CLR Integration</span></span>](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="7d90a-113">Fornece uma introdução à Integração do SQL Server CLR.</span><span class="sxs-lookup"><span data-stu-id="7d90a-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="7d90a-114">Fornece links para tópicos adicionais.</span><span class="sxs-lookup"><span data-stu-id="7d90a-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="7d90a-115">Funções CLR definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="7d90a-115">CLR User-Defined Functions</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 <span data-ttu-id="7d90a-116">Descreve como implementar e usar os vários tipos de funções CLR: funções de agregação com valor de tabela, escalares e definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7d90a-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="7d90a-117">Tipos definido pelo usuário CLR</span><span class="sxs-lookup"><span data-stu-id="7d90a-117">CLR User-Defined Types</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 <span data-ttu-id="7d90a-118">Descreve como implementar e usar tipos CLR definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7d90a-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="7d90a-119">Fornece links para tópicos adicionais.</span><span class="sxs-lookup"><span data-stu-id="7d90a-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="7d90a-120">Procedimentos armazenados CLR</span><span class="sxs-lookup"><span data-stu-id="7d90a-120">CLR Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 <span data-ttu-id="7d90a-121">Descreve como implementar e usar procedimentos armazenados CLR.</span><span class="sxs-lookup"><span data-stu-id="7d90a-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="7d90a-122">Fornece links para tópicos adicionais.</span><span class="sxs-lookup"><span data-stu-id="7d90a-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="7d90a-123">Gatilhos de CLR</span><span class="sxs-lookup"><span data-stu-id="7d90a-123">CLR Triggers</span></span>](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 <span data-ttu-id="7d90a-124">Descreve como implementar e usar gatilhos CLR.</span><span class="sxs-lookup"><span data-stu-id="7d90a-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="7d90a-125">Fornece links para tópicos adicionais.</span><span class="sxs-lookup"><span data-stu-id="7d90a-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="7d90a-126">A conexão de contexto</span><span class="sxs-lookup"><span data-stu-id="7d90a-126">The Context Connection</span></span>](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 <span data-ttu-id="7d90a-127">Descreve a conexão de contexto.</span><span class="sxs-lookup"><span data-stu-id="7d90a-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="7d90a-128">Comportamento específico do processo do SQL Server do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7d90a-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="7d90a-129">Descreve as extensões específicas no processo do SQL Server para o ADO.NET, e a conexão de contexto.</span><span class="sxs-lookup"><span data-stu-id="7d90a-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="7d90a-130">Fornece links para tópicos adicionais.</span><span class="sxs-lookup"><span data-stu-id="7d90a-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d90a-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d90a-131">See also</span></span>

- [<span data-ttu-id="7d90a-132">SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7d90a-132">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="7d90a-133">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="7d90a-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
