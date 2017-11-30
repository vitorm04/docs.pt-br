---
title: "Notificações de consulta no SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 854407d2e6d1341d5917cc78664c1f653e55fa35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="9dd1d-102">Notificações de consulta no SQL Server</span><span class="sxs-lookup"><span data-stu-id="9dd1d-102">Query Notifications in SQL Server</span></span>
<span data-ttu-id="9dd1d-103">Criado utilizando a infraestrutura de Service Broker, as notificações de consulta permitem que os aplicativos sejam notificados quando os dados tiverem sido alterados.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-103">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="9dd1d-104">Esse recurso é especialmente útil para aplicativos que fornecem um cache de informações de um banco de dados, como um aplicativo Web, e precisam ser notificados quando os dados de origem são alterados.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-104">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="9dd1d-105">Há três maneiras de implementar as notificações de consulta usando ADO.NET:</span><span class="sxs-lookup"><span data-stu-id="9dd1d-105">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1.  <span data-ttu-id="9dd1d-106">A implementação de baixo nível é fornecida pela classe `SqlNotificationRequest` que expõe a funcionalidade do lado do servidor, permitindo que você execute um comando com uma solicitação de notificação.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-106">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2.  <span data-ttu-id="9dd1d-107">A implementação de alto nível é fornecida pela classe `SqlDependency`, que é uma classe que fornece uma abstração de alto nível da funcionalidade de notificação entre o aplicativo de origem e o SQL Server, permitindo que você use uma dependência para detectar alterações no servidor.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-107">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="9dd1d-108">Na maioria dos casos, esse é o modo mais simples e mais eficiente de aproveitar o recurso de notificações do SQL Server por aplicativos cliente gerenciados usando o provedor de dados .NET Framework para SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-108">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3.  <span data-ttu-id="9dd1d-109">Além disso, os aplicativos Web criados usando o ASP.NET 2.0 ou posterior podem usar as classes auxiliares `SqlCacheDependency`.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-109">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="9dd1d-110">As notificações de consulta são usadas para aplicativos que precisam atualizar exibições ou caches em resposta a alterações nos dados subjacentes.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-110">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="9dd1d-111">O Microsoft SQL Server permite que aplicativos do .NET Framework enviem um comando ao SQL Server e solicitem a notificação se executar o mesmo comando produzir conjuntos de resultados diferentes dos recuperados inicialmente.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-111">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="9dd1d-112">As notificações geradas no servidor são enviados por filas a serem processadas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-112">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="9dd1d-113">Você pode configurar notificações para as instruções SELECT e EXECUTE.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-113">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="9dd1d-114">Ao usar uma instrução EXECUTE, o SQL Server registra uma notificação para o comando executado em vez da própria instrução EXECUTE.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-114">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="9dd1d-115">O comando deve atender aos requisitos e limitações para uma instrução SELECT.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-115">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="9dd1d-116">Quando um comando que registra uma notificação contém mais de uma declaração, o Mecanismo de Banco de Dados cria uma notificação para cada instrução no lote.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-116">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="9dd1d-117">Se você estiver desenvolvendo um aplicativo em que você precisa notificações de subsegundos confiável quando dados são alterados, examine as seções **Planejando uma estratégia de notificações de consulta eficiente** e **alternativas para notificações de consulta** no [planejando notificações](http://go.microsoft.com/fwlink/?LinkId=211984) tópico nos Manuais Online do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-117">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](http://go.microsoft.com/fwlink/?LinkId=211984) topic in SQL Server Books Online.</span></span> <span data-ttu-id="9dd1d-118">Para obter mais informações sobre as notificações de consulta e o SQL Server Service Broker, consulte os seguintes links para tópicos nos Manuais Online do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-118">For more information about Query Notifications and SQL Server Service Broker, see the following links to topics in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="9dd1d-119">**SQL Server Books Online** (Guias online do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9dd1d-119">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="9dd1d-120">Usando notificações de consulta</span><span class="sxs-lookup"><span data-stu-id="9dd1d-120">Using Query Notifications</span></span>](http://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [<span data-ttu-id="9dd1d-121">Criando uma consulta para notificação</span><span class="sxs-lookup"><span data-stu-id="9dd1d-121">Creating a Query for Notification</span></span>](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [<span data-ttu-id="9dd1d-122">O Service Broker</span><span class="sxs-lookup"><span data-stu-id="9dd1d-122">Service Broker</span></span>](http://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [<span data-ttu-id="9dd1d-123">InfoCenter do desenvolvedor do Service Broker</span><span class="sxs-lookup"><span data-stu-id="9dd1d-123">Service Broker Developer InfoCenter</span></span>](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [<span data-ttu-id="9dd1d-124">Desenvolvimento (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="9dd1d-124">Development (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="in-this-section"></a><span data-ttu-id="9dd1d-125">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="9dd1d-125">In This Section</span></span>  
 [<span data-ttu-id="9dd1d-126">Habilitar notificações de consulta</span><span class="sxs-lookup"><span data-stu-id="9dd1d-126">Enabling Query Notifications</span></span>](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 <span data-ttu-id="9dd1d-127">Descreve como usar as notificações de consulta, incluindo os requisitos para habilitá-las e usá-las.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-127">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="9dd1d-128">SqlDependency em um aplicativo ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9dd1d-128">SqlDependency in an ASP.NET Application</span></span>](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="9dd1d-129">Demonstra como usar as notificações de consulta de um aplicativo ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-129">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="9dd1d-130">Detectando alterações com SqlDependency</span><span class="sxs-lookup"><span data-stu-id="9dd1d-130">Detecting Changes with SqlDependency</span></span>](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="9dd1d-131">Demonstra como detectar quando os resultados da consulta serão diferentes dos recebidos originalmente.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-131">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="9dd1d-132">Execução de SqlCommand com um SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="9dd1d-132">SqlCommand Execution with a SqlNotificationRequest</span></span>](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="9dd1d-133">Demonstra a configuração de um objeto <xref:System.Data.SqlClient.SqlCommand> para trabalhar com uma notificação de consulta.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-133">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9dd1d-134">Referência</span><span class="sxs-lookup"><span data-stu-id="9dd1d-134">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="9dd1d-135">Descreve a classe <xref:System.Data.Sql.SqlNotificationRequest> e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-135">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="9dd1d-136">Descreve a classe <xref:System.Data.SqlClient.SqlDependency> e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-136">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="9dd1d-137">Descreve a classe <xref:System.Web.Caching.SqlCacheDependency> e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="9dd1d-137">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd1d-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9dd1d-138">See Also</span></span>  
 <span data-ttu-id="9dd1d-139">[SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="9dd1d-139">[SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)</span></span>  
 <span data-ttu-id="9dd1d-140">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="9dd1d-140">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
