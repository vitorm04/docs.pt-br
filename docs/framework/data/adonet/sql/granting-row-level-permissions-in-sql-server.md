---
title: Conceder permissões de nível de linha no SQL Server
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 0b34eaee4b66a2be82049816f0a98b9f53012303
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554847"
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="63c59-102">Conceder permissões de nível de linha no SQL Server</span><span class="sxs-lookup"><span data-stu-id="63c59-102">Granting Row-Level Permissions in SQL Server</span></span>

<span data-ttu-id="63c59-103">Em alguns cenários, há um requisito para controlar o acesso aos dados em um nível mais granular do que o que simplesmente conceder, revogar ou negar permissões fornece.</span><span class="sxs-lookup"><span data-stu-id="63c59-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="63c59-104">Por exemplo, um aplicativo de banco de dados do hospital pode exigir que os médicos individuais estejam restritos a acessar informações relacionadas apenas a seus pacientes.</span><span class="sxs-lookup"><span data-stu-id="63c59-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="63c59-105">Existem requisitos semelhantes em muitos ambientes, incluindo aplicativos financeiros, de lei, governamentais e militares.</span><span class="sxs-lookup"><span data-stu-id="63c59-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="63c59-106">Para ajudar a resolver esses cenários, o SQL Server 2016 fornece um recurso de [segurança em nível de linha](/sql/relational-databases/security/row-level-security) que simplifica e centraliza a lógica de acesso em nível de linha em uma política de segurança.</span><span class="sxs-lookup"><span data-stu-id="63c59-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](/sql/relational-databases/security/row-level-security) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="63c59-107">Para versões anteriores do SQL Server, uma funcionalidade semelhante pode ser obtida usando exibições para aplicar a filtragem em nível de linha.</span><span class="sxs-lookup"><span data-stu-id="63c59-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>

## <a name="implementing-row-level-filtering"></a><span data-ttu-id="63c59-108">Implementando a filtragem em nível de linha</span><span class="sxs-lookup"><span data-stu-id="63c59-108">Implementing Row-level Filtering</span></span>

<span data-ttu-id="63c59-109">A filtragem em nível de linha é usada para aplicativos que armazenam informações em uma única tabela, como no exemplo de hospital acima.</span><span class="sxs-lookup"><span data-stu-id="63c59-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="63c59-110">Para implementar a filtragem em nível de linha, cada linha tem uma coluna que define um parâmetro de diferenciação, como um nome de usuário, rótulo ou outro identificador.</span><span class="sxs-lookup"><span data-stu-id="63c59-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="63c59-111">Você cria uma política de segurança ou uma exibição na tabela, que filtra as linhas que o usuário pode acessar.</span><span class="sxs-lookup"><span data-stu-id="63c59-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="63c59-112">Em seguida, você cria procedimentos armazenados parametrizados, que controlam os tipos de consultas que o usuário pode executar.</span><span class="sxs-lookup"><span data-stu-id="63c59-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>

<span data-ttu-id="63c59-113">O exemplo a seguir descreve como configurar a filtragem em nível de linha com base em um usuário ou nome de logon:</span><span class="sxs-lookup"><span data-stu-id="63c59-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>

- <span data-ttu-id="63c59-114">Crie a tabela, adicionando uma coluna para armazenar o nome.</span><span class="sxs-lookup"><span data-stu-id="63c59-114">Create the table, adding a column to store the name.</span></span>

- <span data-ttu-id="63c59-115">Habilitar Filtragem em nível de linha:</span><span class="sxs-lookup"><span data-stu-id="63c59-115">Enable row-level filtering:</span></span>

  - <span data-ttu-id="63c59-116">Se você estiver usando o SQL Server 2016 ou superior, ou o [banco de dados SQL do Azure](/azure/sql-database/), crie uma política de segurança que adiciona um predicado na tabela que restringe as linhas retornadas àquelas que correspondem ao usuário do banco de dados atual (usando a função interna CURRENT_USER ()) ou o nome de logon atual (usando a função interna SUSER_SNAME ()):</span><span class="sxs-lookup"><span data-stu-id="63c59-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>

      ```sql
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

  - <span data-ttu-id="63c59-117">Se você estiver usando uma versão do SQL Server anterior a 2016, poderá obter uma funcionalidade semelhante usando uma exibição:</span><span class="sxs-lookup"><span data-stu-id="63c59-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- <span data-ttu-id="63c59-118">Crie procedimentos armazenados para selecionar, inserir, atualizar e excluir dados.</span><span class="sxs-lookup"><span data-stu-id="63c59-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="63c59-119">Se a filtragem for aplicada por uma política de segurança, os procedimentos armazenados devem executar essas operações na tabela base diretamente; caso contrário, se a filtragem for aplicada por um modo de exibição, os procedimentos armazenados deverão operar em relação à exibição.</span><span class="sxs-lookup"><span data-stu-id="63c59-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="63c59-120">A política de segurança ou a exibição filtrará automaticamente as linhas retornadas ou modificadas por consultas de usuário, e o procedimento armazenado fornecerá um limite de segurança mais difícil para impedir que os usuários com acesso direto a consultas executem com êxito consultas que podem inferir a existência de dados filtrados.</span><span class="sxs-lookup"><span data-stu-id="63c59-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>

- <span data-ttu-id="63c59-121">Para procedimentos armazenados que inserem dados, Capture o nome de usuário usando a mesma função especificada na política de segurança ou exibição e insira esse valor na coluna nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="63c59-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>

- <span data-ttu-id="63c59-122">Negue todas as permissões nas tabelas (e exibições, se aplicável) à `public` função.</span><span class="sxs-lookup"><span data-stu-id="63c59-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="63c59-123">Os usuários não poderão herdar permissões de outras funções de banco de dados, pois o predicado de filtro é baseado em nomes de usuário ou de logon, não em funções.</span><span class="sxs-lookup"><span data-stu-id="63c59-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>

- <span data-ttu-id="63c59-124">Conceda EXECUTE nos procedimentos armazenados para funções de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="63c59-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="63c59-125">Os usuários só podem acessar dados por meio dos procedimentos armazenados fornecidos.</span><span class="sxs-lookup"><span data-stu-id="63c59-125">Users can only access data through the stored procedures provided.</span></span>

## <a name="see-also"></a><span data-ttu-id="63c59-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="63c59-126">See also</span></span>

- [<span data-ttu-id="63c59-127">Segurança em nível de linha</span><span class="sxs-lookup"><span data-stu-id="63c59-127">Row-Level Security</span></span>](/sql/relational-databases/security/row-level-security)
- [<span data-ttu-id="63c59-128">Protegendo aplicativos ADO.NET</span><span class="sxs-lookup"><span data-stu-id="63c59-128">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="63c59-129">Visão geral de segurança do SQL Server</span><span class="sxs-lookup"><span data-stu-id="63c59-129">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="63c59-130">Cenários de Segurança de Aplicativo no SQL Server</span><span class="sxs-lookup"><span data-stu-id="63c59-130">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="63c59-131">Gerenciando permissões com procedimentos armazenados no SQL Server</span><span class="sxs-lookup"><span data-stu-id="63c59-131">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="63c59-132">Gravação de SQL Dinâmico Seguro no SQL Server</span><span class="sxs-lookup"><span data-stu-id="63c59-132">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="63c59-133">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="63c59-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
