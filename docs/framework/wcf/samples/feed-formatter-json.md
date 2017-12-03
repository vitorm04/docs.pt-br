---
title: Formatador do feed (JSON)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c9ce141c2292d4afe6900aba93c972b63abb2056
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="feed-formatter-json"></a>Formatador do feed (JSON)
Este exemplo mostra como serializar uma instância de um <xref:System.ServiceModel.Syndication.SyndicationFeed> classe no formato de notação JSON (JavaScript Object) usando um personalizado <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="architecture-of-the-sample"></a>Arquitetura do exemplo  
 O exemplo implementa uma classe denominada `JsonFeedFormatter` que herda de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. O `JsonFeedFormatter` classe depende de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> para ler e gravar os dados no formato JSON. Internamente, o formatador usa um conjunto personalizado de tipos de contrato de dados denominado `JsonSyndicationFeed` e `JsonSyndicationItem` para controlar o formato dos dados JSON produzidos pelo serializador. Esses detalhes de implementação estão ocultos do usuário final, permitindo que chama a ser feita em relação ao padrão <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem> classes.  
  
## <a name="writing-json-feeds"></a>Feeds JSON de gravação  
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
  
## <a name="reading-a-json-feed"></a>Ler um feed JSON  
 Obtendo um <xref:System.ServiceModel.Syndication.SyndicationFeed> de um fluxo de JSON formatado de dados pode ser feito com o `JsonFeedFormatter` como mostrar no código a seguir.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
  
## <a name="see-also"></a>Consulte também
