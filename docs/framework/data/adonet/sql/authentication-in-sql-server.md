---
title: Autenticação no SQL Server
description: Saiba mais sobre a autenticação com SQL Server para ADO.NET, incluindo o modo de autenticação do Windows e o modo misto.
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 2c4f62391a0d9b5ada27f56eef4c3467d99b4c6d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197521"
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="76c52-103">Autenticação no SQL Server</span><span class="sxs-lookup"><span data-stu-id="76c52-103">Authentication in SQL Server</span></span>

<span data-ttu-id="76c52-104">O SQL Server dá suporte a dois modos de autenticação, autenticação do Windows e modo misto.</span><span class="sxs-lookup"><span data-stu-id="76c52-104">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
- <span data-ttu-id="76c52-105">A autenticação do Windows é o padrão, e é geralmente conhecida como segurança integrada porque esse modelo de segurança do SQL Server está integrado com o Windows.</span><span class="sxs-lookup"><span data-stu-id="76c52-105">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="76c52-106">Contas específicas de usuário e de grupo do Windows são confiáveis para fazer logon no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="76c52-106">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="76c52-107">Os usuários do Windows que já foram autenticados não precisam apresentar credenciais adicionais.</span><span class="sxs-lookup"><span data-stu-id="76c52-107">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
- <span data-ttu-id="76c52-108">O modo misto oferece suporte à autenticação pelo Windows e pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="76c52-108">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="76c52-109">Os pares de nome de usuário e senha são mantidos dentro do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="76c52-109">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="76c52-110">Recomendamos usar a autenticação do Windows sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="76c52-110">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="76c52-111">A autenticação do Windows usa uma série de mensagens criptografadas para autenticar usuários no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="76c52-111">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="76c52-112">Quando os logons do SQL Server são usados, os nomes e as senhas de logon criptografados do SQL Server são passados pela rede, o que os torna menos seguros.</span><span class="sxs-lookup"><span data-stu-id="76c52-112">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="76c52-113">Com a autenticação do Windows, os usuários já estão conectados no Windows e não precisam fazer logon separadamente no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="76c52-113">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="76c52-114">O `SqlConnection.ConnectionString` a seguir especifica a autenticação do Windows sem exigir que os usuários informem um nome de usuário ou senha.</span><span class="sxs-lookup"><span data-stu-id="76c52-114">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span></span>  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> <span data-ttu-id="76c52-115">Os logons são diferentes dos usuários de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="76c52-115">Logins are distinct from database users.</span></span> <span data-ttu-id="76c52-116">Você precisa mapear logons ou grupos do Windows para usuários ou funções de banco de dados em uma operação separada.</span><span class="sxs-lookup"><span data-stu-id="76c52-116">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="76c52-117">Em seguida, conceda permissões a usuários ou funções para acessar objetos de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="76c52-117">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="76c52-118">Cenários de autenticação</span><span class="sxs-lookup"><span data-stu-id="76c52-118">Authentication Scenarios</span></span>  

 <span data-ttu-id="76c52-119">A autenticação do Windows é geralmente a melhor opção nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="76c52-119">Windows authentication is usually the best choice in the following situations:</span></span>  
  
- <span data-ttu-id="76c52-120">Há um controlador de domínio.</span><span class="sxs-lookup"><span data-stu-id="76c52-120">There is a domain controller.</span></span>  
  
- <span data-ttu-id="76c52-121">O aplicativo e o banco de dados estão no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="76c52-121">The application and the database are on the same computer.</span></span>  
  
- <span data-ttu-id="76c52-122">Você está usando uma instância do SQL Server Express ou LocalDB.</span><span class="sxs-lookup"><span data-stu-id="76c52-122">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="76c52-123">Os logons do SQL Server geralmente são usados nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="76c52-123">SQL Server logins are often used in the following situations:</span></span>  
  
- <span data-ttu-id="76c52-124">Se você tiver um grupo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="76c52-124">If you have a workgroup.</span></span>  
  
- <span data-ttu-id="76c52-125">Os usuários se conectam de diferentes domínios não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="76c52-125">Users connect from different, non-trusted domains.</span></span>  
  
- <span data-ttu-id="76c52-126">Aplicativos de Internet, como o ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="76c52-126">Internet applications, such as ASP.NET.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76c52-127">Especificar a autenticação do Windows não desabilita os logons do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="76c52-127">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="76c52-128">Use a instrução ALTER LOGIN DISABLE do Transact-SQL para desabilitar logons do SQL Server com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="76c52-128">Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="76c52-129">Tipos de logon</span><span class="sxs-lookup"><span data-stu-id="76c52-129">Login Types</span></span>  

 <span data-ttu-id="76c52-130">O SQL Server dá suporte a três tipos de logon:</span><span class="sxs-lookup"><span data-stu-id="76c52-130">SQL Server supports three types of logins:</span></span>  
  
- <span data-ttu-id="76c52-131">Uma conta de usuário do Windows local ou uma conta de domínio confiável.</span><span class="sxs-lookup"><span data-stu-id="76c52-131">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="76c52-132">O SQL Server depende do Windows para autenticar as contas de usuário do Windows.</span><span class="sxs-lookup"><span data-stu-id="76c52-132">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
- <span data-ttu-id="76c52-133">Grupo do Windows.</span><span class="sxs-lookup"><span data-stu-id="76c52-133">Windows group.</span></span> <span data-ttu-id="76c52-134">Permitir acesso a um grupo do Windows permite acesso a todos os logons de usuário do Windows que são membros do grupo.</span><span class="sxs-lookup"><span data-stu-id="76c52-134">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
- <span data-ttu-id="76c52-135">Logon do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="76c52-135">SQL Server login.</span></span> <span data-ttu-id="76c52-136">O SQL Server armazena o nome de usuário e um hash da senha no banco de dados mestre, usando métodos de autenticação interna para verificar tentativas de logon.</span><span class="sxs-lookup"><span data-stu-id="76c52-136">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76c52-137">O SQL Server fornece os logons criados de certificados ou chaves assimétricas que são usados somente para assinatura de código.</span><span class="sxs-lookup"><span data-stu-id="76c52-137">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="76c52-138">Eles não podem ser usados para a conexão com o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="76c52-138">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="76c52-139">Autenticação de modo misto</span><span class="sxs-lookup"><span data-stu-id="76c52-139">Mixed Mode Authentication</span></span>  

 <span data-ttu-id="76c52-140">Se você deve usar a autenticação de modo misto, deverá criar os logons do SQL Server, que são armazenados no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="76c52-140">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="76c52-141">Em seguida, você terá que fornecer o nome de usuário e a senha do SQL Server em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="76c52-141">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="76c52-142">O SQL Server é instalado com um logon do SQL Server chamado `sa` (uma abreviação de "administrador do sistema").</span><span class="sxs-lookup"><span data-stu-id="76c52-142">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="76c52-143">Atribua uma senha forte ao logon do `sa` e não use o logon do `sa` em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76c52-143">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="76c52-144">O logon do `sa` mapeia para a função de servidor fixa `sysadmin`, que tem credenciais administrativas irrevogáveis no servidor inteiro.</span><span class="sxs-lookup"><span data-stu-id="76c52-144">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="76c52-145">Não haverá limites para o dano potencial se um invasor obtiver acesso como administrador do sistema.</span><span class="sxs-lookup"><span data-stu-id="76c52-145">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="76c52-146">Todos os membros do grupo `BUILTIN\Administrators` do Windows (grupo do administrador local) são membros da função `sysadmin` por padrão, mas podem ser removidos dessa função.</span><span class="sxs-lookup"><span data-stu-id="76c52-146">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="76c52-147">SQL Server fornece mecanismos de política de senha do Windows para SQL Server logons.</span><span class="sxs-lookup"><span data-stu-id="76c52-147">SQL Server provides Windows password policy mechanisms for SQL Server logins.</span></span> <span data-ttu-id="76c52-148">As políticas de complexidade de senha são projetadas para deter ataques de força bruta aumentando o número de possíveis senhas.</span><span class="sxs-lookup"><span data-stu-id="76c52-148">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="76c52-149">SQL Server pode aplicar a mesma complexidade e políticas de expiração às senhas usadas no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="76c52-149">SQL Server can apply the same complexity and expiration policies to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="76c52-150">Concatenar cadeias de conexão da entrada do usuário pode deixá-lo vulnerável a um ataque de injeção de cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="76c52-150">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="76c52-151">Use o <xref:System.Data.SqlClient.SqlConnectionStringBuilder> para criar cadeias de conexão sintaticamente válidas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="76c52-151">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="76c52-152">Para obter mais informações, confira [Construtores de cadeias de conexão](../connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="76c52-152">For more information, see [Connection String Builders](../connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="76c52-153">Recursos externos</span><span class="sxs-lookup"><span data-stu-id="76c52-153">External Resources</span></span>  

 <span data-ttu-id="76c52-154">Para obter mais informações, consulte os recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="76c52-154">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="76c52-155">Recurso</span><span class="sxs-lookup"><span data-stu-id="76c52-155">Resource</span></span>|<span data-ttu-id="76c52-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="76c52-156">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="76c52-157">Entidades</span><span class="sxs-lookup"><span data-stu-id="76c52-157">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="76c52-158">Descreve logons e outras entidades de segurança no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="76c52-158">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76c52-159">Veja também</span><span class="sxs-lookup"><span data-stu-id="76c52-159">See also</span></span>

- [<span data-ttu-id="76c52-160">Protegendo aplicativos ADO.NET</span><span class="sxs-lookup"><span data-stu-id="76c52-160">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="76c52-161">Cenários de Segurança de Aplicativo no SQL Server</span><span class="sxs-lookup"><span data-stu-id="76c52-161">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="76c52-162">Conectando a uma Fonte de Dados</span><span class="sxs-lookup"><span data-stu-id="76c52-162">Connecting to a Data Source</span></span>](../connecting-to-a-data-source.md)
- [<span data-ttu-id="76c52-163">Cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="76c52-163">Connection Strings</span></span>](../connection-strings.md)
- [<span data-ttu-id="76c52-164">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="76c52-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
