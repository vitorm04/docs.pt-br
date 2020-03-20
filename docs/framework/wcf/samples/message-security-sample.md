---
title: Exemplo de segurança de mensagem
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 43e1a9104bdd44509d86bd198559c5e7477a9964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183524"
---
# <a name="message-security-sample"></a><span data-ttu-id="77e74-102">Exemplo de segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="77e74-102">Message Security Sample</span></span>
<span data-ttu-id="77e74-103">Esta amostra demonstra como implementar um `basicHttpBinding` aplicativo que usa a segurança e a mensagem.</span><span class="sxs-lookup"><span data-stu-id="77e74-103">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="77e74-104">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="77e74-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77e74-105">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="77e74-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="77e74-106">O modo `basicHttpBinding` de segurança pode ser `Message`definido `Transport` `TransportWithMessageCredential`para `TransportCredentialOnly` `None`os seguintes valores: , , e .</span><span class="sxs-lookup"><span data-stu-id="77e74-106">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="77e74-107">No seguinte arquivo de serviço de amostra App.config, a definição de ponto final especifica e faz referência a `basicHttpBinding` uma configuração de vinculação nomeada, `Binding1`conforme mostrado na seguinte configuração de amostra:</span><span class="sxs-lookup"><span data-stu-id="77e74-107">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
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
  
 <span data-ttu-id="77e74-108">A configuração `mode` de vinculação define `Message` o `clientCredentialType` atributo do [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) de segurança e define o atributo da [ \<mensagem>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) como `Certificate` mostrado na seguinte configuração de amostra:</span><span class="sxs-lookup"><span data-stu-id="77e74-108">The binding configuration sets the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
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
  
 <span data-ttu-id="77e74-109">O certificado que o serviço usa para autenticar-se ao cliente é definido `serviceCredentials` na seção de comportamentos do arquivo de configuração o elemento.</span><span class="sxs-lookup"><span data-stu-id="77e74-109">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="77e74-110">O modo de validação que se aplica ao certificado que o cliente usa para autenticar-se ao serviço também é definido na seção de comportamentos o `clientCertificate` elemento.</span><span class="sxs-lookup"><span data-stu-id="77e74-110">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
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
  
 <span data-ttu-id="77e74-111">Os mesmos detalhes de vinculação e segurança são especificados no arquivo de configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="77e74-111">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="77e74-112">A identidade do chamador é exibida na janela do console de serviço usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="77e74-112">The identity of the caller is displayed in the service console window by using the following code:</span></span>  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 <span data-ttu-id="77e74-113">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="77e74-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="77e74-114">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="77e74-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="77e74-115">Para configurar e construir a amostra</span><span class="sxs-lookup"><span data-stu-id="77e74-115">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="77e74-116">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="77e74-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="77e74-117">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="77e74-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="77e74-118">Para executar a amostra na mesma máquina</span><span class="sxs-lookup"><span data-stu-id="77e74-118">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="77e74-119">Executar Setup.bat da pasta de instalação de amostra.</span><span class="sxs-lookup"><span data-stu-id="77e74-119">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="77e74-120">Isso instala todos os certificados necessários para a execução da amostra.</span><span class="sxs-lookup"><span data-stu-id="77e74-120">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="77e74-121">O arquivo de lote Setup.bat foi projetado para ser executado a partir de um prompt de comando do Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="77e74-121">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="77e74-122">Requer que a variável ambiente MSSDK aponte para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="77e74-122">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="77e74-123">Essa variável de ambiente é definida automaticamente dentro de um prompt de comando Do Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="77e74-123">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2. <span data-ttu-id="77e74-124">Execute o aplicativo de serviço a partir de \service\bin.</span><span class="sxs-lookup"><span data-stu-id="77e74-124">Run the service application from \service\bin.</span></span>  
  
3. <span data-ttu-id="77e74-125">Execute o aplicativo cliente a partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="77e74-125">Run the client application from \client\bin.</span></span> <span data-ttu-id="77e74-126">A atividade do cliente é exibida no aplicativo do console cliente.</span><span class="sxs-lookup"><span data-stu-id="77e74-126">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="77e74-127">Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="77e74-127">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
5. <span data-ttu-id="77e74-128">Remova os certificados executando Cleanup.bat quando terminar com a amostra.</span><span class="sxs-lookup"><span data-stu-id="77e74-128">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="77e74-129">Outras amostras de segurança usam os mesmos certificados.</span><span class="sxs-lookup"><span data-stu-id="77e74-129">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="77e74-130">Para executar a amostra através de máquinas</span><span class="sxs-lookup"><span data-stu-id="77e74-130">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="77e74-131">Crie um diretório na máquina de serviço para os binários de serviço.</span><span class="sxs-lookup"><span data-stu-id="77e74-131">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="77e74-132">Copie os arquivos do programa de serviço para o diretório de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="77e74-132">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="77e74-133">Copie também os arquivos Setup.bat, Cleanup.bat e ImportClientCert.bat para o servidor.</span><span class="sxs-lookup"><span data-stu-id="77e74-133">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3. <span data-ttu-id="77e74-134">Crie um diretório na máquina cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="77e74-134">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="77e74-135">Copie os arquivos do programa cliente para o diretório do cliente na máquina cliente.</span><span class="sxs-lookup"><span data-stu-id="77e74-135">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="77e74-136">Copie também os arquivos Setup.bat, Cleanup.bat e ImportServiceCert.bat para o cliente.</span><span class="sxs-lookup"><span data-stu-id="77e74-136">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="77e74-137">No servidor, `setup.bat service`execute.</span><span class="sxs-lookup"><span data-stu-id="77e74-137">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="77e74-138">A `setup.bat` execução com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado da máquina e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="77e74-138">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="77e74-139">Editar Service.exe.config para refletir o novo `findValue` nome do certificado (no atributo no [ \<elemento serviceCertificate>)](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) que é o mesmo que o nome de domínio totalmente qualificado da máquina.</span><span class="sxs-lookup"><span data-stu-id="77e74-139">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="77e74-140">Também altere o valor do endereço base para especificar um nome de máquina totalmente qualificado em vez de localhost`.`</span><span class="sxs-lookup"><span data-stu-id="77e74-140">Also change the value of the base address to specify a fully-qualified machine name instead of localhost`.`</span></span>  
  
7. <span data-ttu-id="77e74-141">Copie o arquivo Service.cer do diretório de serviço para o diretório do cliente na máquina cliente.</span><span class="sxs-lookup"><span data-stu-id="77e74-141">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="77e74-142">No cliente, `setup.bat client`corra.</span><span class="sxs-lookup"><span data-stu-id="77e74-142">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="77e74-143">A `setup.bat` execução com o `client` argumento cria um certificado de cliente chamado client.com e exporta o certificado do cliente para um arquivo chamado Client.cer.</span><span class="sxs-lookup"><span data-stu-id="77e74-143">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="77e74-144">No arquivo Client.exe.config na máquina cliente, altere o valor do endereço do ponto final para corresponder ao novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="77e74-144">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="77e74-145">Você faz isso substituindo o localhost pelo nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="77e74-145">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="77e74-146">Também altere o atributo `findValue` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) do>de certificado padrão para o novo nome do certificado de serviço, que é o nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="77e74-146">Also change the `findValue` attribute of the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="77e74-147">Copie o arquivo Client.cer do diretório do cliente para o diretório de serviço situado no servidor.</span><span class="sxs-lookup"><span data-stu-id="77e74-147">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="77e74-148">No cliente, execute ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="77e74-148">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="77e74-149">Isso importa o certificado de serviço do arquivo Service.cer para a loja CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="77e74-149">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="77e74-150">No servidor, execute ImportClientCert.bat, Isso importa o certificado do cliente do arquivo Client.cer para a loja LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="77e74-150">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="77e74-151">Na máquina de serviço, execute Service.exe a partir de um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="77e74-151">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="77e74-152">Na máquina cliente, inicie client.exe a partir de uma janela de solicitação de comando.</span><span class="sxs-lookup"><span data-stu-id="77e74-152">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1. <span data-ttu-id="77e74-153">Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="77e74-153">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="77e74-154">Para limpar depois da amostra</span><span class="sxs-lookup"><span data-stu-id="77e74-154">To clean up after the sample</span></span>  
  
- <span data-ttu-id="77e74-155">Executar Cleanup.bat na pasta amostras depois de terminar de executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="77e74-155">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="77e74-156">Este script não remove certificados de serviço em um cliente ao executar esta amostra em máquinas.</span><span class="sxs-lookup"><span data-stu-id="77e74-156">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="77e74-157">Se você tiver executado amostras de Windows Communication Foundation (WCF) que usam certificados em máquinas, certifique-se de limpar os certificados de serviço que foram instalados na loja CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="77e74-157">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="77e74-158">Para fazer isso, use `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` o seguinte comando: Por exemplo:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="77e74-158">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="77e74-159">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="77e74-159">The samples may already be installed on your machine.</span></span> <span data-ttu-id="77e74-160">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="77e74-160">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="77e74-161">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="77e74-161">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="77e74-162">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="77e74-162">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
