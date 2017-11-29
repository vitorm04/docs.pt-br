---
title: WCF Data Services 4.5
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d1ef95ac84872b2cc39ec3a93abab10c39cd7738
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5
O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] (anteriormente conhecido como "ADO.NET Data Services") é um componente do .NET Framework que permite criar serviços que usam o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] para expor e consumir dados na Web ou na intranet usando a semântica de [REST (Transferência de Estado Representacional)](http://go.microsoft.com/fwlink/?LinkId=113919). O [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] expõe dados como recursos endereçáveis por URIs. Os dados são acessados e alterados usando os verbos HTTP padrão GET, PUT, POST e DELETE. O [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usa as convenções de relacionamento de entidade do [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md) para expor recursos como conjuntos de entidades relacionadas por associações.  
  
 O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] usa o protocolo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] para endereçar e atualizar recursos. Assim, é possível acessar esses serviços de qualquer cliente que dê suporte a [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. O [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] permite solicitar e gravar dados em recursos usando formatos de transferência conhecidos: Atom, um conjunto de padrões de troca e atualização de dados como XML, e JSON (JavaScript Object Notation), um formato de troca de dados baseado em texto usado extensivamente em aplicativos AJAX.  
  
 O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pode expor os dados originados de várias fontes como feeds [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. As ferramentas do Visual Studio facilitam a criação de um serviço baseado em [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] por meio de um modelo de dados Entity Framework do ADO.NET. Você também pode criar feeds [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] com base em classes CLR (Common Language Runtime) e até mesmo dados de associação tardia ou não tipados.  
  
 O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] também inclui um conjunto de bibliotecas cliente, um para aplicativos cliente .NET Framework gerais e outro especificamente para aplicativos baseados no Silverlight. Essas bibliotecas de clientes fornecem um modelo de programação baseado em objeto quando você acessa um feed [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de ambientes como o .NET Framework e o Silverlight.  
  
## <a name="where-should-i-start"></a>Onde devo começar?  
 Dependendo dos seus interesses, comece pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] em um dos tópicos a seguir.  
  
 Desejo ir diretamente para…  
 -   [Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)  
  
-   [Introdução](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [Silverlight Quickstart](http://go.microsoft.com/fwlink/?LinkID=192782) (Início rápido do Silverlight)  
  
-   [Silverlight Quickstart for Windows Phone Development](http://go.microsoft.com/fwlink/?LinkID=214535) (Guia de início rápido do Silverlight para desenvolvimento do Windows Phone)  
  
 Mostre-me apenas algum código…  
 -   [Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)  
  
-   [How to: Execute Data Service Queries](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md) (Como executar consultas de serviço de dados)  
  
-   [How to: Bind Data to Windows Presentation Foundation Elements](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md) (Como associar dados aos elementos do Windows Presentation Foundation)  
  
 Desejo saber mais sobre [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]…  
 -   [Whitepaper: Introducing OData](http://go.microsoft.com/fwlink/?LinkId=220867) (White paper: Introdução ao OData)  
  
-   [Site do Protocolo Open Data](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [OData: SDK](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [OData: Frequently Asked Questions](http://go.microsoft.com/fwlink/?LinkId=185867) (OData: perguntas frequentes)  
  
 Desejo assistir a alguns vídeos…  
 -   [Beginner's Guide to WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=220864) (Guia do iniciante do WCF Data Services)  
  
-   [WCF Data Services Developer Videos](http://go.microsoft.com/fwlink/?LinkId=220861) (Vídeos para desenvolvedores do WCF Data Services)  
  
-   [OData: Developers Web site](http://go.microsoft.com/fwlink/?LinkId=185866) (OData: site para desenvolvedores)  
  
 Desejo ver exemplos completos  
 -   [WCF Data Services Documentation Samples on MSDN Samples Gallery](http://go.microsoft.com/fwlink/?LinkID=220865) (Amostras de documentação do WCF Data Services na galeria de amostras do MSDN)  
  
-   [Other WCF Data Services Samples on MSDN Samples Gallery](http://go.microsoft.com/fwlink/?LinkId=220866) (Outras amostras do WCF Data Services na galeria de amostras do MSDN)  
  
-   [OData: SDK](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 Como ele se integra ao Visual Studio?  
 -   [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)  
  
-   [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md) (Criando o serviço de dados)  
  
-   [Entity Framework Provider](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md) (Provedor de Entity Framework)  
  
 O que posso fazer com ele?  
 -   [Visão Geral](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [Whitepaper: Introducing OData](http://go.microsoft.com/fwlink/?LinkId=220867) (White paper: Introdução ao OData)  
  
-   [Application Scenarios](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md) (Cenários de aplicativo)  
  
 Desejo usar o Silverlight…  
 -   [Silverlight Quickstart](http://go.microsoft.com/fwlink/?LinkID=192782) (Início rápido do Silverlight)  
  
-   [WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [Getting Started with Silverlight](http://go.microsoft.com/fwlink/?LinkId=148366) (Introdução ao Silverlight)  
  
 Desejo criar um aplicativo para Windows Phone…  
 -   [Silverlight Quickstart for Windows Phone Development](http://go.microsoft.com/fwlink/?LinkID=214535) (Guia de início rápido do Silverlight para desenvolvimento do Windows Phone)  
  
-   [Open Data Protocol () Client for Windows Phone](http://go.microsoft.com/fwlink/?LinkID=208749) [Cliente do OData (Open Data Protocol) para Windows Phone]  
  
 Desejo usar LINQ…  
 -   [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)  
  
-   [LINQ Considerations](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md) (Considerações sobre LINQ)  
  
-   [How to: Execute Data Service Queries](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md) (Como executar consultas de serviço de dados)  
  
 Ainda preciso de mais informações…  
 -   [Blog da equipe do WCF Data Services](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [Recursos](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [WCF Data Services Developer Center](http://go.microsoft.com/fwlink/?LinkId=220868) (Central de desenvolvedores do WCF Data Services)  
  
-   [Site do Protocolo Open Data](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão Geral](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 Apresenta uma visão geral dos recursos e da funcionalidade disponíveis no [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
 [What's New in WCF Data Services](http://msdn.microsoft.com/en-us/cf22cad5-b8d9-472b-8d7c-b863b64eaae8) (Novidades no WCF Data Services)  
 Descreve as novas funcionalidades no [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] e o suporte para novos recursos do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
  
 [Introdução](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 Descreve como expor e consumir feeds [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usando o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)  
 Descreve como criar e configurar um serviço de dados que expõe feeds [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)  
 Descreve como usar bibliotecas de clientes para consumir feeds [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de um aplicativo de cliente do .NET Framework.  
  
## <a name="see-also"></a>Consulte também  
 [Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919) [REST (Transferência de Estado Representacional)]
