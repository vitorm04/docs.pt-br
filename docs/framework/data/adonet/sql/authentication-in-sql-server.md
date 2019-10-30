---
title: Autenticação no SQL Server
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 09f7825fd6b4f852b24142ea297c078bd8a1e221
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040265"
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="3db8d-102">Autenticação no SQL Server</span><span class="sxs-lookup"><span data-stu-id="3db8d-102">Authentication in SQL Server</span></span>
<span data-ttu-id="3db8d-103">O SQL Server dá suporte a dois modos de autenticação, modo de autenticação do Windows e modo misto.</span><span class="sxs-lookup"><span data-stu-id="3db8d-103">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
- <span data-ttu-id="3db8d-104">A autenticação do Windows é o padrão e, muitas vezes, é conhecida como segurança integrada porque esse modelo de segurança SQL Server é totalmente integrado ao Windows.</span><span class="sxs-lookup"><span data-stu-id="3db8d-104">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="3db8d-105">As contas de usuário e grupos específicas do Windows são confiáveis para fazer logon no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3db8d-105">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="3db8d-106">Os usuários do Windows que tiverem sido autenticados não precisam apresentar credenciais adicionais.</span><span class="sxs-lookup"><span data-stu-id="3db8d-106">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
- <span data-ttu-id="3db8d-107">O modo misto dá suporte à autenticação pelo Windows e por SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3db8d-107">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="3db8d-108">Os pares de nome de usuário e senha são mantidos no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3db8d-108">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3db8d-109">Recomendamos usar a autenticação do Windows sempre que for possível.</span><span class="sxs-lookup"><span data-stu-id="3db8d-109">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="3db8d-110">A autenticação do Windows usa uma série de mensagens criptografadas para autenticar usuários no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3db8d-110">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="3db8d-111">Quando são usados SQL Server logons, SQL Server nomes de logon e senhas criptografadas são transmitidos pela rede, o que os torna menos seguros.</span><span class="sxs-lookup"><span data-stu-id="3db8d-111">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="3db8d-112">Com a autenticação do Windows, os usuários já estão conectados no Windows e não precisam fazer logon separadamente para SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3db8d-112">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="3db8d-113">O `SqlConnection.ConnectionString` a seguir especifica a autenticação do Windows sem exigir que os usuários forneçam um nome de usuário ou senha.</span><span class="sxs-lookup"><span data-stu-id="3db8d-113">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span></span>  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> <span data-ttu-id="3db8d-114">Os logons são distintos dos usuários do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3db8d-114">Logins are distinct from database users.</span></span> <span data-ttu-id="3db8d-115">Você deve mapear logons ou grupos do Windows para usuários de banco de dados ou funções em uma operação separada.</span><span class="sxs-lookup"><span data-stu-id="3db8d-115">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="3db8d-116">Em seguida, você concede permissões para usuários ou funções para acessar os objetos de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3db8d-116">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="3db8d-117">Cenários de autenticação</span><span class="sxs-lookup"><span data-stu-id="3db8d-117">Authentication Scenarios</span></span>  
 <span data-ttu-id="3db8d-118">A autenticação do Windows geralmente é a melhor escolha nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="3db8d-118">Windows authentication is usually the best choice in the following situations:</span></span>  
  
- <span data-ttu-id="3db8d-119">Há um controlador de domínio.</span><span class="sxs-lookup"><span data-stu-id="3db8d-119">There is a domain controller.</span></span>  
  
- <span data-ttu-id="3db8d-120">O aplicativo e o banco de dados estão no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="3db8d-120">The application and the database are on the same computer.</span></span>  
  
- <span data-ttu-id="3db8d-121">Você está usando uma instância de SQL Server Express ou LocalDB.</span><span class="sxs-lookup"><span data-stu-id="3db8d-121">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="3db8d-122">Os logons do SQL Server são geralmente usados nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="3db8d-122">SQL Server logins are often used in the following situations:</span></span>  
  
- <span data-ttu-id="3db8d-123">Se você tiver um grupo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3db8d-123">If you have a workgroup.</span></span>  
  
- <span data-ttu-id="3db8d-124">Os usuários se conectam de domínios diferentes e não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="3db8d-124">Users connect from different, non-trusted domains.</span></span>  
  
- <span data-ttu-id="3db8d-125">Aplicativos de Internet, como ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3db8d-125">Internet applications, such as ASP.NET.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3db8d-126">A especificação da autenticação do Windows não desabilita os logons do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3db8d-126">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="3db8d-127">Use a instrução ALTER LOGIN DISABLE Transact-SQL para desabilitar os logons de SQL Server altamente privilegiados.</span><span class="sxs-lookup"><span data-stu-id="3db8d-127">Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="3db8d-128">Tipos de logon</span><span class="sxs-lookup"><span data-stu-id="3db8d-128">Login Types</span></span>  
 <span data-ttu-id="3db8d-129">O SQL Server dá suporte a três tipos de logons:</span><span class="sxs-lookup"><span data-stu-id="3db8d-129">SQL Server supports three types of logins:</span></span>  
  
- <span data-ttu-id="3db8d-130">Uma conta de usuário local do Windows ou uma conta de domínio confiável.</span><span class="sxs-lookup"><span data-stu-id="3db8d-130">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="3db8d-131">SQL Server se baseia no Windows para autenticar as contas de usuário do Windows.</span><span class="sxs-lookup"><span data-stu-id="3db8d-131">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
- <span data-ttu-id="3db8d-132">Grupo do Windows.</span><span class="sxs-lookup"><span data-stu-id="3db8d-132">Windows group.</span></span> <span data-ttu-id="3db8d-133">Conceder acesso a um grupo do Windows concede acesso a todos os logons de usuário do Windows que são membros do grupo.</span><span class="sxs-lookup"><span data-stu-id="3db8d-133">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
- <span data-ttu-id="3db8d-134">SQL Server logon.</span><span class="sxs-lookup"><span data-stu-id="3db8d-134">SQL Server login.</span></span> <span data-ttu-id="3db8d-135">SQL Server armazena o nome de usuário e um hash da senha no banco de dados mestre, usando métodos de autenticação interna para verificar as tentativas de logon.</span><span class="sxs-lookup"><span data-stu-id="3db8d-135">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3db8d-136">SQL Server fornece logons criados a partir de certificados ou chaves assimétricas que são usadas somente para assinatura de código.</span><span class="sxs-lookup"><span data-stu-id="3db8d-136">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="3db8d-137">Eles não podem ser usados para se conectar ao SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3db8d-137">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="3db8d-138">Autenticação de modo misto</span><span class="sxs-lookup"><span data-stu-id="3db8d-138">Mixed Mode Authentication</span></span>  
 <span data-ttu-id="3db8d-139">Se você precisar usar a autenticação de modo misto, deverá criar SQL Server logons, que são armazenados em SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3db8d-139">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="3db8d-140">Em seguida, você precisa fornecer o nome de usuário e a senha do SQL Server em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3db8d-140">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3db8d-141">O SQL Server é instalado com um logon do SQL Server chamado `sa` (uma abreviação de "administrador do sistema").</span><span class="sxs-lookup"><span data-stu-id="3db8d-141">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="3db8d-142">Atribua uma senha forte para o logon do `sa` e não use o logon do `sa` em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3db8d-142">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="3db8d-143">O logon do `sa` mapeia para a função de servidor fixa `sysadmin`, que tem credenciais administrativas irrevogáveis no servidor inteiro.</span><span class="sxs-lookup"><span data-stu-id="3db8d-143">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="3db8d-144">Não haverá limites para o dano potencial se um invasor obtiver acesso como administrador do sistema.</span><span class="sxs-lookup"><span data-stu-id="3db8d-144">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="3db8d-145">Todos os membros do grupo de `BUILTIN\Administrators` do Windows (o grupo do administrador local) são membros da função `sysadmin` por padrão, mas podem ser removidos dessa função.</span><span class="sxs-lookup"><span data-stu-id="3db8d-145">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="3db8d-146">SQL Server fornece mecanismos de política de senha do Windows para SQL Server logons quando ele é executado no [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] ou em versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="3db8d-146">SQL Server provides Windows password policy mechanisms for SQL Server logins when it is running on [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] or later versions.</span></span> <span data-ttu-id="3db8d-147">As políticas de complexidade de senha foram criadas para intimidar ataques de força bruta aumentando o número de senhas possíveis.</span><span class="sxs-lookup"><span data-stu-id="3db8d-147">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="3db8d-148">SQL Server pode aplicar a mesma complexidade e políticas de expiração usadas em [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] a senhas usadas dentro de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3db8d-148">SQL Server can apply the same complexity and expiration policies used in [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3db8d-149">Concatenar cadeias de conexão de entrada do usuário pode deixá-lo vulnerável a um ataque de injeção de cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="3db8d-149">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="3db8d-150">Use o <xref:System.Data.SqlClient.SqlConnectionStringBuilder> para criar cadeias de conexão válidas sintaticamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3db8d-150">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="3db8d-151">Para obter mais informações, confira [Construtores de cadeias de conexão](../connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="3db8d-151">For more information, see [Connection String Builders](../connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="3db8d-152">Recursos externos</span><span class="sxs-lookup"><span data-stu-id="3db8d-152">External Resources</span></span>  
 <span data-ttu-id="3db8d-153">Para obter mais informações, consulte os seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="3db8d-153">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="3db8d-154">Recurso</span><span class="sxs-lookup"><span data-stu-id="3db8d-154">Resource</span></span>|<span data-ttu-id="3db8d-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="3db8d-155">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="3db8d-156">Entidades</span><span class="sxs-lookup"><span data-stu-id="3db8d-156">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="3db8d-157">Descreve os logons e outras entidades de segurança no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3db8d-157">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3db8d-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3db8d-158">See also</span></span>

- <span data-ttu-id="3db8d-159">[Securing ADO.NET Applications](../securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3db8d-159">[Securing ADO.NET Applications](../securing-ado-net-applications.md)</span></span>
- [<span data-ttu-id="3db8d-160">Cenários de segurança do aplicativo no SQL Server</span><span class="sxs-lookup"><span data-stu-id="3db8d-160">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="3db8d-161">Conectando a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="3db8d-161">Connecting to a Data Source</span></span>](../connecting-to-a-data-source.md)
- [<span data-ttu-id="3db8d-162">Cadeia de Conexão</span><span class="sxs-lookup"><span data-stu-id="3db8d-162">Connection Strings</span></span>](../connection-strings.md)
- <span data-ttu-id="3db8d-163">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3db8d-163">[ADO.NET Overview](../ado-net-overview.md)</span></span>
