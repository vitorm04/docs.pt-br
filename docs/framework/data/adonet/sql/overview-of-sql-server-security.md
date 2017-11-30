---
title: "Visão geral de segurança do SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d93d077153cd15534175c1e60e63a765ce893c71
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="overview-of-sql-server-security"></a><span data-ttu-id="671f4-102">Visão geral de segurança do SQL Server</span><span class="sxs-lookup"><span data-stu-id="671f4-102">Overview of SQL Server Security</span></span>
<span data-ttu-id="671f4-103">Uma estratégia de defesa em profundidade, com a sobreposição de camadas de segurança, é a melhor maneira de ameaças de segurança do contador.</span><span class="sxs-lookup"><span data-stu-id="671f4-103">A defense-in-depth strategy, with overlapping layers of security, is the best way to counter security threats.</span></span> <span data-ttu-id="671f4-104">SQL Server fornece uma arquitetura de segurança que foi projetada para permitir que os administradores de banco de dados e desenvolvedores criar aplicativos de banco de dados seguro e ameaças de contador.</span><span class="sxs-lookup"><span data-stu-id="671f4-104">SQL Server provides a security architecture that is designed to allow database administrators and developers to create secure database applications and counter threats.</span></span> <span data-ttu-id="671f4-105">Cada versão do SQL Server melhorou em versões anteriores do SQL Server com a introdução de novos recursos e funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="671f4-105">Each version of SQL Server has improved on previous versions of SQL Server with the introduction of new features and functionality.</span></span> <span data-ttu-id="671f4-106">No entanto, a segurança não é fornecido na caixa.</span><span class="sxs-lookup"><span data-stu-id="671f4-106">However, security does not ship in the box.</span></span> <span data-ttu-id="671f4-107">Cada aplicativo é exclusivo em seus requisitos de segurança.</span><span class="sxs-lookup"><span data-stu-id="671f4-107">Each application is unique in its security requirements.</span></span> <span data-ttu-id="671f4-108">Os desenvolvedores precisam entender qual combinação de recursos e funcionalidade são mais apropriados para o contador de ameaças conhecidas e para prever as ameaças que podem surgir no futuro.</span><span class="sxs-lookup"><span data-stu-id="671f4-108">Developers need to understand which combination of features and functionality are most appropriate to counter known threats, and to anticipate threats that may arise in the future.</span></span>  
  
 <span data-ttu-id="671f4-109">Uma instância do SQL Server contém uma coleção hierárquica de entidades, começando com o servidor.</span><span class="sxs-lookup"><span data-stu-id="671f4-109">A SQL Server instance contains a hierarchical collection of entities, starting with the server.</span></span> <span data-ttu-id="671f4-110">Cada servidor contém vários bancos de dados e cada banco de dados contém uma coleção de objetos protegíveis.</span><span class="sxs-lookup"><span data-stu-id="671f4-110">Each server contains multiple databases, and each database contains a collection of securable objects.</span></span> <span data-ttu-id="671f4-111">Todo protegível do SQL Server associada *permissões* que podem ser concedidas a um *principal*, que é um grupo individual, ou processo concedeu acesso ao SQL Server.</span><span class="sxs-lookup"><span data-stu-id="671f4-111">Every SQL Server securable has associated *permissions* that can be granted to a *principal*, which is an individual, group or process granted access to SQL Server.</span></span> <span data-ttu-id="671f4-112">A estrutura de segurança do SQL Server gerencia o acesso a entidades podem ser protegidos por meio de *autenticação* e *autorização*.</span><span class="sxs-lookup"><span data-stu-id="671f4-112">The SQL Server security framework manages access to securable entities through *authentication* and *authorization*.</span></span>  
  
-   <span data-ttu-id="671f4-113">Autenticação é o processo de fazer logon no SQL Server pelo qual uma entidade de segurança solicita acesso ao enviar as credenciais que o servidor é avaliada.</span><span class="sxs-lookup"><span data-stu-id="671f4-113">Authentication is the process of logging on to SQL Server by which a principal requests access by submitting credentials that the server evaluates.</span></span> <span data-ttu-id="671f4-114">A autenticação estabelece a identidade do usuário ou processo que está sendo autenticado.</span><span class="sxs-lookup"><span data-stu-id="671f4-114">Authentication establishes the identity of the user or process being authenticated.</span></span>  
  
-   <span data-ttu-id="671f4-115">A autorização é o processo de determinar quais recursos podem ser protegidos pode acessar uma entidade de segurança e quais operações são permitidas para esses recursos.</span><span class="sxs-lookup"><span data-stu-id="671f4-115">Authorization is the process of determining which securable resources a principal can access, and which operations are allowed for those resources.</span></span>  
  
 <span data-ttu-id="671f4-116">Os tópicos nesta seção abordam conceitos básicos de segurança do SQL Server, fornecendo links para a documentação completa na versão relevante dos Manuais Online do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="671f4-116">The topics in this section cover SQL Server security fundamentals, providing links to the complete documentation in the relevant version of SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="671f4-117">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="671f4-117">In This Section</span></span>  
 [<span data-ttu-id="671f4-118">Autenticação no SQL Server</span><span class="sxs-lookup"><span data-stu-id="671f4-118">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 <span data-ttu-id="671f4-119">Descreve os logons e autenticação no SQL Server e fornece links para recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="671f4-119">Describes logins and authentication in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="671f4-120">Servidor e funções de banco de dados no SQL Server</span><span class="sxs-lookup"><span data-stu-id="671f4-120">Server and Database Roles in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 <span data-ttu-id="671f4-121">Descreve as funções fixas de servidor e banco de dados, funções de banco de dados personalizado e contas internas e fornece links para recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="671f4-121">Describes fixed server and database roles, custom database roles, and built-in accounts and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="671f4-122">Propriedade e separação do esquema de usuário no SQL Server</span><span class="sxs-lookup"><span data-stu-id="671f4-122">Ownership and User-Schema Separation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 <span data-ttu-id="671f4-123">Descreve a separação de propriedade e o esquema de usuário do objeto e fornece links para recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="671f4-123">Describes object ownership and  user-schema separation and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="671f4-124">Autorização e permissões no SQL Server</span><span class="sxs-lookup"><span data-stu-id="671f4-124">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 <span data-ttu-id="671f4-125">Descreve a concessão de permissões usando o princípio de menos privilégios e fornece links para recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="671f4-125">Describes granting permissions using the principle of least privilege and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="671f4-126">Criptografia de dados no SQL Server</span><span class="sxs-lookup"><span data-stu-id="671f4-126">Data Encryption in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 <span data-ttu-id="671f4-127">Descreve as opções de criptografia de dados no SQL Server e fornece links para recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="671f4-127">Describes data encryption options in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="671f4-128">Segurança da integração CLR no SQL Server</span><span class="sxs-lookup"><span data-stu-id="671f4-128">CLR Integration Security in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 <span data-ttu-id="671f4-129">Fornece links para recursos de segurança de integração do CLR.</span><span class="sxs-lookup"><span data-stu-id="671f4-129">Provides links to CLR integration security resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="671f4-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="671f4-130">See Also</span></span>  
 <span data-ttu-id="671f4-131">[Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="671f4-131">[Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)</span></span>  
 <span data-ttu-id="671f4-132">[SQL Server Security](../../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="671f4-132">[SQL Server Security](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)</span></span>  
 [<span data-ttu-id="671f4-133">Cenários de segurança do aplicativo no SQL Server</span><span class="sxs-lookup"><span data-stu-id="671f4-133">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 <span data-ttu-id="671f4-134">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="671f4-134">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
