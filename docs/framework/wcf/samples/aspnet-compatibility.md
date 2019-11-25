---
title: Compatibilidade ASP.NET
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: af03b16081f0e33764d3ef83519f6e50e6b97152
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141807"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="0f25b-102">Compatibilidade ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0f25b-102">ASP.NET Compatibility</span></span>

<span data-ttu-id="0f25b-103">Este exemplo demonstra como habilitar o modo de compatibilidade ASP.NET no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0f25b-103">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="0f25b-104">Os serviços em execução no modo de compatibilidade do ASP.NET participam totalmente do pipeline de aplicativo do ASP.NET e podem fazer uso de recursos do ASP.NET, como autorização de arquivo/URL, estado de sessão e a classe de <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="0f25b-104">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="0f25b-105">A classe <xref:System.Web.HttpContext> permite acesso a cookies, sessões e outros recursos do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0f25b-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="0f25b-106">Esse modo requer que as associações usem o transporte HTTP e o próprio serviço deve ser hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="0f25b-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>

<span data-ttu-id="0f25b-107">Neste exemplo, o cliente é um aplicativo de console (um executável) e o serviço é hospedado no Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="0f25b-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="0f25b-108">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="0f25b-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="0f25b-109">Este exemplo exige um pool de aplicativos .NET Framework 4 para ser executado.</span><span class="sxs-lookup"><span data-stu-id="0f25b-109">This sample requires a .NET Framework 4 application pool in order to run.</span></span> <span data-ttu-id="0f25b-110">Para criar um novo pool de aplicativos ou para modificar o pool de aplicativos padrão, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="0f25b-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>

1. <span data-ttu-id="0f25b-111">Abra **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="0f25b-111">Open **Control Panel**.</span></span>  <span data-ttu-id="0f25b-112">Abra o miniaplicativo **Ferramentas administrativas** no título **sistema e segurança** .</span><span class="sxs-lookup"><span data-stu-id="0f25b-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="0f25b-113">Abra o miniaplicativo **Gerenciador do serviços de informações da Internet (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="0f25b-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>

2. <span data-ttu-id="0f25b-114">Expanda o modo de exibição de árvore no painel **conexões** .</span><span class="sxs-lookup"><span data-stu-id="0f25b-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="0f25b-115">Selecione o nó **pools de aplicativos** .</span><span class="sxs-lookup"><span data-stu-id="0f25b-115">Select the **Application Pools** node.</span></span>

3. <span data-ttu-id="0f25b-116">Para definir o pool de aplicativos padrão a ser usado .NET Framework 4 (o que pode causar problemas de incompatibilidade com os sites existentes), clique com o botão direito do mouse no item de lista **DefaultAppPool** e selecione **configurações básicas.** .</span><span class="sxs-lookup"><span data-stu-id="0f25b-116">To set the default application pool to use .NET Framework 4 (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="0f25b-117">Defina o pull-down da **versão do .NET Framework** para o **.NET Framework v 4.0.30128** (ou posterior).</span><span class="sxs-lookup"><span data-stu-id="0f25b-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>

4. <span data-ttu-id="0f25b-118">Para criar um novo pool de aplicativos que usa o .NET Framework 4 (para preservar a compatibilidade de outros aplicativos), clique com o botão direito do mouse no nó **pools de aplicativos** e selecione **Adicionar pool de aplicativos...** .</span><span class="sxs-lookup"><span data-stu-id="0f25b-118">To create a new application pool that uses .NET Framework 4 (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="0f25b-119">Nomeie o novo pool de aplicativos e defina o pull-down da **versão do .NET Framework** para o **.NET Framework v 4.0.30128** (ou posterior).</span><span class="sxs-lookup"><span data-stu-id="0f25b-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="0f25b-120">Depois de executar as etapas de configuração abaixo, clique com o botão direito do mouse no aplicativo **ServiceModelSamples** e selecione **gerenciar aplicativo**, **Configurações avançadas...** .</span><span class="sxs-lookup"><span data-stu-id="0f25b-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="0f25b-121">Defina o **pool de aplicativos** para o novo pool de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="0f25b-121">Set the **Application Pool** to the new application pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f25b-122">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0f25b-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0f25b-123">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0f25b-123">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="0f25b-124">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="0f25b-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0f25b-125">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0f25b-125">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`

<span data-ttu-id="0f25b-126">Este exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="0f25b-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="0f25b-127">O contrato de `ICalculator` foi modificado como o contrato de `ICalculatorSession` para permitir que um conjunto de operações seja executado, mantendo um resultado em execução.</span><span class="sxs-lookup"><span data-stu-id="0f25b-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculatorSession
{
    [OperationContract]
    void Clear();
    [OperationContract]
    void AddTo(double n);
    [OperationContract]
    void SubtractFrom(double n);
    [OperationContract]
    void MultiplyBy(double n);
    [OperationContract]
    void DivideBy(double n);
    [OperationContract]
    double Result();
}
```

<span data-ttu-id="0f25b-128">O serviço mantém o estado, usando o recurso, para cada cliente, uma vez que várias operações de serviço são chamadas para executar um cálculo.</span><span class="sxs-lookup"><span data-stu-id="0f25b-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="0f25b-129">O cliente pode recuperar o resultado atual chamando `Result` e pode limpar o resultado para zero chamando `Clear`.</span><span class="sxs-lookup"><span data-stu-id="0f25b-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>

<span data-ttu-id="0f25b-130">O serviço usa a sessão ASP.NET para armazenar o resultado para cada sessão de cliente.</span><span class="sxs-lookup"><span data-stu-id="0f25b-130">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="0f25b-131">Isso permite que o serviço Mantenha o resultado em execução para cada cliente em várias chamadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="0f25b-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>

> [!NOTE]
> <span data-ttu-id="0f25b-132">O estado de sessão do ASP.NET e as sessões do WCF são coisas muito diferentes.</span><span class="sxs-lookup"><span data-stu-id="0f25b-132">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="0f25b-133">Consulte a [sessão](../../../../docs/framework/wcf/samples/session.md) para obter detalhes sobre as sessões do WCF.</span><span class="sxs-lookup"><span data-stu-id="0f25b-133">See [Session](../../../../docs/framework/wcf/samples/session.md) for details on WCF sessions.</span></span>

<span data-ttu-id="0f25b-134">O serviço tem uma dependência profunda no estado de sessão ASP.NET e requer que o modo de compatibilidade ASP.NET funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="0f25b-134">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="0f25b-135">Esses requisitos são expressos declarativamente aplicando o atributo `AspNetCompatibilityRequirements`.</span><span class="sxs-lookup"><span data-stu-id="0f25b-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>

```csharp
[AspNetCompatibilityRequirements(RequirementsMode =
                       AspNetCompatibilityRequirementsMode.Required)]
public class CalculatorService : ICalculatorSession
{
    double Result
    {  // store result in AspNet Session
       get {
          if (HttpContext.Current.Session["Result"] != null)
             return (double)HttpContext.Current.Session["Result"];
          return 0.0D;
       }
       set
       {
          HttpContext.Current.Session["Result"] = value;
       }
    }
    public void Clear()
    {
        Result = 0.0D;
    }
    public void AddTo(double n)
    {
        Result += n;
    }
    public void SubtractFrom(double n)
    {
        Result -= n;
    }
    public void MultiplyBy(double n)
    {
        Result *= n;
    }
    public void DivideBy(double n)
    {
        Result /= n;
    }
    public double Result()
    {
        return Result;
    }
}
```

<span data-ttu-id="0f25b-136">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="0f25b-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0f25b-137">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="0f25b-137">Press ENTER in the client window to shut down the client.</span></span>

```console
0, + 100, - 50, * 17.65, / 2 = 441.25
Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0f25b-138">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0f25b-138">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="0f25b-139">Certifique-se de ter executado o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0f25b-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="0f25b-140">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0f25b-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="0f25b-141">Depois que a solução tiver sido criada, execute Setup. bat para configurar o aplicativo ServiceModelSamples no IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="0f25b-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="0f25b-142">O diretório ServiceModelSamples agora deve aparecer como um aplicativo IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="0f25b-142">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="0f25b-143">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0f25b-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f25b-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f25b-144">See also</span></span>

- [<span data-ttu-id="0f25b-145">Exemplos de persistência e de hospedagem do AppFabric</span><span class="sxs-lookup"><span data-stu-id="0f25b-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
