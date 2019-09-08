---
title: Gerando a biblioteca do cliente de serviço de dados (serviços de dados WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: d53f2d209d6fb0a6f3cadb96245338060ece87db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780295"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Gerando a biblioteca do cliente de serviço de dados (serviços de dados WCF)
Um serviço de dados que implementa [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] o pode retornar um documento de metadados de serviço que descreve o modelo de [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] dados exposto pelo feed. Para obter mais informações, [consulte OData: Documento](https://go.microsoft.com/fwlink/?LinkId=186070)de metadados de serviço. Você pode usar a caixa de diálogo **Adicionar referência de serviço** no Visual Studio para adicionar uma referência [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]a um serviço baseado em. Quando você usa essa ferramenta para adicionar uma referência aos metadados retornados por um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed em um projeto de cliente, ele executa as seguintes ações:  
  
- Solicita o documento de metadados de serviço do serviço de dados e interpreta os metadados retornados.  
  
    > [!NOTE]
    > Os metadados retornados são armazenados no projeto do cliente como um arquivo. edmx. Este arquivo .edmx não pode ser aberto usando o Designer de Modelo de Dados de Entidade porque não tem o mesmo formato que um arquivo .edmx usado pelo Entity Framework. Você pode exibir esse arquivo de metadados usando o Editor de XML ou qualquer outro editor de texto. Para obter mais informações, consulte [o \[MC-\]edmx: Modelo de dados de entidade para especificação de formato](https://go.microsoft.com/fwlink/?LinkID=178833) de empacotamento de serviços de dados  
  
- Gera uma representação do serviço como uma classe do contêiner de entidade que herda de <xref:System.Data.Services.Client.DataServiceContext>. Essa classe do contêiner de entidade gerada parece o contêiner de entidade que as ferramentas de Modelo de Dados de Entidade geram. Para obter mais informações, consulte [Visão geral dos serviços de objeto (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
- Gera classes de dados para os tipos de modelo de dados que ela descobre nos metadados de serviço.  
  
- Adiciona uma referência ao assembly do `System.Data.Services.Client` ao projeto.  
  
 Para obter mais informações, confira [Como: Adicione uma referência](how-to-add-a-data-service-reference-wcf-data-services.md)de serviço de dados.  
  
 As classes de serviço de dados do cliente também podem ser geradas usando a ferramenta [datasvcutil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) no prompt de comando. Para obter mais informações, confira [Como: Gerar manualmente classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)de serviço de dados do cliente.  
  
## <a name="client-data-type-mapping"></a>Mapeamento de tipo de dados de cliente  
 Quando você usa a caixa de diálogo **Adicionar referência de serviço** no Visual Studio `DataSvcUtil.exe` ou a ferramenta para gerar classes de dados de cliente baseadas [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] em um feed, os tipos de dados .NET Framework são mapeados para os tipos primitivos do modelo de dados da seguinte maneira:  
  
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
  
 Para obter mais informações, [consulte OData: Tipos](https://go.microsoft.com/fwlink/?LinkId=186072)de dados primitivos.  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
- [Quickstart](quickstart-wcf-data-services.md) (Início rápido)
