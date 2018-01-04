---
title: Fluxo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab56dd7938f2c7594627b54b4cb61b4e0f6b28fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="stream"></a>Fluxo
O exemplo de fluxo demonstra o uso de fluxo de comunicação de modo de transferência. O serviço expõe diversas operações que enviam e recebem fluxos. Este exemplo é hospedado automaticamente. O cliente e o serviço são programas de console.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]pode comunicar-se em dois modos de transferência — em buffer ou de fluxo contínuo. No modo de transferência do buffer padrão, uma mensagem deve ser entregue completamente antes de um destinatário possa lê-lo. No modo de transferência de streaming, o receptor pode começar a processar a mensagem antes de entregar completamente. O modo de streaming é útil quando as informações que são passadas é demoradas e podem ser processadas em série. O modo contínuo também é útil quando a mensagem é muito grande para ser totalmente armazenada em buffer.  
  
## <a name="streaming-and-service-contracts"></a>Fluxo contínuo e contratos de serviço  
 Streaming é algo a ser considerado ao projetar um contrato de serviço. Se uma operação recebe ou retorna grandes quantidades de dados, você deve considerar o fluxo de dados para evitar a utilização de memória alta devido a buffer de mensagens de entrada ou saídas. Para transmitir dados, o parâmetro que contém a que os dados devem ser o único parâmetro na mensagem. Por exemplo, se a mensagem de entrada for a ser transmitido, a operação deve ter exatamente um parâmetro de entrada. Da mesma forma, se a mensagem de saída é a transmissão, a operação deve ter exatamente uma saída ou um valor de retorno. No caso, o parâmetro ou retorno valor de tipo deve ser `Stream`, `Message`, ou `IXmlSerializable`. Este é o contrato de serviço usado neste exemplo de streaming.  
  
```  
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
  
 O `GetStream` operação recebe alguns dados de entrada como uma cadeia de caracteres, que é armazenado em buffer e retorna um `Stream`, que é transmitido. Por outro lado, `UploadStream` assume um `Stream` (Streaming) e retorna um `bool` (em buffer). `EchoStream`Obtém e retorna `Stream` e é um exemplo de uma operação cujas entradas e mensagens de saída ambos são transmitidas. Por fim, `GetReversedStream` não usa nenhuma entrada e retorna um `Stream` (Streaming).  
  
## <a name="enabling-streamed-transfers"></a>Habilitar transferências em fluxo  
 Definindo contratos de operação conforme descritos anteriormente, você fornece streaming no nível do modelo de programação. Se você parar, o transporte ainda armazena em buffer o conteúdo da mensagem inteira. Para habilitar o fluxo de transporte, selecione um modo de transferência no elemento de associação de transporte. O elemento de associação tem um `TransferMode` propriedade que pode ser definida como `Buffered`, `Streamed`, `StreamedRequest`, ou `StreamedResponse`. Definir o modo de transferência para `Streamed` permite transmitir comunicação nas duas direções. Definir o modo de transferência para `StreamedRequest` ou `StreamedResponse` permite transmitir comunicação em apenas a uma solicitação ou resposta, respectivamente.  
  
 O `basicHttpBinding` expõe o `TransferMode` propriedade na associação de forma `NetTcpBinding` e `NetNamedPipeBinding`. Para outros transportes, você deve criar uma associação personalizada para definir o modo de transferência.  
  
 O código do exemplo de configuração a seguir mostra a configuração de `TransferMode` propriedade para streaming no `basicHttpBinding` e uma associação HTTP personalizada:  
  
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
  
 Além de configuração de `transferMode` para `Streamed`, os conjuntos de código de configuração anterior a `maxReceivedMessageSize` 64 MB. Como um mecanismo de defesa, `maxReceivedMessageSize` locais que o tamanho máximo permitido de mensagens em um limite de recebimento. O padrão `maxReceivedMessageSize` é 64 KB, que geralmente é muito baixa para cenários de streaming.  
  
## <a name="processing-data-as-it-is-streamed"></a>Processamento de dados conforme ele é transmitido  
 As operações `GetStream`, `UploadStream` e `EchoStream` todos lidam com enviar dados diretamente de um arquivo ou salvar dados recebidos diretamente para um arquivo. No entanto, em alguns casos, há um requisito para enviar ou receber grandes quantidades de dados e executar algum processamento em partes dos dados que está sendo enviado ou recebido. É uma maneira de abordar esses cenários gravar um fluxo personalizado (uma classe que deriva de <xref:System.IO.Stream>) que processa os dados conforme ela é lida ou gravada. O `GetReversedStream` operação e `ReverseStream` classe são um exemplo disso.  
  
 `GetReversedStream`cria e retorna uma nova instância da `ReverseStream`. O processamento real ocorre como o sistema lê de que `ReverseStream` objeto. O `ReverseStream.Read` implementação grava um bloco de bytes do arquivo de base, reverte-los e retorna os bytes invertidos. Isso não reverte o conteúdo do arquivo inteiro; ele reserva um bloco de bytes de cada vez. Este é um exemplo para mostrar como você pode executar o processamento de fluxo que o conteúdo está sendo lidos ou gravados de e para o fluxo.  
  
```  
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
 Para executar o exemplo, primeiro crie o serviço e o cliente seguindo as instruções no final deste documento. Inicie o serviço e o cliente em duas janelas de console diferentes. Quando o cliente é iniciado, ele espera para que você pressione ENTER quando o serviço está pronto. O cliente, em seguida, chama os métodos `GetStream()`, `UploadStream()` e `GetReversedStream()` primeiro por HTTP e, em seguida, por meio de TCP. Aqui está um exemplo de saída do serviço, seguido pela saída de exemplo do cliente:  
  
 Saída do serviço:  
  
```  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 Saída de cliente:  
  
```  
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
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Se você usar o Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
  
## <a name="see-also"></a>Consulte também
