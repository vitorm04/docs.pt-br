---
title: "Segurança do SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: abb7c9322a9b7ddfd3e0add4d8b9be6941c5e240
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-security"></a>Segurança do SQL Server
O [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] tem muitos recursos que oferecem suporte à criação de aplicativos de banco de dados seguros.  
  
 As considerações de segurança comuns são aplicáveis, como o roubo de dados ou o vandalismo, independentemente da versão do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] que você está usando. A integridade de dados também deve ser considerada como um problema de segurança. Se os dados não forem protegidos, eles poderão se tornar inúteis, caso a manipulação de dados ad hoc seja permitida e os dados sejam modificados de forma inadvertida ou mal-intencionada com valores incorretos, ou excluídos totalmente. Além disso, há geralmente requisitos legais que devem ser cumpridos, como o armazenamento correto de informações confidenciais. Armazenar alguns tipos de dados pessoais é totalmente proibido, dependendo das leis aplicáveis em uma jurisdição específica.  
  
 Cada versão do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] tem recursos de segurança diferentes, assim como cada versão do Windows, com versões mais recentes que aprimoram a funcionalidade das mais antigas. É importante entender que os recursos de segurança não podem garantir sozinhos um aplicativo de banco de dados seguro. Cada aplicativo de banco de dados é exclusivo em seus requisitos, ambiente de execução, modelo de implantação, localização física e população de usuário. Alguns aplicativos que são locais no escopo podem precisar apenas de segurança mínima, enquanto outros aplicativos locais ou aplicativos implantados pela Internet podem exigir rígidas medidas de segurança, bem como monitoramento e avaliação constantes.  
  
 Os requisitos de segurança de um aplicativo de banco de dados do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] devem ser considerados em tempo de design, não depois. Avaliar as ameaças no início do ciclo de desenvolvimento oferece a você a oportunidade de atenuar potenciais danos onde quer que uma vulnerabilidade seja detectada.  
  
 Mesmo que o design inicial de um aplicativo seja bom, novas ameaças poderão emergir à medida que o sistema evoluir. Ao criar várias linhas de defesa em torno do seu banco de dados, você pode minimizar os danos impostos por uma violação de segurança. A primeira linha de defesa é reduzir a área da superfície de ataque nunca concedendo mais permissões do que as absolutamente necessárias.  
  
 Os tópicos nesta seção descrevem resumidamente os recursos de segurança do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] que são relevantes para os desenvolvedores, com links para tópicos relevantes nos Manuais Online do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] e outros recursos que fornecem uma cobertura mais detalhada.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de segurança do SQL Server](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 Descreve os recursos de arquitetura e segurança do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
 [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 Contém os tópicos que abordam vários cenários de segurança de aplicativos para o ADO.NET e aplicativos do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
 [Segurança do SQL Server Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 Descreve as considerações de segurança para o [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Segurança e proteção (mecanismo de banco de dados)](http://msdn2.microsoft.com/library/bb510589\(SQL.100\).aspx.)  
 Tópicos de segurança dos Manuais Online do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
 [Considerações de segurança para o SQL Server](http://go.microsoft.com/fwlink/?LinkId=98587)  
 Tópicos de segurança dos Manuais Online do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
