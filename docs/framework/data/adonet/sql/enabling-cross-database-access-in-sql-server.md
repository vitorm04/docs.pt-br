---
title: Habilitando o acesso entre bancos de dados no SQL Server
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: 70b4b7b55311bfc5dba1b537a603e0d15d7f3d9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877688"
---
# <a name="enabling-cross-database-access-in-sql-server"></a>Habilitando o acesso entre bancos de dados no SQL Server
O encadeamento de propriedade entre bancos de dados ocorre quando um procedimento em um banco de dados depende dos objetos em outro banco de dados. Uma cadeia de propriedade entre bancos de dados funciona como a cadeia de propriedade dentro de um único banco de dados, exceto que uma cadeia de propriedade exige que todos os proprietários de objetos sejam mapeados para a mesma conta de logon. Se o objeto de origem no banco de dados de origem e os objetos de destino nos bancos de dados de destino forem de propriedade da mesma conta de logon, o SQL Server não verificará permissões nos objetos de destino.  
  
## <a name="off-by-default"></a>Desativado por padrão  
 A cadeia de propriedade nos bancos de dados é desativada por padrão. A Microsoft recomenda que você desabilite a propriedade do banco de dados porque o encadeamento expõe você aos seguintes riscos de segurança:  
  
-   Os proprietários de banco de dados e os membros de `db_ddladmin` ou das funções de banco de dados de `db_owners` podem criar os objetos pertencentes a outros usuários. Esses objetos podem potencialmente ser destinados a objetos em outros bancos de dados. Isso significa que, se você habilitar o encadeamento de propriedades entre banco de dados, deverá confiar completamente nesses usuários com dados em todos os bancos de dados.  
  
-   Os usuários com a permissão CREATE DATABASE podem criar novos bancos de dados e anexar bancos de dados existentes. Se o encadeamento de propriedades entre banco de dados estiver habilitado, esses usuários poderão acessar objetos em outros bancos de dados que possam não ter privilégios nos bancos de dados recém-criados ou anexados.  
  
## <a name="enabling-cross-database-ownership-chaining"></a>Habilitando o encadeamento de propriedades entre banco de dados  
 O encadeamento de propriedades entre banco de dados deve ser habilitado apenas em ambientes onde você possa confiar completamente em usuários altamente privilegiados. Pode ser configurado durante a instalação para todos os bancos de dados, ou seletivamente para os bancos de dados específicos usando comandos [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]`sp_configure` e `ALTER DATABASE`.  
  
 Para configurar seletivamente o encadeamento de propriedades entre banco de dados, use `sp_configure` para desativá-lo para o servidor. Use o comando ALTER DATABASE com SET DB_CHAINING ON para configurar o encadeamento de propriedades entre banco de dados para somente os bancos de dados que exigirem isso.  
  
 O exemplo a seguir ativa o encadeamento de propriedades entre banco de dados para todos os bancos de dados:  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 O exemplo a seguir ativa o encadeamento de propriedades entre banco de dados para bancos de dados específicos:  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a>SQL dinâmico  
 O encadeamento de propriedades entre bancos de dados não funciona nos casos em que as instruções SQL criadas dinamicamente são executadas a menos que o mesmo usuário exista em ambos os bancos de dados. Resolva isso no SQL Server criando um procedimento armazenado que acessa os dados em outro banco de dados e assinando o procedimento armazenado com um certificado existente em ambos os bancos de dados. Isso concede acesso de usuários aos recursos de banco de dados usados pelo procedimento sem conceder-lhes o acesso ao banco de dados ou permissões.  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Estendendo a representação de banco de dados com EXECUTE AS](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) e [opção Cross DB Ownership Chaining](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).|Artigos descrevem como configurar o encadeamento de bancos de dados para uma instância do SQL Server.|  
  
## <a name="see-also"></a>Consulte também

- [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [Visão geral de segurança do SQL Server](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Gerenciando permissões com procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Escrevendo SQL dinâmico seguro no SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [Assinando procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
