---
title: Codificação de MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: f54a22b0004623c8aef8f2788ed7d59f7d777ce7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189057"
---
# <a name="mtom-encoding"></a><span data-ttu-id="ced44-102">Codificação de MTOM</span><span class="sxs-lookup"><span data-stu-id="ced44-102">MTOM Encoding</span></span>
<span data-ttu-id="ced44-103">Este exemplo demonstra o uso da mensagem MTOM Message Transmission Optimization Mechanism () codificação com WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="ced44-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="ced44-104">MTOM é um mecanismo para a transmissão de anexos binários grandes com mensagens SOAP como bytes brutos, permitindo mensagens menores.</span><span class="sxs-lookup"><span data-stu-id="ced44-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ced44-105">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ced44-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ced44-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ced44-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ced44-107">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ced44-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ced44-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ced44-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="ced44-109">Por padrão, o WSHttpBinding envia e as mensagens recebidas como XML de texto normal.</span><span class="sxs-lookup"><span data-stu-id="ced44-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="ced44-110">Para habilitar o envio e recebimento de mensagens MTOM, defina as `messageEncoding` atributo na configuração da associação (como no seguinte exemplo de código), ou diretamente na associação usando o `MessageEncoding` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ced44-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="ced44-111">O serviço ou cliente agora pode enviar e receber mensagens MTOM.</span><span class="sxs-lookup"><span data-stu-id="ced44-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="ced44-112">O codificador MTOM pode otimizar as matrizes de bytes e fluxos.</span><span class="sxs-lookup"><span data-stu-id="ced44-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="ced44-113">Neste exemplo, a operação usa um `Stream` parâmetro e, portanto, pode ser otimizada.</span><span class="sxs-lookup"><span data-stu-id="ced44-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="ced44-114">O contrato escolhido para este exemplo transmite dados binários para o serviço e recebe o número de bytes carregados como o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="ced44-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="ced44-115">Quando o serviço está instalado e o cliente é executado, ele imprime o número 1000, o que indica que todos os 1.000 bytes foram recebidos.</span><span class="sxs-lookup"><span data-stu-id="ced44-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="ced44-116">O restante da saída lista os tamanhos de mensagem otimizados e não otimizados para várias cargas.</span><span class="sxs-lookup"><span data-stu-id="ced44-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
```  
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
  
 <span data-ttu-id="ced44-117">A finalidade para usar o MTOM é otimizar a transmissão de grandes cargas de binárias.</span><span class="sxs-lookup"><span data-stu-id="ced44-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="ced44-118">Enviando uma mensagem SOAP usando MTOM tem uma sobrecarga considerável para transferências binárias pequenas, mas se torna uma grande economia quando elas aumentarem ao longo de alguns milhares de bytes.</span><span class="sxs-lookup"><span data-stu-id="ced44-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="ced44-119">A razão para isso é que o texto normal XML codifica dados binários usando Base64, que requer quatro caracteres para todos os três bytes e aumenta o tamanho dos dados em um terço.</span><span class="sxs-lookup"><span data-stu-id="ced44-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="ced44-120">MTOM é capaz de transmitir dados binários como bytes brutos, economizando o tempo de codificação/decodificação e resultante é mensagens menores.</span><span class="sxs-lookup"><span data-stu-id="ced44-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="ced44-121">O limite de alguns milhares de bytes é pequeno em comparação com os documentos de negócios de hoje e fotografias digitais.</span><span class="sxs-lookup"><span data-stu-id="ced44-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ced44-122">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ced44-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ced44-123">Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="ced44-123">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="ced44-124">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ced44-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="ced44-125">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ced44-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="ced44-126">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ced44-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ced44-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ced44-127">See Also</span></span>
