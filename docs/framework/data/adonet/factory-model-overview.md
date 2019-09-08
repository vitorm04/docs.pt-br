---
title: Visão geral do modelo de fábrica
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 7d50ddd3b02b66a5b2be41eaba5cf9a497b5f1b3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795081"
---
# <a name="factory-model-overview"></a>Visão geral do modelo de fábrica
O <xref:System.Data.Common> ADO.NET 2,0 introduziu novas classes base no namespace. As classes base são abstratas, o que significa que elas não podem ser instanciadas diretamente. Elas incluem <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand> <xref:System.Data.SqlClient> e e são compartilhadas pelos provedores de dados .NET Framework, como e <xref:System.Data.OleDb>. <xref:System.Data.Common.DbDataAdapter> A adição de classes base simplifica a adição de funcionalidade aos provedores de dados de .NET Framework sem a necessidade de criar novas interfaces.  
  
 O ADO.NET 2,0 também introduziu classes base abstratas, que permitem que um desenvolvedor escreva código de acesso a dados genérico que não depende de um provedor de dados específico.  
  
## <a name="the-factory-design-pattern"></a>O padrão de design de fábrica  
 O modelo de programação para escrever código independente de provedor é baseado no uso do padrão de design "Factory", que usa uma única API para acessar bancos de dados entre vários provedores. Esse padrão é adequadamente nomeado, pois chama o uso de um objeto especializado exclusivamente para criar outros objetos, muito parecido com uma fábrica do mundo real. Para obter uma descrição mais detalhada do padrão de design de fábrica, consulte [escrevendo código de acesso a dados genérico em ASP.NET 2,0 e ADO.NET 2,0](https://go.microsoft.com/fwlink/?LinkId=55915).
  
 A partir do ADO.NET 2,0, <xref:System.Data.Common.DbProviderFactories> a classe `static` fornece ( `Shared` ou em Visual Basic) métodos para criar <xref:System.Data.Common.DbProviderFactory> uma instância. Em seguida, a instância retorna um objeto com rigidez de tipos correto com base nas informações do provedor e na cadeia de conexão fornecida em tempo de execução.  
  
## <a name="see-also"></a>Consulte também

- [Obtendo um DbProviderFactory](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand e DbException](dbconnection-dbcommand-and-dbexception.md)
- [Modificando dados com um DbDataAdapter](modifying-data-with-a-dbdataadapter.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
