---
title: Segurança de mensagem através do enfileiramento de mensagem
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: d27ee01636e37ac8f09c4f7dc497f14bfac1b0f1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424118"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="2959c-102">Segurança de mensagem através do enfileiramento de mensagem</span><span class="sxs-lookup"><span data-stu-id="2959c-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="2959c-103">Este exemplo demonstra como implementar um aplicativo que usa o WS-Security com autenticação de certificado X. 509v3 para o cliente e requer autenticação de servidor usando o certificado X. 509v3 do servidor no MSMQ.</span><span class="sxs-lookup"><span data-stu-id="2959c-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="2959c-104">Às vezes, a segurança de mensagem é mais desejável garantir que as mensagens no armazenamento MSMQ permaneçam criptografadas e o aplicativo possa executar sua própria autenticação da mensagem.</span><span class="sxs-lookup"><span data-stu-id="2959c-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="2959c-105">Este exemplo é baseado no exemplo de [associação MSMQ transacionado](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="2959c-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="2959c-106">As mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="2959c-106">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2959c-107">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="2959c-107">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2959c-108">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2959c-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="2959c-109">Se o serviço for executado primeiro, ele verificará se a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="2959c-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="2959c-110">Se a fila não estiver presente, o serviço criará uma.</span><span class="sxs-lookup"><span data-stu-id="2959c-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="2959c-111">Você pode executar o serviço primeiro para criar a fila ou pode criar um por meio do Gerenciador de filas MSMQ.</span><span class="sxs-lookup"><span data-stu-id="2959c-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="2959c-112">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="2959c-112">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="2959c-113">Abra Gerenciador do Servidor no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="2959c-113">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="2959c-114">Expanda a guia **recursos** .</span><span class="sxs-lookup"><span data-stu-id="2959c-114">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="2959c-115">Clique com o botão direito do mouse em **filas de mensagens particulares**e selecione **nova** **fila privada**.</span><span class="sxs-lookup"><span data-stu-id="2959c-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="2959c-116">Marque a caixa **transacional** .</span><span class="sxs-lookup"><span data-stu-id="2959c-116">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="2959c-117">Insira `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="2959c-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="2959c-118">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2959c-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="2959c-119">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="2959c-119">To run the sample on the same computer</span></span>

1. <span data-ttu-id="2959c-120">Verifique se o caminho inclui a pasta que contém MakeCert. exe e FindPrivateKey. exe.</span><span class="sxs-lookup"><span data-stu-id="2959c-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2. <span data-ttu-id="2959c-121">Execute setup. bat na pasta de instalação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="2959c-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="2959c-122">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="2959c-122">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2959c-123">Certifique-se de remover os certificados executando Cleanup. bat quando tiver concluído o exemplo.</span><span class="sxs-lookup"><span data-stu-id="2959c-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="2959c-124">Outros exemplos de segurança usam os mesmos certificados.</span><span class="sxs-lookup"><span data-stu-id="2959c-124">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="2959c-125">Inicie o Service. exe em \service\bin.</span><span class="sxs-lookup"><span data-stu-id="2959c-125">Launch Service.exe from \service\bin.</span></span>  
  
4. <span data-ttu-id="2959c-126">Inicie o Client. exe em \client\bin.</span><span class="sxs-lookup"><span data-stu-id="2959c-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="2959c-127">A atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="2959c-127">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="2959c-128">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2959c-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="2959c-129">Para executar o exemplo entre computadores</span><span class="sxs-lookup"><span data-stu-id="2959c-129">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="2959c-130">Copie os arquivos Setup. bat, Cleanup. bat e ImportClientCert. bat para o computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="2959c-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2. <span data-ttu-id="2959c-131">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="2959c-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3. <span data-ttu-id="2959c-132">Copie os arquivos de programa do cliente para o diretório cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="2959c-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="2959c-133">Copie também os arquivos Setup. bat, Cleanup. bat e ImportServiceCert. bat para o cliente.</span><span class="sxs-lookup"><span data-stu-id="2959c-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4. <span data-ttu-id="2959c-134">No servidor, execute `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="2959c-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="2959c-135">A execução de `setup.bat` com o argumento `service` cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service. cer.</span><span class="sxs-lookup"><span data-stu-id="2959c-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5. <span data-ttu-id="2959c-136">Edite o Service. exe. config do serviço para refletir o novo nome do certificado (no atributo `findValue` na [\<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)Service-Certificate), que é o mesmo que o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="2959c-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6. <span data-ttu-id="2959c-137">Copie o arquivo Service. cer do diretório de serviço para o diretório cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="2959c-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7. <span data-ttu-id="2959c-138">No cliente, execute `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="2959c-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="2959c-139">A execução de `setup.bat` com o argumento `client` cria um certificado de cliente chamado client.com e exporta o certificado do cliente para um arquivo chamado Client. cer.</span><span class="sxs-lookup"><span data-stu-id="2959c-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8. <span data-ttu-id="2959c-140">No arquivo client. exe. config no computador cliente, altere o valor de endereço do ponto de extremidade para corresponder ao novo endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="2959c-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="2959c-141">Faça isso substituindo localhost pelo nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="2959c-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="2959c-142">Você também deve alterar o nome do certificado do serviço para ser o mesmo que o nome de domínio totalmente qualificado do computador de serviço (no atributo `findValue` no elemento `defaultCertificate` de `serviceCertificate` em `clientCredentials`).</span><span class="sxs-lookup"><span data-stu-id="2959c-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="2959c-143">Copie o arquivo client. cer do diretório cliente para o diretório de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="2959c-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="2959c-144">No cliente, execute `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="2959c-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="2959c-145">Isso importa o certificado de serviço do arquivo Service. cer para o repositório CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="2959c-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="2959c-146">No servidor, execute `ImportClientCert.bat`, isso importa o certificado do cliente do arquivo. cer do cliente para o repositório LocalMachine-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="2959c-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="2959c-147">No computador do serviço, inicie o Service. exe no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2959c-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="2959c-148">No computador cliente, inicie o Client. exe no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2959c-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="2959c-149">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2959c-149">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="2959c-150">Para limpar após o exemplo</span><span class="sxs-lookup"><span data-stu-id="2959c-150">To clean up after the sample</span></span>  
  
- <span data-ttu-id="2959c-151">Execute o Cleanup. bat na pasta Samples depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="2959c-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2959c-152">Esse script não remove certificados de serviço em um cliente ao executar esse exemplo em computadores.</span><span class="sxs-lookup"><span data-stu-id="2959c-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="2959c-153">Se você tiver executado Windows Communication Foundation (WCF) exemplos que usam certificados entre computadores, certifique-se de limpar os certificados de serviço que foram instalados no repositório CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="2959c-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="2959c-154">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="2959c-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="2959c-155">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2959c-155">Requirements</span></span>
 <span data-ttu-id="2959c-156">Este exemplo requer que o MSMQ esteja instalado e em execução.</span><span class="sxs-lookup"><span data-stu-id="2959c-156">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="2959c-157">Demonstra</span><span class="sxs-lookup"><span data-stu-id="2959c-157">Demonstrates</span></span>
 <span data-ttu-id="2959c-158">O cliente criptografa a mensagem usando a chave pública do serviço e assina a mensagem usando seu próprio certificado.</span><span class="sxs-lookup"><span data-stu-id="2959c-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="2959c-159">O serviço que lê a mensagem da fila autentica o certificado do cliente com o certificado em seu repositório de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="2959c-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="2959c-160">Em seguida, ele descriptografa a mensagem e envia a mensagem para a operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="2959c-160">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="2959c-161">Como a mensagem de Windows Communication Foundation (WCF) é transportada como uma carga no corpo da mensagem MSMQ, o corpo permanece criptografado no armazenamento MSMQ.</span><span class="sxs-lookup"><span data-stu-id="2959c-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="2959c-162">Isso protege a mensagem contra a divulgação indesejada da mensagem.</span><span class="sxs-lookup"><span data-stu-id="2959c-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="2959c-163">Observe que o MSMQ em si não reconhece se a mensagem que está carregando é criptografada.</span><span class="sxs-lookup"><span data-stu-id="2959c-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="2959c-164">O exemplo demonstra como a autenticação mútua no nível da mensagem pode ser usada com o MSMQ.</span><span class="sxs-lookup"><span data-stu-id="2959c-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="2959c-165">Os certificados são trocados fora de banda.</span><span class="sxs-lookup"><span data-stu-id="2959c-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="2959c-166">Esse é sempre o caso com o aplicativo enfileirado porque o serviço e o cliente não precisam estar em funcionamento ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="2959c-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="2959c-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="2959c-167">Description</span></span>
 <span data-ttu-id="2959c-168">O exemplo de código de cliente e serviço é o mesmo que o exemplo de [associação MSMQ transacionado](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) com uma diferença.</span><span class="sxs-lookup"><span data-stu-id="2959c-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="2959c-169">O contrato de operação é anotado com o nível de proteção, o que sugere que a mensagem deve ser assinada e criptografada.</span><span class="sxs-lookup"><span data-stu-id="2959c-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="2959c-170">Para garantir que a mensagem seja protegida usando o token necessário para identificar o serviço e o cliente, o app. config contém informações de credenciais.</span><span class="sxs-lookup"><span data-stu-id="2959c-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="2959c-171">A configuração do cliente especifica o certificado de serviço para autenticar o serviço.</span><span class="sxs-lookup"><span data-stu-id="2959c-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="2959c-172">Ele usa seu armazenamento LocalMachine como o repositório confiável para contar com a validade do serviço.</span><span class="sxs-lookup"><span data-stu-id="2959c-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="2959c-173">Ele também especifica o certificado de cliente que é anexado com a mensagem para autenticação de serviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="2959c-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <system.serviceModel>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                binding="netMsmqBinding"
                bindingConfiguration="messageSecurityBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"
                behaviorConfiguration="ClientCertificateBehavior" />
    </client>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate"/>
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <!--
        The clientCredentials behavior allows one to define a certificate to present to a service.
        A certificate is used by a client to authenticate itself to the service and provide message integrity.
        This configuration references the "client.com" certificate installed during the setup instructions.
        -->
          <clientCredentials>
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />
            <serviceCertificate>
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="2959c-174">Observe que o modo de segurança é definido como Message e o ClientCredentialtype é definido como Certificate.</span><span class="sxs-lookup"><span data-stu-id="2959c-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="2959c-175">A configuração de serviço inclui um comportamento de serviço que especifica as credenciais do serviço que são usadas quando o cliente autentica o serviço.</span><span class="sxs-lookup"><span data-stu-id="2959c-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="2959c-176">O nome da entidade do certificado do servidor é especificado no atributo `findValue` no [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="2959c-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />
  </appSettings>

  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"
          behaviorConfiguration="PurchaseOrderServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
          </baseAddresses>
        </host>
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                  binding="netMsmqBinding"
                  bindingConfiguration="messageSecurityBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="PurchaseOrderServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <!--
               The serviceCredentials behavior allows one to define a service certificate.
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.
               This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
            <clientCertificate>
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </clientCertificate>
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="2959c-177">O exemplo demonstra como controlar a autenticação usando a configuração e como obter a identidade do chamador do contexto de segurança, conforme mostrado no código de exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2959c-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

```csharp
// Service class which implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    private string GetCallerIdentity()
    {
        // The client certificate is not mapped to a Windows identity by default.
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information
        // in the certificate that the client used to authenticate itself to the service.
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }
  //…
}
```

 <span data-ttu-id="2959c-178">Quando executado, o código de serviço exibe a identificação do cliente.</span><span class="sxs-lookup"><span data-stu-id="2959c-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="2959c-179">Veja a seguir um exemplo de saída do código de serviço:</span><span class="sxs-lookup"><span data-stu-id="2959c-179">The following is a sample output from the service code:</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

## <a name="comments"></a><span data-ttu-id="2959c-180">Comentários</span><span class="sxs-lookup"><span data-stu-id="2959c-180">Comments</span></span>

- <span data-ttu-id="2959c-181">Criando o certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="2959c-181">Creating the client certificate.</span></span>

     <span data-ttu-id="2959c-182">A linha a seguir no arquivo em lotes cria o certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="2959c-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="2959c-183">O nome do cliente especificado é usado no nome da entidade do certificado criado.</span><span class="sxs-lookup"><span data-stu-id="2959c-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="2959c-184">O certificado é armazenado no repositório de `My` no local do repositório de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2959c-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="2959c-185">Instalando o certificado do cliente no repositório de certificados confiáveis do servidor.</span><span class="sxs-lookup"><span data-stu-id="2959c-185">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="2959c-186">A linha a seguir no arquivo em lotes copia o certificado do cliente no repositório TrustedPeople do servidor para que o servidor possa fazer as decisões relevantes de confiança ou sem confiança.</span><span class="sxs-lookup"><span data-stu-id="2959c-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="2959c-187">Para que um certificado instalado na TrustedPeople Store seja confiável para um serviço Windows Communication Foundation (WCF), o modo de validação de certificado do cliente deve ser definido como `PeerOrChainTrust` ou `PeerTrust` valor.</span><span class="sxs-lookup"><span data-stu-id="2959c-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="2959c-188">Consulte o exemplo de configuração de serviço anterior para saber como isso pode ser feito usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2959c-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="2959c-189">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="2959c-189">Creating the server certificate.</span></span>

     <span data-ttu-id="2959c-190">As linhas a seguir do arquivo em lotes setup. bat criam o certificado do servidor a ser usado:</span><span class="sxs-lookup"><span data-stu-id="2959c-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="2959c-191">A variável% SERVER_NAME% especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="2959c-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="2959c-192">O certificado é armazenado no armazenamento LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="2959c-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="2959c-193">Se o arquivo em lotes de instalação for executado com um argumento de serviço (por exemplo, `setup.bat service`), o% SERVER_NAME% conterá o nome de domínio totalmente qualificado do computador. Caso contrário, o padrão é localhost</span><span class="sxs-lookup"><span data-stu-id="2959c-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

- <span data-ttu-id="2959c-194">Instalando o certificado do servidor no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="2959c-194">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="2959c-195">A linha a seguir copia o certificado do servidor no repositório de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="2959c-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="2959c-196">Essa etapa é necessária porque os certificados gerados pelo MakeCert. exe não são implicitamente confiáveis pelo sistema cliente.</span><span class="sxs-lookup"><span data-stu-id="2959c-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="2959c-197">Se você já tiver um certificado com raiz em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de popular o repositório de certificados do cliente com o certificado do servidor não será necessária.</span><span class="sxs-lookup"><span data-stu-id="2959c-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="2959c-198">Se você estiver usando uma edição que não seja a U. S. inglês do Microsoft Windows, deverá editar o arquivo setup. bat e substituir o nome da conta "NT AUTHORITY\NETWORK SERVICE" pelo equivalente regional.</span><span class="sxs-lookup"><span data-stu-id="2959c-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2959c-199">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2959c-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2959c-200">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2959c-200">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="2959c-201">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="2959c-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2959c-202">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="2959c-202">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
