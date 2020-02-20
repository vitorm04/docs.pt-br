---
title: Notificações de consulta no SQL Server
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 11d9a1a800bea4224853a57b128ca89c9f2cf781
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452364"
---
# <a name="query-notifications-in-sql-server"></a>Notificações de consulta no SQL Server
Com base na infraestrutura do Service Broker, as notificações de consulta permitem que os aplicativos sejam notificados em caso de alteração nos dados. Esse recurso é particularmente útil para aplicativos que fornecem um cache de informações de um banco de dados, como um aplicativo da Web, e precisam ser notificados quando os dados de origem são alterados.  
  
 Há três maneiras de implementar as notificações de consulta usando ADO.NET:  
  
1. A implementação de baixo nível é fornecida pela classe `SqlNotificationRequest` que expõe a funcionalidade do lado do servidor, permitindo que você execute um comando com uma solicitação de notificação.  
  
2. A implementação de alto nível é fornecida pela classe `SqlDependency`, que é uma classe que fornece uma abstração de alto nível da funcionalidade de notificação entre o aplicativo de origem e o SQL Server, permitindo que você use uma dependência para detectar alterações no servidor. Na maioria dos casos, esse é o modo mais simples e mais eficiente de aproveitar o recurso de notificações do SQL Server por aplicativos cliente gerenciados usando o provedor de dados .NET Framework para SQL Server.  
  
3. Além disso, os aplicativos Web criados usando o ASP.NET 2.0 ou posterior podem usar as classes auxiliares `SqlCacheDependency`.  
  
 As notificações de consulta são usadas para aplicativos que precisam atualizar exibições ou caches em resposta a alterações nos dados subjacentes. O Microsoft SQL Server permite que aplicativos do .NET Framework enviem um comando ao SQL Server e solicitem a notificação se executar o mesmo comando produzir conjuntos de resultados diferentes dos recuperados inicialmente. As notificações geradas no servidor são enviadas pelas filas para serem processadas posteriormente.  
  
 Você pode configurar notificações para as instruções SELECT e EXECUTE. Ao usar uma instrução EXECUTE, o SQL Server registra uma notificação para o comando executado em vez da própria instrução EXECUTE. O comando deve atender os requisitos e as limitações de uma instrução SELECT. Quando um comando que registra uma notificação contiver mais de uma instrução, o Mecanismo de Banco de Dados criará uma notificação para cada instrução no lote.  
  
 Se você estiver desenvolvendo um aplicativo onde precisa de notificações de subsegundo confiáveis quando os dados forem alterados, examine as seções **planejando uma estratégia de notificações de consulta eficiente** e **alternativas para notificações de consulta** no artigo [planejamento de notificações](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105)) . Para obter mais informações sobre notificações de consulta e SQL Server Service Broker, consulte os seguintes links para artigos na documentação do SQL Server.  
  
 **Documentação do SQL Server**  
  
- [Usando notificações de consulta](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))  
  
- [Criando uma consulta para notificação](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Desenvolvimento (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))  
  
- [Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Guia do desenvolvedor (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="in-this-section"></a>Nesta seção  
 [Habilitando notificações de consulta](enabling-query-notifications.md)  
 Descreve como usar as notificações de consulta, incluindo os requisitos para habilitá-las e usá-las.  
  
 [SqlDependency em um aplicativo ASP.NET](sqldependency-in-an-aspnet-app.md)  
 Demonstra como usar as notificações de consulta de um aplicativo ASP.NET.  
  
 [Detectando alterações com SqlDependency](detecting-changes-with-sqldependency.md)  
 Demonstra como detectar quando os resultados da consulta serão diferentes dos recebidos originalmente.  
  
 [Execução de SqlCommand com um SqlNotificationRequest](sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Demonstra a configuração de um objeto <xref:System.Data.SqlClient.SqlCommand> para trabalhar com uma notificação de consulta.  
  
## <a name="reference"></a>Referência  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 Descreve a classe <xref:System.Data.Sql.SqlNotificationRequest> e todos os seus membros.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 Descreve a classe <xref:System.Data.SqlClient.SqlDependency> e todos os seus membros.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 Descreve a classe <xref:System.Web.Caching.SqlCacheDependency> e todos os seus membros.  
  
## <a name="see-also"></a>Confira também

- [SQL Server e ADO.NET](index.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
