---
title: Concedendo permissões de nível de linha no SQL Server
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 4a4b45e13a16b357be28a1383648e98890567ea9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749149"
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="d2e54-102">Concedendo permissões de nível de linha no SQL Server</span><span class="sxs-lookup"><span data-stu-id="d2e54-102">Granting Row-Level Permissions in SQL Server</span></span>
<span data-ttu-id="d2e54-103">Em alguns cenários, há um requisito para controlar o acesso a dados em um nível mais granular do que simplesmente concedendo, revogando ou negando permissões fornece.</span><span class="sxs-lookup"><span data-stu-id="d2e54-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="d2e54-104">Por exemplo, um aplicativo de banco de dados do hospital pode exigir médicos individuais serão restritas a acesso a informações relacionadas ao somente seus pacientes.</span><span class="sxs-lookup"><span data-stu-id="d2e54-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="d2e54-105">Existem requisitos semelhantes em muitos ambientes, incluindo finanças, lei, governo e militares aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d2e54-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="d2e54-106">Para ajudar a lidar com esses cenários, o SQL Server 2016 fornece uma [segurança em nível de linha](https://msdn.microsoft.com/library/dn765131.aspx) recurso que simplifica e centraliza a lógica de acesso de nível de linha em uma política de segurança.</span><span class="sxs-lookup"><span data-stu-id="d2e54-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](https://msdn.microsoft.com/library/dn765131.aspx) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="d2e54-107">Para versões anteriores do SQL Server, uma funcionalidade semelhante pode ser obtida usando modos de exibição para aplicar a filtragem de nível de linha.</span><span class="sxs-lookup"><span data-stu-id="d2e54-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>  
  
## <a name="implementing-row-level-filtering"></a><span data-ttu-id="d2e54-108">Implementando a filtragem de nível de linha</span><span class="sxs-lookup"><span data-stu-id="d2e54-108">Implementing Row-level Filtering</span></span>  
 <span data-ttu-id="d2e54-109">Filtragem de nível de linha é usado para armazenar informações em uma única tabela, como no exemplo acima hospital de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d2e54-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="d2e54-110">Para implementar filtragem de cada linha de nível de linha tem uma coluna que define um parâmetro de diferenciação, como um nome de usuário, o rótulo ou outro identificador.</span><span class="sxs-lookup"><span data-stu-id="d2e54-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="d2e54-111">Você cria uma política de segurança ou uma exibição em tabela, que filtra as linhas que o usuário pode acessar.</span><span class="sxs-lookup"><span data-stu-id="d2e54-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="d2e54-112">Você, em seguida, criar procedimentos armazenados com parâmetros que controlam os tipos de consultas que o usuário pode executar.</span><span class="sxs-lookup"><span data-stu-id="d2e54-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>  
  
 <span data-ttu-id="d2e54-113">O exemplo a seguir descreve como configurar a filtragem de nível de linha com base em um nome de usuário ou logon:</span><span class="sxs-lookup"><span data-stu-id="d2e54-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>  
  
-   <span data-ttu-id="d2e54-114">Crie a tabela, adicionando uma coluna para armazenar o nome.</span><span class="sxs-lookup"><span data-stu-id="d2e54-114">Create the table, adding a column to store the name.</span></span>  
  
-   <span data-ttu-id="d2e54-115">Habilite a filtragem de nível de linha:</span><span class="sxs-lookup"><span data-stu-id="d2e54-115">Enable row-level filtering:</span></span>  
  
    -   <span data-ttu-id="d2e54-116">Se você estiver usando o SQL Server 2016 ou superior, ou [banco de dados SQL](https://docs.microsoft.com/azure/sql-database/), crie uma política de segurança que adiciona um predicado na tabela de restringir as linhas retornadas para aquelas que correspondem a um o atual usuário de banco de dados (usando o CURRENT_USER() função interna) ou o nome de logon atual (usando a função interna de suser_sname ()):</span><span class="sxs-lookup"><span data-stu-id="d2e54-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>  
  
        ```tsql  
        CREATE SCHEMA Security  
        GO  
  
        CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)  
            RETURNS TABLE  
            WITH SCHEMABINDING  
        AS  
            RETURN SELECT 1 AS accessResult  
            WHERE @UserName = SUSER_SNAME()  
        GO  
  
        CREATE SECURITY POLICY Security.userAccessPolicy  
            ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,  
            ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable  
        GO  
        ```  
  
    -   <span data-ttu-id="d2e54-117">Se você estiver usando uma versão do SQL Server antes de 2016, você pode obter funcionalidade semelhante usando um modo de exibição:</span><span class="sxs-lookup"><span data-stu-id="d2e54-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>  
  
        ```tsql  
        CREATE VIEW vw_MyTable  
        AS  
            RETURN SELECT * FROM MyTable  
            WHERE UserName = SUSER_SNAME()  
        GO  
        ```  
  
-   <span data-ttu-id="d2e54-118">Crie procedimentos armazenados para selecionar, inserir, atualizar e excluir dados.</span><span class="sxs-lookup"><span data-stu-id="d2e54-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="d2e54-119">Se a filtragem é imposta por uma política de segurança, os procedimentos armazenados devem executar essas operações na tabela base diretamente. Caso contrário, se a filtragem é imposta por uma exibição, os procedimentos armazenados devem operar em vez disso, com base na exibição.</span><span class="sxs-lookup"><span data-stu-id="d2e54-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="d2e54-120">A política de segurança ou a exibição filtrarão automaticamente as linhas retornadas ou modificados por consultas de usuário e o procedimento armazenado fornece um limite de segurança mais difícil para impedir que os usuários com acesso de consulta direta com êxito a execução de consultas que podem inferir o existência de dados filtrados.</span><span class="sxs-lookup"><span data-stu-id="d2e54-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>  
  
-   <span data-ttu-id="d2e54-121">Para procedimentos armazenados que inserem dados, capturar o nome de usuário usando a mesma função especificada na política de segurança ou na exibição e inserir esse valor na coluna Nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="d2e54-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>  
  
-   <span data-ttu-id="d2e54-122">Negar todas as permissões em tabelas (e modos de exibição, se aplicável) para o `public` função.</span><span class="sxs-lookup"><span data-stu-id="d2e54-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="d2e54-123">Os usuários não poderão herdar permissões de outras funções de banco de dados, como o predicado de filtro se baseia em nomes de usuário ou logon, não em funções.</span><span class="sxs-lookup"><span data-stu-id="d2e54-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>  
  
-   <span data-ttu-id="d2e54-124">Grant EXECUTE nos procedimentos armazenados para funções de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d2e54-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="d2e54-125">Os usuários só podem acessar dados por meio de procedimentos armazenados fornecidos.</span><span class="sxs-lookup"><span data-stu-id="d2e54-125">Users can only access data through the stored procedures provided.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="d2e54-126">Recursos externos</span><span class="sxs-lookup"><span data-stu-id="d2e54-126">External Resources</span></span>  
 <span data-ttu-id="d2e54-127">Para obter mais informações, consulte o seguinte recurso.</span><span class="sxs-lookup"><span data-stu-id="d2e54-127">For more information, see the following resource.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d2e54-128">[Implementando a segurança de nível de linha e célula no classificadas bancos de dados usando o SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=98227) no site do TechCenter do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d2e54-128">[Implementing Row- and Cell-Level Security in Classified Databases Using SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=98227) on the SQL Server TechCenter site.</span></span>|<span data-ttu-id="d2e54-129">Descreve como usar a segurança em nível de linha e célula para atender aos requisitos de segurança de banco de dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="d2e54-129">Describes how to use row- and cell-level security to meet classified database security requirements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2e54-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2e54-130">See Also</span></span>  
 [<span data-ttu-id="d2e54-131">Segurança em nível de linha</span><span class="sxs-lookup"><span data-stu-id="d2e54-131">Row-Level Security</span></span>](https://msdn.microsoft.com/library/dn765131.aspx)  
 <span data-ttu-id="d2e54-132">[Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="d2e54-132">[Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)</span></span>  
 [<span data-ttu-id="d2e54-133">Visão geral de segurança do SQL Server</span><span class="sxs-lookup"><span data-stu-id="d2e54-133">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="d2e54-134">Cenários de segurança do aplicativo no SQL Server</span><span class="sxs-lookup"><span data-stu-id="d2e54-134">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="d2e54-135">Gerenciando permissões com procedimentos armazenados no SQL Server</span><span class="sxs-lookup"><span data-stu-id="d2e54-135">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="d2e54-136">Escrevendo SQL dinâmico seguro no SQL Server</span><span class="sxs-lookup"><span data-stu-id="d2e54-136">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 <span data-ttu-id="d2e54-137">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="d2e54-137">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
