---
title: Visão geral do WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: bca07bf776f20443c4ccd2af69fc8c0b4eec5a88
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991096"
---
# <a name="wcf-data-services-overview"></a>Visão geral do WCF Data Services
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]permite a criação e o consumo de serviços de dados para a Web ou uma intranet [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]usando o. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]permite que você exponha seus dados como recursos que são endereçáveis por URIs. Isso permite que você acesse e altere dados usando a semântica da REST (transferência de estado de reapresentação), especificamente os verbos HTTP padrão de GET, PUT, POST e DELETE. Este tópico fornece uma visão geral dos padrões e das práticas definidas pelo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] e também das instalações fornecidas pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] para aproveitar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] os aplicativos baseados em .NET Framework.  
  
## <a name="address-data-as-resources"></a>Dados de endereço como recursos  
 O [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] expõe dados como recursos endereçáveis por URIs. Os caminhos de recurso são construídos com base nas convenções de relacionamento de entidade do Modelo de Dados de Entidade. Nesse modelo, as entidades representam unidades operacionais de dados em um domínio de aplicativo, como clientes, pedidos, itens e produtos. Para obter mais informações, consulte [modelo de dados de entidade](../adonet/entity-data-model.md).  
  
 No [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], você endereça recursos de entidade como um conjunto de entidades que contém instâncias de tipos de entidades. Por exemplo, o URI <https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders> retorna todos os pedidos `Northwind` do serviço de dados que estão relacionados ao cliente com um `CustomerID` valor de`ALFKI.`  
  
 As expressões de consulta permitem executar operações tradicionais de consulta em recursos, como filtragem, classificação e paginação. Por exemplo, o URI <https://services.odata.org/Northwind/Northwind.svc/Customers( ' ALFKI ')/Orders? $Filter = frete gt 50 > filtra os recursos para retornar apenas os pedidos com um custo de frete de mais de $50. Para obter mais informações, consulte [acessando recursos do serviço de dados](accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Acesso a dados interoperáveis  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]baseia-se em protocolos padrão da Internet para tornar os serviços de dados interoperáveis com aplicativos que não usam o .NET Framework. Como você pode usar URIs padrão para endereçar dados, seu aplicativo pode acessar e alterar os dados usando a semântica de REST (transferência de estado de reapresentação), especificamente os verbos HTTP padrão de GET, PUT, POST e DELETE. Isso permite acessar esses serviços de qualquer cliente que possa analisar e acessar dados transmitidos por protocolos HTTP padrão.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]define um conjunto de extensões para o protocolo de publicação Atom (AtomPub). Ele dá suporte a solicitações e respostas HTTP em mais de um formato de dados para acomodar vários aplicativos e plataformas cliente. Um feed [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] pode representar dados em Atom, JSON (JavaScript Object Notation) e como XML sem formatação. Quando Atom é o formato padrão, o formato do feed é especificado no cabeçalho da solicitação HTTP. Para obter mais informações, [consulte OData: Formato](https://go.microsoft.com/fwlink/?LinkID=185794) Atom e [OData: Formato](https://go.microsoft.com/fwlink/?LinkID=185795)JSON.  
  
 Ao publicar dados como um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] o depende de outros recursos da Internet existentes para operações como armazenamento em cache e autenticação. Para fazer isso, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] o integra-se com os aplicativos e serviços de hospedagem existentes, como ASP.net, Windows Communication Foundation (WCF) e serviços de informações da Internet (IIS).  
  
## <a name="storage-independence"></a>Independência de armazenamento  
 Embora os recursos sejam resolvidos com base em um modelo de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] relacionamento [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de entidade, exponha feeds independentemente da fonte de dados subjacente. Depois [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] que o aceita uma solicitação HTTP para um recurso que um URI identifica, a solicitação é desserializada e uma representação dessa solicitação é passada para [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] um provedor. Esse provedor converte a solicitação em um formato específico da fonte de dados e executa a solicitação na fonte de dados subjacente. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]alcança a independência de armazenamento, separando o modelo conceitual que aborda [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] os recursos prescritos pelo esquema específico da fonte de dados subjacente.  
  
 O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] é integrado ao ADO.NET Entity Framework para permitir a criação de serviços de dados que exponham dados relacionais. Você pode usar as ferramentas do Modelo de Dados de Entidade para criar um modelo de dados que contenha recursos endereçáveis como entidades e definir, ao mesmo tempo, o mapeamento entre esse modelo e as tabelas no banco de dados subjacente. Para obter mais informações, consulte [provedor de Entity Framework](entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]também permite que você crie serviços de dados que expõem todas as estruturas de dados que retornam uma implementação da <xref:System.Linq.IQueryable%601> interface. Isso permite criar serviços de dados que expõem dados de tipos .NET Framework. Há suporte para operações de criação, atualização e exclusão quando você também implementa a interface <xref:System.Data.Services.IUpdatable>. Para obter mais informações, consulte [provedor de reflexão](reflection-provider-wcf-data-services.md).  
  
 Para obter uma ilustração de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] como o se integra a esses provedores de dados, consulte o diagrama arquitetônico mais adiante neste tópico.  
  
## <a name="custom-business-logic"></a>Lógica de negócios personalizada  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]facilita a adição de lógica de negócios personalizada a um serviço de dados por meio de operações e interceptores de serviço. As operações de serviço são métodos definidos no servidor que são endereçáveis por URIs no mesmo formulário que os recursos de dados. As operações de serviço também podem usar a sintaxe de expressão de consulta para filtrar, ordenar e paginar dados retornados por uma operação. Por exemplo, o URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` representa uma chamada para uma operação de serviço `GetOrdersByCity` chamada no serviço de dados Northwind que retorna pedidos para clientes de Londres, com resultados paginados `OrderDate`classificados por. Para obter mais informações, consulte [operações de serviço](service-operations-wcf-data-services.md).  
  
 Os interceptores permitem que a lógica personalizada do aplicativo seja integrada ao processamento de mensagens de solicitação e de resposta por um serviço de dados. Os interceptores são chamados quando uma ação de consulta, inserção, atualização ou exclusão ocorre no conjunto de entidades especificado. Um interceptor poderá, então, alterar dados, impor uma política de autorização ou até mesmo terminar a operação. Os métodos de interceptor devem ser explicitamente registrados para um conjunto de entidades específico exposto por um serviço de dados. Para obter mais informações, consulte [Interceptors](interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>Bibliotecas cliente  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]define um conjunto de padrões uniformes para interagir com os serviços de dados. Isso oferece uma oportunidade de criar componentes reutilizáveis baseados nesses serviços, como bibliotecas do lado do cliente que facilitam o consumo de serviços de dados.  
  
 O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclui bibliotecas cliente para aplicativos cliente baseados no .NET Framework e no Silverlight. Essas bibliotecas cliente permitem interagir com serviços de dados usando objetos .NET Framework. Eles também dão suporte a consultas baseadas em objeto e consultas LINQ, carregamento de objetos relacionados, controle de alterações e resolução de identidade. Para obter mais informações, consulte [WCF Data Services biblioteca de cliente](wcf-data-services-client-library.md).  
  
 Além das [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] bibliotecas de cliente incluídas com o .NET Framework e com o Silverlight, há outras bibliotecas de cliente que permitem que você consuma um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed em aplicativos cliente, como PHP, Ajax e aplicativos Java. Para obter mais informações, consulte o [SDK do OData](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Visão geral da arquitetura  
 O diagrama a seguir ilustra [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] a arquitetura para [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Expor feeds [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]e usar esses feeds bibliotecas de cliente habilitadas para o:  
  
 ![Captura de tela mostrando um diagrama de arquitetura de WCF Data Services.](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services 4.5](index.md)
- [Introdução](getting-started-with-wcf-data-services.md)
- [Defining WCF Data Services](defining-wcf-data-services.md) (Definindo o WCF Data Services)
- [Acessando recursos do serviço de dados (WCF Data Services)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919) [REST (Transferência de Estado Representacional)]
