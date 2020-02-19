---
title: Integração do Common Language Runtime do SQL
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: 12ae15d72644e314aa694f8d169bc8f45fa284a2
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452338"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="09f5f-102">Integração do Common Language Runtime do SQL</span><span class="sxs-lookup"><span data-stu-id="09f5f-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="09f5f-103">O SQL Server 2005 introduziu a integração do componente CLR do .NET Framework para Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="09f5f-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="09f5f-104">Isso significa que você pode gravar procedimentos armazenados, gatilhos, tipos definidos pelo usuário, funções definidas pelo usuário, agregações definidas pelo usuário e funções de streaming com valor de tabela, usando qualquer linguagem do .NET Framework, incluindo o Microsoft Visual Basic .NET e o Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="09f5f-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="09f5f-105">O namespace <xref:Microsoft.SqlServer.Server> contém um conjunto de APIs de modo que o código gerenciado possa interagir com o ambiente do Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="09f5f-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="09f5f-106">Esta seção descreve os recursos e os comportamentos específicos para a integração de CLR e as extensões específicas no processo do SQL Server para o ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="09f5f-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="09f5f-107">Esta seção é destinada para fornecer somente as informações suficientes para começar a programar com a integração de CLR do SQL Server, e não para ser abrangente.</span><span class="sxs-lookup"><span data-stu-id="09f5f-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="09f5f-108">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="09f5f-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="09f5f-109">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="09f5f-109">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="09f5f-110">Conceitos de programação da Integração CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="09f5f-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](/sql/relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts)  
  
## <a name="in-this-section"></a><span data-ttu-id="09f5f-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="09f5f-111">In This Section</span></span>  
 [<span data-ttu-id="09f5f-112">Introdução à integração de CLR do SQL Server</span><span class="sxs-lookup"><span data-stu-id="09f5f-112">Introduction to SQL Server CLR Integration</span></span>](introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="09f5f-113">Fornece uma introdução à Integração do SQL Server CLR.</span><span class="sxs-lookup"><span data-stu-id="09f5f-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="09f5f-114">Fornece links para tópicos adicionais.</span><span class="sxs-lookup"><span data-stu-id="09f5f-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="09f5f-115">Funções do CLR definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="09f5f-115">CLR User-Defined Functions</span></span>](clr-user-defined-functions.md)  
 <span data-ttu-id="09f5f-116">Descreve como implementar e usar os vários tipos de funções CLR: com valor de tabela, escalares e funções de agregação definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="09f5f-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="09f5f-117">Tipos definidos pelo usuário do CLR</span><span class="sxs-lookup"><span data-stu-id="09f5f-117">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
 <span data-ttu-id="09f5f-118">Descreve como implementar e usar tipos definidos pelo usuário CLR.</span><span class="sxs-lookup"><span data-stu-id="09f5f-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="09f5f-119">Fornece links para tópicos adicionais.</span><span class="sxs-lookup"><span data-stu-id="09f5f-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="09f5f-120">Procedimentos armazenados CLR</span><span class="sxs-lookup"><span data-stu-id="09f5f-120">CLR Stored Procedures</span></span>](clr-stored-procedures.md)  
 <span data-ttu-id="09f5f-121">Descreve como implementar e usar procedimentos armazenados CLR.</span><span class="sxs-lookup"><span data-stu-id="09f5f-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="09f5f-122">Fornece links para tópicos adicionais.</span><span class="sxs-lookup"><span data-stu-id="09f5f-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="09f5f-123">Gatilhos CLR</span><span class="sxs-lookup"><span data-stu-id="09f5f-123">CLR Triggers</span></span>](clr-triggers.md)  
 <span data-ttu-id="09f5f-124">Descreve como implementar e usar gatilhos CLR.</span><span class="sxs-lookup"><span data-stu-id="09f5f-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="09f5f-125">Fornece links para tópicos adicionais.</span><span class="sxs-lookup"><span data-stu-id="09f5f-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="09f5f-126">A Conexão de contexto</span><span class="sxs-lookup"><span data-stu-id="09f5f-126">The Context Connection</span></span>](the-context-connection.md)  
 <span data-ttu-id="09f5f-127">Descreve a conexão de contexto.</span><span class="sxs-lookup"><span data-stu-id="09f5f-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="09f5f-128">Comportamento específico em processo do SQL Server do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09f5f-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="09f5f-129">Descreve as extensões específicas no processo do SQL Server para o ADO.NET, e a conexão de contexto.</span><span class="sxs-lookup"><span data-stu-id="09f5f-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="09f5f-130">Fornece links para tópicos adicionais.</span><span class="sxs-lookup"><span data-stu-id="09f5f-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09f5f-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="09f5f-131">See also</span></span>

- [<span data-ttu-id="09f5f-132">SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09f5f-132">SQL Server and ADO.NET</span></span>](index.md)
- <span data-ttu-id="09f5f-133">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="09f5f-133">[ADO.NET Overview](../ado-net-overview.md)</span></span>
