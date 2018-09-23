---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 9ece2fe051855d0fd39556f56a4343ead2c437bc
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46702794"
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5

WCF Data Services (anteriormente conhecido como "ADO.NET Data Services") é um componente do .NET Framework que permite que você crie serviços que usam o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] para expor e consumir dados na Web ou intranet usando a semântica de [ transferência de estado representacional (REST)](https://go.microsoft.com/fwlink/?LinkId=113919). OData expõem dados como recursos que são endereçáveis por URIs. Os dados são acessados e alterados usando os verbos HTTP padrão GET, PUT, POST e DELETE. OData usa as convenções de relacionamento entre entidades do [modelo de dados de entidade](../../../../docs/framework/data/adonet/entity-data-model.md) para expor recursos como conjuntos de entidades relacionadas por associações.

WCF Data Services usa o protocolo OData para endereçamento e atualização de recursos. Dessa forma, você pode acessar esses serviços de qualquer cliente que dê suporte a OData. OData lhe permite solicitar e gravar dados em recursos usando formatos de transferência conhecidos: Atom, um conjunto de padrões de troca e atualização de dados como XML e JSON JavaScript Object Notation (), um formato de troca de dados com base em texto usado extensivamente em AJAX aplicativo.

WCF Data Services pode expor dados provenientes de várias fontes como feeds OData. Ferramentas do Visual Studio facilitam a criação de um serviço baseado em OData usando um modelo de dados do ADO.NET Entity Framework. Você também pode criar feeds OData com base em classes do common language runtime (CLR) e dados de até mesmo associação tardia ou não tipados.

WCF Data Services também inclui um conjunto de bibliotecas de cliente, um para aplicativos de cliente do .NET Framework gerais e outro especificamente para aplicativos baseados no Silverlight. Essas bibliotecas de cliente fornecem um modelo de programação baseado em objeto quando você acessa um feed OData em ambientes como o .NET Framework e Silverlight.

## <a name="where-should-i-start"></a>Onde devo começar?

Dependendo dos seus interesses, considere a introdução ao WCF Data Services em um dos tópicos a seguir.

Desejo ir diretamente para...

-   [Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)

-   [Introdução](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

-   [Silverlight Quickstart](https://go.microsoft.com/fwlink/?LinkID=192782) (Início rápido do Silverlight)

-   [Silverlight Quickstart for Windows Phone Development](https://go.microsoft.com/fwlink/?LinkID=214535) (Guia de início rápido do Silverlight para desenvolvimento do Windows Phone)

Mostre-me apenas algum código...

-   [Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)

-   [How to: Execute Data Service Queries](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md) (Como executar consultas de serviço de dados)

-   [How to: Bind Data to Windows Presentation Foundation Elements](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md) (Como associar dados aos elementos do Windows Presentation Foundation)

Quero saber mais sobre OData...

 -   [Whitepaper: Introducing OData](https://go.microsoft.com/fwlink/?LinkId=220867) (White paper: Introdução ao OData)

-   [Site do Protocolo Open Data](https://go.microsoft.com/fwlink/?LinkID=184554)

-   [OData: SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

-   [OData: Frequently Asked Questions](https://go.microsoft.com/fwlink/?LinkId=185867) (OData: perguntas frequentes)

Eu desejo assistir a alguns vídeos...

-   [Beginner's Guide to WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=220864) (Guia do iniciante do WCF Data Services)

-   [WCF Data Services Developer Videos](https://go.microsoft.com/fwlink/?LinkId=220861) (Vídeos para desenvolvedores do WCF Data Services)

-   [OData: Developers Web site](https://go.microsoft.com/fwlink/?LinkId=185866) (OData: site para desenvolvedores)

Desejo ver exemplos de ponta a ponta...

-   [WCF Data Services Documentation Samples on MSDN Samples Gallery](https://go.microsoft.com/fwlink/?LinkID=220865) (Amostras de documentação do WCF Data Services na galeria de amostras do MSDN)

-   [Other WCF Data Services Samples on MSDN Samples Gallery](https://go.microsoft.com/fwlink/?LinkId=220866) (Outras amostras do WCF Data Services na galeria de amostras do MSDN)

-   [OData: SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

Como ele se integra ao Visual Studio?

-   [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)

-   [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md) (Criando o serviço de dados)

-   [Entity Framework Provider](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md) (Provedor de Entity Framework)

O que posso fazer com ele?

-   [Visão geral](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

-   [Whitepaper: Introducing OData](https://go.microsoft.com/fwlink/?LinkId=220867) (White paper: Introdução ao OData)

-   [Application Scenarios](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md) (Cenários de aplicativo)

Desejo usar o Silverlight...

-   [Silverlight Quickstart](https://go.microsoft.com/fwlink/?LinkID=192782) (Início rápido do Silverlight)

-   [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)

-   [Getting Started with Silverlight](https://go.microsoft.com/fwlink/?LinkId=148366) (Introdução ao Silverlight)

Desejo usar LINQ...

-   [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)

-   [LINQ Considerations](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md) (Considerações sobre LINQ)

-   [How to: Execute Data Service Queries](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md) (Como executar consultas de serviço de dados)

Eu ainda preciso de mais algumas informações...

-   [Blog da equipe do WCF Data Services](https://go.microsoft.com/fwlink/?LinkID=150511)

-   [Recursos](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

-   [WCF Data Services Developer Center](https://go.microsoft.com/fwlink/?LinkId=220868) (Central de desenvolvedores do WCF Data Services)

-   [Site do Protocolo Open Data](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a>Nesta seção

 [Visão geral](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

 Fornece uma visão geral dos recursos e funcionalidades disponíveis no WCF Data Services.

 [What's New in WCF Data Services](https://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8) (Novidades no WCF Data Services)

 Descreve a nova funcionalidade no WCF Data Services e o suporte para novos recursos do OData.

 [Introdução](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

 Descreve como expor e consumir feeds de OData usando o WCF Data Services.

 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)

 Descreve como criar e configurar um serviço de dados que expõe feeds OData.

 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)

 Descreve como usar bibliotecas de cliente para consumir feeds de OData de um aplicativo de cliente do .NET Framework.

## <a name="see-also"></a>Consulte também

- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919) [REST (Transferência de Estado Representacional)]
