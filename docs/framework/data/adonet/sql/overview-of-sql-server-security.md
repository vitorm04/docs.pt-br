---
title: "Visão geral de segurança do SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ff0a78a852bdbf2fa1eb075273cad317c21fb182
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="overview-of-sql-server-security"></a>Visão geral de segurança do SQL Server
Uma estratégia de defesa em profundidade, com a sobreposição de camadas de segurança, é a melhor maneira de ameaças de segurança do contador. SQL Server fornece uma arquitetura de segurança que foi projetada para permitir que os administradores de banco de dados e desenvolvedores criar aplicativos de banco de dados seguro e ameaças de contador. Cada versão do SQL Server melhorou em versões anteriores do SQL Server com a introdução de novos recursos e funcionalidades. No entanto, a segurança não é fornecido na caixa. Cada aplicativo é exclusivo em seus requisitos de segurança. Os desenvolvedores precisam entender qual combinação de recursos e funcionalidade são mais apropriados para o contador de ameaças conhecidas e para prever as ameaças que podem surgir no futuro.  
  
 Uma instância do SQL Server contém uma coleção hierárquica de entidades, começando com o servidor. Cada servidor contém vários bancos de dados e cada banco de dados contém uma coleção de objetos protegíveis. Todo protegível do SQL Server associada *permissões* que podem ser concedidas a um *principal*, que é um grupo individual, ou processo concedeu acesso ao SQL Server. A estrutura de segurança do SQL Server gerencia o acesso a entidades podem ser protegidos por meio de *autenticação* e *autorização*.  
  
-   Autenticação é o processo de fazer logon no SQL Server pelo qual uma entidade de segurança solicita acesso ao enviar as credenciais que o servidor é avaliada. A autenticação estabelece a identidade do usuário ou processo que está sendo autenticado.  
  
-   A autorização é o processo de determinar quais recursos podem ser protegidos pode acessar uma entidade de segurança e quais operações são permitidas para esses recursos.  
  
 Os tópicos nesta seção abordam conceitos básicos de segurança do SQL Server, fornecendo links para a documentação completa na versão relevante dos Manuais Online do SQL Server.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Autenticação no SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 Descreve os logons e autenticação no SQL Server e fornece links para recursos adicionais.  
  
 [Servidor e funções de banco de dados no SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 Descreve as funções fixas de servidor e banco de dados, funções de banco de dados personalizado e contas internas e fornece links para recursos adicionais.  
  
 [Propriedade e separação do esquema de usuário no SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 Descreve a separação de propriedade e o esquema de usuário do objeto e fornece links para recursos adicionais.  
  
 [Autorização e permissões no SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 Descreve a concessão de permissões usando o princípio de menos privilégios e fornece links para recursos adicionais.  
  
 [Criptografia de dados no SQL Server](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 Descreve as opções de criptografia de dados no SQL Server e fornece links para recursos adicionais.  
  
 [Segurança da integração CLR no SQL Server](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 Fornece links para recursos de segurança de integração do CLR.  
  
## <a name="see-also"></a>Consulte também  
 [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [SQL Server Security](../../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)  
 [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
