---
title: Segurança do SQL Server
ms.date: 03/30/2017
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.openlocfilehash: 4aa4feadb6305f8a0ea6f99c2add780d6fca95cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927595"
---
# <a name="sql-server-security"></a>Segurança do SQL Server
SQL Server tem muitos recursos que dão suporte à criação de aplicativos de banco de dados seguro.  
  
 Aplicam as considerações de segurança comuns, como o roubo de dados ou o vandalismo, independentemente da versão do SQL Server que você está usando. A integridade de dados também deve ser considerada como um problema de segurança. Se os dados não forem protegidos, eles poderão se tornar inúteis, caso a manipulação de dados ad hoc seja permitida e os dados sejam modificados de forma inadvertida ou mal-intencionada com valores incorretos, ou excluídos totalmente. Além disso, há geralmente requisitos legais que devem ser cumpridos, como o armazenamento correto de informações confidenciais. Armazenar alguns tipos de dados pessoais é totalmente proibido, dependendo das leis aplicáveis em uma jurisdição específica.  
  
 Cada versão do SQL Server tem recursos de segurança diferentes, que cada versão do Windows, com versões mais recentes que aprimoram a funcionalidade das mais antigas. É importante entender que os recursos de segurança não podem garantir sozinhos um aplicativo de banco de dados seguro. Cada aplicativo de banco de dados é exclusivo em seus requisitos, ambiente de execução, modelo de implantação, localização física e população de usuário. Alguns aplicativos que são locais no escopo podem precisar apenas de segurança mínima, enquanto outros aplicativos locais ou aplicativos implantados pela Internet podem exigir rígidas medidas de segurança, bem como monitoramento e avaliação constantes.  
  
 Requisitos de segurança de um aplicativo de banco de dados do SQL Server devem ser considerados em tempo de design, não como uma consideração posterior. Avaliar as ameaças no início do ciclo de desenvolvimento oferece a você a oportunidade de atenuar potenciais danos onde quer que uma vulnerabilidade seja detectada.  
  
 Mesmo que o design inicial de um aplicativo seja bom, novas ameaças poderão emergir à medida que o sistema evoluir. Ao criar várias linhas de defesa em torno do seu banco de dados, você pode minimizar os danos impostos por uma violação de segurança. A primeira linha de defesa é reduzir a área da superfície de ataque nunca concedendo mais permissões do que as absolutamente necessárias.  
  
 Os tópicos nesta seção descrevem brevemente os recursos de segurança no SQL Server que são relevantes para os desenvolvedores, com links para tópicos relevantes nos Manuais Online do SQL Server e outros recursos que oferecem cobertura mais detalhada.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de segurança do SQL Server](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 Descreve os recursos de arquitetura e segurança do SQL Server.  
  
 [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 Contém tópicos que abordam vários cenários de segurança de aplicativo para aplicativos do SQL Server e ADO.NET.  
  
 [Segurança do SQL Server Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 Descreve as considerações de segurança para o SQL Server Express.  
  
## <a name="related-sections"></a>Seções relacionadas  
[Central de segurança do mecanismo de banco de dados do SQL Server e banco de dados SQL do Azure](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
Descreve as considerações de segurança para SQL Server e banco de dados SQL.

[Considerações de segurança para uma instalação do SQL Server](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
Descreve problemas de segurança a serem considerados antes de instalar o SQL Server.

## <a name="see-also"></a>Consulte também

- [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)
