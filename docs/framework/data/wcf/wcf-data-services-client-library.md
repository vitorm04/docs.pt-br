---
title: Biblioteca de cliente do WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 74b3e50c36f0b3238b8fb74ca1ea1b336e0983c0
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568778"
---
# <a name="wcf-data-services-client-library"></a>Biblioteca de cliente do WCF Data Services
Qualquer aplicativo pode interagir com um serviço de dados baseado em Protocolo Open Data (OData) se ele puder enviar uma solicitação HTTP e processar o feed OData que um serviço de dados retorna. Essa interoperabilidade permite acessar serviços baseados em OData de uma ampla variedade de aplicativos habilitados para a Web. A WCF Data Services inclui bibliotecas de cliente que fornecem uma experiência de programação mais rica quando você consome feeds OData de aplicativos baseados em .NET Framework ou Silverlight.  
  
 As duas principais classes de biblioteca de cliente são as classes <xref:System.Data.Services.Client.DataServiceContext> e <xref:System.Data.Services.Client.DataServiceQuery%601>. A classe <xref:System.Data.Services.Client.DataServiceContext> encapsula as operações que têm suporte em um serviço de dados especificado. Embora os serviços OData sejam sem estado, o contexto não é. Portanto, você pode usar a classe <xref:System.Data.Services.Client.DataServiceContext> para manter o estado no cliente entre as interações com o serviço de dados a fim de dar suporte a recursos como o gerenciamento de alterações. Essa classe também gerencia identidades e rastreia alterações. A classe <xref:System.Data.Services.Client.DataServiceQuery%601> representa uma consulta em um conjunto de entidades específico.  
  
 Esta seção descreve como usar bibliotecas de cliente para acessar e modificar dados de um aplicativo cliente do .NET Framework. Para obter mais informações sobre como usar a biblioteca de cliente do WCF Data Services com um aplicativo baseado no Silverlight, consulte [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=186016). Outras bibliotecas de cliente estão disponíveis para permitir que você consuma um feed OData em outros tipos de aplicativos. Para obter mais informações, consulte o [SDK do OData](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)  
 Descreve como gerar uma biblioteca de cliente e classes de serviço de dados do cliente baseadas em feeds OData.  
  
 [Querying the Data Service](querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)  
 Descreve como consultar um serviço de dados de um aplicativo com base no .NET Framework usando bibliotecas de cliente.  
  
 [Carregando conteúdo adiado](loading-deferred-content-wcf-data-services.md)  
 Descreve como carregar o conteúdo adicional não incluído na resposta da consulta inicial.  
  
 [Atualizando o serviço de dados](updating-the-data-service-wcf-data-services.md)  
 Descreve como criar, modificar e excluir entidades e relações usando as bibliotecas de cliente.  
  
 [Operações assíncronas](asynchronous-operations-wcf-data-services.md)  
 Descreve os recursos fornecidos pelas bibliotecas de cliente para trabalhar com um serviço de dados de uma maneira assíncrona.  
  
 [Operações de envio em lote](batching-operations-wcf-data-services.md)  
 Descreve como enviar várias solicitações para o serviço de dados em um único lote usando as bibliotecas de cliente.  
  
 [Associando dados a controles](binding-data-to-controls-wcf-data-services.md)  
 Descreve como associar controles a um feed OData retornado por um serviço de dados.  
  
 [Chamar operações de serviço](calling-service-operations-wcf-data-services.md)  
 Descreve como usar o proxy do cliente de biblioteca para chamar operações de serviço.  
  
 [Gerenciando o contexto do serviço de dados](managing-the-data-service-context-wcf-data-services.md)  
 Descreve as opções para gerenciar o comportamento da biblioteca de cliente.  
  
 [Trabalhando com os dados binários](working-with-binary-data-wcf-data-services.md)  
 Descreve como acessar e alterar os dados binários retornados pelo serviço de dados como um fluxo de dados.  
  
## <a name="see-also"></a>Consulte também

- [Defining WCF Data Services](defining-wcf-data-services.md) (Definindo o WCF Data Services)
- [Introdução](getting-started-with-wcf-data-services.md)
