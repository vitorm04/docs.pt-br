---
title: NamedPipe Activation
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: a7d940d6be56160945ca0f8697361314af96bc0b
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487548"
---
# <a name="namedpipe-activation"></a><span data-ttu-id="d6353-102">NamedPipe Activation</span><span class="sxs-lookup"><span data-stu-id="d6353-102">NamedPipe Activation</span></span>

<span data-ttu-id="d6353-103">Este exemplo demonstra como hospedar um serviço que usa o serviço de ativação de processos do Windows (WAS) para ativar um serviço que se comunica por pipes de nomes.</span><span class="sxs-lookup"><span data-stu-id="d6353-103">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="d6353-104">Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e requer [!INCLUDE[wv](../../../../includes/wv-md.md)] para executar.</span><span class="sxs-lookup"><span data-stu-id="d6353-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and requires [!INCLUDE[wv](../../../../includes/wv-md.md)] to run.</span></span>

> [!NOTE]
> <span data-ttu-id="d6353-105">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="d6353-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6353-106">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d6353-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d6353-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d6353-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d6353-108">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="d6353-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d6353-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="d6353-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a><span data-ttu-id="d6353-110">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="d6353-110">Sample Details</span></span>

<span data-ttu-id="d6353-111">O exemplo consiste em um programa de console de cliente (.exe) e uma biblioteca de serviço (. dll) hospedado em um processo de trabalho ativado, o Windows WAS Process Activation Services ().</span><span class="sxs-lookup"><span data-stu-id="d6353-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="d6353-112">Atividade do cliente está visível na janela do console.</span><span class="sxs-lookup"><span data-stu-id="d6353-112">Client activity is visible in the console window.</span></span>

<span data-ttu-id="d6353-113">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="d6353-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="d6353-114">O contrato é definido o `ICalculator` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir), conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d6353-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>

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

<span data-ttu-id="d6353-115">O cliente faz solicitações síncronas para uma operação matemática determinada e a implementação do serviço calcula e retorna o resultado apropriado.</span><span class="sxs-lookup"><span data-stu-id="d6353-115">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>

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

<span data-ttu-id="d6353-116">O exemplo usa uma modificação `netNamedPipeBinding` associação sem segurança.</span><span class="sxs-lookup"><span data-stu-id="d6353-116">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="d6353-117">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="d6353-117">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="d6353-118">O tipo de associação para o serviço é especificado no elemento de ponto de extremidade `binding` conforme mostrado no seguinte exemplo de configuração do atributo.</span><span class="sxs-lookup"><span data-stu-id="d6353-118">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>

<span data-ttu-id="d6353-119">Se você quiser usar uma associação de pipe nomeado protegida, altere o modo de segurança do servidor para a configuração de segurança desejado e execute svcutil.exe novamente no cliente para obter o arquivo de configuração de um cliente atualizado.</span><span class="sxs-lookup"><span data-stu-id="d6353-119">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>

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

<span data-ttu-id="d6353-120">Informações de ponto de extremidade do cliente são configuradas como mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d6353-120">The client’s endpoint information is configured as shown in the following sample code.</span></span>

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

<span data-ttu-id="d6353-121">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="d6353-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d6353-122">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="d6353-122">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d6353-123">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="d6353-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d6353-124">Certifique-se de que o IIS 7.0 é instalado.</span><span class="sxs-lookup"><span data-stu-id="d6353-124">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="d6353-125">O IIS 7.0 é necessária para a ativação do WAS.</span><span class="sxs-lookup"><span data-stu-id="d6353-125">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="d6353-126">Verifique se você tiver executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d6353-126">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="d6353-127">Além disso, você deve instalar os componentes de ativação não HTTP do WCF:</span><span class="sxs-lookup"><span data-stu-id="d6353-127">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="d6353-128">No menu **Iniciar**, selecione **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="d6353-128">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="d6353-129">Selecione **programas e recursos**.</span><span class="sxs-lookup"><span data-stu-id="d6353-129">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="d6353-130">Clique em **ativar ou desativar a componentes do Windows**.</span><span class="sxs-lookup"><span data-stu-id="d6353-130">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="d6353-131">Expanda o **Microsoft .NET Framework 3.0** nó e verifique se o **ativação não HTTP do Windows Communication Foundation** recurso.</span><span class="sxs-lookup"><span data-stu-id="d6353-131">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="d6353-132">Configure o Windows processo Activation Service (WAS) para dar suporte à ativação de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="d6353-132">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>

    <span data-ttu-id="d6353-133">Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado AddNetPipeSiteBinding.cmd localizado no diretório de exemplo.</span><span class="sxs-lookup"><span data-stu-id="d6353-133">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="d6353-134">Para dar suporte à ativação de pipe, o site padrão primeiro deve ser associado ao protocolo NET. pipe.</span><span class="sxs-lookup"><span data-stu-id="d6353-134">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="d6353-135">Isso pode ser feito usando appcmd.exe, que é instalado com o conjunto de ferramentas de gerenciamento do IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="d6353-135">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="d6353-136">Em um prompt de comando com privilégios elevados (administrador), execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="d6353-136">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="d6353-137">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="d6353-137">This command is a single line of text.</span></span>

        <span data-ttu-id="d6353-138">Este comando adiciona uma associação de site do NET. pipe para o site padrão.</span><span class="sxs-lookup"><span data-stu-id="d6353-138">This command adds a net.pipe site binding to the default Web site.</span></span>

    2. <span data-ttu-id="d6353-139">Embora todos os aplicativos dentro de um site compartilham uma associação de pipe comuns, cada aplicativo pode habilitar o suporte do NET. pipe individualmente.</span><span class="sxs-lookup"><span data-stu-id="d6353-139">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="d6353-140">Para habilitar o NET. pipe para o aplicativo /servicemodelsamples, execute o seguinte comando em um prompt de comando elevado.</span><span class="sxs-lookup"><span data-stu-id="d6353-140">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > <span data-ttu-id="d6353-141">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="d6353-141">This command is a single line of text.</span></span>

        <span data-ttu-id="d6353-142">Este comando habilita o aplicativo /servicemodelsamples sejam acessados usando ambos `http://localhost/servicemodelsamples` e `net.tcp://localhost/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="d6353-142">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="d6353-143">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d6353-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="d6353-144">Remova a associação de site do NET. pipe que é adicionado para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="d6353-144">Remove the net.pipe site binding you added for this sample.</span></span>

    <span data-ttu-id="d6353-145">Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado RemoveNetPipeSiteBinding.cmd localizado no diretório de exemplo:</span><span class="sxs-lookup"><span data-stu-id="d6353-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="d6353-146">Remova o NET. TCP da lista de protocolos habilitados, executando o seguinte comando em um prompt de comando elevado.</span><span class="sxs-lookup"><span data-stu-id="d6353-146">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="d6353-147">Esse comando deve ser inserido como uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="d6353-147">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="d6353-148">Remova a associação de site do NET. TCP, executando o seguinte comando em um prompt de comando elevado.</span><span class="sxs-lookup"><span data-stu-id="d6353-148">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>

        ```
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="d6353-149">Esse comando deve ser digitado como uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="d6353-149">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6353-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6353-150">See also</span></span>

- <span data-ttu-id="d6353-151">[Hospedagem de AppFabric e persistência exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d6353-151">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
