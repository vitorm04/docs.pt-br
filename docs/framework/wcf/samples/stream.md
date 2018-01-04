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
# <a name="stream"></a><span data-ttu-id="e6028-102">Fluxo</span><span class="sxs-lookup"><span data-stu-id="e6028-102">Stream</span></span>
<span data-ttu-id="e6028-103">O exemplo de fluxo demonstra o uso de fluxo de comunicação de modo de transferência.</span><span class="sxs-lookup"><span data-stu-id="e6028-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="e6028-104">O serviço expõe diversas operações que enviam e recebem fluxos.</span><span class="sxs-lookup"><span data-stu-id="e6028-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="e6028-105">Este exemplo é hospedado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e6028-105">This sample is self-hosted.</span></span> <span data-ttu-id="e6028-106">O cliente e o serviço são programas de console.</span><span class="sxs-lookup"><span data-stu-id="e6028-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6028-107">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="e6028-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="e6028-108">pode comunicar-se em dois modos de transferência — em buffer ou de fluxo contínuo.</span><span class="sxs-lookup"><span data-stu-id="e6028-108"> can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="e6028-109">No modo de transferência do buffer padrão, uma mensagem deve ser entregue completamente antes de um destinatário possa lê-lo.</span><span class="sxs-lookup"><span data-stu-id="e6028-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="e6028-110">No modo de transferência de streaming, o receptor pode começar a processar a mensagem antes de entregar completamente.</span><span class="sxs-lookup"><span data-stu-id="e6028-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="e6028-111">O modo de streaming é útil quando as informações que são passadas é demoradas e podem ser processadas em série.</span><span class="sxs-lookup"><span data-stu-id="e6028-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="e6028-112">O modo contínuo também é útil quando a mensagem é muito grande para ser totalmente armazenada em buffer.</span><span class="sxs-lookup"><span data-stu-id="e6028-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="e6028-113">Fluxo contínuo e contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="e6028-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="e6028-114">Streaming é algo a ser considerado ao projetar um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="e6028-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="e6028-115">Se uma operação recebe ou retorna grandes quantidades de dados, você deve considerar o fluxo de dados para evitar a utilização de memória alta devido a buffer de mensagens de entrada ou saídas.</span><span class="sxs-lookup"><span data-stu-id="e6028-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="e6028-116">Para transmitir dados, o parâmetro que contém a que os dados devem ser o único parâmetro na mensagem.</span><span class="sxs-lookup"><span data-stu-id="e6028-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="e6028-117">Por exemplo, se a mensagem de entrada for a ser transmitido, a operação deve ter exatamente um parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="e6028-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="e6028-118">Da mesma forma, se a mensagem de saída é a transmissão, a operação deve ter exatamente uma saída ou um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="e6028-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="e6028-119">No caso, o parâmetro ou retorno valor de tipo deve ser `Stream`, `Message`, ou `IXmlSerializable`.</span><span class="sxs-lookup"><span data-stu-id="e6028-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="e6028-120">Este é o contrato de serviço usado neste exemplo de streaming.</span><span class="sxs-lookup"><span data-stu-id="e6028-120">The following is the service contract used in this streaming sample.</span></span>  
  
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
  
 <span data-ttu-id="e6028-121">O `GetStream` operação recebe alguns dados de entrada como uma cadeia de caracteres, que é armazenado em buffer e retorna um `Stream`, que é transmitido.</span><span class="sxs-lookup"><span data-stu-id="e6028-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="e6028-122">Por outro lado, `UploadStream` assume um `Stream` (Streaming) e retorna um `bool` (em buffer).</span><span class="sxs-lookup"><span data-stu-id="e6028-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="e6028-123">`EchoStream`Obtém e retorna `Stream` e é um exemplo de uma operação cujas entradas e mensagens de saída ambos são transmitidas.</span><span class="sxs-lookup"><span data-stu-id="e6028-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="e6028-124">Por fim, `GetReversedStream` não usa nenhuma entrada e retorna um `Stream` (Streaming).</span><span class="sxs-lookup"><span data-stu-id="e6028-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="e6028-125">Habilitar transferências em fluxo</span><span class="sxs-lookup"><span data-stu-id="e6028-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="e6028-126">Definindo contratos de operação conforme descritos anteriormente, você fornece streaming no nível do modelo de programação.</span><span class="sxs-lookup"><span data-stu-id="e6028-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="e6028-127">Se você parar, o transporte ainda armazena em buffer o conteúdo da mensagem inteira.</span><span class="sxs-lookup"><span data-stu-id="e6028-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="e6028-128">Para habilitar o fluxo de transporte, selecione um modo de transferência no elemento de associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="e6028-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="e6028-129">O elemento de associação tem um `TransferMode` propriedade que pode ser definida como `Buffered`, `Streamed`, `StreamedRequest`, ou `StreamedResponse`.</span><span class="sxs-lookup"><span data-stu-id="e6028-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="e6028-130">Definir o modo de transferência para `Streamed` permite transmitir comunicação nas duas direções.</span><span class="sxs-lookup"><span data-stu-id="e6028-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="e6028-131">Definir o modo de transferência para `StreamedRequest` ou `StreamedResponse` permite transmitir comunicação em apenas a uma solicitação ou resposta, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e6028-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="e6028-132">O `basicHttpBinding` expõe o `TransferMode` propriedade na associação de forma `NetTcpBinding` e `NetNamedPipeBinding`.</span><span class="sxs-lookup"><span data-stu-id="e6028-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="e6028-133">Para outros transportes, você deve criar uma associação personalizada para definir o modo de transferência.</span><span class="sxs-lookup"><span data-stu-id="e6028-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="e6028-134">O código do exemplo de configuração a seguir mostra a configuração de `TransferMode` propriedade para streaming no `basicHttpBinding` e uma associação HTTP personalizada:</span><span class="sxs-lookup"><span data-stu-id="e6028-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
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
  
 <span data-ttu-id="e6028-135">Além de configuração de `transferMode` para `Streamed`, os conjuntos de código de configuração anterior a `maxReceivedMessageSize` 64 MB.</span><span class="sxs-lookup"><span data-stu-id="e6028-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="e6028-136">Como um mecanismo de defesa, `maxReceivedMessageSize` locais que o tamanho máximo permitido de mensagens em um limite de recebimento.</span><span class="sxs-lookup"><span data-stu-id="e6028-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="e6028-137">O padrão `maxReceivedMessageSize` é 64 KB, que geralmente é muito baixa para cenários de streaming.</span><span class="sxs-lookup"><span data-stu-id="e6028-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="e6028-138">Processamento de dados conforme ele é transmitido</span><span class="sxs-lookup"><span data-stu-id="e6028-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="e6028-139">As operações `GetStream`, `UploadStream` e `EchoStream` todos lidam com enviar dados diretamente de um arquivo ou salvar dados recebidos diretamente para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e6028-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="e6028-140">No entanto, em alguns casos, há um requisito para enviar ou receber grandes quantidades de dados e executar algum processamento em partes dos dados que está sendo enviado ou recebido.</span><span class="sxs-lookup"><span data-stu-id="e6028-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="e6028-141">É uma maneira de abordar esses cenários gravar um fluxo personalizado (uma classe que deriva de <xref:System.IO.Stream>) que processa os dados conforme ela é lida ou gravada.</span><span class="sxs-lookup"><span data-stu-id="e6028-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="e6028-142">O `GetReversedStream` operação e `ReverseStream` classe são um exemplo disso.</span><span class="sxs-lookup"><span data-stu-id="e6028-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="e6028-143">`GetReversedStream`cria e retorna uma nova instância da `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="e6028-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="e6028-144">O processamento real ocorre como o sistema lê de que `ReverseStream` objeto.</span><span class="sxs-lookup"><span data-stu-id="e6028-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="e6028-145">O `ReverseStream.Read` implementação grava um bloco de bytes do arquivo de base, reverte-los e retorna os bytes invertidos.</span><span class="sxs-lookup"><span data-stu-id="e6028-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="e6028-146">Isso não reverte o conteúdo do arquivo inteiro; ele reserva um bloco de bytes de cada vez.</span><span class="sxs-lookup"><span data-stu-id="e6028-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="e6028-147">Este é um exemplo para mostrar como você pode executar o processamento de fluxo que o conteúdo está sendo lidos ou gravados de e para o fluxo.</span><span class="sxs-lookup"><span data-stu-id="e6028-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
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
  
## <a name="running-the-sample"></a><span data-ttu-id="e6028-148">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="e6028-148">Running the Sample</span></span>  
 <span data-ttu-id="e6028-149">Para executar o exemplo, primeiro crie o serviço e o cliente seguindo as instruções no final deste documento.</span><span class="sxs-lookup"><span data-stu-id="e6028-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="e6028-150">Inicie o serviço e o cliente em duas janelas de console diferentes.</span><span class="sxs-lookup"><span data-stu-id="e6028-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="e6028-151">Quando o cliente é iniciado, ele espera para que você pressione ENTER quando o serviço está pronto.</span><span class="sxs-lookup"><span data-stu-id="e6028-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="e6028-152">O cliente, em seguida, chama os métodos `GetStream()`, `UploadStream()` e `GetReversedStream()` primeiro por HTTP e, em seguida, por meio de TCP.</span><span class="sxs-lookup"><span data-stu-id="e6028-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="e6028-153">Aqui está um exemplo de saída do serviço, seguido pela saída de exemplo do cliente:</span><span class="sxs-lookup"><span data-stu-id="e6028-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="e6028-154">Saída do serviço:</span><span class="sxs-lookup"><span data-stu-id="e6028-154">Service Output:</span></span>  
  
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
  
 <span data-ttu-id="e6028-155">Saída de cliente:</span><span class="sxs-lookup"><span data-stu-id="e6028-155">Client Output:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e6028-156">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e6028-156">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e6028-157">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e6028-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e6028-158">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e6028-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="e6028-159">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e6028-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6028-160">Se você usar o Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.</span><span class="sxs-lookup"><span data-stu-id="e6028-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e6028-161">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e6028-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e6028-162">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e6028-162">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e6028-163">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e6028-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e6028-164">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e6028-164">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
  
## <a name="see-also"></a><span data-ttu-id="e6028-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6028-165">See Also</span></span>
