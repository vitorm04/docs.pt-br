---
title: Exemplo de Streaming Feeds
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 7a887fa1eceac4d8ee323f03fd5bc536bb1dc579
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143961"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="5298b-102">Exemplo de Streaming Feeds</span><span class="sxs-lookup"><span data-stu-id="5298b-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="5298b-103">Esta amostra demonstra como gerenciar feeds de sindicalização que contêm um grande número de itens.</span><span class="sxs-lookup"><span data-stu-id="5298b-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="5298b-104">No servidor, a amostra demonstra como retardar <xref:System.ServiceModel.Syndication.SyndicationItem> a criação de objetos individuais no feed até imediatamente antes de o item ser gravado no fluxo de rede.</span><span class="sxs-lookup"><span data-stu-id="5298b-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="5298b-105">No cliente, a amostra mostra como um feed de sindicância personalizado pode ser usado para ler itens individuais do fluxo de rede para que o feed que está sendo lido nunca seja totalmente tamponado na memória.</span><span class="sxs-lookup"><span data-stu-id="5298b-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="5298b-106">Para demonstrar melhor a capacidade de streaming da API de sindicância, esta amostra usa um cenário um tanto improvável no qual o servidor expõe um feed que contém um número infinito de itens.</span><span class="sxs-lookup"><span data-stu-id="5298b-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="5298b-107">Neste caso, o servidor continua gerando novos itens no feed até determinar que o cliente leu um número especificado de itens da alimentação (por padrão, 10).</span><span class="sxs-lookup"><span data-stu-id="5298b-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="5298b-108">Para simplificar, tanto o cliente quanto o servidor são implementados `ItemCounter` no mesmo processo e usam um objeto compartilhado para acompanhar quantos itens o cliente produziu.</span><span class="sxs-lookup"><span data-stu-id="5298b-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="5298b-109">O `ItemCounter` tipo existe apenas com o propósito de permitir que o cenário amostral termine de forma limpa, e não é um elemento central do padrão que está sendo demonstrado.</span><span class="sxs-lookup"><span data-stu-id="5298b-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="5298b-110">A demonstração faz uso de iteradores `yield return` Visual C# (usando a palavra-chave construa).</span><span class="sxs-lookup"><span data-stu-id="5298b-110">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="5298b-111">Para obter mais informações sobre os iterizadores, consulte o tópico "Usando Iteradores" no MSDN.</span><span class="sxs-lookup"><span data-stu-id="5298b-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="5298b-112">Serviço</span><span class="sxs-lookup"><span data-stu-id="5298b-112">Service</span></span>  
 <span data-ttu-id="5298b-113">O serviço implementa <xref:System.ServiceModel.Web.WebGetAttribute> um contrato básico que consiste em uma operação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5298b-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="5298b-114">O serviço implementa este `ItemGenerator` contrato usando uma classe <xref:System.ServiceModel.Syndication.SyndicationItem> para criar um fluxo potencialmente infinito de instâncias usando um iterizador, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5298b-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
```csharp
class ItemGenerator  
{  
    public IEnumerable<SyndicationItem> GenerateItems()  
    {  
        while (counter.GetCount() < maxItemsRead)  
        {  
            itemsReturned++;  
            yield return CreateNextItem();  
        }  
  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="5298b-115">Quando a implementação do serviço `ItemGenerator.GenerateItems()` cria o feed, a saída é usada em vez de uma coleção tampão de itens.</span><span class="sxs-lookup"><span data-stu-id="5298b-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
```csharp
public Atom10FeedFormatter StreamedFeed()  
{  
    SyndicationFeed feed = new SyndicationFeed("Streamed feed", "Feed to test streaming", null);  
    //Generate an infinite stream of items. Both the client and the service share  
    //a reference to the ItemCounter, which allows the sample to terminate  
    //execution after the client has read 10 items from the stream  
    ItemGenerator itemGenerator = new ItemGenerator(this.counter, 10);  
  
    feed.Items = itemGenerator.GenerateItems();  
    return feed.GetAtom10Formatter();  
}  
```  
  
 <span data-ttu-id="5298b-116">Como resultado, o fluxo de itens nunca é totalmente tamponado na memória.</span><span class="sxs-lookup"><span data-stu-id="5298b-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="5298b-117">Você pode observar esse comportamento definindo `yield return` um ponto `ItemGenerator.GenerateItems()` de ruptura na declaração dentro do método e observando que esse `StreamedFeed()` ponto de ruptura é encontrado pela primeira vez após o serviço ter retornado o resultado do método.</span><span class="sxs-lookup"><span data-stu-id="5298b-117">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="5298b-118">Cliente</span><span class="sxs-lookup"><span data-stu-id="5298b-118">Client</span></span>  
 <span data-ttu-id="5298b-119">O cliente nesta amostra <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> usa uma implementação personalizada que atrasa a materialização de itens individuais no feed em vez de tamponá-los na memória.</span><span class="sxs-lookup"><span data-stu-id="5298b-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="5298b-120">A `StreamedAtom10FeedFormatter` instância personalizada é usada da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="5298b-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="5298b-121">Normalmente, uma <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> chamada não retorna até que todo o conteúdo do feed tenha sido lido da rede e tamponado na memória.</span><span class="sxs-lookup"><span data-stu-id="5298b-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="5298b-122">No entanto, `StreamedAtom10FeedFormatter` <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> o objeto substitui-se para retornar um iterator em vez de uma coleção tamponada, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5298b-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
```csharp  
protected override IEnumerable<SyndicationItem> ReadItems(XmlReader reader, SyndicationFeed feed, out bool areAllItemsRead)  
{  
    areAllItemsRead = false;  
    return DelayReadItems(reader, feed);  
}  
  
private IEnumerable<SyndicationItem> DelayReadItems(XmlReader reader, SyndicationFeed feed)  
{  
    while (reader.IsStartElement("entry", "http://www.w3.org/2005/Atom"))  
    {  
        yield return this.ReadItem(reader, feed);  
    }  
  
    reader.ReadEndElement();  
}  
```  
  
 <span data-ttu-id="5298b-123">Como resultado, cada item não é lido da rede até `ReadItems()` que o aplicativo cliente que atravessa os resultados esteja pronto para usá-lo.</span><span class="sxs-lookup"><span data-stu-id="5298b-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="5298b-124">Você pode observar esse comportamento definindo `yield return` um `StreamedAtom10FeedFormatter.DelayReadItems()` ponto de ruptura na declaração dentro de e `ReadFrom()` percebendo que esse ponto de ruptura é encontrado pela primeira vez após a chamada ser concluída.</span><span class="sxs-lookup"><span data-stu-id="5298b-124">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="5298b-125">As instruções a seguir mostram como construir e executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="5298b-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="5298b-126">Observe que, embora o servidor pare de gerar itens depois que o cliente leu 10 itens, a saída mostra que o cliente lê significativamente mais de 10 itens.</span><span class="sxs-lookup"><span data-stu-id="5298b-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="5298b-127">Isso porque a ligação de rede utilizada pela amostra transmite dados em segmentos de quatro quilobytes (KB).</span><span class="sxs-lookup"><span data-stu-id="5298b-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="5298b-128">Como tal, o cliente recebe 4KB de dados de itens antes de ter a oportunidade de ler até mesmo um item.</span><span class="sxs-lookup"><span data-stu-id="5298b-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="5298b-129">Este é um comportamento normal (o envio de dados HTTP transmitidos em segmentos de tamanho razoável aumenta o desempenho).</span><span class="sxs-lookup"><span data-stu-id="5298b-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5298b-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5298b-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5298b-131">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5298b-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5298b-132">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5298b-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5298b-133">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5298b-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5298b-134">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5298b-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5298b-135">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5298b-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5298b-136">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="5298b-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5298b-137">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5298b-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="5298b-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="5298b-138">See also</span></span>

- [<span data-ttu-id="5298b-139">Feed de diagnóstico independente</span><span class="sxs-lookup"><span data-stu-id="5298b-139">Stand-Alone Diagnostics Feed</span></span>](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
