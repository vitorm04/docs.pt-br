---
title: Formatador do feed (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 46328034c3867cd2af598b41bd71f23d7594e0e9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814647"
---
# <a name="feed-formatter-json"></a>Formatador do feed (JSON)
Este exemplo mostra como serializar uma instância de um <xref:System.ServiceModel.Syndication.SyndicationFeed> classe no formato de notação JSON (JavaScript Object) usando uma personalização <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> e o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="architecture-of-the-sample"></a>Arquitetura do exemplo  
 O exemplo implementa uma classe chamada `JsonFeedFormatter` que herda de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. O `JsonFeedFormatter` classe depende o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> para ler e gravar os dados no formato JSON. Internamente, o formatador utiliza um conjunto personalizado de tipos de contrato de dados denominado `JsonSyndicationFeed` e `JsonSyndicationItem` para controlar o formato dos dados JSON produzidos pelo serializador. Esses detalhes de implementação são ocultados do usuário final, que permite chamadas sejam feitas em relação ao padrão <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem> classes.  
  
## <a name="writing-json-feeds"></a>Gravando JSON feeds  
 Gravar um feed JSON pode ser feito usando o `JsonFeedFormatter` (implementado neste exemplo) com o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> conforme mostrado no código de exemplo a seguir.  
  
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
  
## <a name="reading-a-json-feed"></a>Leitura de um feed JSON  
 Como obter um <xref:System.ServiceModel.Syndication.SyndicationFeed> de um fluxo da JSON formatado de dados pode ser feito com o `JsonFeedFormatter` conforme mostrado no código a seguir.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
  
