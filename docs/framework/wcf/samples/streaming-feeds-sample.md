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
# <a name="streaming-feeds-sample"></a>Exemplo de Streaming Feeds
Esta amostra demonstra como gerenciar feeds de sindicalização que contêm um grande número de itens. No servidor, a amostra demonstra como retardar <xref:System.ServiceModel.Syndication.SyndicationItem> a criação de objetos individuais no feed até imediatamente antes de o item ser gravado no fluxo de rede.  
  
 No cliente, a amostra mostra como um feed de sindicância personalizado pode ser usado para ler itens individuais do fluxo de rede para que o feed que está sendo lido nunca seja totalmente tamponado na memória.  
  
 Para demonstrar melhor a capacidade de streaming da API de sindicância, esta amostra usa um cenário um tanto improvável no qual o servidor expõe um feed que contém um número infinito de itens. Neste caso, o servidor continua gerando novos itens no feed até determinar que o cliente leu um número especificado de itens da alimentação (por padrão, 10). Para simplificar, tanto o cliente quanto o servidor são implementados `ItemCounter` no mesmo processo e usam um objeto compartilhado para acompanhar quantos itens o cliente produziu. O `ItemCounter` tipo existe apenas com o propósito de permitir que o cenário amostral termine de forma limpa, e não é um elemento central do padrão que está sendo demonstrado.  
  
 A demonstração faz uso de iteradores `yield return` Visual C# (usando a palavra-chave construa). Para obter mais informações sobre os iterizadores, consulte o tópico "Usando Iteradores" no MSDN.  
  
## <a name="service"></a>Serviço  
 O serviço implementa <xref:System.ServiceModel.Web.WebGetAttribute> um contrato básico que consiste em uma operação, conforme mostrado no código a seguir.  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 O serviço implementa este `ItemGenerator` contrato usando uma classe <xref:System.ServiceModel.Syndication.SyndicationItem> para criar um fluxo potencialmente infinito de instâncias usando um iterizador, como mostrado no código a seguir.  
  
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
  
 Quando a implementação do serviço `ItemGenerator.GenerateItems()` cria o feed, a saída é usada em vez de uma coleção tampão de itens.  
  
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
  
 Como resultado, o fluxo de itens nunca é totalmente tamponado na memória. Você pode observar esse comportamento definindo `yield return` um ponto `ItemGenerator.GenerateItems()` de ruptura na declaração dentro do método e observando que esse `StreamedFeed()` ponto de ruptura é encontrado pela primeira vez após o serviço ter retornado o resultado do método.  
  
## <a name="client"></a>Cliente  
 O cliente nesta amostra <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> usa uma implementação personalizada que atrasa a materialização de itens individuais no feed em vez de tamponá-los na memória. A `StreamedAtom10FeedFormatter` instância personalizada é usada da seguinte forma.  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Normalmente, uma <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> chamada não retorna até que todo o conteúdo do feed tenha sido lido da rede e tamponado na memória. No entanto, `StreamedAtom10FeedFormatter` <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> o objeto substitui-se para retornar um iterator em vez de uma coleção tamponada, como mostrado no código a seguir.  
  
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
  
 Como resultado, cada item não é lido da rede até `ReadItems()` que o aplicativo cliente que atravessa os resultados esteja pronto para usá-lo. Você pode observar esse comportamento definindo `yield return` um `StreamedAtom10FeedFormatter.DelayReadItems()` ponto de ruptura na declaração dentro de e `ReadFrom()` percebendo que esse ponto de ruptura é encontrado pela primeira vez após a chamada ser concluída.  
  
 As instruções a seguir mostram como construir e executar a amostra. Observe que, embora o servidor pare de gerar itens depois que o cliente leu 10 itens, a saída mostra que o cliente lê significativamente mais de 10 itens. Isso porque a ligação de rede utilizada pela amostra transmite dados em segmentos de quatro quilobytes (KB). Como tal, o cliente recebe 4KB de dados de itens antes de ter a oportunidade de ler até mesmo um item. Este é um comportamento normal (o envio de dados HTTP transmitidos em segmentos de tamanho razoável aumenta o desempenho).  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Confira também

- [Feed de diagnóstico independente](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
