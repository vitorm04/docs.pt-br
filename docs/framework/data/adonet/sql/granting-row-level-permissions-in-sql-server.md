---
title: "Concedendo permissões de nível de linha no SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a42c8d24a2817fb0a4118927722e7ac1887517a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="granting-row-level-permissions-in-sql-server"></a>Concedendo permissões de nível de linha no SQL Server
Em alguns cenários, há um requisito para controlar o acesso a dados em um nível mais granular do que simplesmente conceder, revogar ou negar permissões fornece. Por exemplo, um aplicativo de banco de dados do hospital pode exigir médicos individuais poder acessar informações relacionadas ao somente seus pacientes. Existem requisitos semelhantes em muitos ambientes, incluindo finanças, lei, governo e aplicativos militares. Para ajudar a resolver esses cenários, o SQL Server 2016 fornece um [segurança em nível de linha](https://msdn.microsoft.com/library/dn765131.aspx) recurso que simplifica e centraliza a lógica de acesso de nível de linha em uma política de segurança. Para versões anteriores do SQL Server, uma funcionalidade semelhante pode ser obtida usando modos de exibição para aplicar a filtragem no nível de linha.  
  
## <a name="implementing-row-level-filtering"></a>Implementando a filtragem de nível de linha  
 Filtragem no nível de linha é usado para armazenar informações em uma única tabela, como no exemplo acima hospital de aplicativos. Para implementar filtragem de cada linha de nível de linha tem uma coluna que define um parâmetro de diferenciação, como um nome de usuário, o rótulo ou outro identificador. Você cria uma política de segurança ou uma exibição na tabela, que filtra as linhas que o usuário pode acessar. Você então pode criar procedimentos armazenados com parâmetros que controlam os tipos de consultas, que o usuário pode executar.  
  
 O exemplo a seguir descreve como configurar a filtragem de nível de linha com base em um nome de usuário ou de logon:  
  
-   Crie a tabela, adicionando uma coluna para armazenar o nome.  
  
-   Habilite a filtragem de nível de linha:  
  
    -   Se você estiver usando o SQL Server 2016 ou posterior, ou [banco de dados do SQL Azure](https://docs.microsoft.com/azure/sql-database/), criar uma política de segurança que adiciona um predicado na tabela restringir as linhas retornadas para aquelas que corresponder ao usuário atual do banco de dados (usando o CURRENT_USER() função interna) ou o nome de logon atual (usando a função interna de suser_sname ()):  
  
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
  
    -   Se você estiver usando uma versão do SQL Server antes de 2016, você pode obter uma funcionalidade semelhante usando um modo de exibição:  
  
        ```tsql  
        CREATE VIEW vw_MyTable  
        AS  
            RETURN SELECT * FROM MyTable  
            WHERE UserName = SUSER_SNAME()  
        GO  
        ```  
  
-   Crie procedimentos armazenados para selecionar, inserir, atualizar e excluir dados. Se a filtragem é aplicada por uma política de segurança, os procedimentos armazenados devem executar essas operações na tabela base diretamente. Caso contrário, se a filtragem é aplicada por uma exibição, os procedimentos armazenados em vez disso, devem operar em relação à exibição. A política de segurança ou a exibição filtrarão automaticamente as linhas retornadas ou modificado por consultas de usuário e o procedimento armazenado fornece um limite de segurança mais difícil para impedir que usuários com acesso de consulta direta com êxito a execução de consultas que podem inferir o existência de dados filtrados.  
  
-   Para procedimentos armazenados que inserem dados, capturar o nome de usuário usando a mesma função especificada na política de segurança ou modo de exibição e inserir esse valor na coluna de nome de usuário.  
  
-   Negar todas as permissões em tabelas (e modos de exibição, se aplicável) para o `public` função. Os usuários não poderão herdar permissões de outras funções de banco de dados, porque o predicado de filtro é baseado no usuário ou nomes de logon, não em funções.  
  
-   Grant EXECUTE nos procedimentos armazenados, funções de banco de dados. Os usuários só podem acessar dados por meio de procedimentos armazenados fornecidos.  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações, consulte o seguinte recurso.  
  
|||  
|-|-|  
|[A implementação da segurança de nível de linha e célula no classificada bancos de dados usando o SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=98227) no site do TechCenter do SQL Server.|Descreve como usar a segurança em nível de linha e célula para atender aos requisitos de segurança de banco de dados classificados.|  
  
## <a name="see-also"></a>Consulte também  
 [Segurança em nível de linha](https://msdn.microsoft.com/library/dn765131.aspx)  
 [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [Visão geral de segurança do SQL Server](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Gerenciando permissões com procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Escrevendo SQL dinâmico seguro no SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
