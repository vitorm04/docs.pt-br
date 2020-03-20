---
title: Codificação de MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 83dbe9e51da1cc9e55bfffb862e2601d70fc7695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144377"
---
# <a name="mtom-encoding"></a><span data-ttu-id="dba63-102">Codificação de MTOM</span><span class="sxs-lookup"><span data-stu-id="dba63-102">MTOM Encoding</span></span>
<span data-ttu-id="dba63-103">Esta amostra demonstra o uso da codificação de mensagem MTOM (Message Transmission Optimization Mechanism, mecanismo de otimização de transmissão de mensagens) com um WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="dba63-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="dba63-104">MTOM é um mecanismo para transmitir grandes anexos binários com mensagens SOAP como bytes brutos, permitindo mensagens menores.</span><span class="sxs-lookup"><span data-stu-id="dba63-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dba63-105">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="dba63-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dba63-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="dba63-106">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dba63-107">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="dba63-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dba63-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="dba63-108">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="dba63-109">Por padrão, o WSHttpBinding envia e recebe mensagens como xML de texto normal.</span><span class="sxs-lookup"><span data-stu-id="dba63-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="dba63-110">Para habilitar o envio e o `messageEncoding` recebimento de mensagens MTOM, defina o atributo na `MessageEncoding` configuração da vinculação (como no código de exemplo a seguir) ou diretamente na vinculação usando a propriedade.</span><span class="sxs-lookup"><span data-stu-id="dba63-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="dba63-111">O serviço ou cliente agora pode enviar e receber mensagens MTOM.</span><span class="sxs-lookup"><span data-stu-id="dba63-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="dba63-112">O codificador MTOM pode otimizar matrizes de bytes e fluxos.</span><span class="sxs-lookup"><span data-stu-id="dba63-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="dba63-113">Nesta amostra, a operação `Stream` utiliza um parâmetro e, portanto, pode ser otimizada.</span><span class="sxs-lookup"><span data-stu-id="dba63-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="dba63-114">O contrato escolhido para esta amostra transmite dados binários para o serviço e recebe o número de bytes carregados como o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="dba63-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="dba63-115">Quando o serviço é instalado e o cliente é executado, ele imprime o número 1000, o que indica que todos os 1000 bytes foram recebidos.</span><span class="sxs-lookup"><span data-stu-id="dba63-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="dba63-116">O restante da saída lista tamanhos de mensagens otimizados e não otimizados para várias cargas.</span><span class="sxs-lookup"><span data-stu-id="dba63-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
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
  
 <span data-ttu-id="dba63-117">O objetivo de usar o MTOM é otimizar a transmissão de grandes cargas binárias.</span><span class="sxs-lookup"><span data-stu-id="dba63-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="dba63-118">O envio de uma mensagem SOAP usando MTOM tem uma sobrecarga perceptível para pequenas cargas binárias, mas torna-se uma grande economia quando eles crescem mais de alguns milhares de bytes.</span><span class="sxs-lookup"><span data-stu-id="dba63-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="dba63-119">A razão para isso é que o XML de texto normal codifica dados binários usando base64, que requer quatro caracteres para cada três bytes, e aumenta o tamanho dos dados em um terço.</span><span class="sxs-lookup"><span data-stu-id="dba63-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="dba63-120">O MTOM é capaz de transmitir dados binários como bytes brutos, salvando o tempo de codificação/decodificação e resultando em mensagens menores.</span><span class="sxs-lookup"><span data-stu-id="dba63-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="dba63-121">O limiar de alguns milhares de bytes é pequeno quando comparado com os documentos de negócios e fotografias digitais de hoje.</span><span class="sxs-lookup"><span data-stu-id="dba63-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dba63-122">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="dba63-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="dba63-123">Instale ASP.NET 4.0 usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="dba63-123">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="dba63-124">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dba63-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="dba63-125">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dba63-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="dba63-126">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dba63-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
