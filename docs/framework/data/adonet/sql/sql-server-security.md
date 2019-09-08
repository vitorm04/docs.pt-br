---
title: Segurança do SQL Server
ms.date: 03/30/2017
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.openlocfilehash: c5fd9cc82a3b1e4ffa217d65c542376fe067db06
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791628"
---
# <a name="sql-server-security"></a>Segurança do SQL Server
SQL Server tem muitos recursos que dão suporte à criação de aplicativos de banco de dados seguros.  
  
 Considerações de segurança comuns, como roubo de dados ou vandalismo, se aplicam independentemente da versão do SQL Server que você está usando. A integridade de dados também deve ser considerada como um problema de segurança. Se os dados não forem protegidos, eles poderão se tornar inúteis, caso a manipulação de dados ad hoc seja permitida e os dados sejam modificados de forma inadvertida ou mal-intencionada com valores incorretos, ou excluídos totalmente. Além disso, há geralmente requisitos legais que devem ser cumpridos, como o armazenamento correto de informações confidenciais. Armazenar alguns tipos de dados pessoais é totalmente proibido, dependendo das leis aplicáveis em uma jurisdição específica.  
  
 Cada versão do SQL Server tem recursos de segurança diferentes, assim como faz cada versão do Windows, com versões posteriores com funcionalidade aprimorada sobre as anteriores. É importante entender que os recursos de segurança não podem garantir sozinhos um aplicativo de banco de dados seguro. Cada aplicativo de banco de dados é exclusivo em seus requisitos, ambiente de execução, modelo de implantação, localização física e população de usuário. Alguns aplicativos que são locais no escopo podem precisar apenas de segurança mínima, enquanto outros aplicativos locais ou aplicativos implantados pela Internet podem exigir rígidas medidas de segurança, bem como monitoramento e avaliação constantes.  
  
 Os requisitos de segurança de um aplicativo de banco de dados SQL Server devem ser considerados em tempo de design, não como uma prioridade. Avaliar as ameaças no início do ciclo de desenvolvimento oferece a você a oportunidade de atenuar potenciais danos onde quer que uma vulnerabilidade seja detectada.  
  
 Mesmo que o design inicial de um aplicativo seja bom, novas ameaças poderão emergir à medida que o sistema evoluir. Ao criar várias linhas de defesa em torno do seu banco de dados, você pode minimizar os danos impostos por uma violação de segurança. A primeira linha de defesa é reduzir a área da superfície de ataque nunca concedendo mais permissões do que as absolutamente necessárias.  
  
 Os tópicos desta seção descrevem brevemente os recursos de segurança do SQL Server que são relevantes para os desenvolvedores, com links para tópicos relevantes em Manuais Online do SQL Server e outros recursos que fornecem cobertura mais detalhada.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de segurança do SQL Server](overview-of-sql-server-security.md)  
 Descreve a arquitetura e os recursos de segurança do SQL Server.  
  
 [Cenários de segurança do aplicativo no SQL Server](application-security-scenarios-in-sql-server.md)  
 Contém tópicos que abordam vários cenários de segurança de aplicativos para aplicativos ADO.NET e SQL Server.  
  
 [Segurança do SQL Server Express](sql-server-express-security.md)  
 Descreve as considerações de segurança para SQL Server Express.  
  
## <a name="related-sections"></a>Seções relacionadas  
[Central de segurança para SQL Server Mecanismo de Banco de Dados e banco de dados SQL do Azure](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
Descreve as considerações de segurança para o SQL Server e o banco de dados SQL do Azure.

[Considerações sobre segurança para uma instalação do SQL Server](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
Descreve as questões de segurança a considerar antes de instalar o SQL Server.

## <a name="see-also"></a>Consulte também

- [Securing ADO.NET Applications](../securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [SQL Server and ADO.NET](index.md) (SQL Server e ADO.NET)
