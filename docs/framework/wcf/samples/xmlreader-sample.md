---
title: Exemplo de XmlReader
ms.date: 03/30/2017
helpviewer_keywords:
- XML Reader
ms.assetid: 60e5848d-7d9c-4ea5-bed9-22758c9ac16c
ms.openlocfilehash: fc25f2fccdc7becb8989c3cabe8b7b82d865fa13
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834511"
---
# <a name="xmlreader-sample"></a><span data-ttu-id="1489b-102">Exemplo de XmlReader</span><span class="sxs-lookup"><span data-stu-id="1489b-102">XmlReader Sample</span></span>
<span data-ttu-id="1489b-103">O exemplo de XmlReader demonstra o processamento de um corpo de mensagem usando um <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="1489b-103">The XmlReader sample demonstrates the processing of a message body using an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="1489b-104">O exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="1489b-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="1489b-105">Uma operação de serviço adicionais, `Sum`, foi adicionada que aceita uma mensagem que contém uma matriz de valores a serem adicionados juntos.</span><span class="sxs-lookup"><span data-stu-id="1489b-105">An additional service operation, `Sum`, has been added that accepts a message that contains an array of values to add together.</span></span> <span data-ttu-id="1489b-106">O serviço lê a mensagem usando um <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="1489b-106">The service reads the message using an <xref:System.Xml.XmlReader>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1489b-107">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="1489b-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1489b-108">A interface de calculadora inclui uma operação de serviço nomeada `Sum` que aceita um <xref:System.ServiceModel.Channels.Message> parâmetro, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1489b-108">The calculator interface includes a service operation named `Sum` that accepts a <xref:System.ServiceModel.Channels.Message> parameter, as shown in the following sample code.</span></span>  
  
```csharp
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
    [OperationContract]  
    Message Sum(Message message);  
}  
```  
  
 <span data-ttu-id="1489b-109">O cliente acessa `Sum` criando primeiro uma matriz de valores inteiros, em seguida, criando uma mensagem da matriz e, em seguida, chamar o `Sum` método usando a mensagem criada, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1489b-109">The client accesses `Sum` by first creating an array of integer values, then creating a message from the array, and then calling the `Sum` method using the created message, as shown in the following sample code.</span></span>  
  
```csharp
CalculatorClient client = new CalculatorClient();  
//...  

// Call the Sum service operation.  
int[] values = { 1, 2, 3, 4, 5 };  
using (new OperationContextScope(client.InnerChannel))  
{  
    Message request = Message.CreateMessage(OperationContext.Current.OutgoingMessageHeaders.MessageVersion, "http://Microsoft.ServiceModel.Samples/ICalculator/Sum", values);  
    Message reply = client.Sum(request);  
    int sum = reply.GetBody<int>();  
  
    Console.WriteLine("Sum(1,2,3,4,5) = {0}", sum);  
}  
```  
  
 <span data-ttu-id="1489b-110">No serviço, a implementação da operação de serviço `Sum` acessa o corpo da mensagem usando um <xref:System.Xml.XmlReader> objeto para iterar os valores de soma.</span><span class="sxs-lookup"><span data-stu-id="1489b-110">In the service, the implementation of the service operation `Sum` accesses the message body using an <xref:System.Xml.XmlReader> object to iterate through the values to sum.</span></span> <span data-ttu-id="1489b-111">O <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> método é chamado para acessar o corpo da mensagem, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1489b-111">The <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> method is called to access the message body, as shown in the following sample code.</span></span>  
  
```csharp  
public int Sum(Message message)  
{  
    int sum = 0;  
    string text = "";  
  
    //The body of the message contains a list of numbers that are read  
    //directly using an XmlReader.  
    XmlReader body = message.GetReaderAtBodyContents ();  
    while (body.Read())  
    {  
        text = body.ReadString().Trim();  
        if (text.Length>0)  
        {  
            sum += Convert.ToInt32(text);  
        }  
    }  
    body.Close();  
    Message response = Message.CreateMessage(  
       "http://Microsoft.ServiceModel.Samples/ICalculator/SumResponse",  
       sum);  
    return response;  
}  
```  
  
 <span data-ttu-id="1489b-112">Quando você executar o exemplo, as solicitações e respostas da operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="1489b-112">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="1489b-113">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="1489b-113">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Sum(1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1489b-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1489b-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1489b-115">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1489b-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1489b-116">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1489b-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1489b-117">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1489b-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1489b-118">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1489b-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1489b-119">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1489b-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1489b-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="1489b-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1489b-121">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="1489b-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\XmlReader`  
  
