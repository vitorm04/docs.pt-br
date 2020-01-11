---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 890f0ba25d8320008228c73660753b9899269fd7
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900994"
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5

WCF Data Services (anteriormente conhecido como "ADO.NET Data Services") é um componente da .NET Framework que permite criar serviços que usam o Protocolo Open Data (OData) para expor e consumir dados pela Web ou intranet usando a semântica da [REST (transferência de estado de reapresentação)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm). OData expõe dados como recursos endereçáveis por URIs. Os dados são acessados e modificados usando verbos HTTP padrão, que são GET, PUT, POST e DELETE. O OData usa as convenções de relacionamento de entidade do [modelo de dados de entidade](../adonet/entity-data-model.md) para expor recursos como conjuntos de entidades relacionadas por associações.

WCF Data Services usa o protocolo OData para endereçar e atualizar recursos. Dessa forma, você pode acessar esses serviços de qualquer cliente que ofereça suporte a OData. O OData permite que você solicite e grave dados em recursos usando formatos de transferência conhecidos: Atom, um conjunto de padrões para a troca e atualização de dados como XML e JavaScript Object Notation (JSON), um formato de troca de dados baseado em texto usado extensivamente no AJAX aplicativos.

WCF Data Services pode expor dados originados de várias fontes como feeds OData. As ferramentas do Visual Studio facilitam a criação de um serviço baseado em OData usando um modelo de dados do ADO.NET Entity Framework. Você também pode criar feeds OData com base em classes Common Language Runtime (CLR) e até mesmo dados de associação tardia ou não tipada.

WCF Data Services também inclui um conjunto de bibliotecas de cliente, uma para aplicativos cliente .NET Framework geral e outra especificamente para aplicativos baseados no Silverlight. Essas bibliotecas de cliente fornecem um modelo de programação baseado em objeto quando você acessa um feed OData de ambientes como o .NET Framework e o Silverlight.

## <a name="where-should-i-start"></a>Onde devo começar?

Dependendo de seus interesses, considere a introdução ao WCF Data Services em um dos tópicos a seguir.

Desejo ir diretamente para...

- [Quickstart](quickstart-wcf-data-services.md) (Início rápido)

- [Introdução](getting-started-with-wcf-data-services.md)

Mostrar apenas alguns códigos...

- [Quickstart](quickstart-wcf-data-services.md) (Início rápido)

- [How to: Execute Data Service Queries](how-to-execute-data-service-queries-wcf-data-services.md) (Como executar consultas de serviço de dados)

- [How to: Bind Data to Windows Presentation Foundation Elements](bind-data-to-wpf-elements-wcf-data-services.md) (Como associar dados aos elementos do Windows Presentation Foundation)

Quero saber mais sobre o OData...

- [Whitepaper: Introducing OData](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf) (White paper: Introdução ao OData)
- [Site do Protocolo Open Data](https://www.odata.org/)
- [OData: SDK](https://www.odata.org/ecosystem/)

Quero ver exemplos de ponta a ponta...

- [Guia de início rápido WCF Data Services](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))
- [SDK do OData – código de exemplo](https://www.odata.org/ecosystem/#sdk)

Como ele se integra ao Visual Studio?

- [Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)

- [Creating the Data Service](creating-the-data-service.md) (Criando o serviço de dados)

- [Entity Framework Provider](entity-framework-provider-wcf-data-services.md) (Provedor de Entity Framework)

O que posso fazer com ele?

- [Visão Geral](wcf-data-services-overview.md)

- [Application Scenarios](application-scenarios-wcf-data-services.md) (Cenários de aplicativo)

Quero usar LINQ...

- [Querying the Data Service](querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)

- [LINQ Considerations](linq-considerations-wcf-data-services.md) (Considerações sobre LINQ)

- [How to: Execute Data Service Queries](how-to-execute-data-service-queries-wcf-data-services.md) (Como executar consultas de serviço de dados)

Ainda preciso de mais algumas informações...

- [Blog da equipe do WCF Data Services](https://docs.microsoft.com/archive/blogs/astoriateam/)

- [Recursos](wcf-data-services-resources.md)

## <a name="in-this-section"></a>Nesta seção

[Visão Geral](wcf-data-services-overview.md)

Fornece uma visão geral dos recursos e funcionalidades disponíveis no WCF Data Services.

[O que há de novo no WCF Data Services 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))

Descreve a nova funcionalidade no WCF Data Services e suporte para novos recursos OData.

[Introdução](getting-started-with-wcf-data-services.md)

Descreve como expor e consumir feeds OData usando WCF Data Services.

[Defining WCF Data Services](defining-wcf-data-services.md) (Definindo o WCF Data Services)

Descreve como criar e configurar um serviço de dados que expõe feeds OData.

[WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)

Descreve como usar bibliotecas de cliente para consumir feeds OData de um aplicativo cliente .NET Framework.

## <a name="see-also"></a>Veja também

- [Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm) [REST (Transferência de Estado Representacional)]
