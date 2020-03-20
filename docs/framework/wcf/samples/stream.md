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
# <a name="stream"></a><span data-ttu-id="461b7-102">STREAM</span><span class="sxs-lookup"><span data-stu-id="461b7-102">Stream</span></span>
<span data-ttu-id="461b7-103">A amostra Stream demonstra o uso da comunicação do modo de transferência de streaming.</span><span class="sxs-lookup"><span data-stu-id="461b7-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="461b7-104">O serviço expõe diversas operações que enviam e recebem fluxos.</span><span class="sxs-lookup"><span data-stu-id="461b7-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="461b7-105">Esta amostra é auto-hospedada.</span><span class="sxs-lookup"><span data-stu-id="461b7-105">This sample is self-hosted.</span></span> <span data-ttu-id="461b7-106">Tanto o cliente quanto o serviço são programas de console.</span><span class="sxs-lookup"><span data-stu-id="461b7-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="461b7-107">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="461b7-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="461b7-108">O Windows Communication Foundation (WCF) pode se comunicar em dois modos de transferência — tamponados ou em streaming.</span><span class="sxs-lookup"><span data-stu-id="461b7-108">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="461b7-109">No modo de transferência tampão padrão, uma mensagem deve ser completamente entregue antes que um receptor possa lê-la.</span><span class="sxs-lookup"><span data-stu-id="461b7-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="461b7-110">No modo de transferência de streaming, o receptor pode começar a processar a mensagem antes de ser completamente entregue.</span><span class="sxs-lookup"><span data-stu-id="461b7-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="461b7-111">O modo de streaming é útil quando as informações passadas são longas e podem ser processadas em série.</span><span class="sxs-lookup"><span data-stu-id="461b7-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="461b7-112">O modo de streaming também é útil quando a mensagem é muito grande para ser totalmente tamponada.</span><span class="sxs-lookup"><span data-stu-id="461b7-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="461b7-113">Contratos de Streaming e Serviços</span><span class="sxs-lookup"><span data-stu-id="461b7-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="461b7-114">O streaming é algo a ser considerado ao projetar um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="461b7-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="461b7-115">Se uma operação receber ou retornar grandes quantidades de dados, você deve considerar o streaming desses dados para evitar a alta utilização da memória devido ao buffer de mensagens de entrada ou saída.</span><span class="sxs-lookup"><span data-stu-id="461b7-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="461b7-116">Para transmitir dados, o parâmetro que contém esses dados deve ser o único parâmetro na mensagem.</span><span class="sxs-lookup"><span data-stu-id="461b7-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="461b7-117">Por exemplo, se a mensagem de entrada for a que deve ser transmitida, a operação deve ter exatamente um parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="461b7-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="461b7-118">Da mesma forma, se a mensagem de saída for transmitida, a operação deve ter exatamente um parâmetro de saída ou um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="461b7-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="461b7-119">Em ambos os casos, o parâmetro ou `Stream` `Message`o `IXmlSerializable`tipo de valor de retorno devem ser, ou .</span><span class="sxs-lookup"><span data-stu-id="461b7-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="461b7-120">A seguir está o contrato de serviço utilizado nesta amostra de streaming.</span><span class="sxs-lookup"><span data-stu-id="461b7-120">The following is the service contract used in this streaming sample.</span></span>  
  
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
  
 <span data-ttu-id="461b7-121">A `GetStream` operação recebe alguns dados de entrada como uma `Stream`seqüência, que é tamponada, e retorna um , que é transmitido.</span><span class="sxs-lookup"><span data-stu-id="461b7-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="461b7-122">Por outro `UploadStream` lado, `Stream` pega um (transmitido) e retorna um `bool` (tampão).</span><span class="sxs-lookup"><span data-stu-id="461b7-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="461b7-123">`EchoStream`leva e `Stream` retorna e é um exemplo de uma operação cujas mensagens de entrada e saída são transmitidas.</span><span class="sxs-lookup"><span data-stu-id="461b7-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="461b7-124">Finalmente, `GetReversedStream` não pega entradas `Stream` e retorna um (transmitido).</span><span class="sxs-lookup"><span data-stu-id="461b7-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="461b7-125">Habilitando transferências transmitidas</span><span class="sxs-lookup"><span data-stu-id="461b7-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="461b7-126">A definição de contratos de operação como descrito anteriormente fornece streaming no nível do modelo de programação.</span><span class="sxs-lookup"><span data-stu-id="461b7-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="461b7-127">Se você parar por aí, o transporte ainda tampona todo o conteúdo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="461b7-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="461b7-128">Para habilitar o fluxo de transporte, selecione um modo de transferência no elemento de ligação do transporte.</span><span class="sxs-lookup"><span data-stu-id="461b7-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="461b7-129">O elemento de `TransferMode` ligação tem uma `Buffered` `Streamed`propriedade `StreamedRequest`que `StreamedResponse`pode ser definida como, ou .</span><span class="sxs-lookup"><span data-stu-id="461b7-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="461b7-130">Definir o modo `Streamed` de transferência para permitir a comunicação por streaming em ambas as direções.</span><span class="sxs-lookup"><span data-stu-id="461b7-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="461b7-131">Definir o modo `StreamedRequest` `StreamedResponse` de transferência ou habilitar a comunicação por streaming apenas na solicitação ou resposta, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="461b7-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="461b7-132">O `basicHttpBinding` expõe `TransferMode` a propriedade na `NetTcpBinding` ligação `NetNamedPipeBinding`como faz e .</span><span class="sxs-lookup"><span data-stu-id="461b7-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="461b7-133">Para outros transportes, você deve criar uma vinculação personalizada para definir o modo de transferência.</span><span class="sxs-lookup"><span data-stu-id="461b7-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="461b7-134">O código de configuração a `TransferMode` seguir da `basicHttpBinding` amostra mostra a configuração da propriedade para o streaming na e uma vinculação HTTP personalizada:</span><span class="sxs-lookup"><span data-stu-id="461b7-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
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
  
 <span data-ttu-id="461b7-135">Além de definir `transferMode` `Streamed`o to , o `maxReceivedMessageSize` código de configuração anterior define o de 64MB.</span><span class="sxs-lookup"><span data-stu-id="461b7-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="461b7-136">Como mecanismo de `maxReceivedMessageSize` defesa, coloca um limite no tamanho máximo permitido das mensagens no recebimento.</span><span class="sxs-lookup"><span data-stu-id="461b7-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="461b7-137">O `maxReceivedMessageSize` padrão é 64 KB, que geralmente é muito baixo para cenários de streaming.</span><span class="sxs-lookup"><span data-stu-id="461b7-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="461b7-138">Processamento de dados à medida que é transmitido</span><span class="sxs-lookup"><span data-stu-id="461b7-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="461b7-139">As `GetStream`operações , `UploadStream` e `EchoStream` todas lidam com o envio de dados diretamente de um arquivo ou a economia de dados recebidos diretamente para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="461b7-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="461b7-140">No entanto, em alguns casos, há a exigência de enviar ou receber grandes quantidades de dados e realizar algum processamento em pedaços dos dados como eles estão sendo enviados ou recebidos.</span><span class="sxs-lookup"><span data-stu-id="461b7-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="461b7-141">Uma maneira de abordar tais cenários é escrever um <xref:System.IO.Stream>fluxo personalizado (uma classe que deriva de ) que processa dados à medida que são lidos ou escritos.</span><span class="sxs-lookup"><span data-stu-id="461b7-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="461b7-142">A `GetReversedStream` operação `ReverseStream` e a classe são um exemplo disso.</span><span class="sxs-lookup"><span data-stu-id="461b7-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="461b7-143">`GetReversedStream`cria e retorna uma `ReverseStream`nova instância de .</span><span class="sxs-lookup"><span data-stu-id="461b7-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="461b7-144">O processamento real acontece quando o `ReverseStream` sistema lê a partir desse objeto.</span><span class="sxs-lookup"><span data-stu-id="461b7-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="461b7-145">A `ReverseStream.Read` implementação lê um pedaço de bytes do arquivo subjacente, inverte-os e retorna os bytes invertidos.</span><span class="sxs-lookup"><span data-stu-id="461b7-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="461b7-146">Isso não reverte todo o conteúdo do arquivo; ele inverte um pedaço de bytes de cada vez.</span><span class="sxs-lookup"><span data-stu-id="461b7-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="461b7-147">Este é um exemplo para mostrar como você pode executar o processamento de fluxo à medida que o conteúdo está sendo lido ou escrito de e para o fluxo.</span><span class="sxs-lookup"><span data-stu-id="461b7-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
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
  
## <a name="running-the-sample"></a><span data-ttu-id="461b7-148">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="461b7-148">Running the Sample</span></span>  
 <span data-ttu-id="461b7-149">Para executar a amostra, primeiro construa o serviço e o cliente seguindo as instruções no final deste documento.</span><span class="sxs-lookup"><span data-stu-id="461b7-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="461b7-150">Em seguida, inicie o serviço e o cliente em duas janelas de console diferentes.</span><span class="sxs-lookup"><span data-stu-id="461b7-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="461b7-151">Quando o cliente começa, ele espera que você pressione ENTER quando o serviço estiver pronto.</span><span class="sxs-lookup"><span data-stu-id="461b7-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="461b7-152">Em seguida, o `GetStream()`cliente `UploadStream()` `GetReversedStream()` chama os métodos , e primeiro sobre HTTP e depois sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="461b7-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="461b7-153">Aqui está um exemplo de saída do serviço seguido de saída de exemplo do cliente:</span><span class="sxs-lookup"><span data-stu-id="461b7-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="461b7-154">Saída de serviço:</span><span class="sxs-lookup"><span data-stu-id="461b7-154">Service Output:</span></span>  
  
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
  
 <span data-ttu-id="461b7-155">Saída do cliente:</span><span class="sxs-lookup"><span data-stu-id="461b7-155">Client Output:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="461b7-156">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="461b7-156">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="461b7-157">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="461b7-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="461b7-158">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="461b7-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="461b7-159">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="461b7-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="461b7-160">Se você usar Svcutil.exe para regenerar a configuração desta amostra, certifique-se de modificar o nome do ponto final na configuração do cliente para corresponder ao código do cliente.</span><span class="sxs-lookup"><span data-stu-id="461b7-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="461b7-161">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="461b7-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="461b7-162">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="461b7-162">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="461b7-163">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="461b7-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="461b7-164">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="461b7-164">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
