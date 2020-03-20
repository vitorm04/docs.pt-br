---
title: Sessão confiável de WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 8898dfedc6ba7deceb5a6e6856b7c7e6ad79d047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143493"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="9b4bb-102">Sessão confiável de WS</span><span class="sxs-lookup"><span data-stu-id="9b4bb-102">WS Reliable Session</span></span>
<span data-ttu-id="9b4bb-103">Esta amostra demonstra o uso de sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="9b4bb-104">Sessões confiáveis fornecem suporte para mensagens e sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="9b4bb-105">A comunicação confiável de mensagens tenta a falha e permite que as garantias de entrega sejam especificadas, como a chegada por ordem das mensagens.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="9b4bb-106">As sessões mantêm o estado para os clientes entre as chamadas.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="9b4bb-107">A amostra implementa sessões para manter o estado do cliente e especifica garantias de entrega por ordem.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9b4bb-108">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9b4bb-109">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9b4bb-110">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="9b4bb-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9b4bb-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="9b4bb-112">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="9b4bb-113">Os recursos de sessão confiáveis são ativados e configurados nos arquivos de configuração do aplicativo para o cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="9b4bb-114">Nesta amostra, o serviço está hospedado no Internet Information Services (IIS) e o cliente é um aplicativo de console (.exe).</span><span class="sxs-lookup"><span data-stu-id="9b4bb-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b4bb-115">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9b4bb-116">A amostra `wsHttpBinding`usa o .</span><span class="sxs-lookup"><span data-stu-id="9b4bb-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="9b4bb-117">A vinculação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="9b4bb-118">O tipo de vinculação é especificado `binding` no atributo do elemento endpoint, conforme mostrado na configuração da amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="9b4bb-119">O ponto final `bindingConfiguration` contém um atributo que faz referência a uma configuração vinculante chamada "Binding1".</span><span class="sxs-lookup"><span data-stu-id="9b4bb-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="9b4bb-120">A configuração de vinculação `enabled` permite sessões confiáveis definindo o atributo do [ \<>de Sessão confiável](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) para `true`.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="9b4bb-121">As garantias de entrega para sessões ordenadas `true` são `false`controladas definindo o atributo ordenado para ou .</span><span class="sxs-lookup"><span data-stu-id="9b4bb-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="9b4bb-122">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="9b4bb-123">A classe de <xref:System.ServiceModel.InstanceContextMode.PerSession> implementação de serviço satistece a manutenção de uma instância de classe separada para cada cliente, conforme mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="9b4bb-124">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9b4bb-125">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9b4bb-126">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="9b4bb-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9b4bb-127">Instale ASP.NET 4.0 usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="9b4bb-127">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="9b4bb-128">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9b4bb-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="9b4bb-129">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9b4bb-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="9b4bb-130">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9b4bb-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
