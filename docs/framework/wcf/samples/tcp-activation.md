---
title: Ativação TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: c10cc1edfb06d55fc8a59a32bf905c95b20a19dc
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084618"
---
# <a name="tcp-activation"></a><span data-ttu-id="5a907-102">Ativação TCP</span><span class="sxs-lookup"><span data-stu-id="5a907-102">TCP Activation</span></span>
<span data-ttu-id="5a907-103">Este exemplo demonstra como hospedar um serviço que usa Windows processo WAS (Activation Services) para ativar um serviço que se comunica através do protocolo NET. TCP.</span><span class="sxs-lookup"><span data-stu-id="5a907-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="5a907-104">Este exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5a907-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a907-105">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5a907-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5a907-106">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5a907-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5a907-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5a907-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5a907-108">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="5a907-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a907-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5a907-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`  
  
 <span data-ttu-id="5a907-110">O exemplo consiste em um programa de console de cliente (.exe) e uma biblioteca de serviço (. dll) hospedado em um processo de trabalho ativado pelo WAS.</span><span class="sxs-lookup"><span data-stu-id="5a907-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="5a907-111">Atividade do cliente está visível na janela do console.</span><span class="sxs-lookup"><span data-stu-id="5a907-111">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="5a907-112">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="5a907-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="5a907-113">O contrato é definido o `ICalculator` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir), conforme mostrado no código de exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5a907-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>  
  
```  
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
  
 <span data-ttu-id="5a907-114">A implementação do serviço calcula e retorna o resultado apropriado:</span><span class="sxs-lookup"><span data-stu-id="5a907-114">The service implementation calculates and returns the appropriate result:</span></span>  
  
```  
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
  
 <span data-ttu-id="5a907-115">O exemplo usa uma variante do NET. TCP associação com segurança desativada e o compartilhamento de porta do TCP está habilitado.</span><span class="sxs-lookup"><span data-stu-id="5a907-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="5a907-116">Se você quiser usar uma associação segura de TCP, altere o modo de segurança do servidor para a configuração desejada e execute novamente o Svcutil.exe no cliente para gerar um arquivo de configuração de cliente de atualização.</span><span class="sxs-lookup"><span data-stu-id="5a907-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>  
  
 <span data-ttu-id="5a907-117">O exemplo a seguir mostra a configuração para o serviço:</span><span class="sxs-lookup"><span data-stu-id="5a907-117">The following sample shows the configuration for the service:</span></span>  
  
```xml  
<system.serviceModel>  
  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->  
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexTcpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="PortSharingBinding" portSharingEnabled="true">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
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
  
 <span data-ttu-id="5a907-118">Ponto de extremidade do cliente é configurado como mostrado no código de exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5a907-118">The client's endpoint is configured as shown in the following sample code:</span></span>  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <netTcpBinding>  
          <binding name="NetTcpBinding_ICalculator">  
            <security mode="None"/>  
          </binding>  
        </netTcpBinding>  
    </bindings>  
    <client>  
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"  
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />  
    </client>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5a907-119">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="5a907-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5a907-120">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="5a907-120">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5a907-121">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5a907-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5a907-122">Certifique-se de que [!INCLUDE[iisver](../../../../includes/iisver-md.md)] está instalado.</span><span class="sxs-lookup"><span data-stu-id="5a907-122">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed.</span></span> [!INCLUDE[iisver](../../../../includes/iisver-md.md)]<span data-ttu-id="5a907-123"> é necessário para a ativação do WAS.</span><span class="sxs-lookup"><span data-stu-id="5a907-123"> is required for WAS activation.</span></span>  
  
2.  <span data-ttu-id="5a907-124">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a907-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
     <span data-ttu-id="5a907-125">Além disso, você deve instalar os componentes de ativação não HTTP do WCF:</span><span class="sxs-lookup"><span data-stu-id="5a907-125">In addition, you must install the WCF non-HTTP activation components:</span></span>  
  
    1.  <span data-ttu-id="5a907-126">Dos **inicie** menu, escolha **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="5a907-126">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="5a907-127">Selecione **programas e recursos**.</span><span class="sxs-lookup"><span data-stu-id="5a907-127">Select **Programs and Features**.</span></span>  
  
    3.  <span data-ttu-id="5a907-128">Clique em **ativar ou desativar a componentes do Windows**.</span><span class="sxs-lookup"><span data-stu-id="5a907-128">Click **Turn Windows Components on or Off**.</span></span>  
  
    4.  <span data-ttu-id="5a907-129">Expanda o **Microsoft .NET Framework 3.0** nó e verifique se o **ativação não HTTP do Windows Communication Foundation** recurso.</span><span class="sxs-lookup"><span data-stu-id="5a907-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3.  <span data-ttu-id="5a907-130">Configure o WAS para dar suporte à ativação de TCP.</span><span class="sxs-lookup"><span data-stu-id="5a907-130">Configure WAS to support TCP activation.</span></span>  
  
     <span data-ttu-id="5a907-131">Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado AddNetTcpSiteBinding.cmd localizado no diretório de exemplo.</span><span class="sxs-lookup"><span data-stu-id="5a907-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="5a907-132">Para dar suporte à ativação de NET. TCP, o site padrão primeiro deve ser associado a uma porta NET. TCP.</span><span class="sxs-lookup"><span data-stu-id="5a907-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="5a907-133">Isso pode ser feito usando Appcmd.exe, que é instalado com o conjunto de ferramentas de gerenciamento do Internet Information Services 7.0 (IIS).</span><span class="sxs-lookup"><span data-stu-id="5a907-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="5a907-134">Em um prompt de comando com nível de administrador, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="5a907-134">From an administrator-level command prompt, run the following command:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!TIP]
        >  <span data-ttu-id="5a907-135">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="5a907-135">This command is a single line of text.</span></span> <span data-ttu-id="5a907-136">Este comando adiciona uma associação de site do NET. TCP para o site padrão escuta na porta TCP 808 com qualquer nome de host.</span><span class="sxs-lookup"><span data-stu-id="5a907-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>  
  
    2.  <span data-ttu-id="5a907-137">Embora todos os aplicativos dentro de um site compartilham uma associação comum de NET. TCP, cada aplicativo pode habilitar o suporte do NET. TCP individualmente.</span><span class="sxs-lookup"><span data-stu-id="5a907-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="5a907-138">Para habilitar o NET. TCP para o aplicativo /servicemodelsamples, execute o seguinte comando em um prompt de comando com nível de administrador:</span><span class="sxs-lookup"><span data-stu-id="5a907-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="5a907-139">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="5a907-139">This command is a single line of text.</span></span> <span data-ttu-id="5a907-140">Este comando habilita o aplicativo /servicemodelsamples sejam acessados usando ambos http://localhost/servicemodelsamples e net.tcp://localhost/servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="5a907-140">This command enables the /servicemodelsamples application to be accessed using both http://localhost/servicemodelsamples and net.tcp://localhost/servicemodelsamples.</span></span>  
  
4.  <span data-ttu-id="5a907-141">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a907-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="5a907-142">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a907-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
     <span data-ttu-id="5a907-143">Remova a associação de site do NET. TCP que é adicionado para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="5a907-143">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="5a907-144">Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado RemoveNetTcpSiteBinding.cmd localizado no diretório de exemplo.</span><span class="sxs-lookup"><span data-stu-id="5a907-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="5a907-145">Remova NET. TCP da lista de protocolos habilitados, executando o seguinte comando em um prompt de comando com nível de administrador:</span><span class="sxs-lookup"><span data-stu-id="5a907-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="5a907-146">Esse comando deve ser inserido como uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="5a907-146">This command must be entered as a single line of text.</span></span>  
  
    2.  <span data-ttu-id="5a907-147">Remova a associação do site NET. TCP, executando o seguinte comando em um prompt de comando com nível de administrador:</span><span class="sxs-lookup"><span data-stu-id="5a907-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="5a907-148">Esse comando deve ser digitado como uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="5a907-148">This command must be typed in as a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a907-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a907-149">See Also</span></span>  
 [<span data-ttu-id="5a907-150">Hospedagem de AppFabric e persistência exemplos</span><span class="sxs-lookup"><span data-stu-id="5a907-150">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
