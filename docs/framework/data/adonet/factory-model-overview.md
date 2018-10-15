---
title: Visão geral do modelo de fábrica
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 18a0e26554db1be68cd0f22773fa04cb44c495a7
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316292"
---
# <a name="factory-model-overview"></a>Visão geral do modelo de fábrica
O ADO.NET 2.0 introduziu novas classes de base no <xref:System.Data.Common> namespace. As classes base são abstratas, o que significa que eles não podem ser instanciados diretamente. Eles incluem <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, e <xref:System.Data.Common.DbDataAdapter> e são compartilhadas por provedores de dados do .NET Framework, como <xref:System.Data.SqlClient> e <xref:System.Data.OleDb>. A adição de classes base simplifica a adição da funcionalidade para os provedores de dados .NET Framework sem ter que criar novas interfaces.  
  
 O ADO.NET 2.0 também introduziu classes base abstratas, que permitem que um desenvolvedor escreva o código de acesso a dados genéricos que não depende de um provedor de dados específico.  
  
## <a name="the-factory-design-pattern"></a>O padrão de Design de fábrica  
 O modelo de programação para escrever código independente de provedor baseia-se no uso do padrão de design "fábrica", que usa uma única API para acessar bancos de dados em vários provedores. Esse padrão foi apropriadamente denominado, pois ele chama o uso de um objeto especializado exclusivamente para criar outros objetos, assim como uma fábrica do mundo real. Para obter uma descrição mais detalhada do padrão de design fábrica, consulte [escrevendo genérico dados acesso código no ASP.NET 2.0 e o ADO.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=55915).
  
 Começando com o ADO.NET 2.0, o <xref:System.Data.Common.DbProviderFactories> classe fornece `static` (ou `Shared` no Visual Basic) métodos para criar um <xref:System.Data.Common.DbProviderFactory> instância. A instância, em seguida, retorna um objeto fortemente tipado correto com base em informações do provedor e a cadeia de conexão fornecida em tempo de execução.  
  
## <a name="see-also"></a>Consulte também  
 [Obtendo um DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [DbConnection, DbCommand e DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [Modificando dados com um DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
