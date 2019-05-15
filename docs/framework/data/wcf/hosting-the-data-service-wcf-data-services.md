---
title: Hospeda o serviço de dados (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: 4886103f7f0246eaacd12c3f12d50a055e650959
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582677"
---
# <a name="hosting-the-data-service-wcf-data-services"></a>Hospeda o serviço de dados (WCF Data Services)
Usando o WCF Data Services, você pode criar um serviço que expõe dados como um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed. Esse serviço de dados é definido como uma classe que herda de <xref:System.Data.Services.DataService%601>. Essa classe fornece a funcionalidade necessária para processar mensagens de solicitação, realizar atualizações na fonte de dados e gerar mensagens de respostas, conforme exigido pelo OData. No entanto, um serviço de dados não é possível associar a e escuta um soquete de rede para solicitações HTTP de entrada. Para essa funcionalidade necessária, o serviço de dados se baseia em um componente de hospedagem.

 O host de serviço de dados executa as seguintes tarefas em nome do serviço de dados:

- Escuta as solicitações e encaminha essas solicitações para o serviço de dados.

- Cria uma instância do serviço de dados para cada solicitação.

- Solicita que o serviço de dados processar a solicitação de entrada.

- Envia a resposta em nome do serviço de dados.

 Para simplificar a hospedagem de um serviço de dados, o WCF Data Services foi projetado para integrar com o Windows Communication Foundation (WCF). O serviço de dados fornece uma implementação de WCF padrão que serve como o host de serviço de dados em um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo. Portanto, você pode hospedar um serviço de dados em uma das seguintes maneiras:

- Em um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo.

- Em um aplicativo gerenciado que oferece suporte aos serviços do WCF auto-hospedado.

- Em alguns outro host de serviço de dados personalizados.

## <a name="hosting-a-data-service-in-an-aspnet-application"></a>Hospedar um serviço de dados em um aplicativo ASP.NET

Quando você usa o **Adicionar Novo Item** caixa de diálogo no Visual Studio 2015 para definir um serviço de dados em um aplicativo ASP.NET, a ferramenta gera dois novos arquivos no projeto. O primeiro arquivo tem um `.svc` extensão e instrui o tempo de execução do WCF como criar uma instância de serviço de dados. A seguir está um exemplo desse arquivo para o serviço de dados de exemplo Northwind criado quando você conclui o [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):

```
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 Essa diretiva diz ao aplicativo para criar o host de serviço para a classe de serviço de dados nomeado usando o <xref:System.Data.Services.DataServiceHostFactory> classe.

 A página code-behind para o `.svc` arquivo contém a classe que é a implementação do serviço de dados em si, é definido da seguinte maneira para o serviço de dados de exemplo Northwind:

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 Como um serviço de dados se comporta como um serviço WCF, o serviço de dados se integra com [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] e segue o modelo de programação Web do WCF. Para obter mais informações, consulte [serviços WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) e [modelo de programação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).

## <a name="self-hosted-wcf-services"></a>Serviços WCF auto-hospedado
 Como ele incorpora uma implementação de WCF, o WCF Data Services oferecem suporte auto-hospedagem em um serviço de dados como um serviço WCF. Um serviço pode ser auto-hospedado em qualquer aplicativo do .NET Framework, como um aplicativo de console. O <xref:System.Data.Services.DataServiceHost> classe, que herda de <xref:System.ServiceModel.Web.WebServiceHost>, é usado para instanciar o serviço de dados em um endereço específico.

 Hospedagem interna pode ser usada para desenvolvimento e teste, pois isso pode tornar mais fácil de implantar e solucionar problemas do serviço. No entanto, esse tipo de hospedagem não fornece recursos de hospedagem e gerenciamento avançados fornecidos pelo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ou pelo Internet Information Services (IIS). Para obter mais informações, consulte [hospedagem em um aplicativo gerenciado](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).

## <a name="defining-a-custom-data-service-host"></a>Definindo um Host de serviço de dados personalizados
 Para casos em que a implementação de host do WCF é restritiva demais, você também pode definir um host personalizado para um serviço de dados. Qualquer classe que implemente <xref:System.Data.Services.IDataServiceHost> interface pode ser usada como o host de rede para um serviço de dados. Um host personalizado deve implementar a <xref:System.Data.Services.IDataServiceHost> de interface e ser capaz de lidar com as seguintes responsabilidades básicas do host do serviço de dados:

- Fornece o serviço de dados com o caminho raiz do serviço.

- Processar informações de cabeçalhos de solicitação e resposta ao apropriado <xref:System.Data.Services.IDataServiceHost> implementação de membro.

- Trate as exceções geradas pelo serviço de dados.

- Valide parâmetros na cadeia de caracteres de consulta.

## <a name="see-also"></a>Consulte também

- [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)
- [Expondo seus dados como um serviço](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
- [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
