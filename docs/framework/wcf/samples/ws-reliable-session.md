---
title: Sessão confiável de WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 68123ba9a273bf2c1eaa7b3747930ebca386064b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589689"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="784c5-102">Sessão confiável de WS</span><span class="sxs-lookup"><span data-stu-id="784c5-102">WS Reliable Session</span></span>
<span data-ttu-id="784c5-103">Este exemplo demonstra o uso de sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="784c5-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="784c5-104">As sessões confiáveis oferecem suporte para mensagens e sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="784c5-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="784c5-105">O sistema de mensagens confiável repete a comunicação em caso de falha e permite que as garantias de entrega sejam especificadas, como a chegada de mensagens em ordem.</span><span class="sxs-lookup"><span data-stu-id="784c5-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="784c5-106">As sessões mantêm o estado para clientes entre chamadas.</span><span class="sxs-lookup"><span data-stu-id="784c5-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="784c5-107">O exemplo implementa sessões para manter o estado do cliente e especifica garantias de entrega em ordem.</span><span class="sxs-lookup"><span data-stu-id="784c5-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="784c5-108">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="784c5-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="784c5-109">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="784c5-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="784c5-110">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="784c5-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="784c5-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="784c5-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="784c5-112">Este exemplo é baseado no [introdução](getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="784c5-112">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="784c5-113">Os recursos de sessão confiáveis são habilitados e configurados nos arquivos de configuração do aplicativo para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="784c5-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="784c5-114">Neste exemplo, o serviço é hospedado no Serviços de Informações da Internet (IIS) e o cliente é um aplicativo de console (. exe).</span><span class="sxs-lookup"><span data-stu-id="784c5-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="784c5-115">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="784c5-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="784c5-116">O exemplo usa o `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="784c5-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="784c5-117">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="784c5-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="784c5-118">O tipo de associação é especificado no atributo do elemento do ponto de extremidade `binding` , conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="784c5-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="784c5-119">O ponto de extremidade contém um `bindingConfiguration` atributo que faz referência a uma configuração de associação chamada "Binding1".</span><span class="sxs-lookup"><span data-stu-id="784c5-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="784c5-120">A configuração de associação permite sessões confiáveis definindo o `enabled` atributo do [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) para `true` .</span><span class="sxs-lookup"><span data-stu-id="784c5-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="784c5-121">As garantias de entrega para sessões ordenadas são controladas definindo o atributo ordenado como `true` ou `false` .</span><span class="sxs-lookup"><span data-stu-id="784c5-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="784c5-122">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="784c5-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="784c5-123">A classe de implementação de serviço implementa <xref:System.ServiceModel.InstanceContextMode.PerSession> a instanciação para manter uma instância de classe separada para cada cliente, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="784c5-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="784c5-124">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="784c5-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="784c5-125">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="784c5-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="784c5-126">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="784c5-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="784c5-127">Instale o ASP.NET 4,0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="784c5-127">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="784c5-128">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="784c5-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="784c5-129">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="784c5-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="784c5-130">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="784c5-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
