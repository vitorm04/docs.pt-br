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
# <a name="feed-formatter-json"></a><span data-ttu-id="ea983-102">Formatador do feed (JSON)</span><span class="sxs-lookup"><span data-stu-id="ea983-102">Feed Formatter (JSON)</span></span>
<span data-ttu-id="ea983-103">Esta amostra mostra como serializar <xref:System.ServiceModel.Syndication.SyndicationFeed> uma instância de uma classe no formato JSON <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> (JavaScript Object Notation, notação de objeto sumido) usando um personalizado e o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ea983-103">This sample shows how to serialize an instance of a <xref:System.ServiceModel.Syndication.SyndicationFeed> class in JavaScript Object Notation (JSON) format by using a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> and the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="architecture-of-the-sample"></a><span data-ttu-id="ea983-104">Arquitetura da Amostra</span><span class="sxs-lookup"><span data-stu-id="ea983-104">Architecture of the Sample</span></span>  
 <span data-ttu-id="ea983-105">A amostra implementa `JsonFeedFormatter` uma classe <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>nomeada que herda de .</span><span class="sxs-lookup"><span data-stu-id="ea983-105">The sample implements a class named `JsonFeedFormatter` that inherits from <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="ea983-106">A `JsonFeedFormatter` classe conta <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> com a leitura e gravação dos dados no formato JSON.</span><span class="sxs-lookup"><span data-stu-id="ea983-106">The `JsonFeedFormatter` class relies on the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to read and write the data in JSON format.</span></span> <span data-ttu-id="ea983-107">Internamente, o formatter usa um conjunto `JsonSyndicationFeed` personalizado `JsonSyndicationItem` de tipos de contrato de dados nomeados e para controlar o formato dos dados JSON produzidos pelo serializador.</span><span class="sxs-lookup"><span data-stu-id="ea983-107">Internally, the formatter uses a custom set of data contract types named `JsonSyndicationFeed` and `JsonSyndicationItem` to control the format of the JSON data produced by the serializer.</span></span> <span data-ttu-id="ea983-108">Esses detalhes de implementação são escondidos do usuário <xref:System.ServiceModel.Syndication.SyndicationFeed> final, permitindo que chamadas sejam feitas contra o padrão e <xref:System.ServiceModel.Syndication.SyndicationItem> as classes.</span><span class="sxs-lookup"><span data-stu-id="ea983-108">These implementation details are hidden from the end user, allowing calls to be made against the standard <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> classes.</span></span>  
  
## <a name="writing-json-feeds"></a><span data-ttu-id="ea983-109">Escrevendo feeds JSON</span><span class="sxs-lookup"><span data-stu-id="ea983-109">Writing JSON feeds</span></span>  
 <span data-ttu-id="ea983-110">A escrita de uma ração JSON pode ser realizada usando o `JsonFeedFormatter` (implementado nesta amostra) com o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="ea983-110">Writing a JSON feed can be accomplished by using the `JsonFeedFormatter` (implemented in this sample) with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> as shown in the following sample code.</span></span>  
  
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
  
## <a name="reading-a-json-feed"></a><span data-ttu-id="ea983-111">Lendo um feed JSON</span><span class="sxs-lookup"><span data-stu-id="ea983-111">Reading a JSON feed</span></span>  
 <span data-ttu-id="ea983-112">A <xref:System.ServiceModel.Syndication.SyndicationFeed> obtenção de um fluxo de dados formatados `JsonFeedFormatter` pelo JSON pode ser realizada com o como mostrar no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ea983-112">Obtaining a <xref:System.ServiceModel.Syndication.SyndicationFeed> from a stream of JSON-formatted data can be accomplished with the `JsonFeedFormatter` as show in the following code.</span></span>  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ea983-113">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ea983-113">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ea983-114">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea983-114">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ea983-115">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea983-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ea983-116">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea983-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ea983-117">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ea983-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ea983-118">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ea983-118">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ea983-119">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="ea983-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ea983-120">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ea983-120">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
