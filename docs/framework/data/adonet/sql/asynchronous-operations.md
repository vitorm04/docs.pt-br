---
title: "Operações assíncronas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6f631d785698ae59370053c4e35307514c44087c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="asynchronous-operations"></a>Operações assíncronas
Algumas operações de banco de dados, como execuções de comando, podem levar muito tempo para concluir. Nesse caso, aplicativos de thread único devem bloquear outras operações e aguarde até que o comando para concluir antes de continuar suas próprias operações. Por outro lado, a capacidade de atribuir a operação de longa execução a um thread em segundo plano permite que o thread de primeiro plano permaneça ativo durante toda a operação. Em um aplicativo do Windows, por exemplo, delegando a operação de longa execução a um thread em segundo plano permite que o thread de interface do usuário continuar responsiva durante a operação está em execução.  
  
 O .NET Framework fornece vários padrões de design assíncronos padrão que os desenvolvedores podem usar para tirar proveito de threads em segundo plano e liberar a interface do usuário ou segmentos de alta prioridade para executar outras operações. ADO.NET oferece suporte a estes mesmos padrões de design no seu <xref:System.Data.SqlClient.SqlCommand> classe. Especificamente, o <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, e <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> métodos, combinados com o <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A>, e <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> métodos, fornecem o suporte assíncrono.  
  
> [!NOTE]
>  Programação assíncrona é dos principais recursos do .NET Framework e ADO.NET aproveita os padrões de design padrão. Para obter mais informações sobre as técnicas assíncronas diferentes disponíveis para desenvolvedores, consulte [chamando métodos síncronos assincronamente](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
 Embora o uso de técnicas assíncronas com o ADO.NET recursos não adicionará considerações especiais, é provável que os desenvolvedores mais usará recursos assíncronos no ADO.NET que em outras áreas do .NET Framework. É importante estar ciente das vantagens e armadilhas de criação de aplicativos multithread. Os exemplos que siga essa seção Mencione várias questões importantes que os desenvolvedores precisa levar em conta ao criar aplicativos que incorporam a funcionalidade multi-threaded.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Aplicativos do Windows que usam retornos de chamada](../../../../../docs/framework/data/adonet/sql/windows-applications-using-callbacks.md)  
 Fornece um exemplo que demonstra como executar um comando assíncrono com segurança, lidar corretamente com a interação com um formulário e seu conteúdo de um thread separado.  
  
 [Aplicativos ASP.NET que usam identificadores de espera](../../../../../docs/framework/data/adonet/sql/aspnet-apps-using-wait-handles.md)  
 Fornece um exemplo que demonstra como executar vários comandos simultâneos em uma página ASP.NET, usando identificadores de espera para gerenciar a operação na conclusão de todos os comandos.  
  
 [Sondagem em aplicativos de Console](../../../../../docs/framework/data/adonet/sql/polling-in-console-applications.md)  
 Fornece um exemplo que demonstra o uso de sondagem para aguardar a conclusão de uma execução de comando assíncrona de um aplicativo de console. Essa técnica também é válida em uma biblioteca de classes ou outro aplicativo sem uma interface do usuário.  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)  
 [Chamando métodos síncronos de forma assíncrona](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
