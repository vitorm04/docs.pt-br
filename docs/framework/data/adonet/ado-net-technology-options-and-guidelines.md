---
title: "Opções e diretrizes da tecnologia ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8577281-38e6-4ce5-b036-572039a4c3d8
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: aa4cefb27ff3fde3f4f31d996a80b19b94ea57e2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="adonet-technology-options-and-guidelines"></a>Opções e diretrizes da tecnologia ADO.NET
A Plataforma de Dados do ADO.NET é uma estratégia de várias versões para diminuir a quantidade de codificação e de manutenção necessária para habilitar os desenvolvedores para programarem com modelos de dados de entidade conceituais. Essa plataforma inclui o ADO.NET Entity Framework e as tecnologias relacionadas.  
  
## <a name="entity-framework"></a>Entity Framework  
 O ADO.NET Entity Framework foi criado para permitir que os desenvolvedores criem aplicativos de acesso a dados programando em um modelo de aplicativo conceitual, em vez de programar diretamente em um esquema de armazenamento relacional. O objetivo é diminuir a quantidade de código e de manutenção necessários a aplicativos orientados a dados. Para obter mais informações, consulte [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
### <a name="entity-data-model-edm"></a>Modelo de Dados de Entidade (EDM)  
 Um EDM (Modelo de Dados de Entidade) é uma especificação de design que define os dados do aplicativo como conjuntos de entidades e relacionamentos. Os dados nesse modelo dão suporte ao mapeamento relacional de objetos e à capacidade de programação de dados entre os limites do aplicativo.  
  
### <a name="object-services"></a>Serviços de Objeto  
 Os Serviços de Objeto permitem que os programadores interajam com o modelo conceitual através de um conjunto de classes CLR (Common Language Runtime). Essas classes podem ser geradas automaticamente no modelo conceitual ou podem ser desenvolvidas independente para refletir a estrutura do modelo conceitual. Os Serviços de Objeto também fornecem suporte à infraestrutura do Entity Framework, incluindo serviços como gerenciamento de estado, controle de alterações, resolução de identidade, relacionamentos de carregamento e navegação, propagação de alterações de objetos para modificações do banco de dados e suporte à criação de consultas para o Entity SQL. Para obter mais informações, consulte [visão geral dos serviços de objeto (Entity Framework)](http://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
### <a name="linq-to-entities"></a>LINQ to Entities  
 O LINQ to Entities é uma implementação do LINQ (consulta integrada à linguagem) que permite que os desenvolvedores criem consultas fortemente tipadas com o contexto de objeto do Entity Framework usando expressões LINQ e operadores de consulta padrão LINQ. O LINQ to Entities permite que os desenvolvedores trabalhem com um modelo conceitual com um mapeamento relacional de objetos muito flexível por meio do Microsoft SQL Server e bancos de dados de terceiros. Para obter mais informações, consulte [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
### <a name="entity-sql"></a>Entity SQL  
 O Entity SQL é uma linguagem de consulta baseada em texto criada para interagir com um Modelo de Dados de Entidade. O Entity SQL é um dialeto SQL que contém constructos para consulta em termos dos conceitos de modelagem de nível mais alto, como herança, tipos complexos e relações explícitas. Os desenvolvedores também podem usar o Entity SQL diretamente com Serviços de Objeto. Para obter mais informações, consulte [linguagem Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
### <a name="entityclient"></a>EntityClient  
 O EntityClient é um novo provedor de dados .NET Framework usado para interagir com um Modelo de Dados de Entidade. O EntityClient segue o padrão do provedor de dados .NET Framework de expor os objetos <xref:System.Data.EntityClient.EntityConnection> e <xref:System.Data.EntityClient.EntityCommand> que retornam um <xref:System.Data.EntityClient.EntityDataReader>. O EntityClient funciona com a linguagem Entity SQL, fornecendo mapeamento flexível para provedores de dados específicos a armazenamento. Para obter mais informações, consulte [EntityClient e Entity SQL](http://msdn.microsoft.com/library/49202ab9-ac98-4b4b-a05c-140e422bf527).  
  
### <a name="entity-data-model-tools"></a>Ferramentas do Modelo de Dados de Entidade  
 O Entity Framework fornece ferramentas de linha de comando, assistentes e designers para facilitar a criação de aplicativos EDM. O controle EntityDataSource dá suporte a cenários de vinculação de dados baseados no EDM. A superfície de programação do controle EntityDataSource é semelhante a outros controles de fonte de dados no Visual Studio. Para obter mais informações, consulte [ferramentas de modelo de dados de entidade ADO.NET](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 O LINQ to SQL é uma implementação do OR/M (mapeamento relacional de objeto) que permite que você modele um banco de dados SQL Server usando classes do .NET Framework. O LINQ to SQL permite que você consulte seu banco de dados usando LINQ, bem como atualize, insira e exclua dados dele. O LINQ to SQL dá suporte a transações, exibições e procedimentos armazenados, fornecendo uma maneira fácil de integrar regras de validação de dados e de lógica de negócios no modelo de dados. Você pode usar o O/R Designer (Designer Relacional de Objeto) para modelar as classes e as associações de entidades que são baseadas em objetos em um banco de dados. Para obter mais informações, consulte [Ferramentas LINQ to SQL no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
## <a name="wcf-data-services"></a>WCF Data Services  
 O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] implanta serviços de dados na Web ou em uma intranet. Os dados são estruturados como entidades e relações de acordo com as especificações do Modelo de Dados de Entidade. Os dados implantados nesse modelo são endereçáveis pelo protocolo HTTP padrão. Para obter mais informações, consulte [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Overview](../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)  
 [What's New in ADO.NET](../../../../docs/framework/data/adonet/whats-new.md) (Novidades no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
