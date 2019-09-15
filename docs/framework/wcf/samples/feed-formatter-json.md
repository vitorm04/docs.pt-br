---
title: Formatador do feed (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 516a114ee577597611c14ce10ad838d85d6a0fb1
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989898"
---
# <a name="feed-formatter-json"></a><span data-ttu-id="f00b3-102">Formatador do feed (JSON)</span><span class="sxs-lookup"><span data-stu-id="f00b3-102">Feed Formatter (JSON)</span></span>
<span data-ttu-id="f00b3-103">Este exemplo mostra como serializar uma instância de uma <xref:System.ServiceModel.Syndication.SyndicationFeed> classe no formato JavaScript Object Notation (JSON) usando um personalizado <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> e o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f00b3-103">This sample shows how to serialize an instance of a <xref:System.ServiceModel.Syndication.SyndicationFeed> class in JavaScript Object Notation (JSON) format by using a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> and the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="architecture-of-the-sample"></a><span data-ttu-id="f00b3-104">Arquitetura do exemplo</span><span class="sxs-lookup"><span data-stu-id="f00b3-104">Architecture of the Sample</span></span>  
 <span data-ttu-id="f00b3-105">O exemplo implementa uma classe denominada `JsonFeedFormatter` herdada de. <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter></span><span class="sxs-lookup"><span data-stu-id="f00b3-105">The sample implements a class named `JsonFeedFormatter` that inherits from <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="f00b3-106">A `JsonFeedFormatter` classe depende do <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> para ler e gravar os dados no formato JSON.</span><span class="sxs-lookup"><span data-stu-id="f00b3-106">The `JsonFeedFormatter` class relies on the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to read and write the data in JSON format.</span></span> <span data-ttu-id="f00b3-107">Internamente, o formatador usa um conjunto personalizado de tipos de contrato `JsonSyndicationFeed` de `JsonSyndicationItem` dados denominados e para controlar o formato dos dados JSON produzidos pelo serializador.</span><span class="sxs-lookup"><span data-stu-id="f00b3-107">Internally, the formatter uses a custom set of data contract types named `JsonSyndicationFeed` and `JsonSyndicationItem` to control the format of the JSON data produced by the serializer.</span></span> <span data-ttu-id="f00b3-108">Esses detalhes de implementação ficam ocultos do usuário final, permitindo que as chamadas sejam feitas em <xref:System.ServiceModel.Syndication.SyndicationFeed> relação <xref:System.ServiceModel.Syndication.SyndicationItem> ao padrão e às classes.</span><span class="sxs-lookup"><span data-stu-id="f00b3-108">These implementation details are hidden from the end user, allowing calls to be made against the standard <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> classes.</span></span>  
  
## <a name="writing-json-feeds"></a><span data-ttu-id="f00b3-109">Gravando feeds JSON</span><span class="sxs-lookup"><span data-stu-id="f00b3-109">Writing JSON feeds</span></span>  
 <span data-ttu-id="f00b3-110">A gravação de um feed JSON pode ser realizada usando `JsonFeedFormatter` o (implementado neste exemplo) com o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f00b3-110">Writing a JSON feed can be accomplished by using the `JsonFeedFormatter` (implemented in this sample) with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> as shown in the following sample code.</span></span>  
  
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
  
## <a name="reading-a-json-feed"></a><span data-ttu-id="f00b3-111">Lendo um feed JSON</span><span class="sxs-lookup"><span data-stu-id="f00b3-111">Reading a JSON feed</span></span>  
 <span data-ttu-id="f00b3-112">Obter um <xref:System.ServiceModel.Syndication.SyndicationFeed> de um fluxo de dados formatados em JSON pode ser feito com `JsonFeedFormatter` o como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f00b3-112">Obtaining a <xref:System.ServiceModel.Syndication.SyndicationFeed> from a stream of JSON-formatted data can be accomplished with the `JsonFeedFormatter` as show in the following code.</span></span>  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f00b3-113">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f00b3-113">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f00b3-114">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f00b3-114">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f00b3-115">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f00b3-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f00b3-116">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f00b3-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f00b3-117">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f00b3-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f00b3-118">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f00b3-118">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f00b3-119">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="f00b3-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f00b3-120">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f00b3-120">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
