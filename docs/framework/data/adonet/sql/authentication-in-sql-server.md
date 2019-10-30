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
# <a name="authentication-in-sql-server"></a>Autenticação no SQL Server
O SQL Server dá suporte a dois modos de autenticação, modo de autenticação do Windows e modo misto.  
  
- A autenticação do Windows é o padrão e, muitas vezes, é conhecida como segurança integrada porque esse modelo de segurança SQL Server é totalmente integrado ao Windows. As contas de usuário e grupos específicas do Windows são confiáveis para fazer logon no SQL Server. Os usuários do Windows que tiverem sido autenticados não precisam apresentar credenciais adicionais.  
  
- O modo misto dá suporte à autenticação pelo Windows e por SQL Server. Os pares de nome de usuário e senha são mantidos no SQL Server.  
  
> [!IMPORTANT]
> Recomendamos usar a autenticação do Windows sempre que for possível. A autenticação do Windows usa uma série de mensagens criptografadas para autenticar usuários no SQL Server. Quando são usados SQL Server logons, SQL Server nomes de logon e senhas criptografadas são transmitidos pela rede, o que os torna menos seguros.  
  
 Com a autenticação do Windows, os usuários já estão conectados no Windows e não precisam fazer logon separadamente para SQL Server. O `SqlConnection.ConnectionString` a seguir especifica a autenticação do Windows sem exigir que os usuários forneçam um nome de usuário ou senha.  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> Os logons são distintos dos usuários do banco de dados. Você deve mapear logons ou grupos do Windows para usuários de banco de dados ou funções em uma operação separada. Em seguida, você concede permissões para usuários ou funções para acessar os objetos de banco de dados.  
  
## <a name="authentication-scenarios"></a>Cenários de autenticação  
 A autenticação do Windows geralmente é a melhor escolha nas seguintes situações:  
  
- Há um controlador de domínio.  
  
- O aplicativo e o banco de dados estão no mesmo computador.  
  
- Você está usando uma instância de SQL Server Express ou LocalDB.  
  
 Os logons do SQL Server são geralmente usados nas seguintes situações:  
  
- Se você tiver um grupo de trabalho.  
  
- Os usuários se conectam de domínios diferentes e não confiáveis.  
  
- Aplicativos de Internet, como ASP.NET.  
  
> [!NOTE]
> A especificação da autenticação do Windows não desabilita os logons do SQL Server. Use a instrução ALTER LOGIN DISABLE Transact-SQL para desabilitar os logons de SQL Server altamente privilegiados.  
  
## <a name="login-types"></a>Tipos de logon  
 O SQL Server dá suporte a três tipos de logons:  
  
- Uma conta de usuário local do Windows ou uma conta de domínio confiável. SQL Server se baseia no Windows para autenticar as contas de usuário do Windows.  
  
- Grupo do Windows. Conceder acesso a um grupo do Windows concede acesso a todos os logons de usuário do Windows que são membros do grupo.  
  
- SQL Server logon. SQL Server armazena o nome de usuário e um hash da senha no banco de dados mestre, usando métodos de autenticação interna para verificar as tentativas de logon.  
  
> [!NOTE]
> SQL Server fornece logons criados a partir de certificados ou chaves assimétricas que são usadas somente para assinatura de código. Eles não podem ser usados para se conectar ao SQL Server.  
  
## <a name="mixed-mode-authentication"></a>Autenticação de modo misto  
 Se você precisar usar a autenticação de modo misto, deverá criar SQL Server logons, que são armazenados em SQL Server. Em seguida, você precisa fornecer o nome de usuário e a senha do SQL Server em tempo de execução.  
  
> [!IMPORTANT]
> O SQL Server é instalado com um logon do SQL Server chamado `sa` (uma abreviação de "administrador do sistema"). Atribua uma senha forte para o logon do `sa` e não use o logon do `sa` em seu aplicativo. O logon do `sa` mapeia para a função de servidor fixa `sysadmin`, que tem credenciais administrativas irrevogáveis no servidor inteiro. Não haverá limites para o dano potencial se um invasor obtiver acesso como administrador do sistema. Todos os membros do grupo de `BUILTIN\Administrators` do Windows (o grupo do administrador local) são membros da função `sysadmin` por padrão, mas podem ser removidos dessa função.  
  
 SQL Server fornece mecanismos de política de senha do Windows para SQL Server logons quando ele é executado no [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] ou em versões posteriores. As políticas de complexidade de senha foram criadas para intimidar ataques de força bruta aumentando o número de senhas possíveis. SQL Server pode aplicar a mesma complexidade e políticas de expiração usadas em [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] a senhas usadas dentro de SQL Server.  
  
> [!IMPORTANT]
> Concatenar cadeias de conexão de entrada do usuário pode deixá-lo vulnerável a um ataque de injeção de cadeia de conexão. Use o <xref:System.Data.SqlClient.SqlConnectionStringBuilder> para criar cadeias de conexão válidas sintaticamente em tempo de execução. Para obter mais informações, confira [Construtores de cadeias de conexão](../connection-string-builders.md).  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Entidades](/sql/relational-databases/security/authentication-access/principals-database-engine)|Descreve os logons e outras entidades de segurança no SQL Server.|  
  
## <a name="see-also"></a>Consulte também

- [Securing ADO.NET Applications](../securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [Cenários de segurança do aplicativo no SQL Server](application-security-scenarios-in-sql-server.md)
- [Conectando a uma fonte de dados](../connecting-to-a-data-source.md)
- [Cadeia de Conexão](../connection-strings.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
