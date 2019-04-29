---
title: Operações assíncronas
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: 72c2cc33185cb7fba5b8c8ce8d3805a6bb76f8d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663967"
---
# <a name="asynchronous-operations"></a>Operações assíncronas
Algumas operações de banco de dados, como execuções de comando, podem levar um tempo significativo para ser concluído. Nesse caso, aplicativos de thread único devem bloquear outras operações e aguarde até que o comando seja concluído antes que possa continuar suas próprias operações. Em contraste, sendo capaz de atribuir a operação de longa execução a um thread em segundo plano permite que o thread de primeiro plano permaneça ativo durante toda a operação. Em um aplicativo do Windows, por exemplo, delegando a operação de longa execução a um thread em segundo plano permite que o thread da interface do usuário continuar responsiva enquanto a operação está em execução.  
  
 O .NET Framework fornece vários padrões de design assíncrono padrão que os desenvolvedores podem usar para tirar proveito dos threads em segundo plano e liberar a interface do usuário ou segmentos de alta prioridade para concluir outras operações. ADO.NET oferece suporte a esses mesmos padrões de design em seu <xref:System.Data.SqlClient.SqlCommand> classe. Especificamente, o <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, e <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> métodos, emparelhados com o <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A>, e <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> métodos, fornecem o suporte assíncrono.  
  
> [!NOTE]
>  Programação assíncrona é um recurso principal do .NET Framework e ADO.NET tira total proveito dos padrões de design padrão. Para obter mais informações sobre as diferentes técnicas assíncronas disponíveis para desenvolvedores, consulte [chamando métodos síncronos assincronamente](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
 Embora o uso de técnicas assíncronas com o ADO.NET recursos não adiciona quaisquer considerações especiais, é provável que mais desenvolvedores usará recursos assíncronos no ADO.NET que em outras áreas do .NET Framework. É importante conhecer as vantagens e desvantagens da criação de aplicativos multithread. Os exemplos a seguir esse ponto de seção os vários problemas importantes que os desenvolvedores precisará levar em conta ao criar aplicativos que incorporam a funcionalidade de vários threads.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Aplicativos do Windows que usam retornos de chamada](../../../../../docs/framework/data/adonet/sql/windows-applications-using-callbacks.md)  
 Fornece um exemplo que demonstra como executar um comando assíncrono com segurança, tratar corretamente a interação com um formulário e seu conteúdo de um thread separado.  
  
 [Aplicativos ASP.NET que usam identificadores de espera](../../../../../docs/framework/data/adonet/sql/aspnet-apps-using-wait-handles.md)  
 Fornece um exemplo que demonstra como executar vários comandos simultâneos em uma página ASP.NET, usando os identificadores de espera para a operação após a conclusão de todos os comandos de gerenciamento.  
  
 [Sondagem em aplicativos de Console](../../../../../docs/framework/data/adonet/sql/polling-in-console-applications.md)  
 Fornece um exemplo que demonstra o uso de sondagem para aguardar a conclusão de uma execução de comando assíncrono de um aplicativo de console. Essa técnica também é válida em uma biblioteca de classes ou em outro aplicativo sem uma interface do usuário.  
  
## <a name="see-also"></a>Consulte também

- [SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)
- [Chamando métodos síncronos de forma assíncrona](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
