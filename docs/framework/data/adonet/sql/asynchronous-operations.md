---
title: Operações assíncronas
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: 55cb9472c23f09b3f0f248a795dbad62af8ff37f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782608"
---
# <a name="asynchronous-operations"></a>Operações assíncronas
Algumas operações de banco de dados, como execuções de comando, podem levar muito tempo para serem concluídas. Nesse caso, aplicativos de thread único devem bloquear outras operações e aguardar que o comando seja concluído antes que possam continuar suas próprias operações. Por outro lado, ser capaz de atribuir a operação de longa execução a um thread em segundo plano permite que o thread em primeiro plano permaneça ativo durante a operação. Em um aplicativo do Windows, por exemplo, delegar a operação de execução longa para um thread em segundo plano permite que o thread da interface do usuário permaneça responsivo enquanto a operação está em execução.  
  
 O .NET Framework fornece vários padrões de design assíncrono padrão que os desenvolvedores podem usar para aproveitar os threads em segundo plano e liberar a interface do usuário ou threads de alta prioridade para concluir outras operações. O ADO.net dá suporte a esses mesmos padrões <xref:System.Data.SqlClient.SqlCommand> de design em sua classe. Especificamente, os <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>métodos <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, e <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> , emparelhados com os <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>métodos, <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A>e <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> fornecem o suporte assíncrono.  
  
> [!NOTE]
> A programação assíncrona é um recurso fundamental do .NET Framework, e o ADO.NET aproveita totalmente os padrões de design padrão. Para obter mais informações sobre as diferentes técnicas assíncronas disponíveis para desenvolvedores, consulte [chamando métodos síncronos de forma](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)assíncrona.  
  
 Embora o uso de técnicas assíncronas com recursos ADO.NET não adicione nenhuma consideração especial, é provável que mais desenvolvedores usem recursos assíncronos no ADO.NET do que em outras áreas do .NET Framework. É importante estar ciente dos benefícios e das armadilhas da criação de aplicativos multissegmentados. Os exemplos a seguir nesta seção apontam vários problemas importantes que os desenvolvedores precisarão levar em conta ao criar aplicativos que incorporam a funcionalidade multithread.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Aplicativos do Windows que usam retornos de chamada](windows-applications-using-callbacks.md)  
 Fornece um exemplo que demonstra como executar um comando assíncrono com segurança, manipulando corretamente a interação com um formulário e seu conteúdo de um thread separado.  
  
 [Aplicativos ASP.NET que usam identificadores de espera](aspnet-apps-using-wait-handles.md)  
 Fornece um exemplo que demonstra como executar vários comandos simultâneos de uma página do ASP.NET, usando identificadores de espera para gerenciar a operação na conclusão de todos os comandos.  
  
 [Sondagem em aplicativos de Console](polling-in-console-applications.md)  
 Fornece um exemplo que demonstra o uso de sondagem para aguardar a conclusão de uma execução de comando assíncrono de um aplicativo de console. Essa técnica também é válida em uma biblioteca de classes ou outro aplicativo sem uma interface do usuário.  
  
## <a name="see-also"></a>Consulte também

- [SQL Server and ADO.NET](index.md) (SQL Server e ADO.NET)
- [Chamando métodos síncronos de forma assíncrona](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
