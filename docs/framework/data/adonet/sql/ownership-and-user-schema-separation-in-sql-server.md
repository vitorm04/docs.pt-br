---
title: Propriedade e separação do esquema do usuário no SQL Server
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: 68a65cb950c54be9a4f9354a6ca20cbeeaafb938
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092599"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a>Propriedade e separação do esquema do usuário no SQL Server
Um conceito central de segurança do SQL Server é que os proprietários de objetos têm permissões irrevogáveis administrá-los. Você não pode remover os privilégios de um proprietário de objeto e não pode eliminar usuários de um banco de dados se eles possuírem objetos nele.  
  
## <a name="user-schema-separation"></a>Separação do esquema do usuário  
 A separação do esquema do usuário permite maior flexibilidade em gerenciar permissões do objeto de banco de dados. Um *esquema* é um contêiner denominado para objetos de banco de dados, que lhe permite agrupar objetos em namespaces separados. Por exemplo, o banco de dados de exemplo AdventureWorks contém esquemas para Production, Sales e HumanResources.  
  
 A sintaxe de nomeação de quatro partes para referir-se a objetos especifica o nome do esquema.  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a>Proprietários e permissões do esquema  
 Os esquemas podem ser de propriedade de qualquer entidade de banco de dados, e uma única entidade pode possuir vários esquemas. Você pode aplicar regras de segurança a um esquema, que são herdadas por todos os objetos no esquema. Depois que você configurar permissões de acesso para um esquema, essas permissões serão aplicadas automaticamente à medida que novos objetos forem adicionados ao esquema. Os usuários podem ser atribuídos a um esquema padrão, e vários usuários do banco de dados podem compartilhar o mesmo esquema.  
  
 Por padrão, quando os desenvolvedores criam objetos em um esquema, os objetos são possuídos pela entidade de segurança que possui o esquema, não pelo desenvolvedor. A propriedade do objeto pode ser transferida com a instrução ALTER AUTHORIZATION do Transact-SQL. Um esquema também pode conter objetos que são possuídos por diferentes usuários e ter as permissões mais granulares que as atribuídas ao esquema, embora isso não seja recomendado porque adiciona complexidade a permissões de gerenciamento. Os objetos podem ser movidos entre esquemas e a propriedade do esquema pode ser transferida entre entidades de segurança. Os usuários do banco de dados podem ser removidos sem afetar esquemas.  
  
### <a name="built-in-schemas"></a>Esquemas internos  
 O SQL Server vem com dez esquemas predefinidos que têm os mesmos nomes que os usuários e as funções internas do banco de dados. Eles existem principalmente para compatibilidade com versões anteriores. Você pode remover os esquemas que têm os mesmos nomes que as funções de banco de dados fixas se não precisar deles. Você não pode remover os esquemas a seguir:  
  
-   `dbo`  
  
-   `guest`  
  
-   `sys`  
  
-   `INFORMATION_SCHEMA`  
  
 Se você removê-los do banco de dados modelo, eles não aparecerão em novos bancos de dados.  
  
> [!NOTE]
>  Os esquemas `sys` e `INFORMATION_SCHEMA` são reservados para objetos do sistema. Você não pode criar objetos nesses esquemas e não pode removê-los.  
  
#### <a name="the-dbo-schema"></a>O esquema dbo  
 O esquema `dbo` é o esquema padrão para um banco de dados recém-criado. O esquema `dbo` é de propriedade da conta de usuário do `dbo`. Por padrão, os usuários criados com o comando CREATE USER do Transact-SQL têm `dbo` como o esquema padrão.  
  
 Os usuários que são atribuídos ao esquema `dbo` não herdam as permissões da conta de usuário do `dbo`. Nenhuma permissão é herdada de um esquema por usuários; as permissões de esquema são herdadas pelos objetos de banco de dados contidos no esquema.  
  
> [!NOTE]
>  Quando os objetos de banco de dados são referenciados usando um nome de uma parte, o SQL Server primeiro procura no esquema padrão do usuário. Se o objeto não for encontrado lá, o SQL Server procurará em seguida no esquema `dbo`. Se o objeto não estiver no esquema `dbo`, um erro será retornado.  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações sobre a propriedade e os esquemas do objeto, consulte os recursos a seguir.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Separação do esquema de usuário](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))|Descreve as alterações introduzidas pela separação do esquema do usuário. Inclui o novo comportamento, o seu impacto na propriedade, as exibições do catálogo e as permissões.|  
  
## <a name="see-also"></a>Consulte também
- [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Autenticação no SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [Servidor e funções de banco de dados no SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)
- [Autorização e permissões no SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
