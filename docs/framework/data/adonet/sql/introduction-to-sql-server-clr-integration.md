---
title: Introdução à Integração do SQL Server CLR
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: 2f65e8690aa52f0442b4bee3b98bb1ea86e064a5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110697"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="d0c33-102">Introdução à Integração do SQL Server CLR</span><span class="sxs-lookup"><span data-stu-id="d0c33-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="d0c33-103">O CLR (Common Language Runtime) é o coração do Microsoft .NET Framework e fornece o ambiente de execução para todo o código do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0c33-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="d0c33-104">O código que é executado dentro do CLR é conhecido como código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d0c33-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="d0c33-105">O CLR fornece várias funções e serviços necessários para a execução do programa, incluindo a compilação just-in-time (JIT), alocação e gerenciamento de memória, imposição de segurança de tipo, manipulação de exceção, gerenciamento de segmento e segurança.</span><span class="sxs-lookup"><span data-stu-id="d0c33-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="d0c33-106">Com o CLR hospedado no Microsoft SQL Server (chamado de integração de CLR), você pode criar procedimentos armazenados, gatilhos, funções definidas pelo usuário, tipos definidos pelo usuário e agregados definidos pelo usuário no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d0c33-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="d0c33-107">Como o código gerenciado compila para código nativo antes de execução, você pode obter aumentos significativos de desempenho em alguns cenários.</span><span class="sxs-lookup"><span data-stu-id="d0c33-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="d0c33-108">O código gerenciado usa CAS (segurança de acesso do código), links de código e domínios de aplicativo para impedir que os assemblies executem determinadas operações.</span><span class="sxs-lookup"><span data-stu-id="d0c33-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="d0c33-109">O SQL Server usa CAS para ajudar a proteger o código gerenciado e evitar o comprometimento do sistema operacional ou servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d0c33-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="d0c33-110">Esta seção é destinada para fornecer somente as informações suficientes para começar a programar com a integração de CLR do SQL Server, e não para ser abrangente.</span><span class="sxs-lookup"><span data-stu-id="d0c33-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="d0c33-111">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="d0c33-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 **<span data-ttu-id="d0c33-112">Manuais Online do SQL Server</span><span class="sxs-lookup"><span data-stu-id="d0c33-112">SQL Server Books Online</span></span>**  
  
-   [<span data-ttu-id="d0c33-113">Visão geral da integração do CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="d0c33-113">Common Language Runtime (CLR) Integration Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="d0c33-114">Habilitando a integração de CLR</span><span class="sxs-lookup"><span data-stu-id="d0c33-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="d0c33-115">O recurso de integração do CLR (Common Language Runtime) está desativado por padrão no Microsoft SQL Server e deve ser habilitado para usar os objetos que são implementados usando a integração de CLR.</span><span class="sxs-lookup"><span data-stu-id="d0c33-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="d0c33-116">Para habilitar a integração de CLR usando Transact-SQL, use a opção `clr enabled` do procedimento armazenado `sp_configure` conforme mostrado:</span><span class="sxs-lookup"><span data-stu-id="d0c33-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="d0c33-117">Você pode desabilitar a integração de CLR configurando a opção `clr enabled` como 0.</span><span class="sxs-lookup"><span data-stu-id="d0c33-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="d0c33-118">Quando você desabilita a integração de CLR, o SQL Server para de executar todas rotinas de CLR e descarrega todos os domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d0c33-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="d0c33-119">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="d0c33-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 **<span data-ttu-id="d0c33-120">Manuais Online do SQL Server</span><span class="sxs-lookup"><span data-stu-id="d0c33-120">SQL Server Books Online</span></span>**  
  
-   [<span data-ttu-id="d0c33-121">Habilitando a integração de CLR</span><span class="sxs-lookup"><span data-stu-id="d0c33-121">Enabling CLR Integration</span></span>](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="d0c33-122">Implantando um assembly de CLR</span><span class="sxs-lookup"><span data-stu-id="d0c33-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="d0c33-123">Uma vez que os métodos de CLR foram testados e verificados no servidor de teste, eles podem ser distribuídos para servidores de produção usando um script de implantação.</span><span class="sxs-lookup"><span data-stu-id="d0c33-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="d0c33-124">O script de implantação pode ser gerado manualmente ou usando o SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="d0c33-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="d0c33-125">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="d0c33-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 **<span data-ttu-id="d0c33-126">Manuais Online do SQL Server</span><span class="sxs-lookup"><span data-stu-id="d0c33-126">SQL Server Books Online</span></span>**  
  
1.  [<span data-ttu-id="d0c33-127">Implantando objetos de banco de dados de CLR</span><span class="sxs-lookup"><span data-stu-id="d0c33-127">Deploying CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="d0c33-128">Segurança de integração de CLR</span><span class="sxs-lookup"><span data-stu-id="d0c33-128">CLR Integration Security</span></span>  
 <span data-ttu-id="d0c33-129">O modelo de segurança de integração do Microsoft SQL Server com o CLR (Common Language Runtime) do Microsoft .NET Framework gerencia e protege o acesso entre diferentes tipos de objetos CLR e não CLR que são executados no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d0c33-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="d0c33-130">Esses objetos podem ser chamados por uma instrução Transact-SQL ou outro objeto CLR que é executado no servidor.</span><span class="sxs-lookup"><span data-stu-id="d0c33-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="d0c33-131">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="d0c33-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 **<span data-ttu-id="d0c33-132">Manuais Online do SQL Server</span><span class="sxs-lookup"><span data-stu-id="d0c33-132">SQL Server Books Online</span></span>**  
  
-   [<span data-ttu-id="d0c33-133">Segurança de integração de CLR</span><span class="sxs-lookup"><span data-stu-id="d0c33-133">CLR Integration Security</span></span>](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="d0c33-134">Depurando um assembly de CLR</span><span class="sxs-lookup"><span data-stu-id="d0c33-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="d0c33-135">O Microsoft SQL Server fornece suporte para depurar o Transact-SQL e objetos CLR (Common Language Runtime) no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d0c33-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="d0c33-136">Depurar funciona entre linguagens: os usuários podem entrar perfeitamente em objetos CLR de Transact-SQL e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="d0c33-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="d0c33-137">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="d0c33-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 **<span data-ttu-id="d0c33-138">Manuais Online do SQL Server</span><span class="sxs-lookup"><span data-stu-id="d0c33-138">SQL Server Books Online</span></span>**  
  
-   [<span data-ttu-id="d0c33-139">Depurando objetos de banco de dados de CLR</span><span class="sxs-lookup"><span data-stu-id="d0c33-139">Debugging CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="d0c33-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0c33-140">See also</span></span>

- [<span data-ttu-id="d0c33-141">Segurança de acesso do código e o ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d0c33-141">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)
- [<span data-ttu-id="d0c33-142">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="d0c33-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
