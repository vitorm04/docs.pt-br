---
title: Exemplo de Streaming Feeds
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: f37e7791bc407a57432fb9f6900ad8f19ff4eb52
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044686"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="4767f-102">Exemplo de Streaming Feeds</span><span class="sxs-lookup"><span data-stu-id="4767f-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="4767f-103">Este exemplo demonstra como gerenciar feeds de distribuição que contêm um grande número de itens.</span><span class="sxs-lookup"><span data-stu-id="4767f-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="4767f-104">No servidor, o exemplo demonstra como atrasar a criação de objetos individuais <xref:System.ServiceModel.Syndication.SyndicationItem> no feed até imediatamente antes que o item seja gravado no fluxo de rede.</span><span class="sxs-lookup"><span data-stu-id="4767f-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="4767f-105">No cliente, o exemplo mostra como um formatador de feed de agregação personalizado pode ser usado para ler itens individuais do fluxo de rede para que o feed que está sendo lido nunca seja totalmente armazenado em buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="4767f-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="4767f-106">Para demonstrar melhor o recurso de streaming da API de distribuição, este exemplo usa um cenário um pouco improvável, no qual o servidor expõe um feed que contém um número infinito de itens.</span><span class="sxs-lookup"><span data-stu-id="4767f-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="4767f-107">Nesse caso, o servidor continua gerando novos itens no feed até determinar que o cliente leu um número especificado de itens do feed (por padrão, 10).</span><span class="sxs-lookup"><span data-stu-id="4767f-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="4767f-108">Para simplificar, o cliente e o servidor são implementados no mesmo processo e usam um objeto `ItemCounter` compartilhado para controlar quantos itens o cliente produziu.</span><span class="sxs-lookup"><span data-stu-id="4767f-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="4767f-109">O `ItemCounter` tipo existe somente para permitir que o cenário de exemplo seja encerrado corretamente e não seja um elemento básico do padrão que está sendo demonstrado.</span><span class="sxs-lookup"><span data-stu-id="4767f-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="4767f-110">A demonstração usa iteradores visuais C# (usando a construção de `yield return` palavra-chave).</span><span class="sxs-lookup"><span data-stu-id="4767f-110">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="4767f-111">Para obter mais informações sobre iteradores, consulte o tópico "usando iteradores" no MSDN.</span><span class="sxs-lookup"><span data-stu-id="4767f-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="4767f-112">Serviço</span><span class="sxs-lookup"><span data-stu-id="4767f-112">Service</span></span>  
 <span data-ttu-id="4767f-113">O serviço implementa um contrato <xref:System.ServiceModel.Web.WebGetAttribute> básico que consiste em uma operação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4767f-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="4767f-114">O serviço implementa esse contrato usando uma `ItemGenerator` classe para criar um fluxo potencialmente infinito de <xref:System.ServiceModel.Syndication.SyndicationItem> instâncias usando um iterador, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4767f-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="4767f-115">Quando a implementação do serviço cria o feed, a saída `ItemGenerator.GenerateItems()` do é usada em vez de uma coleção de itens em buffer.</span><span class="sxs-lookup"><span data-stu-id="4767f-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
```  
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
  
 <span data-ttu-id="4767f-116">Como resultado, o fluxo de itens nunca é totalmente armazenado em buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="4767f-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="4767f-117">Você pode observar esse comportamento definindo um ponto de interrupção na `yield return` instrução dentro `ItemGenerator.GenerateItems()` do método e observando que esse ponto de interrupção é encontrado pela primeira vez após o serviço ter `StreamedFeed()` retornado o resultado do método.</span><span class="sxs-lookup"><span data-stu-id="4767f-117">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="4767f-118">Cliente</span><span class="sxs-lookup"><span data-stu-id="4767f-118">Client</span></span>  
 <span data-ttu-id="4767f-119">O cliente neste exemplo usa uma implementação personalizada <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> que atrasa a materialização de itens individuais no feed em vez de armazenar em buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="4767f-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="4767f-120">A instância `StreamedAtom10FeedFormatter` personalizada é usada da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="4767f-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="4767f-121">Normalmente, uma chamada para <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> não retorna até que todo o conteúdo do feed tenha sido lido da rede e armazenado em buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="4767f-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="4767f-122">No entanto `StreamedAtom10FeedFormatter` , o <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> objeto substitui para retornar um iterador em vez de uma coleção em buffer, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4767f-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="4767f-123">Como resultado, cada item não é lido da rede até que o aplicativo cliente que atravessa os resultados `ReadItems()` esteja pronto para usá-lo.</span><span class="sxs-lookup"><span data-stu-id="4767f-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="4767f-124">Você pode observar esse comportamento definindo um ponto de interrupção na `yield return` instrução dentro de `StreamedAtom10FeedFormatter.DelayReadItems()` e percebendo que esse ponto de interrupção é encontrado pela primeira vez após a chamada `ReadFrom()` a ser concluída.</span><span class="sxs-lookup"><span data-stu-id="4767f-124">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="4767f-125">As instruções a seguir mostram como compilar e executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="4767f-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="4767f-126">Observe que, embora o servidor pare de gerar itens depois que o cliente leu 10 itens, a saída mostra que o cliente lê significativamente mais de 10 itens.</span><span class="sxs-lookup"><span data-stu-id="4767f-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="4767f-127">Isso ocorre porque a associação de rede usada pelo exemplo transmite dados em segmentos de quatro kilobytes (KB).</span><span class="sxs-lookup"><span data-stu-id="4767f-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="4767f-128">Como tal, o cliente recebe 4 KB de dados do item antes de ter a oportunidade de ler até mesmo um item.</span><span class="sxs-lookup"><span data-stu-id="4767f-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="4767f-129">Esse comportamento é normal (o envio de dados HTTP transmitidos em segmentos de tamanho razoável aumenta o desempenho).</span><span class="sxs-lookup"><span data-stu-id="4767f-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4767f-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4767f-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4767f-131">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4767f-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4767f-132">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4767f-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4767f-133">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4767f-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4767f-134">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4767f-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4767f-135">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4767f-135">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="4767f-136">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="4767f-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4767f-137">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4767f-137">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="4767f-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4767f-138">See also</span></span>

- [<span data-ttu-id="4767f-139">Feed de diagnóstico independente</span><span class="sxs-lookup"><span data-stu-id="4767f-139">Stand-Alone Diagnostics Feed</span></span>](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
