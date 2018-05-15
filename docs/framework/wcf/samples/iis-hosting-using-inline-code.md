---
title: Hospedagem do IIS utilizando código embutido
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 760607bc7ebf2662a7a3a93b2ebf76114580f42b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iis-hosting-using-inline-code"></a><span data-ttu-id="16b50-102">Hospedagem do IIS utilizando código embutido</span><span class="sxs-lookup"><span data-stu-id="16b50-102">IIS Hosting Using Inline Code</span></span>
<span data-ttu-id="16b50-103">Este exemplo demonstra como implementar um serviço hospedado pelo Internet Information Services (IIS), em que o código de serviço está contido na linha em um arquivo. svc e compilado por demanda.</span><span class="sxs-lookup"><span data-stu-id="16b50-103">This sample demonstrates how to implement a service hosted by Internet Information Services (IIS), where the service code is contained in-line in a .svc file and is compiled on demand.</span></span> <span data-ttu-id="16b50-104">Código de serviço também pode ser implementado diretamente nos arquivos de código de origem localizado no diretório de \App_Code do aplicativo ou compilado no assembly implantada no \bin.</span><span class="sxs-lookup"><span data-stu-id="16b50-104">Service code can also be implemented directly in source code files located in the application's \App_Code directory, or compiled into assembly deployed in \bin.</span></span> <span data-ttu-id="16b50-105">Este exemplo demonstra essas técnicas.</span><span class="sxs-lookup"><span data-stu-id="16b50-105">This sample does not demonstrate these techniques.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16b50-106">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="16b50-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="16b50-107">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="16b50-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="16b50-108">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="16b50-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="16b50-109">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="16b50-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="16b50-110">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="16b50-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`  
  
 <span data-ttu-id="16b50-111">O exemplo demonstra um serviço típico que implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="16b50-111">The sample demonstrates a typical service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="16b50-112">O serviço está hospedado no IIS e o código de serviço é totalmente contido no arquivo svc.</span><span class="sxs-lookup"><span data-stu-id="16b50-112">The service is hosted in IIS and the service code is entirely contained in the Service.svc file.</span></span> <span data-ttu-id="16b50-113">O serviço é host ativados e compilado sob demanda, a primeira mensagem enviada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="16b50-113">The service is host-activated and compiled on-demand by the first message sent to the service.</span></span> <span data-ttu-id="16b50-114">Não há sem a necessidade de pré-compilação.</span><span class="sxs-lookup"><span data-stu-id="16b50-114">There is no pre-compilation necessary.</span></span> <span data-ttu-id="16b50-115">O serviço implementa uma `ICalculator` contrato conforme definido no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="16b50-115">The service implements an `ICalculator` contract as defined in the following code:</span></span>  
  
```  
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
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
}  
```  
  
 <span data-ttu-id="16b50-116">A implementação do serviço calcula e retorna o resultado apropriado.</span><span class="sxs-lookup"><span data-stu-id="16b50-116">The service implementation calculates and returns the appropriate result.</span></span>  
  
```  
<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>   
…  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 <span data-ttu-id="16b50-117">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="16b50-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="16b50-118">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="16b50-118">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="16b50-119">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="16b50-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="16b50-120">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16b50-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="16b50-121">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16b50-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="16b50-122">Depois que a solução foi criada, execute bat para configurar o aplicativo ServiceModelSamples em [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="16b50-122">After the solution has been built, run setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="16b50-123">O diretório ServiceModelSamples agora deve aparecer como um [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16b50-123">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="16b50-124">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16b50-124">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="16b50-125">Para obter um exemplo sobre como criar um aplicativo cliente que possa chamar esse serviço, consulte [como: criar um cliente](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="16b50-125">For an example on how to create a client application that can call this service, see [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16b50-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16b50-126">See Also</span></span>  
 [<span data-ttu-id="16b50-127">Exemplos de persistência e hospedagem de AppFabric</span><span class="sxs-lookup"><span data-stu-id="16b50-127">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
