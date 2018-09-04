---
title: Biblioteca de cliente do WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 4f389530b287d1c7a11a88972ef948347d3ea533
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508954"
---
# <a name="wcf-data-services-client-library"></a>Biblioteca de cliente do WCF Data Services
Qualquer aplicativo pode interagir com um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]-com base em serviço de dados se ele pode enviar uma solicitação HTTP e processar o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed que um serviço de dados retorna. Esta interoperabilidade permite que você acesse [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-com base em serviços em um amplo aplicativos de intervalo da Web habilitado. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclui bibliotecas de cliente que fornecem uma experiência mais rica de programação quando você consome [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds a partir do .NET Framework ou aplicativos baseados no Silverlight.  
  
 As duas principais classes de biblioteca de cliente são as classes <xref:System.Data.Services.Client.DataServiceContext> e <xref:System.Data.Services.Client.DataServiceQuery%601>. A classe <xref:System.Data.Services.Client.DataServiceContext> encapsula as operações que têm suporte em um serviço de dados especificado. Embora os serviços do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] sejam sem estado, o contexto não é. Portanto, você pode usar o <xref:System.Data.Services.Client.DataServiceContext> classe para manter o estado no cliente entre interações com o serviço de dados para dar suporte a recursos como o gerenciamento de alterações. Essa classe também gerencia identidades e rastreia alterações. A classe <xref:System.Data.Services.Client.DataServiceQuery%601> representa uma consulta em um conjunto de entidades específico.  
  
 Esta seção descreve como usar bibliotecas de cliente para acessar e modificar dados de um aplicativo cliente do .NET Framework. Para obter mais informações sobre como usar o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente com um aplicativo baseado no Silverlight, consulte [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=186016). Outras bibliotecas de cliente estão disponíveis que permitem consumir um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed em outros tipos de aplicativos. Para obter mais informações, consulte o [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)  
 Descreve como gerar uma biblioteca de cliente e classes de serviço de dados do cliente que se baseiam no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.  
  
 [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)  
 Descreve como consultar um serviço de dados de um aplicativo com base no .NET Framework usando bibliotecas de cliente.  
  
 [Carregando conteúdo adiado](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 Descreve como carregar o conteúdo adicional não incluído na resposta da consulta inicial.  
  
 [Atualizando o serviço de dados](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 Descreve como criar, modificar e excluir entidades e relações usando as bibliotecas de cliente.  
  
 [Operações assíncronas](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 Descreve os recursos fornecidos pelas bibliotecas de cliente para trabalhar com um serviço de dados de uma maneira assíncrona.  
  
 [Operações de envio em lote](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 Descreve como enviar várias solicitações para o serviço de dados em um único lote usando as bibliotecas de cliente.  
  
 [Associando dados a controles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 Descreve como associar controles a um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed retornado por um serviço de dados.  
  
 [Chamar operações de serviço](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 Descreve como usar o proxy do cliente de biblioteca para chamar operações de serviço.  
  
 [Gerenciando o contexto do serviço de dados](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 Descreve as opções para gerenciar o comportamento da biblioteca de cliente.  
  
 [Trabalhando com os dados binários](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 Descreve como acessar e alterar os dados binários retornados pelo serviço de dados como um fluxo de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)  
 [Introdução](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
