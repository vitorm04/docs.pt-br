---
title: "Autenticação no SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
caps.latest.revision: "9"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fa9a23f00e7ce3b52c2ff64c8b22e1b4b8727b97
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="authentication-in-sql-server"></a>Autenticação no SQL Server
O [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] dá suporte a dois modos de autenticação, autenticação do Windows e modo misto.  
  
-   A autenticação do Windows é o padrão, e é geralmente conhecida como segurança integrada porque esse modelo de segurança do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] está integrado com o Windows. As contas de usuário e grupos específicas do Windows são confiáveis para fazer logon no SQL Server. Os usuários do Windows que tiverem sido autenticados não precisam apresentar credenciais adicionais.  
  
-   O modo misto oferece suporte à autenticação pelo Windows e pelo [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Os pares de nome de usuário e senha são mantidos dentro do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]
>  Recomendamos usar a autenticação do Windows sempre que for possível. A autenticação do Windows usa uma série de mensagens criptografadas para autenticar usuários no [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Quando os logons do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] são usados, os nomes e as senhas de logon do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] são passados pela rede, o que os torna menos seguros.  
  
 Com a autenticação do Windows, os usuários já estão conectados no Windows e não precisam fazer logon separadamente no [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. O `SqlConnection.ConnectionString` a seguir especifica a autenticação do Windows sem exigir nome de usuário ou senha.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  Os logons são distintos dos usuários do banco de dados. Você deve mapear logons ou grupos do Windows para usuários de banco de dados ou funções em uma operação separada. Em seguida, você concede permissões para usuários ou funções para acessar os objetos de banco de dados.  
  
## <a name="authentication-scenarios"></a>Cenários de autenticação  
 A autenticação do Windows geralmente é a melhor escolha nas seguintes situações:  
  
-   Há um controlador de domínio.  
  
-   O aplicativo e o banco de dados estão no mesmo computador.  
  
-   Você está usando uma instância do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express ou LocalDB.  
  
 Os logons do SQL Server são geralmente usados nas seguintes situações:  
  
-   Se você tiver um grupo de trabalho.  
  
-   Os usuários se conectam de domínios diferentes e não confiáveis.  
  
-   Aplicativos de Internet, como [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  
  
> [!NOTE]
>  Especificar a autenticação do Windows não desabilita os logons do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Use a instrução ALTER LOGIN DISABLE do [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] para desabilitar logons do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] com altos privilégios.  
  
## <a name="login-types"></a>Tipos de logon  
 O [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] dá suporte a três tipos de logons:  
  
-   Uma conta de usuário local do Windows ou uma conta de domínio confiável. O [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] depende do Windows para autenticar as contas de usuário do Windows.  
  
-   Grupo do Windows. Conceder acesso a um grupo do Windows concede acesso a todos os logons de usuário do Windows que são membros do grupo.  
  
-   Logon do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. O [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] armazena o nome de usuário e um hash da senha no banco de dados mestre, usando métodos de autenticação interna para verificar tentativas de logon.  
  
> [!NOTE]
>  O [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] fornece os logons criados de certificados ou chaves assimétricas que são usados somente para assinar o código. Eles não podem ser usados para se conectar ao [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
## <a name="mixed-mode-authentication"></a>Autenticação de modo misto  
 Se você deve usar a autenticação de modo misto, deverá criar os logons do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], que são armazenados no SQL Server. Em seguida, você terá que fornecer o nome de usuário e a senha do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] em tempo de execução.  
  
> [!IMPORTANT]
>  O [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] é instalado com um logon do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] chamado `sa` (uma abreviação de “administrador do sistema”). Atribua uma senha forte para o logon do `sa` e não use o logon do `sa` em seu aplicativo. O logon do `sa` mapeia para a função de servidor fixa `sysadmin`, que tem credenciais administrativas irrevogáveis no servidor inteiro. Não haverá limites para o dano potencial se um invasor obtiver acesso como administrador do sistema. Todos os membros do Windows `BUILTIN\Administrators` (grupo de administradores locais) são membros do `sysadmin` função por padrão, mas pode ser removido da função.  
  
 O [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] fornece mecanismos de política de senha do Windows para logons do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] quando estiver sendo executado no [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] ou em versões posteriores. As políticas de complexidade de senha foram criadas para intimidar ataques de força bruta aumentando o número de senhas possíveis. O [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] pode aplicar a mesma complexidade e as políticas de expiração usadas no [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] a senhas usadas dentro do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]
>  Concatenar cadeias de conexão de entrada do usuário pode deixá-lo vulnerável a um ataque de injeção de cadeia de conexão. Use o <xref:System.Data.SqlClient.SqlConnectionStringBuilder> para criar cadeias de conexão válidas sintaticamente em tempo de execução. Para obter mais informações, consulte [construtores de cadeia de Conexão](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Entidades](http://msdn.microsoft.com/library/bb543165.aspx) na [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Manuais Online|Descreve logons e outras entidades de segurança no [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].|  
  
## <a name="see-also"></a>Consulte também  
 [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Conectando a uma fonte de dados](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Cadeia de Conexão](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
