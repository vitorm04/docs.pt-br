---
title: Introdução à Integração do SQL Server CLR
description: A integração CLR com o SQL Server dá suporte a procedimentos armazenados, gatilhos, funções definidas pelo usuário, tipos definidos pelo usuário e agregações definidas pelo usuário em código gerenciado.
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: 969afd7dea4aadf88bbb69cbe85d9cd84b233e4f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194551"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="e2d2b-103">Introdução à Integração do SQL Server CLR</span><span class="sxs-lookup"><span data-stu-id="e2d2b-103">Introduction to SQL Server CLR Integration</span></span>

<span data-ttu-id="e2d2b-104">O CLR (Common Language Runtime) é o centro do Microsoft .NET Framework; ele fornece o ambiente de execução para todo o código do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-104">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="e2d2b-105">O código executado no CLR é chamado de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-105">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="e2d2b-106">O CLR fornece diversas funções e serviços necessários para a execução de programas, incluindo a compilação JIT (Just-In-Time), alocação e gerenciamento de memória, imposição de segurança de tipos, tratamento de exceções, gerenciamento de threads e segurança.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-106">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="e2d2b-107">Com o CLR hospedado no Microsoft SQL Server (a chamada integração CLR), você pode criar procedimentos armazenados, gatilhos, funções definidas pelo usuário, tipos definidos pelo usuário e agregações definidas pelo usuário no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-107">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="e2d2b-108">Como o código gerenciado é compilado em código nativo antes da execução, você pode obter aumentos significativos de desempenho em alguns cenários.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-108">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="e2d2b-109">O código gerenciado usa CAS (segurança de acesso do código), links de código e domínios de aplicativo para impedir que os assemblies executem determinadas operações.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-109">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="e2d2b-110">O SQL Server usa CAS para ajudar a proteger o código gerenciado e evitar o comprometimento do sistema operacional ou servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-110">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="e2d2b-111">Esta seção é destinada para fornecer somente as informações suficientes para começar a programar com a integração de CLR do SQL Server, e não para ser abrangente.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-111">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="e2d2b-112">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-112">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e2d2b-113">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="e2d2b-113">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="e2d2b-114">Visão geral da integração CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="e2d2b-114">Common Language Runtime (CLR) Integration Overview</span></span>](/sql/relational-databases/clr-integration/common-language-runtime-integration-overview)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="e2d2b-115">Habilitando integração CLR</span><span class="sxs-lookup"><span data-stu-id="e2d2b-115">Enabling CLR Integration</span></span>  

 <span data-ttu-id="e2d2b-116">O recurso de integração do CLR (Common Language Runtime) está desativado por padrão no Microsoft SQL Server e deve ser habilitado para usar os objetos que são implementados usando a integração de CLR.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-116">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="e2d2b-117">Para habilitar a integração de CLR usando Transact-SQL, use a opção `clr enabled` do procedimento armazenado `sp_configure` conforme mostrado:</span><span class="sxs-lookup"><span data-stu-id="e2d2b-117">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```sql  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="e2d2b-118">Você pode desabilitar a integração de CLR configurando a opção `clr enabled` como 0.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-118">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="e2d2b-119">Quando você desabilita a integração de CLR, o SQL Server para de executar todas rotinas de CLR e descarrega todos os domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-119">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="e2d2b-120">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-120">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e2d2b-121">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="e2d2b-121">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="e2d2b-122">Habilitando a integração CLR</span><span class="sxs-lookup"><span data-stu-id="e2d2b-122">Enabling CLR Integration</span></span>](/sql/relational-databases/clr-integration/clr-integration-enabling)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="e2d2b-123">Implantando um assembly de CLR</span><span class="sxs-lookup"><span data-stu-id="e2d2b-123">Deploying a CLR Assembly</span></span>  

 <span data-ttu-id="e2d2b-124">Quando testados e verificados no servidor de teste, os métodos do CLR podem ser distribuídos para servidores de produção usando um script de implantação.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-124">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="e2d2b-125">O script de implantação pode ser gerado manualmente ou usando o SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-125">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="e2d2b-126">Para obter informações mais detalhadas, consulte a versão da documentação do SQL Server para a versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-126">For more detailed information, see the version of SQL Server documentation for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e2d2b-127">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="e2d2b-127">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="e2d2b-128">Implantando objetos de banco de dados CLR</span><span class="sxs-lookup"><span data-stu-id="e2d2b-128">Deploying CLR Database Objects</span></span>](/sql/relational-databases/clr-integration/deploying-clr-database-objects)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="e2d2b-129">Segurança da integração CLR</span><span class="sxs-lookup"><span data-stu-id="e2d2b-129">CLR Integration Security</span></span>  

 <span data-ttu-id="e2d2b-130">O modelo de segurança de integração do Microsoft SQL Server com o CLR (Common Language Runtime) do Microsoft .NET Framework gerencia e protege o acesso entre diferentes tipos de objetos CLR e não CLR que são executados no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-130">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="e2d2b-131">Esses objetos podem ser chamados por uma instrução Transact-SQL ou outro objeto CLR que é executado no servidor.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-131">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="e2d2b-132">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-132">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e2d2b-133">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="e2d2b-133">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="e2d2b-134">Segurança da integração CLR</span><span class="sxs-lookup"><span data-stu-id="e2d2b-134">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="e2d2b-135">Depurando um assembly de CLR</span><span class="sxs-lookup"><span data-stu-id="e2d2b-135">Debugging a CLR Assembly</span></span>  

 <span data-ttu-id="e2d2b-136">O Microsoft SQL Server fornece suporte para depurar o Transact-SQL e objetos CLR (Common Language Runtime) no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-136">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="e2d2b-137">Depurar funciona entre linguagens: os usuários podem entrar perfeitamente em objetos CLR de Transact-SQL e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-137">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="e2d2b-138">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="e2d2b-138">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e2d2b-139">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="e2d2b-139">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="e2d2b-140">Depurando objetos de banco de dados CLR</span><span class="sxs-lookup"><span data-stu-id="e2d2b-140">Debugging CLR Database Objects</span></span>](/sql/relational-databases/clr-integration/debugging-clr-database-objects)  
  
## <a name="see-also"></a><span data-ttu-id="e2d2b-141">Veja também</span><span class="sxs-lookup"><span data-stu-id="e2d2b-141">See also</span></span>

- [<span data-ttu-id="e2d2b-142">Segurança de acesso do código e o ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e2d2b-142">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="e2d2b-143">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e2d2b-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
