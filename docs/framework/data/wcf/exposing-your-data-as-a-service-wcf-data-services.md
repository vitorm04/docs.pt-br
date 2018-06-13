---
title: Expondo seus dados como um serviço (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 1ab349125419a0589d68ccb821009f8227c942e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363558"
---
# <a name="exposing-your-data-as-a-service-wcf-data-services"></a>Expondo seus dados como um serviço (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integra-se com o Visual Studio para que você possa definir mais facilmente os serviços para expor seus dados como [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feeds. Criando um serviço de dados que expõe um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed envolve as seguintes etapas básicas:  
  
1.  **Definir** **o modelo de dados**. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] oferece suporte nativo a modelos de dados que se baseiam o [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md). Para obter mais informações, consulte [como: criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
     O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] também dá suporte a modelos de dados que se baseiam em objetos CLR (Common Language Runtime) que retornam uma instância da interface <xref:System.Linq.IQueryable%601>. Isso permite que você implante os serviços de dados se baseiam em listas, matrizes e coleções do .NET Framework. Para permitir criar, atualizar e excluir operações sobre essas estruturas de dados, você também deve implementar o <xref:System.Data.Services.IUpdatable> interface. Para obter mais informações, consulte [como: criar um serviço de dados usando o provedor de reflexão](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
     Para cenários mais avançados, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclui um conjunto de provedores que lhe permitem definir um modelo de dados com base nos tipos de dados de associação tardia. Para obter mais informações, consulte [provedores de serviço de dados personalizados](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
2.  **Crie o serviço de dados.** O serviço de dados mais básico expõe uma classe herdada da classe <xref:System.Data.Services.DataService%601>, com um tipo `T` que é o nome qualificado para namespace do contêiner de entidade. Para obter mais informações, consulte [definindo o WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
3.  **Configure o serviço de dados.** Por padrão, o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] desativa o acesso a recursos que são expostos por um contêiner de entidade. O <xref:System.Data.Services.DataServiceConfiguration> interface permite que você configure o acesso a recursos e operações de serviço, especifique a versão com suporte do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]e para definir outros comportamentos de todo o serviço, como o envio em lote comportamentos ou o número máximo de entidades que podem retornado em uma única resposta. Para obter mais informações, consulte [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Para obter um exemplo de como criar um serviço de dados simples com base no banco de dados de exemplo Northwind, consulte [Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [Visão geral](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)
