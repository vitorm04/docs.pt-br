---
title: "Visão geral do modelo de fábrica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 54d8db28fec710aba2307d826e147eb9bab13ab9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="factory-model-overview"></a>Visão geral do modelo de fábrica
O ADO.NET 2.0 introduziu novas classes base no <xref:System.Data.Common> namespace. As classes base serão abstratas, o que significa que eles não podem ser instanciados diretamente. Eles incluem <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, e <xref:System.Data.Common.DbDataAdapter> e são compartilhados pelos provedores de dados do .NET Framework, como <xref:System.Data.SqlClient> e <xref:System.Data.OleDb>. A adição de classes base simplifica adicionando funcionalidade para os provedores de dados do .NET Framework sem a necessidade de criar novas interfaces.  
  
 O ADO.NET 2.0 também introduziu classes base abstratas, que permitem que um desenvolvedor gravar o código de acesso a dados genéricos que não dependem de um provedor de dados específico.  
  
## <a name="the-factory-design-pattern"></a>O padrão de Design de fábrica  
 O modelo de programação para escrever código independente de provedor baseia-se no uso do padrão de design "fábrica", que usa uma única API para acessar bancos de dados em vários provedores. Esse padrão é denominado adequadamente, pois ele exige o uso de um objeto especializado exclusivamente para criar outros objetos, como uma fábrica do mundo real. Para obter uma descrição mais detalhada do padrão de design de fábrica, consulte "[escrever o código de acesso de dados genérico no ASP.NET 2.0 e o ADO.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=55915)" e "Genérico de codificação com o ADO.NET 2.0 Base de Classes e fábricas de" [http:// MSDN.microsoft.com/library/default.asp?URL=/Library/dnvs05/HTML/vsgenerics.asp](http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) no MSDN.  
  
 Começando com o ADO.NET 2.0, o <xref:System.Data.Common.DbProviderFactories> classe fornece `static` (ou `Shared` no Visual Basic) métodos para criar um <xref:System.Data.Common.DbProviderFactory> instância. A instância, em seguida, retorna um objeto fortemente tipado correto com base em informações do provedor e a cadeia de caracteres de conexão fornecido no tempo de execução.  
  
## <a name="see-also"></a>Consulte também  
 [Obtendo um DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [DbConnection, DbCommand e DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [Modificando dados com um DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
