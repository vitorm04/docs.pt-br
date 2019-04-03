---
title: Exemplo de segurança de mensagem
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 23304ba3be88e327f84943daf0dcd751d564d5f7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825580"
---
# <a name="message-security-sample"></a><span data-ttu-id="5e70e-102">Exemplo de segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="5e70e-102">Message Security Sample</span></span>
<span data-ttu-id="5e70e-103">Este exemplo demonstra como implementar um aplicativo que usa o `basicHttpBinding` e segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5e70e-103">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="5e70e-104">Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="5e70e-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e70e-105">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5e70e-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5e70e-106">O modo de segurança de `basicHttpBinding` podem ser definidas com os seguintes valores: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` e `None`.</span><span class="sxs-lookup"><span data-stu-id="5e70e-106">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="5e70e-107">No App. config arquivo seguinte serviço de exemplo, a definição de ponto de extremidade Especifica o `basicHttpBinding` e faz referência a uma configuração de ligação nomeada `Binding1`, conforme mostrado no seguinte exemplo de configuração:</span><span class="sxs-lookup"><span data-stu-id="5e70e-107">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
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
  </services>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5e70e-108">Os conjuntos de configuração de associação a `mode` atributo do [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) para `Message` e define o `clientCredentialType` atributo do [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)para `Certificate` conforme mostrado no seguinte exemplo de configuração:</span><span class="sxs-lookup"><span data-stu-id="5e70e-108">The binding configuration sets the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
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
  
 <span data-ttu-id="5e70e-109">O certificado que o serviço usa para se autenticar para o cliente é definido na seção behaviors do arquivo de configuração sob o `serviceCredentials` elemento.</span><span class="sxs-lookup"><span data-stu-id="5e70e-109">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="5e70e-110">O modo de validação que se aplica ao certificado que o cliente usa para autenticar-se com o serviço também é definido na seção de comportamentos no `clientCertificate` elemento.</span><span class="sxs-lookup"><span data-stu-id="5e70e-110">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
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
  
 <span data-ttu-id="5e70e-111">Os mesmos detalhes de associação e segurança são especificados no arquivo de configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="5e70e-111">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="5e70e-112">A identidade do chamador é exibida na janela do console de serviço, usando o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="5e70e-112">The identity of the caller is displayed in the service console window by using the following code:</span></span>  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 <span data-ttu-id="5e70e-113">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="5e70e-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5e70e-114">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="5e70e-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="5e70e-115">Para configurar e compilar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5e70e-115">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="5e70e-116">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e70e-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5e70e-117">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e70e-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="5e70e-118">Para executar o exemplo na mesma máquina</span><span class="sxs-lookup"><span data-stu-id="5e70e-118">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="5e70e-119">Execute Setup. bat da pasta de instalação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="5e70e-119">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="5e70e-120">Essa opção instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="5e70e-120">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5e70e-121">O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="5e70e-121">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="5e70e-122">Ele requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="5e70e-122">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="5e70e-123">Essa variável de ambiente é definido automaticamente dentro de um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="5e70e-123">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2.  <span data-ttu-id="5e70e-124">Execute o aplicativo de serviço do \service\bin.</span><span class="sxs-lookup"><span data-stu-id="5e70e-124">Run the service application from \service\bin.</span></span>  
  
3.  <span data-ttu-id="5e70e-125">Execute o aplicativo de cliente do \Client\Bin.</span><span class="sxs-lookup"><span data-stu-id="5e70e-125">Run the client application from \client\bin.</span></span> <span data-ttu-id="5e70e-126">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="5e70e-126">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="5e70e-127">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5e70e-127">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
5.  <span data-ttu-id="5e70e-128">Remova os certificados com a execução CleanUp quando você terminar com o exemplo.</span><span class="sxs-lookup"><span data-stu-id="5e70e-128">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="5e70e-129">Outros exemplos de segurança usam os mesmos certificados.</span><span class="sxs-lookup"><span data-stu-id="5e70e-129">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="5e70e-130">Para executar o exemplo entre máquinas</span><span class="sxs-lookup"><span data-stu-id="5e70e-130">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="5e70e-131">Crie um diretório na máquina do serviço para os binários de serviço.</span><span class="sxs-lookup"><span data-stu-id="5e70e-131">Create a directory on the service machine for the service binaries.</span></span>  
  
2.  <span data-ttu-id="5e70e-132">Copie os arquivos de programa de serviço para o diretório de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="5e70e-132">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="5e70e-133">Também copie os arquivos Setup. bat, CleanUp e ImportClientCert.bat para o servidor.</span><span class="sxs-lookup"><span data-stu-id="5e70e-133">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3.  <span data-ttu-id="5e70e-134">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="5e70e-134">Create a directory on the client machine for the client binaries.</span></span>  
  
4.  <span data-ttu-id="5e70e-135">Copie os arquivos de programa do cliente para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="5e70e-135">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="5e70e-136">Também copie os arquivos Setup. bat, CleanUp e ImportServiceCert.bat ao cliente.</span><span class="sxs-lookup"><span data-stu-id="5e70e-136">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="5e70e-137">No servidor, execute `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="5e70e-137">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="5e70e-138">Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="5e70e-138">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="5e70e-139">Editar Service.exe.config para refletir o novo nome do certificado (na `findValue` de atributo na [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) elemento) que é o mesmo que o nome de domínio totalmente qualificado da máquina.</span><span class="sxs-lookup"><span data-stu-id="5e70e-139">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="5e70e-140">Também altere o valor do endereço base para especificar um nome de máquina totalmente qualificado em vez do localhost`.`</span><span class="sxs-lookup"><span data-stu-id="5e70e-140">Also change the value of the base address to specify a fully-qualified machine name instead of localhost`.`</span></span>  
  
7.  <span data-ttu-id="5e70e-141">Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="5e70e-141">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8.  <span data-ttu-id="5e70e-142">No cliente, execute `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="5e70e-142">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="5e70e-143">Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado client.com e exporta o certificado de cliente para um arquivo chamado da CER.</span><span class="sxs-lookup"><span data-stu-id="5e70e-143">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="5e70e-144">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="5e70e-144">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="5e70e-145">Você pode fazer isso substituindo o localhost com o nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="5e70e-145">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="5e70e-146">Também alterar o `findValue` atributo o [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) para o novo nome de certificado de serviço que é o nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="5e70e-146">Also change the `findValue` attribute of the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="5e70e-147">Copie o arquivo de Client. cer do diretório do cliente para o diretório de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="5e70e-147">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="5e70e-148">No cliente, execute ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="5e70e-148">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="5e70e-149">Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople store.</span><span class="sxs-lookup"><span data-stu-id="5e70e-149">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="5e70e-150">No servidor, execute ImportClientCert.bat, isso importa o certificado do cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="5e70e-150">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="5e70e-151">No computador do serviço, execute Service.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="5e70e-151">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="5e70e-152">No computador cliente, inicie Client.exe em uma janela do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="5e70e-152">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1.  <span data-ttu-id="5e70e-153">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5e70e-153">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="5e70e-154">Para limpar após a amostra</span><span class="sxs-lookup"><span data-stu-id="5e70e-154">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="5e70e-155">Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="5e70e-155">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5e70e-156">Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre máquinas.</span><span class="sxs-lookup"><span data-stu-id="5e70e-156">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="5e70e-157">Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados no CurrentUser - TrustedPeople store.</span><span class="sxs-lookup"><span data-stu-id="5e70e-157">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="5e70e-158">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="5e70e-158">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e70e-159">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5e70e-159">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5e70e-160">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5e70e-160">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5e70e-161">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="5e70e-161">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5e70e-162">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5e70e-162">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
  
