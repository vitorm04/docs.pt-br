---
title: "Exemplo de segurança de mensagem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
caps.latest.revision: "33"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: a26356346ca3dfea858f286dd32cb08b0e3b3591
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-sample"></a><span data-ttu-id="83041-102">Exemplo de segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="83041-102">Message Security Sample</span></span>
<span data-ttu-id="83041-103">Este exemplo demonstra como implementar um aplicativo que usa o `basicHttpBinding` e segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="83041-103">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="83041-104">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de cálculo.</span><span class="sxs-lookup"><span data-stu-id="83041-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83041-105">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="83041-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="83041-106">O modo de segurança de `basicHttpBinding` podem ser definidas para os seguintes valores: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` e `None`.</span><span class="sxs-lookup"><span data-stu-id="83041-106">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="83041-107">No seguinte exemplo serviço App. config arquivo, a definição de ponto de extremidade Especifica o `basicHttpBinding` e faz referência a uma configuração de associação denominada `Binding1`, conforme mostrado no exemplo de configuração:</span><span class="sxs-lookup"><span data-stu-id="83041-107">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>   …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="83041-108">Os conjuntos de configuração de associação de `mode` atributo do [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) para `Message` e define o `clientCredentialType` atributo do [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)para `Certificate` conforme mostrado no exemplo de configuração:</span><span class="sxs-lookup"><span data-stu-id="83041-108">The binding configuration sets the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="83041-109">O certificado que o serviço usa para se autenticar para o cliente é definido na seção do arquivo de configuração em comportamentos a `serviceCredentials` elemento.</span><span class="sxs-lookup"><span data-stu-id="83041-109">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="83041-110">O modo de validação que se aplica ao certificado que o cliente usa para se autenticar para o serviço também é definido na seção comportamentos no `clientCertificate` elemento.</span><span class="sxs-lookup"><span data-stu-id="83041-110">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"   
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication   
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="83041-111">O mesmo detalhes de associação e segurança é especificado no arquivo de configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="83041-111">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="83041-112">A identidade do chamador é exibida na janela do console de serviço usando o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="83041-112">The identity of the caller is displayed in the service console window by using the following code:</span></span>  
  
```  
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```  
  
 <span data-ttu-id="83041-113">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="83041-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="83041-114">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="83041-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="83041-115">Para configurar e criar o exemplo</span><span class="sxs-lookup"><span data-stu-id="83041-115">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="83041-116">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="83041-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="83041-117">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="83041-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="83041-118">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="83041-118">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="83041-119">Execute bat da pasta de instalação do exemplo.</span><span class="sxs-lookup"><span data-stu-id="83041-119">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="83041-120">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="83041-120">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="83041-121">O arquivo em lotes bat é projetado para ser executado de um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="83041-121">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="83041-122">Isso requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="83041-122">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="83041-123">Essa variável de ambiente é definida automaticamente em um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="83041-123">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2.  <span data-ttu-id="83041-124">Execute o aplicativo de serviço do \service\bin.</span><span class="sxs-lookup"><span data-stu-id="83041-124">Run the service application from \service\bin.</span></span>  
  
3.  <span data-ttu-id="83041-125">Execute o aplicativo cliente de \Client\Bin.</span><span class="sxs-lookup"><span data-stu-id="83041-125">Run the client application from \client\bin.</span></span> <span data-ttu-id="83041-126">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="83041-126">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="83041-127">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="83041-127">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
5.  <span data-ttu-id="83041-128">Remova os certificados executando Cleanup.bat quando você tiver terminado com o exemplo.</span><span class="sxs-lookup"><span data-stu-id="83041-128">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="83041-129">Outros exemplos de segurança usam os mesmos certificados.</span><span class="sxs-lookup"><span data-stu-id="83041-129">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="83041-130">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="83041-130">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="83041-131">Crie um diretório no computador de serviço para os binários de serviço.</span><span class="sxs-lookup"><span data-stu-id="83041-131">Create a directory on the service machine for the service binaries.</span></span>  
  
2.  <span data-ttu-id="83041-132">Copie os arquivos de programa do serviço para o diretório de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="83041-132">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="83041-133">Também copie os arquivos. bat, Cleanup.bat e ImportClientCert.bat para o servidor.</span><span class="sxs-lookup"><span data-stu-id="83041-133">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3.  <span data-ttu-id="83041-134">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="83041-134">Create a directory on the client machine for the client binaries.</span></span>  
  
4.  <span data-ttu-id="83041-135">Copie os arquivos de programa do cliente para o diretório de cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="83041-135">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="83041-136">Também copie os arquivos. bat, Cleanup.bat e ImportServiceCert.bat ao cliente.</span><span class="sxs-lookup"><span data-stu-id="83041-136">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="83041-137">No servidor, execute `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="83041-137">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="83041-138">Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="83041-138">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="83041-139">Editar Service.exe.config para refletir o novo nome de certificado (no `findValue` atributo o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) elemento) que é o mesmo que o nome de domínio totalmente qualificado da máquina.</span><span class="sxs-lookup"><span data-stu-id="83041-139">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="83041-140">Também alterar o valor do endereço base para especificar um nome de computador totalmente qualificado em vez de localhost`.`</span><span class="sxs-lookup"><span data-stu-id="83041-140">Also change the value of the base address to specify a fully-qualified machine name instead of localhost`.`</span></span>  
  
7.  <span data-ttu-id="83041-141">Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="83041-141">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8.  <span data-ttu-id="83041-142">No cliente, execute `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="83041-142">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="83041-143">Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado client.com e exporta o certificado de cliente para um arquivo chamado cer.</span><span class="sxs-lookup"><span data-stu-id="83041-143">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="83041-144">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="83041-144">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="83041-145">Para fazer isso, substituindo o host local com o nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="83041-145">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="83041-146">Alterar também o `findValue` atributo do [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) para o novo nome de certificado de serviço que é o nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="83041-146">Also change the `findValue` attribute of the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="83041-147">Copie o arquivo CER do diretório do cliente para o diretório de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="83041-147">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="83041-148">No cliente, execute ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="83041-148">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="83041-149">Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="83041-149">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="83041-150">No servidor, execute ImportClientCert.bat, isso importa o certificado de cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="83041-150">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="83041-151">No computador de serviço, execute Service.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="83041-151">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="83041-152">No computador cliente, inicie Client.exe em uma janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="83041-152">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1.  <span data-ttu-id="83041-153">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="83041-153">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="83041-154">A limpeza após a amostra</span><span class="sxs-lookup"><span data-stu-id="83041-154">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="83041-155">Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="83041-155">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="83041-156">Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre máquinas.</span><span class="sxs-lookup"><span data-stu-id="83041-156">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="83041-157">Se você tiver executado [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] exemplos que usam certificados em computadores, certifique-se de desmarcar os certificados de serviço que foram instalados em CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="83041-157">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="83041-158">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="83041-158">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="83041-159">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="83041-159">The samples may already be installed on your machine.</span></span> <span data-ttu-id="83041-160">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="83041-160">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="83041-161">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="83041-161">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83041-162">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="83041-162">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
  
## <a name="see-also"></a><span data-ttu-id="83041-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83041-163">See Also</span></span>
