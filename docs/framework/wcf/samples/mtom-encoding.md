---
title: Codificação de MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 4156ebed22dc775aa69cf473dc89a26d7e2070d7
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714762"
---
# <a name="mtom-encoding"></a><span data-ttu-id="ae668-102">Codificação de MTOM</span><span class="sxs-lookup"><span data-stu-id="ae668-102">MTOM Encoding</span></span>
<span data-ttu-id="ae668-103">Este exemplo demonstra o uso da codificação de mensagens do mecanismo de otimização de transmissão de mensagens (MTOM) com uma WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="ae668-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="ae668-104">MTOM é um mecanismo para transmitir anexos binários grandes com mensagens SOAP como bytes brutos, permitindo mensagens menores.</span><span class="sxs-lookup"><span data-stu-id="ae668-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ae668-105">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ae668-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ae668-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ae668-106">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="ae668-107">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="ae668-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ae668-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ae668-108">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="ae668-109">Por padrão, o WSHttpBinding envia e recebe mensagens como XML de texto normal.</span><span class="sxs-lookup"><span data-stu-id="ae668-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="ae668-110">Para habilitar o envio e o recebimento de mensagens MTOM, defina o atributo `messageEncoding` na configuração da Associação (como no código de exemplo a seguir) ou diretamente na associação usando a propriedade `MessageEncoding`.</span><span class="sxs-lookup"><span data-stu-id="ae668-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="ae668-111">O serviço ou cliente agora pode enviar e receber mensagens MTOM.</span><span class="sxs-lookup"><span data-stu-id="ae668-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="ae668-112">O codificador MTOM pode otimizar matrizes de bytes e fluxos.</span><span class="sxs-lookup"><span data-stu-id="ae668-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="ae668-113">Neste exemplo, a operação usa um parâmetro `Stream` e, portanto, pode ser otimizada.</span><span class="sxs-lookup"><span data-stu-id="ae668-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="ae668-114">O contrato escolhido para este exemplo transmite dados binários para o serviço e recebe o número de bytes carregados como o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="ae668-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="ae668-115">Quando o serviço é instalado e o cliente é executado, ele imprime o número 1000, que indica que todos os 1000 bytes foram recebidos.</span><span class="sxs-lookup"><span data-stu-id="ae668-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="ae668-116">O restante da saída lista os tamanhos de mensagem otimizados e não otimizados para várias cargas.</span><span class="sxs-lookup"><span data-stu-id="ae668-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
```console
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="ae668-117">A finalidade de usar o MTOM é otimizar a transmissão de grandes cargas binárias.</span><span class="sxs-lookup"><span data-stu-id="ae668-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="ae668-118">O envio de uma mensagem SOAP usando MTOM tem uma sobrecarga perceptível para pequenos conteúdos binários, mas se torna uma grande economia quando eles crescem em poucos milhares de bytes.</span><span class="sxs-lookup"><span data-stu-id="ae668-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="ae668-119">O motivo disso é que o XML de texto normal codifica dados binários usando base64, que requer quatro caracteres para cada três bytes e aumenta o tamanho dos dados em um terço.</span><span class="sxs-lookup"><span data-stu-id="ae668-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="ae668-120">O MTOM é capaz de transmitir dados binários como bytes brutos, salvar o tempo de codificação/decodificação e resultar em mensagens menores.</span><span class="sxs-lookup"><span data-stu-id="ae668-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="ae668-121">O limite de alguns mil bytes é pequeno quando comparado aos documentos de negócios atuais e às fotografias digitais.</span><span class="sxs-lookup"><span data-stu-id="ae668-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ae668-122">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ae668-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ae668-123">Instale o ASP.NET 4,0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="ae668-123">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="ae668-124">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae668-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="ae668-125">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae668-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="ae668-126">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae668-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
