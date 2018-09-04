---
title: Expondo seus dados como um serviço (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: ba316aeda0a0a7e80af8e37a6a62e88652b9635b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520409"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>Expor seus dados como um serviço (WCF Data Services)

WCF Data Services se integra com o Visual Studio para que você possa definir mais facilmente os serviços para expor seus dados como [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feeds. Criar um serviço de dados que expõe um feed OData envolve as seguintes etapas básicas:

1.  **Defina o modelo de dados.** WCF Data Services dá suporte nativo a modelos de dados que se baseiam os [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md). Para obter mais informações, consulte [como: criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).

     Modelos de dados se baseiam em objetos common language runtime (CLR) que retornam uma instância do WCF Data Services também oferece suporte a <xref:System.Linq.IQueryable%601> interface. Isso permite que você implante os serviços de dados se baseiam em listas, matrizes e coleções do .NET Framework. Para permitir criar, atualizar e excluir operações sobre essas estruturas de dados, você também deve implementar o <xref:System.Data.Services.IUpdatable> interface. Para obter mais informações, consulte [como: criar um serviço de dados usando o provedor de reflexão](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).

     Para cenários mais avançados, o WCF Data Services inclui um conjunto de provedores que permitem que você definir um modelo de dados com base nos tipos de dados de associação tardia. Para obter mais informações, consulte [provedores de serviço de dados personalizado](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).

2.  **Crie o serviço de dados.** O serviço de dados mais básico expõe uma classe herdada da classe <xref:System.Data.Services.DataService%601>, com um tipo `T` que é o nome qualificado para namespace do contêiner de entidade. Para obter mais informações, consulte [definindo o WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).

3.  **Configure o serviço de dados.** Por padrão, o WCF Data Services desabilita o acesso aos recursos que são expostos por um contêiner de entidade. O <xref:System.Data.Services.DataServiceConfiguration> interface permite que você configure o acesso aos recursos e operações de serviço, especifique a versão compatível do OData e para definir outros comportamentos de serviços, como comportamentos de lote ou o número máximo de entidades que podem ser retornados em uma única resposta. Para obter mais informações, consulte [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

Para obter um exemplo de como criar um serviço de dados simples que se baseia no banco de dados de exemplo Northwind, consulte [Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).

## <a name="see-also"></a>Consulte também

- [Introdução](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [Visão geral](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)