---
title: STREAM
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: f22339ca298f053fa636cc37281276051c70f6d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183327"
---
# <a name="stream"></a>STREAM
A amostra Stream demonstra o uso da comunicação do modo de transferência de streaming. O serviço expõe diversas operações que enviam e recebem fluxos. Esta amostra é auto-hospedada. Tanto o cliente quanto o serviço são programas de console.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 O Windows Communication Foundation (WCF) pode se comunicar em dois modos de transferência — tamponados ou em streaming. No modo de transferência tampão padrão, uma mensagem deve ser completamente entregue antes que um receptor possa lê-la. No modo de transferência de streaming, o receptor pode começar a processar a mensagem antes de ser completamente entregue. O modo de streaming é útil quando as informações passadas são longas e podem ser processadas em série. O modo de streaming também é útil quando a mensagem é muito grande para ser totalmente tamponada.  
  
## <a name="streaming-and-service-contracts"></a>Contratos de Streaming e Serviços  
 O streaming é algo a ser considerado ao projetar um contrato de serviço. Se uma operação receber ou retornar grandes quantidades de dados, você deve considerar o streaming desses dados para evitar a alta utilização da memória devido ao buffer de mensagens de entrada ou saída. Para transmitir dados, o parâmetro que contém esses dados deve ser o único parâmetro na mensagem. Por exemplo, se a mensagem de entrada for a que deve ser transmitida, a operação deve ter exatamente um parâmetro de entrada. Da mesma forma, se a mensagem de saída for transmitida, a operação deve ter exatamente um parâmetro de saída ou um valor de retorno. Em ambos os casos, o parâmetro ou `Stream` `Message`o `IXmlSerializable`tipo de valor de retorno devem ser, ou . A seguir está o contrato de serviço utilizado nesta amostra de streaming.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamingSample  
{  
    [OperationContract]  
    Stream GetStream(string data);  
    [OperationContract]  
    bool UploadStream(Stream stream);  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
    [OperationContract]  
    Stream GetReversedStream();  
  
}  
```  
  
 A `GetStream` operação recebe alguns dados de entrada como uma `Stream`seqüência, que é tamponada, e retorna um , que é transmitido. Por outro `UploadStream` lado, `Stream` pega um (transmitido) e retorna um `bool` (tampão). `EchoStream`leva e `Stream` retorna e é um exemplo de uma operação cujas mensagens de entrada e saída são transmitidas. Finalmente, `GetReversedStream` não pega entradas `Stream` e retorna um (transmitido).  
  
## <a name="enabling-streamed-transfers"></a>Habilitando transferências transmitidas  
 A definição de contratos de operação como descrito anteriormente fornece streaming no nível do modelo de programação. Se você parar por aí, o transporte ainda tampona todo o conteúdo da mensagem. Para habilitar o fluxo de transporte, selecione um modo de transferência no elemento de ligação do transporte. O elemento de `TransferMode` ligação tem uma `Buffered` `Streamed`propriedade `StreamedRequest`que `StreamedResponse`pode ser definida como, ou . Definir o modo `Streamed` de transferência para permitir a comunicação por streaming em ambas as direções. Definir o modo `StreamedRequest` `StreamedResponse` de transferência ou habilitar a comunicação por streaming apenas na solicitação ou resposta, respectivamente.  
  
 O `basicHttpBinding` expõe `TransferMode` a propriedade na `NetTcpBinding` ligação `NetNamedPipeBinding`como faz e . Para outros transportes, você deve criar uma vinculação personalizada para definir o modo de transferência.  
  
 O código de configuração a `TransferMode` seguir da `basicHttpBinding` amostra mostra a configuração da propriedade para o streaming na e uma vinculação HTTP personalizada:  
  
```xml  
<!-- An example basicHttpBinding using streaming. -->  
<basicHttpBinding>  
  <binding name="HttpStreaming" maxReceivedMessageSize="67108864"  
           transferMode="Streamed"/>  
</basicHttpBinding>  
<!-- An example customBinding using HTTP and streaming.-->  
<customBinding>  
  <binding name="Soap12">  
    <textMessageEncoding messageVersion="Soap12WSAddressing10" />  
    <httpTransport transferMode="Streamed"  
                   maxReceivedMessageSize="67108864"/>  
  </binding>  
</customBinding>  
```  
  
 Além de definir `transferMode` `Streamed`o to , o `maxReceivedMessageSize` código de configuração anterior define o de 64MB. Como mecanismo de `maxReceivedMessageSize` defesa, coloca um limite no tamanho máximo permitido das mensagens no recebimento. O `maxReceivedMessageSize` padrão é 64 KB, que geralmente é muito baixo para cenários de streaming.  
  
## <a name="processing-data-as-it-is-streamed"></a>Processamento de dados à medida que é transmitido  
 As `GetStream`operações , `UploadStream` e `EchoStream` todas lidam com o envio de dados diretamente de um arquivo ou a economia de dados recebidos diretamente para um arquivo. No entanto, em alguns casos, há a exigência de enviar ou receber grandes quantidades de dados e realizar algum processamento em pedaços dos dados como eles estão sendo enviados ou recebidos. Uma maneira de abordar tais cenários é escrever um <xref:System.IO.Stream>fluxo personalizado (uma classe que deriva de ) que processa dados à medida que são lidos ou escritos. A `GetReversedStream` operação `ReverseStream` e a classe são um exemplo disso.  
  
 `GetReversedStream`cria e retorna uma `ReverseStream`nova instância de . O processamento real acontece quando o `ReverseStream` sistema lê a partir desse objeto. A `ReverseStream.Read` implementação lê um pedaço de bytes do arquivo subjacente, inverte-os e retorna os bytes invertidos. Isso não reverte todo o conteúdo do arquivo; ele inverte um pedaço de bytes de cada vez. Este é um exemplo para mostrar como você pode executar o processamento de fluxo à medida que o conteúdo está sendo lido ou escrito de e para o fluxo.  
  
```csharp
class ReverseStream : Stream  
{  
  
    FileStream inStream;  
    internal ReverseStream(string filePath)  
    {  
        //Opens the file and places a StreamReader around it.  
        inStream = File.OpenRead(filePath);  
    }  
  
    // Other methods removed for brevity.  
  
    public override int Read(byte[] buffer, int offset, int count)  
    {  
        int countRead=inStream.Read(buffer, offset,count);  
        ReverseBuffer(buffer, offset, countRead);  
        return countRead;  
    }  
  
    public override void Close()  
    {  
        inStream.Close();  
        base.Close();  
    }  
    protected override void Dispose(bool disposing)  
    {  
        inStream.Dispose();  
        base.Dispose(disposing);  
    }  
    void ReverseBuffer(byte[] buffer, int offset, int count)  
    {  
        int i, j;  
        for (i = offset, j = offset + count - 1; i < j; i++, j--)  
        {  
            byte currenti = buffer[i];  
            buffer[i] = buffer[j];  
            buffer[j] = currenti;  
        }  
  
    }  
}  
```  
  
## <a name="running-the-sample"></a>Executando o exemplo  
 Para executar a amostra, primeiro construa o serviço e o cliente seguindo as instruções no final deste documento. Em seguida, inicie o serviço e o cliente em duas janelas de console diferentes. Quando o cliente começa, ele espera que você pressione ENTER quando o serviço estiver pronto. Em seguida, o `GetStream()`cliente `UploadStream()` `GetReversedStream()` chama os métodos , e primeiro sobre HTTP e depois sobre TCP. Aqui está um exemplo de saída do serviço seguido de saída de exemplo do cliente:  
  
 Saída de serviço:  
  
```console  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 Saída do cliente:  
  
```console  
Press <ENTER> when service is ready  
------ Using HTTP ------
Calling GetStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
------ Using Custom HTTP ------  
Calling GetStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Se você usar Svcutil.exe para regenerar a configuração desta amostra, certifique-se de modificar o nome do ponto final na configuração do cliente para corresponder ao código do cliente.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
