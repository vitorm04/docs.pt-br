---
title: Fluxo
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: f6ca887240ec4f6a304f0d5972790837c0121721
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007793"
---
# <a name="stream"></a>Fluxo
O exemplo de Stream demonstra o uso de fluxo de comunicação de modo de transferência. O serviço expõe diversas operações que enviam e recebem transmissões. Este exemplo é auto-hospedado. O cliente e o serviço são programas de console.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Windows Communication Foundation (WCF) podem se comunicar em dois modos de transferência — em buffer ou de streaming. No modo de transferência em buffer padrão, uma mensagem deve ser entregue completamente antes de um destinatário possa lê-lo. No modo de transferência de streaming, o receptor pode começar a processar a mensagem antes que seja entregue completamente. O modo de streaming é útil quando as informações que são passadas são demoradas e podem ser processadas em série. Modo de streaming também é útil quando a mensagem é muito grande para ser totalmente armazenada em buffer.  
  
## <a name="streaming-and-service-contracts"></a>Streaming e contratos de serviço  
 Streaming é algo a ser considerados ao criar um contrato de serviço. Se uma operação recebe ou retorna grandes quantidades de dados, você deve considerar esses dados para evitar a utilização de memória alta devido a buffer de mensagens de entrada ou saídas de streaming. Para transmitir dados, o parâmetro que contém a que os dados devem ser o único parâmetro na mensagem. Por exemplo, se a mensagem de entrada é à ser transmitido, a operação deve ter exatamente um parâmetro de entrada. Da mesma forma, se a mensagem de saída deve ser transmitido, a operação deve ter exatamente um parâmetro de saída ou um valor de retorno. No caso, o parâmetro ou retorno valor de tipo deve ser `Stream`, `Message`, ou `IXmlSerializable`. Este é o contrato de serviço usado neste exemplo de streaming.  
  
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
  
 O `GetStream` operação recebe alguns dados de entrada como uma cadeia de caracteres, que é armazenada em buffer e retorna um `Stream`, que é transmitido. Por outro lado, `UploadStream` usa um `Stream` (em fluxo) e retorna um `bool` (em buffer). `EchoStream` usa e retorna `Stream` é um exemplo de uma operação cujas entradas e as mensagens de saída são transmitidas. Por fim, `GetReversedStream` não usa nenhuma entrada e retorna um `Stream` (em fluxo).  
  
## <a name="enabling-streamed-transfers"></a>Habilitar transferências em streaming  
 Definindo contratos de operação conforme descritos anteriormente, você fornece no nível do modelo de programação de streaming. Se você parar por aqui, o transporte ainda armazena em buffer o conteúdo da mensagem inteira. Para habilitar o streaming de transporte, selecione um modo de transferência no elemento de associação de transporte. O elemento de associação tem um `TransferMode` propriedade pode ser definida como `Buffered`, `Streamed`, `StreamedRequest`, ou `StreamedResponse`. Definir o modo de transferência para `Streamed` permite a comunicação em ambas as direções de fluxo. Definir o modo de transferência para `StreamedRequest` ou `StreamedResponse` permite transmitir a comunicação apenas a solicitação ou resposta, respectivamente.  
  
 O `basicHttpBinding` expõe o `TransferMode` propriedade na associação como faz `NetTcpBinding` e `NetNamedPipeBinding`. Para outros transportes, você deve criar uma ligação personalizada para definir o modo de transferência.  
  
 O código do exemplo de configuração a seguir mostra a configuração de `TransferMode` propriedade para transmissão no `basicHttpBinding` e uma ligação HTTP personalizada:  
  
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
  
 Além de configuração de `transferMode` para `Streamed`, os conjuntos de código de configuração anteriores a `maxReceivedMessageSize` 64 MB. Como um mecanismo de defesa, `maxReceivedMessageSize` coloca um limite para o tamanho máximo permitido de mensagens em receber. O padrão `maxReceivedMessageSize` é de 64 KB, que geralmente é muito baixa para cenários de streaming.  
  
## <a name="processing-data-as-it-is-streamed"></a>Processamento de dados quando ele é distribuído  
 As operações `GetStream`, `UploadStream` e `EchoStream` todos lidam com o envio de dados diretamente de um arquivo ou salvar dados recebidos diretamente para um arquivo. No entanto, em alguns casos, há um requisito para enviar ou receber grandes quantidades de dados e executar algum processamento em partes dos dados enquanto ele é enviado ou recebido. Uma maneira de resolver esses cenários é gravar um fluxo personalizado (uma classe que deriva de <xref:System.IO.Stream>) que processa os dados conforme ela é lida ou gravada. O `GetReversedStream` operação e `ReverseStream` classe são um exemplo disso.  
  
 `GetReversedStream` cria e retorna uma nova instância da `ReverseStream`. O processamento real ocorre conforme o sistema lê do que `ReverseStream` objeto. O `ReverseStream.Read` implementação lê um bloco de bytes do arquivo subjacente, reverta e retorna os bytes invertidos. Isso não reverte o conteúdo do arquivo inteiro; ele reserva um bloco de bytes de cada vez. Este é um exemplo para mostrar como você pode executar o processamento de fluxo como o conteúdo está sendo lidos ou gravados de e para o fluxo.  
  
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
  
## <a name="running-the-sample"></a>A execução do exemplo  
 Para executar o exemplo, primeiro crie o serviço e o cliente seguindo as instruções no final deste documento. Em seguida, inicie o serviço e o cliente nas duas janelas de console diferentes. Quando o cliente é iniciado, ele espera que você pressione ENTER quando o serviço está pronto. O cliente, em seguida, chama os métodos `GetStream()`, `UploadStream()` e `GetReversedStream()` primeiro por HTTP e, em seguida, por meio de TCP. Aqui está um exemplo de saída do serviço, seguido pela saída de exemplo do cliente:  
  
 Saída do serviço:  
  
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
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Se você usar Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
