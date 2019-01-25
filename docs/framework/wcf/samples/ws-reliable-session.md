---
title: Sessão confiável de WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 660fb9a7f60bc95a5039cdf3bad098c330ac969e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682674"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="4645e-102">Sessão confiável de WS</span><span class="sxs-lookup"><span data-stu-id="4645e-102">WS Reliable Session</span></span>
<span data-ttu-id="4645e-103">Este exemplo demonstra o uso de sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="4645e-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="4645e-104">Sessões confiáveis fornecem suporte para o sistema de mensagens confiável e sessões.</span><span class="sxs-lookup"><span data-stu-id="4645e-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="4645e-105">Sistema de mensagens confiável tenta novamente a comunicação em caso de falha e permite que as garantias de entrega seja especificado, como em ordem chegada de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4645e-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="4645e-106">Sessões de mantêm o estado dos clientes entre chamadas.</span><span class="sxs-lookup"><span data-stu-id="4645e-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="4645e-107">O exemplo implementa sessões para manter o estado do cliente e especifica as garantias de entrega em ordem.</span><span class="sxs-lookup"><span data-stu-id="4645e-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4645e-108">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4645e-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4645e-109">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4645e-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4645e-110">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="4645e-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4645e-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4645e-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="4645e-112">Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="4645e-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="4645e-113">Os recursos de sessão confiável estão habilitados e configurados nos arquivos de configuração do aplicativo para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="4645e-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="4645e-114">Neste exemplo, o serviço está hospedado no Internet Information Services (IIS) e o cliente é um aplicativo de console (.exe).</span><span class="sxs-lookup"><span data-stu-id="4645e-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4645e-115">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4645e-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4645e-116">O exemplo usa o `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="4645e-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="4645e-117">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="4645e-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="4645e-118">O tipo de associação é especificado no elemento de ponto de extremidade `binding` conforme mostrado no seguinte exemplo de configuração do atributo.</span><span class="sxs-lookup"><span data-stu-id="4645e-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="4645e-119">O ponto de extremidade contém um `bindingConfiguration` atributo que faz referência a uma configuração de associação chamado "Binding1".</span><span class="sxs-lookup"><span data-stu-id="4645e-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="4645e-120">A configuração de associação permite que as sessões confiáveis, definindo o `enabled` atributo o [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) para `true`.</span><span class="sxs-lookup"><span data-stu-id="4645e-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="4645e-121">Garantias de entrega ordenada sessões são controladas pela definição de atributo ordenada `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="4645e-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="4645e-122">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="4645e-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="4645e-123">A classe de implementação de serviço implementa <xref:System.ServiceModel.InstanceContextMode.PerSession> instanciação para manter uma instância de classe separada para cada cliente, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4645e-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="4645e-124">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="4645e-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4645e-125">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="4645e-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4645e-126">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4645e-126">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4645e-127">Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="4645e-127">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="4645e-128">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4645e-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="4645e-129">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4645e-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="4645e-130">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4645e-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4645e-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4645e-131">See also</span></span>
