---
title: Formatador do feed (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 350e07ad37b09f39fc709e20d8f73a41f9d01f30
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183645"
---
# <a name="feed-formatter-json"></a>Formatador do feed (JSON)
Esta amostra mostra como serializar <xref:System.ServiceModel.Syndication.SyndicationFeed> uma instância de uma classe no formato JSON <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> (JavaScript Object Notation, notação de objeto sumido) usando um personalizado e o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="architecture-of-the-sample"></a>Arquitetura da Amostra  
 A amostra implementa `JsonFeedFormatter` uma classe <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>nomeada que herda de . A `JsonFeedFormatter` classe conta <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> com a leitura e gravação dos dados no formato JSON. Internamente, o formatter usa um conjunto `JsonSyndicationFeed` personalizado `JsonSyndicationItem` de tipos de contrato de dados nomeados e para controlar o formato dos dados JSON produzidos pelo serializador. Esses detalhes de implementação são escondidos do usuário <xref:System.ServiceModel.Syndication.SyndicationFeed> final, permitindo que chamadas sejam feitas contra o padrão e <xref:System.ServiceModel.Syndication.SyndicationItem> as classes.  
  
## <a name="writing-json-feeds"></a>Escrevendo feeds JSON  
 A escrita de uma ração JSON pode ser realizada usando o `JsonFeedFormatter` (implementado nesta amostra) com o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> mostrado no código de amostra a seguir.  
  
```csharp  
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
 A <xref:System.ServiceModel.Syndication.SyndicationFeed> obtenção de um fluxo de dados formatados `JsonFeedFormatter` pelo JSON pode ser realizada com o como mostrar no código a seguir.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
