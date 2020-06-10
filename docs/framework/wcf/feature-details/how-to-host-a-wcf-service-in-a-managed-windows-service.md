---
title: Como hospedar um serviço WCF em um serviço Windows gerenciado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: dbd51abbc30b1010f7c4f206aad9a773eca0a714
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593172"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="52d22-102">Como hospedar um serviço WCF em um serviço Windows gerenciado</span><span class="sxs-lookup"><span data-stu-id="52d22-102">How to: Host a WCF Service in a Managed Windows Service</span></span>

<span data-ttu-id="52d22-103">Este tópico descreve as etapas básicas necessárias para criar um serviço de Windows Communication Foundation (WCF) que é hospedado por um serviço do Windows.</span><span class="sxs-lookup"><span data-stu-id="52d22-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted by a Windows Service.</span></span> <span data-ttu-id="52d22-104">O cenário é habilitado pela opção de Hospedagem de serviço do Windows gerenciado que é um serviço WCF de longa execução hospedado fora do Serviços de Informações da Internet (IIS) em um ambiente seguro que não é ativado pela mensagem.</span><span class="sxs-lookup"><span data-stu-id="52d22-104">The scenario is enabled by the managed Windows service hosting option that is a long-running WCF service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="52d22-105">O tempo de vida do serviço é controlado pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="52d22-105">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="52d22-106">Essa opção de hospedagem está disponível em todas as versões do Windows.</span><span class="sxs-lookup"><span data-stu-id="52d22-106">This hosting option is available in all versions of Windows.</span></span>

<span data-ttu-id="52d22-107">Os serviços Windows podem ser gerenciados com o Microsoft.ManagementConsole.SnapIn no MMC (Console de Gerenciamento Microsoft) e podem ser configurados para início automático quando o sistema for inicializado.</span><span class="sxs-lookup"><span data-stu-id="52d22-107">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="52d22-108">Essa opção de hospedagem consiste em registrar o domínio do aplicativo (AppDomain) que hospeda um serviço WCF como um serviço gerenciado do Windows para que o tempo de vida do processo do serviço seja controlado pelo SCM (Gerenciador de controle de serviço) para serviços do Windows.</span><span class="sxs-lookup"><span data-stu-id="52d22-108">This hosting option consists of registering the application domain (AppDomain) that hosts a WCF service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>

<span data-ttu-id="52d22-109">O código do serviço inclui uma implementação de serviço do contrato do serviço, de uma classe do serviço Windows e de uma classe de instalador.</span><span class="sxs-lookup"><span data-stu-id="52d22-109">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="52d22-110">A classe de implementação de serviço, `CalculatorService` , é um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="52d22-110">The service implementation class, `CalculatorService`, is a WCF service.</span></span> <span data-ttu-id="52d22-111">O `CalculatorWindowsService` é um serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="52d22-111">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="52d22-112">Para qualificar-se como um serviço Windows, a classe herda de `ServiceBase` e implementa os métodos `OnStart` e `OnStop`.</span><span class="sxs-lookup"><span data-stu-id="52d22-112">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="52d22-113">Em `OnStart`, um <xref:System.ServiceModel.ServiceHost> é criado para o tipo `CalculatorService` e é aberto.</span><span class="sxs-lookup"><span data-stu-id="52d22-113">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="52d22-114">Em `OnStop`, o serviço é interrompido e descartado.</span><span class="sxs-lookup"><span data-stu-id="52d22-114">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="52d22-115">O host também é responsável por fornecer um endereço básico ao host de serviço, que foi configurado nas configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="52d22-115">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="52d22-116">A classe de instalador, que herda de <xref:System.Configuration.Install.Installer>, permite que o programa seja instalado como um serviço Windows pela ferramenta Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="52d22-116">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>

## <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="52d22-117">Construir o serviço e fornecer o código de hospedagem</span><span class="sxs-lookup"><span data-stu-id="52d22-117">Construct the service and provide the hosting code</span></span>

1. <span data-ttu-id="52d22-118">Crie um novo projeto de **aplicativo de console** do Visual Studio chamado **serviço**.</span><span class="sxs-lookup"><span data-stu-id="52d22-118">Create a new Visual Studio **Console app** project called **Service**.</span></span>

2. <span data-ttu-id="52d22-119">Renomeie Program.cs como Service.cs.</span><span class="sxs-lookup"><span data-stu-id="52d22-119">Rename Program.cs to Service.cs.</span></span>

3. <span data-ttu-id="52d22-120">Altere o namespace para `Microsoft.ServiceModel.Samples` .</span><span class="sxs-lookup"><span data-stu-id="52d22-120">Change the namespace to `Microsoft.ServiceModel.Samples`.</span></span>

4. <span data-ttu-id="52d22-121">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="52d22-121">Add references to the following assemblies:</span></span>

    - <span data-ttu-id="52d22-122">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="52d22-122">System.ServiceModel.dll</span></span>

    - <span data-ttu-id="52d22-123">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="52d22-123">System.ServiceProcess.dll</span></span>

    - <span data-ttu-id="52d22-124">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="52d22-124">System.Configuration.Install.dll</span></span>

5. <span data-ttu-id="52d22-125">Adicione as instruções de uso a seguir a Service.cs.</span><span class="sxs-lookup"><span data-stu-id="52d22-125">Add the following using statements to Service.cs.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. <span data-ttu-id="52d22-126">Defina o contrato de serviço `ICalculator` como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="52d22-126">Define the `ICalculator` service contract as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. <span data-ttu-id="52d22-127">Implemente o contrato de serviço em uma classe chamada `CalculatorService` como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="52d22-127">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. <span data-ttu-id="52d22-128">Crie uma nova classe chamada `CalculatorWindowsService` que herda da classe <xref:System.ServiceProcess.ServiceBase>.</span><span class="sxs-lookup"><span data-stu-id="52d22-128">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="52d22-129">Adicione uma variável local chamada `serviceHost` para fazer referência à instância <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="52d22-129">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="52d22-130">Defina o método `Main` que chama `ServiceBase.Run(new CalculatorWindowsService)`</span><span class="sxs-lookup"><span data-stu-id="52d22-130">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. <span data-ttu-id="52d22-131">Substitua o método <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> criando e abrindo uma nova instância <xref:System.ServiceModel.ServiceHost> como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="52d22-131">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. <span data-ttu-id="52d22-132">Substitua o método <xref:System.ServiceProcess.ServiceBase.OnStop%2A> fechando <xref:System.ServiceModel.ServiceHost> como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="52d22-132">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. <span data-ttu-id="52d22-133">Crie uma nova classe chamada `ProjectInstaller` que herda de <xref:System.Configuration.Install.Installer> e que é marcada com <xref:System.ComponentModel.RunInstallerAttribute> definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="52d22-133">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="52d22-134">Isso permite que o serviço Windows seja instalado pela ferramenta Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="52d22-134">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. <span data-ttu-id="52d22-135">Remova a classe `Service` que foi gerada quando você criou o projeto.</span><span class="sxs-lookup"><span data-stu-id="52d22-135">Remove the `Service` class that was generated when you created the project.</span></span>

13. <span data-ttu-id="52d22-136">Adicione um arquivo de configuração de aplicativo ao projeto.</span><span class="sxs-lookup"><span data-stu-id="52d22-136">Add an application configuration file to the project.</span></span> <span data-ttu-id="52d22-137">Substitua o conteúdo do arquivo pelo XML de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="52d22-137">Replace the contents of the file with the following configuration XML.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.serviceModel>    <services>
          <!-- This section is optional with the new configuration model
               introduced in .NET Framework 4. -->
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"
                   behaviorConfiguration="CalculatorServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
            <endpoint address=""
                      binding="wsHttpBinding"
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />
          </service>
        </services>
        <behaviors>
          <serviceBehaviors>
            <behavior name="CalculatorServiceBehavior">
              <serviceMetadata httpGetEnabled="true"/>
              <serviceDebug includeExceptionDetailInFaults="False"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>
      </system.serviceModel>
    </configuration>
    ```

     <span data-ttu-id="52d22-138">Clique com o botão direito do mouse no arquivo app. config na **Gerenciador de soluções** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="52d22-138">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="52d22-139">Em **copiar para diretório de saída** , selecione **copiar se mais recente**.</span><span class="sxs-lookup"><span data-stu-id="52d22-139">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>

     <span data-ttu-id="52d22-140">Este exemplo especifica explicitamente pontos de extremidade no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="52d22-140">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="52d22-141">Se você não adicionar nenhum ponto de extremidade ao serviço, o runtime adicionará pontos de extremidade padrão para você.</span><span class="sxs-lookup"><span data-stu-id="52d22-141">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="52d22-142">Neste exemplo, como o serviço tem <xref:System.ServiceModel.Description.ServiceMetadataBehavior> definido como `true`, seu serviço também possui metadados de publicação habilitados.</span><span class="sxs-lookup"><span data-stu-id="52d22-142">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> <span data-ttu-id="52d22-143">Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../simplified-configuration.md) e [Configuração simplificada para serviços WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="52d22-143">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="install-and-run-the-service"></a><span data-ttu-id="52d22-144">Instalar e executar o serviço</span><span class="sxs-lookup"><span data-stu-id="52d22-144">Install and run the service</span></span>

1. <span data-ttu-id="52d22-145">Crie a solução para criar o executável `Service.exe`.</span><span class="sxs-lookup"><span data-stu-id="52d22-145">Build the solution to create the `Service.exe` executable.</span></span>

2. <span data-ttu-id="52d22-146">Abra Prompt de Comando do Desenvolvedor para o Visual Studio e navegue até o diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="52d22-146">Open Developer Command Prompt for Visual Studio and navigate to the project directory.</span></span> <span data-ttu-id="52d22-147">Digite `installutil bin\service.exe` no prompt de comando para instalar o serviço do Windows.</span><span class="sxs-lookup"><span data-stu-id="52d22-147">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>

     <span data-ttu-id="52d22-148">Digite `services.msc` no prompt de comando para acessar o SCM.</span><span class="sxs-lookup"><span data-stu-id="52d22-148">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="52d22-149">O serviço Windows deve aparecer em Serviços como “WCFWindowsServiceSample”.</span><span class="sxs-lookup"><span data-stu-id="52d22-149">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="52d22-150">O serviço WCF só poderá responder a clientes se o serviço do Windows estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="52d22-150">The WCF service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="52d22-151">Para iniciar o serviço, clique com o botão direito do mouse no SCM e selecione "Iniciar" ou digite **net start WCFWindowsServiceSample** no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="52d22-151">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>

3. <span data-ttu-id="52d22-152">Se você fizer alterações no serviço, interrompa-o primeiro e desinstale-o.</span><span class="sxs-lookup"><span data-stu-id="52d22-152">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="52d22-153">Para interromper o serviço, clique com o botão direito do mouse no serviço no SCM e selecione "parar" ou **digite net stop WCFWindowsServiceSample** no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="52d22-153">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="52d22-154">Observe que se você interromper o serviço Windows e executar um cliente, uma exceção <xref:System.ServiceModel.EndpointNotFoundException> ocorrerá quando o cliente tentar acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="52d22-154">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="52d22-155">Para desinstalar o tipo de serviço do Windows **InstallUtil/u bin\service.exe** no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="52d22-155">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>

## <a name="example"></a><span data-ttu-id="52d22-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52d22-156">Example</span></span>

<span data-ttu-id="52d22-157">A seguir está uma lista completa do código usado por este tópico:</span><span class="sxs-lookup"><span data-stu-id="52d22-157">The following is a complete listing of the code used by this topic:</span></span>

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

<span data-ttu-id="52d22-158">Como a opção de "auto-hospedagem", o ambiente de hospedagem de serviços Windows requer que algum código de hospedagem seja criado como parte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="52d22-158">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="52d22-159">O serviço é implementado como um aplicativo de console e contém seu próprio código de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="52d22-159">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="52d22-160">Em outros ambientes de hospedagem, como o WAS (Serviço de Ativação de Processos do Windows), hospedado no IIS, não é necessário que os desenvolvedores criem código de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="52d22-160">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>

## <a name="see-also"></a><span data-ttu-id="52d22-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52d22-161">See also</span></span>

- [<span data-ttu-id="52d22-162">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="52d22-162">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="52d22-163">Hospedagem em um aplicativo gerenciado</span><span class="sxs-lookup"><span data-stu-id="52d22-163">Hosting in a Managed Application</span></span>](hosting-in-a-managed-application.md)
- [<span data-ttu-id="52d22-164">Hospedando serviços</span><span class="sxs-lookup"><span data-stu-id="52d22-164">Hosting Services</span></span>](../hosting-services.md)
- <span data-ttu-id="52d22-165">[Recursos de hospedagem do Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="52d22-165">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
