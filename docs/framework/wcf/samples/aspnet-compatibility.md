---
title: Compatibilidade ASP.NET
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: eeb09914fc90848c987127c789379549917063f6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659507"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="1cf42-102">Compatibilidade ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1cf42-102">ASP.NET Compatibility</span></span>
<span data-ttu-id="1cf42-103">Este exemplo demonstra como habilitar o modo de compatibilidade do ASP.NET no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1cf42-103">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="1cf42-104">Serviços em execução no modo participar totalmente no pipeline de aplicativo do ASP.NET e pode tornar a compatibilidade do ASP.NET usam recursos do ASP.NET, como autorização de URL do arquivo, estado de sessão e o <xref:System.Web.HttpContext> classe.</span><span class="sxs-lookup"><span data-stu-id="1cf42-104">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="1cf42-105">O <xref:System.Web.HttpContext> classe permite o acesso a cookies, sessões e outros recursos do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1cf42-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="1cf42-106">Esse modo requer que as associações usam o transporte HTTP e o serviço em si deve ser hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="1cf42-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>  
  
 <span data-ttu-id="1cf42-107">Neste exemplo, o cliente é um aplicativo de console (um executável) e o serviço está hospedado no Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="1cf42-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cf42-108">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="1cf42-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="1cf42-109">Este exemplo requer um [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] pool de aplicativos para executar.</span><span class="sxs-lookup"><span data-stu-id="1cf42-109">This sample requires a [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] application pool in order to run.</span></span> <span data-ttu-id="1cf42-110">Para criar um novo pool de aplicativos, ou para modificar o pool de aplicativos padrão, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="1cf42-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>  

1.  <span data-ttu-id="1cf42-111">Abra **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="1cf42-111">Open **Control Panel**.</span></span>  <span data-ttu-id="1cf42-112">Abra o **ferramentas administrativas** miniaplicativo sob o **sistema e segurança** título.</span><span class="sxs-lookup"><span data-stu-id="1cf42-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="1cf42-113">Abra o **serviços de informações da Internet (IIS) Manager** miniaplicativo.</span><span class="sxs-lookup"><span data-stu-id="1cf42-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>  

2.  <span data-ttu-id="1cf42-114">Expanda o modo de exibição de árvore na **conexões** painel.</span><span class="sxs-lookup"><span data-stu-id="1cf42-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="1cf42-115">Selecione o **Pools de aplicativos** nó.</span><span class="sxs-lookup"><span data-stu-id="1cf42-115">Select the **Application Pools** node.</span></span>  

3.  <span data-ttu-id="1cf42-116">Para definir o pool de aplicativos padrão para usar [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (que pode causar problemas de incompatibilidade com sites existentes), com o botão direito do **DefaultAppPool** do item de lista e selecione **configurações básicas...** .</span><span class="sxs-lookup"><span data-stu-id="1cf42-116">To set the default application pool to use [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="1cf42-117">Defina a **.Net Framework versão** suspenso para **.Net Framework v4.0.30128** (ou posterior).</span><span class="sxs-lookup"><span data-stu-id="1cf42-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>  

4.  <span data-ttu-id="1cf42-118">Para criar um novo pool de aplicativos que usa [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (para preservar a compatibilidade para outros aplicativos), clique com botão direito do **Pools de aplicativos** nó e selecione **Adicionar Pool de aplicativos...** .</span><span class="sxs-lookup"><span data-stu-id="1cf42-118">To create a new application pool that uses [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="1cf42-119">Nomeie o novo pool de aplicativos e defina as **.Net Framework versão** suspenso para **.Net Framework v4.0.30128** (ou posterior).</span><span class="sxs-lookup"><span data-stu-id="1cf42-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="1cf42-120">Depois de executar a instalação as etapas abaixo, clique com botão direito do **ServiceModelSamples** aplicativo e selecione **gerenciar aplicativo**, **configurações avançadas...** .</span><span class="sxs-lookup"><span data-stu-id="1cf42-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="1cf42-121">Defina as **Pool de aplicativos** para o novo pool de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1cf42-121">Set the **Application Pool** to the new application pool.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1cf42-122">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1cf42-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1cf42-123">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1cf42-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1cf42-124">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="1cf42-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1cf42-125">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="1cf42-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 <span data-ttu-id="1cf42-126">Este exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="1cf42-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="1cf42-127">O `ICalculator` contrato foi modificado como o `ICalculatorSession` de contrato para permitir que um conjunto de operações a serem executadas, mantendo um resultado em execução.</span><span class="sxs-lookup"><span data-stu-id="1cf42-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>  
  
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
  
 <span data-ttu-id="1cf42-128">O serviço mantém o estado, usando o recurso para cada cliente, como várias operações de serviço são chamadas para executar um cálculo.</span><span class="sxs-lookup"><span data-stu-id="1cf42-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="1cf42-129">O cliente pode recuperar o resultado atual chamando `Result` e pode limpar o resultado como zero chamando `Clear`.</span><span class="sxs-lookup"><span data-stu-id="1cf42-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>  
  
 <span data-ttu-id="1cf42-130">O serviço usa a sessão do ASP.NET para armazenar o resultado para cada sessão de cliente.</span><span class="sxs-lookup"><span data-stu-id="1cf42-130">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="1cf42-131">Isso permite que o serviço manter o resultado em execução para cada cliente em várias chamadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="1cf42-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1cf42-132">Estado de sessão ASP.NET e as sessões WCF são coisas muito diferentes.</span><span class="sxs-lookup"><span data-stu-id="1cf42-132">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="1cf42-133">Ver [sessão](../../../../docs/framework/wcf/samples/session.md) para obter detalhes sobre as sessões WCF.</span><span class="sxs-lookup"><span data-stu-id="1cf42-133">See [Session](../../../../docs/framework/wcf/samples/session.md) for details on WCF sessions.</span></span>
  
 <span data-ttu-id="1cf42-134">O serviço tem uma dependência profunda no estado de sessão ASP.NET e requer o modo de compatibilidade do ASP.NET para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="1cf42-134">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="1cf42-135">Esses requisitos são expressos declarativamente por meio da aplicação de `AspNetCompatibilityRequirements` atributo.</span><span class="sxs-lookup"><span data-stu-id="1cf42-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>  
  
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
  
 <span data-ttu-id="1cf42-136">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="1cf42-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1cf42-137">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="1cf42-137">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1cf42-138">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1cf42-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1cf42-139">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1cf42-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1cf42-140">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1cf42-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1cf42-141">Depois que a solução foi criada, execute Setup. bat para configurar o aplicativo ServiceModelSamples no [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1cf42-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="1cf42-142">O diretório ServiceModelSamples agora deve aparecer como um [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1cf42-142">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="1cf42-143">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1cf42-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf42-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cf42-144">See Also</span></span>  
 [<span data-ttu-id="1cf42-145">Hospedagem de AppFabric e persistência exemplos</span><span class="sxs-lookup"><span data-stu-id="1cf42-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
