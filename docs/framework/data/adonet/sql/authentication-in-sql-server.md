---
title: Autenticação no SQL Server
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 0172259446724e0be85bd7ca2d15cf299db04e27
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613096"
---
# <a name="authentication-in-sql-server"></a>Autenticação no SQL Server
SQL Server dá suporte a dois modos de autenticação, o modo de autenticação do Windows e o modo misto.  
  
-   Autenticação do Windows é o padrão e é conhecida como segurança integrada porque esse modelo de segurança do SQL Server está totalmente integrado ao Windows. As contas de usuário e grupos específicas do Windows são confiáveis para fazer logon no SQL Server. Os usuários do Windows que tiverem sido autenticados não precisam apresentar credenciais adicionais.  
  
-   Modo misto oferece suporte à autenticação pelo Windows e pelo SQL Server. Os pares de nome e senha do usuário são mantidos dentro do SQL Server.  
  
> [!IMPORTANT]
>  Recomendamos usar a autenticação do Windows sempre que for possível. Autenticação do Windows usa uma série de mensagens criptografadas para autenticar usuários no SQL Server. Quando são usados logons do SQL Server, nomes de logon do SQL Server e as senhas criptografadas são passadas pela rede, o que torna menos seguros.  
  
 Com a autenticação do Windows, os usuários já estão conectados no Windows e não precisa fazer logon separadamente para o SQL Server. O seguinte `SqlConnection.ConnectionString` Especifica autenticação do Windows sem exigir que os usuários forneçam um nome de usuário ou senha.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  Os logons são distintos dos usuários do banco de dados. Você deve mapear logons ou grupos do Windows para usuários de banco de dados ou funções em uma operação separada. Em seguida, você concede permissões para usuários ou funções para acessar os objetos de banco de dados.  
  
## <a name="authentication-scenarios"></a>Cenários de autenticação  
 A autenticação do Windows geralmente é a melhor escolha nas seguintes situações:  
  
-   Há um controlador de domínio.  
  
-   O aplicativo e o banco de dados estão no mesmo computador.  
  
-   Você está usando uma instância do SQL Server Express ou LocalDB.  
  
 Os logons do SQL Server são geralmente usados nas seguintes situações:  
  
-   Se você tiver um grupo de trabalho.  
  
-   Os usuários se conectam de domínios diferentes e não confiáveis.  
  
-   Aplicativos de Internet, como [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  
  
> [!NOTE]
>  Especifica autenticação do Windows não desabilita os logons do SQL Server. Use o ALTER LOGIN DISABLE [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrução para desabilitar os logons do SQL Server altamente privilegiados.  
  
## <a name="login-types"></a>Tipos de logon  
 SQL Server dá suporte a três tipos de logons:  
  
-   Uma conta de usuário local do Windows ou uma conta de domínio confiável. SQL Server se baseia em Windows para autenticar as contas de usuário do Windows.  
  
-   Grupo do Windows. Conceder acesso a um grupo do Windows concede acesso a todos os logons de usuário do Windows que são membros do grupo.  
  
-   Logon do SQL Server. SQL Server armazena o nome de usuário e um hash da senha no banco de dados mestre, usando métodos de autenticação interna para verificar as tentativas de logon.  
  
> [!NOTE]
>  O SQL Server fornece os logons criados de certificados ou chaves assimétricas que são usadas apenas para assinatura de código. Eles não podem ser usados para se conectar ao SQL Server.  
  
## <a name="mixed-mode-authentication"></a>Autenticação de modo misto  
 Se você precisar usar a autenticação de modo misto, você deve criar os logons do SQL Server, que são armazenados no SQL Server. Em seguida, você precisa fornecer o nome de usuário do SQL Server e a senha em tempo de execução.  
  
> [!IMPORTANT]
>  Instala o SQL Server com um logon do SQL Server denominado `sa` (uma abreviação de "administrador do sistema"). Atribua uma senha forte para o logon do `sa` e não use o logon do `sa` em seu aplicativo. O logon do `sa` mapeia para a função de servidor fixa `sysadmin`, que tem credenciais administrativas irrevogáveis no servidor inteiro. Não haverá limites para o dano potencial se um invasor obtiver acesso como administrador do sistema. Todos os membros do Windows `BUILTIN\Administrators` grupo (grupo de administradores locais) são membros do `sysadmin` função por padrão, mas podem ser removidos dessa função.  
  
 O SQL Server fornece mecanismos de política de senha do Windows para logons do SQL Server quando ele é executado em [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] ou versões posteriores. As políticas de complexidade de senha foram criadas para intimidar ataques de força bruta aumentando o número de senhas possíveis. SQL Server pode aplicar as mesmas políticas de complexidade e expiração usadas no [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] para senhas usadas no SQL Server.  
  
> [!IMPORTANT]
>  Concatenar cadeias de conexão de entrada do usuário pode deixá-lo vulnerável a um ataque de injeção de cadeia de conexão. Use o <xref:System.Data.SqlClient.SqlConnectionStringBuilder> para criar cadeias de conexão válidas sintaticamente em tempo de execução. Para obter mais informações, confira [Construtores de cadeias de conexão](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Entidades de segurança](/sql/relational-databases/security/authentication-access/principals-database-engine)|Descreve logons e outras entidades de segurança no SQL Server.|  
  
## <a name="see-also"></a>Consulte também  
 [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Conectando a uma fonte de dados](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Cadeia de Conexão](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
