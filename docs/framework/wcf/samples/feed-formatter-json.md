---
title: Formatador do feed (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 028d2f9abd7e23f18eb90e5ecae8c57da3a871d1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039651"
---
# <a name="feed-formatter-json"></a>Formatador do feed (JSON)
Este exemplo mostra como serializar uma instância de uma <xref:System.ServiceModel.Syndication.SyndicationFeed> classe no formato JavaScript Object Notation (JSON) usando um personalizado <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> e o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="architecture-of-the-sample"></a>Arquitetura do exemplo  
 O exemplo implementa uma classe denominada `JsonFeedFormatter` herdada de. <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> A `JsonFeedFormatter` classe depende do <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> para ler e gravar os dados no formato JSON. Internamente, o formatador usa um conjunto personalizado de tipos de contrato `JsonSyndicationFeed` de `JsonSyndicationItem` dados denominados e para controlar o formato dos dados JSON produzidos pelo serializador. Esses detalhes de implementação ficam ocultos do usuário final, permitindo que as chamadas sejam feitas em <xref:System.ServiceModel.Syndication.SyndicationFeed> relação <xref:System.ServiceModel.Syndication.SyndicationItem> ao padrão e às classes.  
  
## <a name="writing-json-feeds"></a>Gravando feeds JSON  
 A gravação de um feed JSON pode ser realizada usando `JsonFeedFormatter` o (implementado neste exemplo) com o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , conforme mostrado no código de exemplo a seguir.  
  
```  
//Basic feed with sample data  
SyndicationFeed feed = new SyndicationFeed("Custom JSON feed", "A Syndication extensibility sample", null);  
feed.LastUpdatedTime = DateTime.Now;  
feed.Items = from s in new string[] { "hello", "world" }  
select new SyndicationItem()  
{  
    Summary = SyndicationContent.CreatePlaintextContent(s)  
};  
  
//Write the feed out to a MemoryStream in JSON format  
DataContractJsonSerializer writeSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));  
writeSerializer.WriteObject(stream, new JsonFeedFormatter(feed));  
```  
  
## <a name="reading-a-json-feed"></a>Lendo um feed JSON  
 Obter um <xref:System.ServiceModel.Syndication.SyndicationFeed> de um fluxo de dados formatados em JSON pode ser feito com `JsonFeedFormatter` o como mostrado no código a seguir.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
