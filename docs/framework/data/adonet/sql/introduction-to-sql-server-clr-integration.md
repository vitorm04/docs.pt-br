---
title: "Introdução à Integração do SQL Server CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: fe93dc09019938e86279fd6996cd396b290ea3d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="815dd-102">Introdução à Integração do SQL Server CLR</span><span class="sxs-lookup"><span data-stu-id="815dd-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="815dd-103">O CLR (Common Language Runtime) é o coração do Microsoft .NET Framework e fornece o ambiente de execução para todo o código do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="815dd-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="815dd-104">O código que é executado dentro do CLR é conhecido como código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="815dd-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="815dd-105">O CLR fornece várias funções e serviços necessários para a execução do programa, incluindo a compilação just-in-time (JIT), alocação e gerenciamento de memória, imposição de segurança de tipo, manipulação de exceção, gerenciamento de segmento e segurança.</span><span class="sxs-lookup"><span data-stu-id="815dd-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="815dd-106">Com o CLR hospedado no Microsoft SQL Server (chamado de integração de CLR), você pode criar procedimentos armazenados, gatilhos, funções definidas pelo usuário, tipos definidos pelo usuário e agregados definidos pelo usuário no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="815dd-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="815dd-107">Como o código gerenciado compila para código nativo antes de execução, você pode obter aumentos significativos de desempenho em alguns cenários.</span><span class="sxs-lookup"><span data-stu-id="815dd-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="815dd-108">O código gerenciado usa CAS (segurança de acesso do código), links de código e domínios de aplicativo para impedir que os assemblies executem determinadas operações.</span><span class="sxs-lookup"><span data-stu-id="815dd-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="815dd-109">O SQL Server usa CAS para ajudar a proteger o código gerenciado e evitar o comprometimento do sistema operacional ou servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="815dd-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="815dd-110">Esta seção é destinada para fornecer somente as informações suficientes para começar a programar com a integração de CLR do SQL Server, e não para ser abrangente.</span><span class="sxs-lookup"><span data-stu-id="815dd-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="815dd-111">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="815dd-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="815dd-112">**SQL Server Books Online** (Guias online do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="815dd-112">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="815dd-113">Visão geral da integração Common Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="815dd-113">Common Language Runtime (CLR) Integration Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="815dd-114">Habilitando a integração de CLR</span><span class="sxs-lookup"><span data-stu-id="815dd-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="815dd-115">O recurso de integração do CLR (Common Language Runtime) está desativado por padrão no Microsoft SQL Server e deve ser habilitado para usar os objetos que são implementados usando a integração de CLR.</span><span class="sxs-lookup"><span data-stu-id="815dd-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="815dd-116">Para habilitar a integração de CLR usando Transact-SQL, use a opção `clr enabled` do procedimento armazenado `sp_configure` conforme mostrado:</span><span class="sxs-lookup"><span data-stu-id="815dd-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="815dd-117">Você pode desabilitar a integração de CLR configurando a opção `clr enabled` como 0.</span><span class="sxs-lookup"><span data-stu-id="815dd-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="815dd-118">Quando você desabilita a integração de CLR, o SQL Server para de executar todas rotinas de CLR e descarrega todos os domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="815dd-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="815dd-119">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="815dd-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="815dd-120">**SQL Server Books Online** (Guias online do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="815dd-120">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="815dd-121">Habilitando integração CLR</span><span class="sxs-lookup"><span data-stu-id="815dd-121">Enabling CLR Integration</span></span>](http://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="815dd-122">Implantando um assembly de CLR</span><span class="sxs-lookup"><span data-stu-id="815dd-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="815dd-123">Uma vez que os métodos de CLR foram testados e verificados no servidor de teste, eles podem ser distribuídos para servidores de produção usando um script de implantação.</span><span class="sxs-lookup"><span data-stu-id="815dd-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="815dd-124">O script de implantação pode ser gerado manualmente ou usando o SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="815dd-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="815dd-125">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="815dd-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="815dd-126">**SQL Server Books Online** (Guias online do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="815dd-126">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="815dd-127">Implantar objetos de banco de dados CLR</span><span class="sxs-lookup"><span data-stu-id="815dd-127">Deploying CLR Database Objects</span></span>](http://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="815dd-128">Segurança de integração de CLR</span><span class="sxs-lookup"><span data-stu-id="815dd-128">CLR Integration Security</span></span>  
 <span data-ttu-id="815dd-129">O modelo de segurança de integração do Microsoft SQL Server com o CLR (Common Language Runtime) do Microsoft .NET Framework gerencia e protege o acesso entre diferentes tipos de objetos CLR e não CLR que são executados no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="815dd-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="815dd-130">Esses objetos podem ser chamados por uma instrução Transact-SQL ou outro objeto CLR que é executado no servidor.</span><span class="sxs-lookup"><span data-stu-id="815dd-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="815dd-131">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="815dd-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="815dd-132">**SQL Server Books Online** (Guias online do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="815dd-132">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="815dd-133">Segurança da integração CLR</span><span class="sxs-lookup"><span data-stu-id="815dd-133">CLR Integration Security</span></span>](http://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="815dd-134">Depurando um assembly de CLR</span><span class="sxs-lookup"><span data-stu-id="815dd-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="815dd-135">O Microsoft SQL Server fornece suporte para depurar o Transact-SQL e objetos CLR (Common Language Runtime) no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="815dd-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="815dd-136">Depurar funciona entre linguagens: os usuários podem entrar perfeitamente em objetos CLR de Transact-SQL e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="815dd-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="815dd-137">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="815dd-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="815dd-138">**SQL Server Books Online** (Guias online do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="815dd-138">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="815dd-139">Depuração de objetos de banco de dados CLR</span><span class="sxs-lookup"><span data-stu-id="815dd-139">Debugging CLR Database Objects</span></span>](http://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="815dd-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="815dd-140">See Also</span></span>  
 [<span data-ttu-id="815dd-141">Criando objetos do SQL Server 2005 em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="815dd-141">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="815dd-142">Segurança de acesso do código e o ADO.NET</span><span class="sxs-lookup"><span data-stu-id="815dd-142">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="815dd-143">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="815dd-143">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
