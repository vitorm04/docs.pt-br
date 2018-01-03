---
title: "Gerando a biblioteca do cliente de serviço de dados (serviços de dados WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6adbaafe170cf3f5398677d5df3b3d2ff0a95abe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Gerando a biblioteca do cliente de serviço de dados (serviços de dados WCF)
Um serviço de dados que implementa o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] pode retornar um documento de metadados de serviço que descreve o modelo de dados exposto pelo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed. Para obter mais informações, consulte [OData: documento de metadados de serviço](http://go.microsoft.com/fwlink/?LinkId=186070). Você pode usar o **adicionar referência de serviço** caixa de diálogo no Visual Studio para adicionar uma referência a um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-com base em serviço. Quando você usar essa ferramenta para adicionar uma referência para os metadados retornados por uma [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed em um projeto de cliente, ele executa as seguintes ações:  
  
-   Solicita o documento de metadados de serviço do serviço de dados e interpreta os metadados retornados.  
  
    > [!NOTE]
    >  Os metadados retornados são armazenados no projeto do cliente como um arquivo. edmx. Este arquivo .edmx não pode ser aberto usando o Designer de Modelo de Dados de Entidade porque não tem o mesmo formato que um arquivo .edmx usado pelo Entity Framework. Você pode exibir esse arquivo de metadados usando o Editor de XML ou qualquer outro editor de texto. Para obter mais informações, consulte o [ \[MC EDMX\]: modelo de dados de entidade para formato de empacotamento de serviços de dados](http://go.microsoft.com/fwlink/?LinkID=178833) especificação  
  
-   Gera uma representação do serviço como uma classe do contêiner de entidade que herda de <xref:System.Data.Services.Client.DataServiceContext>. Essa classe do contêiner de entidade gerada parece o contêiner de entidade que as ferramentas de Modelo de Dados de Entidade geram. Para obter mais informações, consulte [visão geral dos serviços de objeto (Entity Framework)](http://msdn.microsoft.com/en-us/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
-   Gera classes de dados para os tipos de modelo de dados que ela descobre nos metadados de serviço.  
  
-   Adiciona uma referência ao assembly do `System.Data.Services.Client` ao projeto.  
  
 Para obter mais informações, consulte [como: adicionar uma referência de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 As classes de serviço de dados do cliente também podem ser geradas usando o [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) ferramenta de prompt de comando. Para obter mais informações, consulte [como: manualmente gerar cliente dados Classes de serviço](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>Mapeamento de tipo de dados de cliente  
 Quando você usa o **adicionar referência de serviço** diálogo no Visual Studio ou o `DataSvcUtil.exe` ferramenta para gerar classes de dados do cliente com base em um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, os tipos de dados do .NET Framework são mapeados para os tipos primitivos das modelo de dados da seguinte maneira:  
  
|Tipo do modelo de dados|Tipo de dados do .NET Framework|  
|---------------------|------------------------------|  
|`Edm.Binary`|<xref:System.Byte> `[]`|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 Para obter mais informações, consulte [OData: tipos de dados primitivos](http://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Consulte também  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)  
 [Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)
