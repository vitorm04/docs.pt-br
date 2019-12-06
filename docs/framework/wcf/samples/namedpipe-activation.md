---
title: NamedPipe Activation
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: a562ec51d35af08f49e89b652670e9a57b0f00c2
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837851"
---
# <a name="namedpipe-activation"></a><span data-ttu-id="857ea-102">NamedPipe Activation</span><span class="sxs-lookup"><span data-stu-id="857ea-102">NamedPipe Activation</span></span>

<span data-ttu-id="857ea-103">Este exemplo demonstra a hospedagem de um serviço que usa o WAS (serviço de ativação de processos do Windows) para ativar um serviço que se comunica em pipes de nomes.</span><span class="sxs-lookup"><span data-stu-id="857ea-103">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="857ea-104">Este exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e requer que o Windows Vista seja executado.</span><span class="sxs-lookup"><span data-stu-id="857ea-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and requires Windows Vista to run.</span></span>

> [!NOTE]
> <span data-ttu-id="857ea-105">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="857ea-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="857ea-106">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="857ea-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="857ea-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="857ea-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="857ea-108">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="857ea-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="857ea-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="857ea-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a><span data-ttu-id="857ea-110">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="857ea-110">Sample Details</span></span>

<span data-ttu-id="857ea-111">O exemplo consiste em um programa de console do cliente (. exe) e uma biblioteca de serviços (. dll) hospedados em um processo de trabalho ativado pelo WAS (serviços de ativação de processos do Windows).</span><span class="sxs-lookup"><span data-stu-id="857ea-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="857ea-112">A atividade do cliente fica visível na janela do console.</span><span class="sxs-lookup"><span data-stu-id="857ea-112">Client activity is visible in the console window.</span></span>

<span data-ttu-id="857ea-113">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="857ea-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="857ea-114">O contrato é definido pela interface `ICalculator`, que expõe operações matemáticas (adicionar, subtrair, multiplicar e dividir), conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="857ea-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>

```csharp
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

<span data-ttu-id="857ea-115">O cliente faz solicitações síncronas para uma determinada operação matemática e a implementação do serviço calcula e retorna o resultado apropriado.</span><span class="sxs-lookup"><span data-stu-id="857ea-115">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>

```csharp
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

<span data-ttu-id="857ea-116">O exemplo usa uma associação de `netNamedPipeBinding` modificada sem segurança.</span><span class="sxs-lookup"><span data-stu-id="857ea-116">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="857ea-117">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="857ea-117">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="857ea-118">O tipo de associação para o serviço é especificado no atributo `binding` do elemento de ponto de extremidade, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="857ea-118">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>

<span data-ttu-id="857ea-119">Se você quiser usar uma associação de pipe nomeado segura, altere o modo de segurança do servidor para a configuração de segurança desejada e execute svcutil. exe novamente no cliente para obter um arquivo de configuração de cliente atualizado.</span><span class="sxs-lookup"><span data-stu-id="857ea-119">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>

```xml
<system.serviceModel>
        <services>
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">

        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->
        <endpoint address=""
                  binding="netNamedPipeBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexNamedPipeBinding"
                  contract="IMetadataExchange" />
      </service>
        </services>
        <bindings>
            <netNamedPipeBinding>
                <binding name="Binding1" >
                    <security mode = "None">
                    </security>
                </binding >
            </netNamedPipeBinding>
        </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="857ea-120">As informações de ponto de extremidade do cliente são configuradas conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="857ea-120">The client’s endpoint information is configured as shown in the following sample code.</span></span>

```xml
<system.serviceModel>

    <client>
      <endpoint name=""
                          address="net.pipe://localhost/servicemodelsamples/service.svc"
                          binding="netNamedPipeBinding"
                          bindingConfiguration="Binding1"
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>

    <bindings>

      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.
            Each property is configured with the default value. -->

      <netNamedPipeBinding>
        <binding name="Binding1"
                         maxBufferSize="65536"
                         maxConnections="10">
          <security mode = "None">
          </security>
        </binding >

      </netNamedPipeBinding>
    </bindings>

  </system.serviceModel>
```

<span data-ttu-id="857ea-121">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="857ea-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="857ea-122">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="857ea-122">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="857ea-123">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="857ea-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="857ea-124">Verifique se o IIS 7,0 está instalado.</span><span class="sxs-lookup"><span data-stu-id="857ea-124">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="857ea-125">O IIS 7,0 é necessário para a ativação do WAS.</span><span class="sxs-lookup"><span data-stu-id="857ea-125">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="857ea-126">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="857ea-126">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="857ea-127">Além disso, você deve instalar os componentes de ativação não HTTP do WCF:</span><span class="sxs-lookup"><span data-stu-id="857ea-127">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="857ea-128">No menu **Iniciar**, selecione **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="857ea-128">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="857ea-129">Selecione **programas e recursos**.</span><span class="sxs-lookup"><span data-stu-id="857ea-129">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="857ea-130">Clique em **Ativar ou desativar componentes do Windows**.</span><span class="sxs-lookup"><span data-stu-id="857ea-130">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="857ea-131">Expanda o nó **Microsoft .NET Framework 3,0** e verifique o Windows Communication Foundation recurso de **ativação não http** .</span><span class="sxs-lookup"><span data-stu-id="857ea-131">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="857ea-132">Configure o WAS (serviço de ativação de processos do Windows) para dar suporte à ativação de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="857ea-132">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>

    <span data-ttu-id="857ea-133">Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado AddNetPipeSiteBinding. cmd localizado no diretório de exemplo.</span><span class="sxs-lookup"><span data-stu-id="857ea-133">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="857ea-134">Para dar suporte à ativação do NET. pipe, o site padrão deve primeiro ser associado ao protocolo net. pipe.</span><span class="sxs-lookup"><span data-stu-id="857ea-134">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="857ea-135">Isso pode ser feito usando o Appcmd. exe, que é instalado com o conjunto de ferramentas de gerenciamento do IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="857ea-135">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="857ea-136">Em um prompt de comando elevado (administrador), execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="857ea-136">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="857ea-137">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="857ea-137">This command is a single line of text.</span></span>

        <span data-ttu-id="857ea-138">Este comando adiciona uma associação de site net. pipe ao site padrão.</span><span class="sxs-lookup"><span data-stu-id="857ea-138">This command adds a net.pipe site binding to the default Web site.</span></span>

    2. <span data-ttu-id="857ea-139">Embora todos os aplicativos em um site compartilhem uma associação net. pipe comum, cada aplicativo pode habilitar o suporte a net. pipe individualmente.</span><span class="sxs-lookup"><span data-stu-id="857ea-139">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="857ea-140">Para habilitar net. pipe para o aplicativo/servicemodelsamples, execute o comando a seguir em um prompt de comando elevado.</span><span class="sxs-lookup"><span data-stu-id="857ea-140">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > <span data-ttu-id="857ea-141">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="857ea-141">This command is a single line of text.</span></span>

        <span data-ttu-id="857ea-142">Esse comando permite que o aplicativo/servicemodelsamples seja acessado usando `http://localhost/servicemodelsamples` e `net.tcp://localhost/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="857ea-142">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="857ea-143">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="857ea-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="857ea-144">Remova a associação de site net. pipe que você adicionou para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="857ea-144">Remove the net.pipe site binding you added for this sample.</span></span>

    <span data-ttu-id="857ea-145">Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado RemoveNetPipeSiteBinding. cmd localizado no diretório de exemplo:</span><span class="sxs-lookup"><span data-stu-id="857ea-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="857ea-146">Remova net. TCP da lista de protocolos habilitados executando o comando a seguir em um prompt de comandos com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="857ea-146">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="857ea-147">Esse comando deve ser inserido como uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="857ea-147">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="857ea-148">Remova a associação do site net. TCP executando o comando a seguir em um prompt de comando elevado.</span><span class="sxs-lookup"><span data-stu-id="857ea-148">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="857ea-149">Esse comando deve ser digitado como uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="857ea-149">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="857ea-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="857ea-150">See also</span></span>

- <span data-ttu-id="857ea-151">[Exemplos de persistência e de hospedagem do AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="857ea-151">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
