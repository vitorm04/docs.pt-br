---
title: "Visão geral do WCF Data Services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36abf79ec34b2fff8a3bfa46f2f62e5a787bbfe8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="wcf-data-services-overview"></a>Visão geral do WCF Data Services
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]permite a criação e consumo de serviços de dados para a Web ou uma intranet usando o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]permite que você exponha seus dados como recursos endereçáveis por URIs. Isso permite que você acesse e dados de alteração usando a semântica de transferência de estado representacional (REST), especificamente os verbos HTTP padrão de GET, PUT, POSTAGEM e excluir. Este tópico fornece uma visão geral de padrões e práticas recomendadas definidas pelo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] e também os recursos fornecidos pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] para tirar proveito dos [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] em aplicativos do .NET Framework.  
  
## <a name="address-data-as-resources"></a>Dados de endereço como recursos  
 O [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] expõe dados como recursos endereçáveis por URIs. Os caminhos de recurso são criados com base nas convenções de relação de entidade do modelo de dados de entidade. Nesse modelo, entidades representam operacionais unidades de dados em um domínio de aplicativo, como clientes, pedidos, itens e produtos. Para obter mais informações, consulte [modelo de dados de entidade](../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 No [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], você endereça recursos de entidade como um conjunto de entidades que contém instâncias de tipos de entidades. Por exemplo, o URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` retorna todos os pedidos do `Northwind` serviço de dados que estão relacionadas ao cliente com um `CustomerID` valor`ALFKI.`  
  
 As expressões de consulta permitem executar operações tradicionais de consulta em recursos, como filtragem, classificação e paginação. Por exemplo, o URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` filtra os recursos para retornar somente os pedidos com um custo de frete superior a US$ 50. Para obter mais informações, consulte [acessando recursos do serviço de dados](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Acesso a dados interoperáveis  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]com base em protocolos padrão da Internet para tornar os serviços de dados funciona com aplicativos que não usam o .NET Framework. Como você pode usar o padrão URIs para os dados de endereço, seu aplicativo pode acessar e alterar dados usando a semântica de transferência de estado representacional (REST), especificamente os verbos HTTP padrão de GET, PUT, POSTAGEM e excluir. Isso permite acessar esses serviços de qualquer cliente que possa analisar e acessar dados transmitidos por protocolos HTTP padrão.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]define um conjunto de extensões para o protocolo de publicação Atom (AtomPub). Ele dá suporte a solicitações e respostas HTTP em mais de um formato de dados para acomodar várias plataformas e aplicativos cliente. Um feed [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] pode representar dados em Atom, JSON (JavaScript Object Notation) e como XML sem formatação. Quando Atom é o formato padrão, o formato do feed é especificado no cabeçalho da solicitação HTTP. Para obter mais informações, consulte [OData: formato Atom](http://go.microsoft.com/fwlink/?LinkID=185794) e [OData: formato JSON](http://go.microsoft.com/fwlink/?LinkID=185795).  
  
 Ao publicar dados como uma [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] depende de outros recursos da Internet existentes para operações como cache e autenticação. Para fazer isso, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] se integra com aplicativos de hospedagem existentes e serviços, como ASP.NET, Windows Communication Foundation (WCF) e serviços de informações da Internet (IIS).  
  
## <a name="storage-independence"></a>Independência de armazenamento  
 Embora os recursos sejam resolvidos com base em um modelo de relação de entidade [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] expor [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds, independentemente da fonte de dados subjacente. Depois de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] aceita uma solicitação HTTP para um recurso que identifica um URI, a solicitação é desserializada e uma representação do que a solicitação é passada para um [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] provedor. Este provedor converte a solicitação em um formato específico de fonte de dados e executa a solicitação na fonte de dados subjacente. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]alcança independência de armazenamento, separando o modelo conceitual que aborda recursos indicados pelo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] do esquema específico da fonte de dados subjacente.  
  
 O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] é integrado ao ADO.NET Entity Framework para permitir a criação de serviços de dados que exponham dados relacionais. Você pode usar as ferramentas do Modelo de Dados de Entidade para criar um modelo de dados que contenha recursos endereçáveis como entidades e definir, ao mesmo tempo, o mapeamento entre esse modelo e as tabelas no banco de dados subjacente. Para obter mais informações, consulte [provedor do Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]também permite criar serviços de dados que expõem as estruturas de dados que retornam uma implementação do <xref:System.Linq.IQueryable%601> interface. Isso permite criar serviços de dados que expõem dados de tipos .NET Framework. Há suporte para operações de criação, atualização e exclusão quando você também implementa a interface <xref:System.Data.Services.IUpdatable>. Para obter mais informações, consulte [provedor de reflexão](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).  
  
 Para obter uma ilustração de como [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integra-se com esses provedores de dados, consulte o diagrama de arquitetura neste tópico.  
  
## <a name="custom-business-logic"></a>Lógica de negócios personalizada  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]é fácil adicionar lógica de negócios personalizada para um serviço de dados por meio de operações de serviço e interceptores. As operações de serviço são métodos definidos no servidor que são endereçáveis por URIs no mesmo formulário que os recursos de dados. Operações de serviço também podem usar a sintaxe de expressão de consulta para filtrar, ordem e dados retornados por uma operação da página. Por exemplo, o URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` representa uma chamada para uma operação de serviço chamada `GetOrdersByCity` do serviço de dados Northwind que retorna as ordens para clientes de Londres, com resultados paginados classificados por `OrderDate`. Para obter mais informações, consulte [operações de serviço](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Os interceptores permitem que a lógica personalizada do aplicativo seja integrada ao processamento de mensagens de solicitação e de resposta por um serviço de dados. Os interceptores são chamados quando uma ação de consulta, inserção, atualização ou exclusão ocorre no conjunto de entidades especificado. Um interceptor poderá, então, alterar dados, impor uma política de autorização ou até mesmo terminar a operação. Os métodos de interceptor devem ser explicitamente registrados para um conjunto de entidades específico exposto por um serviço de dados. Para obter mais informações, consulte [interceptores](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>Bibliotecas cliente  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]define um conjunto de padrões uniformes para interagir com os serviços de dados. Isso fornece uma oportunidade para criar componentes reutilizáveis que se baseiam nesses serviços, assim como bibliotecas de cliente que facilitam a consumir os serviços de dados.  
  
 O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclui bibliotecas cliente para aplicativos cliente baseados no .NET Framework e no Silverlight. Essas bibliotecas cliente permitem interagir com serviços de dados usando objetos .NET Framework. Elas também dão suporte a consultas com base no objeto e consultas LINQ, carregando os objetos relacionados, controle de alterações e resolução de identidade. Para obter mais informações, consulte [biblioteca de cliente do WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
 Além de [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] bibliotecas de cliente incluídas com o .NET Framework e Silverlight, há outras bibliotecas de cliente que permitem que você consuma um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed em aplicativos cliente, como aplicativos Java, PHP e AJAX. Para obter mais informações, consulte o [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Visão geral da arquitetura  
 O diagrama a seguir ilustra o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] arquitetura para expor [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds e usar esses feeds em [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-habilitado bibliotecas de cliente:  
  
 ![Diagrama de arquitetura do WCF Data Services](../../../../docs/framework/data/wcf/media/astoriaservicearch.gif "AstoriaServiceArch")  
  
## <a name="see-also"></a>Consulte também  
 [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)  
 [Introdução](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)  
 [Acessando um serviço de dados (WCF Data Services)](http://msdn.microsoft.com/library/1e54a2b9-2ec6-4002-b8f8-c1d8df37c350)  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)  
 [Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919) [REST (Transferência de Estado Representacional)]
