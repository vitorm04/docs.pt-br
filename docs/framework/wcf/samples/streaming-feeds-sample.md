---
title: Exemplo de Streaming Feeds
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 17639273ece804dc531cbbc3ab9135c814ea632d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486575"
---
# <a name="streaming-feeds-sample"></a>Exemplo de Streaming Feeds
Este exemplo demonstra como gerenciar feeds de agregação que contêm um grande número de itens. No servidor, o exemplo demonstra como atrasar a criação de um indivíduo <xref:System.ServiceModel.Syndication.SyndicationItem> objetos dentro do feed até imediatamente antes que o item seja gravado no fluxo de rede.  
  
 No cliente, o exemplo mostra como um formatador do feed de distribuição personalizado pode ser usado para ler itens individuais do fluxo de rede para que o feed que está sendo lido totalmente nunca é armazenada em buffer na memória.  
  
 Para demonstrar melhor o recurso de streaming da API de distribuição, este exemplo usa um cenário improvável no qual o servidor expõe um feed que contém um número infinito de itens. Nesse caso, o servidor continua a gerar novos itens no feed até que ele determina se o cliente tem leitura um número especificado de itens do feed (por padrão, 10). Para simplificar, o cliente e servidor são implementadas no mesmo processo e usar um compartilhado `ItemCounter` produziu um objeto para controlar quantos itens de cliente. O `ItemCounter` tipo existe apenas com o objetivo de permitir que o cenário de exemplo encerrar corretamente e não é um elemento principal do padrão que está sendo demonstrado.  
  
 A demonstração faz uso do Visual c# iteradores (usando o `yield return` construção de palavra-chave). Para obter mais informações sobre iteradores, consulte o tópico "Usando iteradores" no MSDN.  
  
## <a name="service"></a>Serviço  
 O serviço implementa um basic <xref:System.ServiceModel.Web.WebGetAttribute> contrato consiste em uma única operação, conforme mostrado no código a seguir.  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 O serviço implementa esse contrato usando um `ItemGenerator` classe para criar um fluxo potencialmente infinito de <xref:System.ServiceModel.Syndication.SyndicationItem> instâncias usando um iterador, conforme mostrado no código a seguir.  
  
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
  
 Quando a implementação de serviço cria o feed, a saída de `ItemGenerator.GenerateItems()` é usado em vez de uma coleção em buffer de itens.  
  
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
  
 Como resultado, o fluxo de item é nunca totalmente armazenada em buffer na memória. Você pode observar esse comportamento, definindo um ponto de interrupção na `yield return` instrução dentro do `ItemGenerator.GenerateItems()` método e observar que este ponto de interrupção é encontrado pela primeira vez depois que o serviço retornou o resultado do `StreamedFeed()` método.  
  
## <a name="client"></a>Cliente  
 O cliente neste exemplo usa um personalizado <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementação que atrasa a materialização de itens individuais no feed, em vez de armazenamento em buffer na memória. Personalizado `StreamedAtom10FeedFormatter` instância é usada da seguinte maneira.  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Normalmente, uma chamada para <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> não retorna até que todo o conteúdo do feed foram lido na rede e armazenados em buffer na memória. No entanto, o `StreamedAtom10FeedFormatter` substituições do objeto <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> para retornar um iterador em vez de uma coleção em buffer, conforme mostrado no código a seguir.  
  
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
  
 Como resultado, cada item não é lido da rede até que o aplicativo cliente percorrer os resultados de `ReadItems()` está pronto para usá-lo. Você pode observar esse comportamento, definindo um ponto de interrupção na `yield return` instrução dentro de `StreamedAtom10FeedFormatter.DelayReadItems()` e perceba que esse ponto de interrupção é encontrado pela primeira vez após a chamada para `ReadFrom()` é concluída.  
  
 As instruções a seguir mostram como compilar e executar o exemplo. Observe que, embora o servidor para a geração de itens após o cliente ter lido 10 itens, a saída mostra que o cliente lê significativamente mais de 10 itens. Isso ocorre porque a associação de rede usada pelo exemplo transmite os dados em segmentos do quatro kilobyte (KB). Como tal, o cliente recebe 4KB de dados do item antes que ele tenha a oportunidade de ler um item. Esse comportamento é normal (enviando dados transmitidos de HTTP no desempenho de aumentos de segmentos razoavelmente).  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Consulte também  
 [Feed de diagnóstico independente](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
