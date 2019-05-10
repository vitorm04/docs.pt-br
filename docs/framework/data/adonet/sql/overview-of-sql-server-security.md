---
title: Visão geral de segurança do SQL Server
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: 52e6f69c006353fcafcbf8f567675a7c14830f76
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64582807"
---
# <a name="overview-of-sql-server-security"></a>Visão geral de segurança do SQL Server
Uma estratégia de defesa em profundidade, com a sobreposição de camadas de segurança, é a melhor maneira de combater ameaças de segurança. SQL Server fornece uma arquitetura de segurança que foi projetada para permitir que os administradores de banco de dados e os desenvolvedores criem aplicativos de banco de dados seguro e combater ameaças. Cada versão do SQL Server tem melhorado em versões anteriores do SQL Server com a introdução de novos recursos e funcionalidades. No entanto, a segurança não é fornecido na caixa. Cada aplicativo é exclusivo em seus requisitos de segurança. Os desenvolvedores precisam entender qual combinação de recursos e funcionalidade são mais apropriados para combater as ameaças conhecidas e para prever as ameaças que podem surgir no futuro.  
  
 Uma instância do SQL Server contém uma coleção hierárquica de entidades, começando com o servidor. Cada servidor contém vários bancos de dados e cada banco de dados contém uma coleção de objetos protegíveis. Todos os protegíveis do SQL Server está associada *permissões* que podem ser concedidas a um *principal*, que é um grupo individual, ou processo concedeu acesso ao SQL Server. A estrutura de segurança do SQL Server gerencia o acesso a entidades podem ser protegidos por meio *autenticação* e *autorização*.  
  
- Autenticação é o processo de fazer logon no SQL Server pelo qual uma entidade de segurança solicita acesso ao enviar as credenciais que o servidor avalia. A autenticação estabelece a identidade do usuário ou processo que está sendo autenticado.  
  
- A autorização é o processo de determinar quais recursos protegíveis uma entidade de segurança pode acessar e quais operações são permitidas para esses recursos.  
  
 Os tópicos nesta seção abordam conceitos básicos de segurança do SQL Server, fornecendo links para a documentação completa na versão relevante dos Manuais Online do SQL Server.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Autenticação no SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 Descreve logons e autenticação no SQL Server e fornece links para recursos adicionais.  
  
 [Servidor e funções de banco de dados no SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 Descreve funções fixas de servidor e banco de dados, funções de banco de dados personalizado e contas internas e fornece links para recursos adicionais.  
  
 [Propriedade e separação do esquema de usuário no SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 Descreve a separação de propriedade e o esquema de usuário do objeto e fornece links para recursos adicionais.  
  
 [Autorização e permissões no SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 Descreve a concessão de permissões usando o princípio de privilégios mínimos e fornece links para recursos adicionais.  
  
 [Criptografia de dados no SQL Server](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 Descreve as opções de criptografia de dados no SQL Server e fornece links para recursos adicionais.  
  
 [Segurança da integração CLR no SQL Server](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 Fornece links para recursos de segurança de integração de CLR.  
  
## <a name="see-also"></a>Consulte também

- [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [SQL Server Security](../../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)
- [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
