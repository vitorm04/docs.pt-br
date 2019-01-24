---
title: Segurança de mensagem através do enfileiramento de mensagem
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 7303db0e7553e7365d83dfadc377ec265a71891a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583292"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="ca701-102">Segurança de mensagem através do enfileiramento de mensagem</span><span class="sxs-lookup"><span data-stu-id="ca701-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="ca701-103">Este exemplo demonstra como implementar um aplicativo que usa WS-Security com autenticação de certificado X.509v3 para o cliente e requer autenticação de servidor usando o certificado X.509v3 do servidor em relação ao MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ca701-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="ca701-104">Mensagem de segurança, às vezes, é mais desejável para garantir que as mensagens no armazenamento de MSMQ permanecem criptografadas e o aplicativo pode executar sua própria autenticação da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ca701-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="ca701-105">Este exemplo se baseia a [transacionada de associação de MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="ca701-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="ca701-106">As mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="ca701-106">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ca701-107">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ca701-107">To set up, build, and run the sample</span></span>

1.  <span data-ttu-id="ca701-108">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ca701-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="ca701-109">Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="ca701-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="ca701-110">Se a fila não estiver presente, o serviço criará um.</span><span class="sxs-lookup"><span data-stu-id="ca701-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="ca701-111">Você pode executar o serviço pela primeira vez para criar a fila, ou você pode criar um por meio do Gerenciador de fila MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ca701-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="ca701-112">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="ca701-112">Follow these steps to create a queue in Windows 2008.</span></span>

    1.  <span data-ttu-id="ca701-113">Abra o Gerenciador de servidores no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="ca701-113">Open Server Manager in Visual Studio 2012.</span></span>

    2.  <span data-ttu-id="ca701-114">Expanda o **recursos** guia.</span><span class="sxs-lookup"><span data-stu-id="ca701-114">Expand the **Features** tab.</span></span>

    3.  <span data-ttu-id="ca701-115">Clique com botão direito **filas de mensagens privadas**e selecione **New**, **fila particular**.</span><span class="sxs-lookup"><span data-stu-id="ca701-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4.  <span data-ttu-id="ca701-116">Verifique as **transacional** caixa.</span><span class="sxs-lookup"><span data-stu-id="ca701-116">Check the **Transactional** box.</span></span>

    5.  <span data-ttu-id="ca701-117">Insira `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="ca701-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3.  <span data-ttu-id="ca701-118">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ca701-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="ca701-119">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="ca701-119">To run the sample on the same computer</span></span>

1.  <span data-ttu-id="ca701-120">Certifique-se de que o caminho inclui a pasta que contém Makecert.exe e FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="ca701-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2.  <span data-ttu-id="ca701-121">Execute Setup. bat da pasta de instalação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="ca701-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="ca701-122">Essa opção instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ca701-122">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="ca701-123">Certifique-se de que você remova os certificados com a execução CleanUp quando você terminar com o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ca701-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="ca701-124">Outros exemplos de segurança usam os mesmos certificados.</span><span class="sxs-lookup"><span data-stu-id="ca701-124">Other security samples use the same certificates.</span></span>  
  
3.  <span data-ttu-id="ca701-125">Inicie o Service.exe no \service\bin.</span><span class="sxs-lookup"><span data-stu-id="ca701-125">Launch Service.exe from \service\bin.</span></span>  
  
4.  <span data-ttu-id="ca701-126">Inicie o Client.exe no \client\bin.</span><span class="sxs-lookup"><span data-stu-id="ca701-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="ca701-127">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="ca701-127">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="ca701-128">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="ca701-128">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="ca701-129">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="ca701-129">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="ca701-130">Copie os arquivos Setup. bat, CleanUp e ImportClientCert.bat no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="ca701-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2.  <span data-ttu-id="ca701-131">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="ca701-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3.  <span data-ttu-id="ca701-132">Copie os arquivos de programa do cliente para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="ca701-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="ca701-133">Também copie os arquivos Setup. bat, CleanUp e ImportServiceCert.bat ao cliente.</span><span class="sxs-lookup"><span data-stu-id="ca701-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4.  <span data-ttu-id="ca701-134">No servidor, execute `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="ca701-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="ca701-135">Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="ca701-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5.  <span data-ttu-id="ca701-136">Editar service.exe.config do serviço para refletir o novo nome do certificado (na `findValue` de atributo na [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) que é o mesmo que o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="ca701-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6.  <span data-ttu-id="ca701-137">Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="ca701-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7.  <span data-ttu-id="ca701-138">No cliente, execute `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="ca701-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="ca701-139">Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado client.com e exporta o certificado de cliente para um arquivo chamado da CER.</span><span class="sxs-lookup"><span data-stu-id="ca701-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8.  <span data-ttu-id="ca701-140">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="ca701-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="ca701-141">Fazer isso, substitua localhost pelo nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="ca701-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="ca701-142">Você também deve alterar o nome do certificado do serviço para ser o mesmo que o nome de domínio totalmente qualificado do computador do serviço (na `findValue` de atributo na `defaultCertificate` elemento de `serviceCertificate` em `clientCredentials`).</span><span class="sxs-lookup"><span data-stu-id="ca701-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="ca701-143">Copie o arquivo de Client. cer do diretório do cliente para o diretório de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="ca701-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="ca701-144">No cliente, execute `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="ca701-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="ca701-145">Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople store.</span><span class="sxs-lookup"><span data-stu-id="ca701-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="ca701-146">No servidor, execute `ImportClientCert.bat`, isso importa o certificado de cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="ca701-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="ca701-147">No computador do serviço, inicie Service.exe do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ca701-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="ca701-148">No computador cliente, inicie Client.exe do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ca701-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="ca701-149">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="ca701-149">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ca701-150">Para limpar após a amostra</span><span class="sxs-lookup"><span data-stu-id="ca701-150">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="ca701-151">Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="ca701-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ca701-152">Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores.</span><span class="sxs-lookup"><span data-stu-id="ca701-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="ca701-153">Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados no CurrentUser - TrustedPeople store.</span><span class="sxs-lookup"><span data-stu-id="ca701-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="ca701-154">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="ca701-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="ca701-155">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca701-155">Requirements</span></span>
 <span data-ttu-id="ca701-156">Este exemplo requer que o MSMQ está instalado e em execução.</span><span class="sxs-lookup"><span data-stu-id="ca701-156">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ca701-157">Demonstra</span><span class="sxs-lookup"><span data-stu-id="ca701-157">Demonstrates</span></span>
 <span data-ttu-id="ca701-158">O cliente criptografa a mensagem usando a chave pública do serviço e assina a mensagem usando seu próprio certificado.</span><span class="sxs-lookup"><span data-stu-id="ca701-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="ca701-159">O serviço de ler a mensagem da fila autentica o certificado do cliente com o certificado em seu repositório de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="ca701-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="ca701-160">Em seguida, ele descriptografa a mensagem e expede a mensagem para a operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="ca701-160">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="ca701-161">Porque a mensagem do Windows Communication Foundation (WCF) é executada como um conteúdo no corpo da mensagem do MSMQ, o corpo permanece criptografado no armazenamento do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ca701-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="ca701-162">Isso protege a mensagem da divulgação indesejada de mensagem.</span><span class="sxs-lookup"><span data-stu-id="ca701-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="ca701-163">Observe que o MSMQ em si não está ciente se a mensagem que ele esteja carregando é criptografada.</span><span class="sxs-lookup"><span data-stu-id="ca701-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="ca701-164">O exemplo demonstra a autenticação mútua como a mensagem de nível pode ser usado com o MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ca701-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="ca701-165">Os certificados são troca fora de banda.</span><span class="sxs-lookup"><span data-stu-id="ca701-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="ca701-166">Isso é sempre o caso com o aplicativo em fila porque o serviço e o cliente não precisam estar em execução ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="ca701-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="ca701-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca701-167">Description</span></span>
 <span data-ttu-id="ca701-168">O código de cliente e o serviço de exemplo são os mesmos que o [associação de MSMQ transacionado](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) exemplo com uma diferença.</span><span class="sxs-lookup"><span data-stu-id="ca701-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="ca701-169">O contrato de operação é anotado com o nível de proteção, o que sugere que a mensagem deve ser assinada e criptografada.</span><span class="sxs-lookup"><span data-stu-id="ca701-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="ca701-170">Para garantir que a mensagem é protegida usando o token necessário para identificar o serviço e o cliente, o App. config contém informações de credenciais.</span><span class="sxs-lookup"><span data-stu-id="ca701-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="ca701-171">A configuração de cliente especifica o certificado de serviço para autenticar o serviço.</span><span class="sxs-lookup"><span data-stu-id="ca701-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="ca701-172">Ele usa seu armazenamento LocalMachine como o armazenamento confiável contar com a validade do serviço.</span><span class="sxs-lookup"><span data-stu-id="ca701-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="ca701-173">Ela também especifica o certificado do cliente que está associado com a mensagem para a autenticação de serviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="ca701-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

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

 <span data-ttu-id="ca701-174">Observe que o modo de segurança é definido como mensagem e ClientCredentialType está definida como Certificate.</span><span class="sxs-lookup"><span data-stu-id="ca701-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="ca701-175">A configuração de serviço inclui um comportamento de serviço que especifica as credenciais do serviço que são usadas quando o cliente autentica o serviço.</span><span class="sxs-lookup"><span data-stu-id="ca701-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="ca701-176">O nome de assunto do certificado de servidor é especificado na `findValue` de atributo em de [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="ca701-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

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

 <span data-ttu-id="ca701-177">O exemplo demonstra o controle de autenticação usando a configuração e como obter a identidade do chamador do contexto de segurança, conforme mostrado no código de exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="ca701-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

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

 <span data-ttu-id="ca701-178">Quando executado, o código de serviço exibe a identificação de cliente.</span><span class="sxs-lookup"><span data-stu-id="ca701-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="ca701-179">Este é um exemplo de saída do código de serviço:</span><span class="sxs-lookup"><span data-stu-id="ca701-179">The following is a sample output from the service code:</span></span>

```
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

## <a name="comments"></a><span data-ttu-id="ca701-180">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca701-180">Comments</span></span>

-   <span data-ttu-id="ca701-181">Criando o certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="ca701-181">Creating the client certificate.</span></span>

     <span data-ttu-id="ca701-182">A seguinte linha no arquivo de lote cria o certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="ca701-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="ca701-183">O nome do cliente especificado é usado no nome da entidade do certificado criado.</span><span class="sxs-lookup"><span data-stu-id="ca701-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="ca701-184">O certificado é armazenado no `My` armazenar cada a `CurrentUser` local do repositório.</span><span class="sxs-lookup"><span data-stu-id="ca701-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="ca701-185">Instalando o certificado do cliente no repositório de certificados confiáveis do servidor.</span><span class="sxs-lookup"><span data-stu-id="ca701-185">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="ca701-186">A seguinte linha nas cópias do arquivo em lotes que o certificado do cliente em TrustedPeople do servidor armazenar para que o servidor possa fazer a relação de confiança relevante ou decisões de confiança não.</span><span class="sxs-lookup"><span data-stu-id="ca701-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="ca701-187">Para um certificado instalado no repositório de TrustedPeople ser confiável por um serviço do Windows Communication Foundation (WCF), o modo de validação de certificado do cliente deve ser definido como `PeerOrChainTrust` ou `PeerTrust` valor.</span><span class="sxs-lookup"><span data-stu-id="ca701-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="ca701-188">Consulte o exemplo de configuração de serviço anterior para saber como isso pode ser feito usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ca701-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

-   <span data-ttu-id="ca701-189">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="ca701-189">Creating the server certificate.</span></span>

     <span data-ttu-id="ca701-190">As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado:</span><span class="sxs-lookup"><span data-stu-id="ca701-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="ca701-191">A variável % SERVER_NAME % Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="ca701-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="ca701-192">O certificado é armazenado no repositório de LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="ca701-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="ca701-193">Se o arquivo de lote é executado com um argumento de serviço (como, `setup.bat service`) % % SERVER_NAME contém o nome de domínio totalmente qualificado do computador. Caso contrário, o padrão é localhost</span><span class="sxs-lookup"><span data-stu-id="ca701-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

-   <span data-ttu-id="ca701-194">Instalar o certificado do servidor no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="ca701-194">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="ca701-195">A linha a seguir copia o certificado do servidor para o repositório de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="ca701-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="ca701-196">Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="ca701-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ca701-197">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="ca701-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="ca701-198">Se você estiver usando um fora dos EUA Edição em inglês do Microsoft Windows, você deve editar o Setup. bat de arquivo e substitua o nome da conta "NT AUTHORITY\NETWORK SERVICE" com seu equivalente regional.</span><span class="sxs-lookup"><span data-stu-id="ca701-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="ca701-199">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ca701-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ca701-200">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ca701-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ca701-201">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ca701-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ca701-202">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ca701-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
  
## <a name="see-also"></a><span data-ttu-id="ca701-203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca701-203">See also</span></span>
