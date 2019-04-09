---
title: Associação HTTP de federação do WS 2007
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 07becd0fc5cbbd9a8b90de2d20654a63b62e3085
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153394"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="22fa0-102">Associação HTTP de federação do WS 2007</span><span class="sxs-lookup"><span data-stu-id="22fa0-102">WS 2007 Federation HTTP Binding</span></span>
<span data-ttu-id="22fa0-103">Este exemplo demonstra o uso de <xref:System.ServiceModel.WS2007FederationHttpBinding>, um padrão de associação que você pode usar para criar cenários federados esse suporte de versão 1.3 da especificação WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="22fa0-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22fa0-104">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="22fa0-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="22fa0-105">O exemplo consiste em um programa de cliente baseada em console (Client.exe), um programa de serviço de token de segurança baseada em console (Securitytokenservice.exe) e um programa de serviço baseada em console (Service.exe).</span><span class="sxs-lookup"><span data-stu-id="22fa0-105">The sample consists of a console-based client program (Client.exe), a console-based security token service program (Securitytokenservice.exe), and a console-based service program (Service.exe).</span></span> <span data-ttu-id="22fa0-106">O serviço implementa um contrato que define um padrão de comunicação de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="22fa0-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="22fa0-107">O contrato é definido o `ICalculator` interface, que expõe operações matemáticas (`Add`, `Subtract`, `Multiply`, e `Divide`).</span><span class="sxs-lookup"><span data-stu-id="22fa0-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="22fa0-108">O cliente obtém um token de segurança do Security Token Service (STS) e faz solicitações síncronas para o serviço para uma operação matemática determinado.</span><span class="sxs-lookup"><span data-stu-id="22fa0-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="22fa0-109">O serviço responde com o resultado.</span><span class="sxs-lookup"><span data-stu-id="22fa0-109">The service then replies with the result.</span></span> <span data-ttu-id="22fa0-110">Atividade do cliente está visível na janela do console.</span><span class="sxs-lookup"><span data-stu-id="22fa0-110">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="22fa0-111">O exemplo faz o `ICalculator` contrato disponíveis usando o `ws2007FederationHttpBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="22fa0-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="22fa0-112">A configuração desta associação no cliente é mostrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="22fa0-112">The configuration of this binding on the client is shown in the following code.</span></span>  
  
```xml  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Endpoint address and binding for Security Token Service -->  
          <issuer address ="http://localhost:8000/sts/windows"   
                  binding ="ws2007HttpBinding" />                
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="22fa0-113">Sobre o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), o `security` valor Especifica o modo de segurança deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="22fa0-113">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="22fa0-114">Neste exemplo, `message` segurança for usada, o que é por isso que o [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) especificado dentro de [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="22fa0-114">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="22fa0-115">O [ \<emissor >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) elemento dentro de [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Especifica o endereço e a associação para o STS que emite um token de segurança para o cliente para que o cliente possa autenticar o `ICalculator` service.</span><span class="sxs-lookup"><span data-stu-id="22fa0-115">The [\<issuer>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>  
  
 <span data-ttu-id="22fa0-116">A configuração desta associação de serviço é mostrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="22fa0-116">The configuration of this binding on the service is shown in the following code.</span></span>  
  
```xml  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Metadata address for Security Token Service -->  
          <issuerMetadata address ="http://localhost:8000/sts/mex" >  
            <identity>  
              <certificateReference storeLocation ="CurrentUser"   
                                    storeName="TrustedPeople"   
                                    x509FindType ="FindBySubjectDistinguishedName"   
                                    findValue ="CN=STS" />  
            </identity>  
          </issuerMetadata>  
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="22fa0-117">Sobre o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), o `security` valor Especifica o modo de segurança deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="22fa0-117">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="22fa0-118">Neste exemplo, `message` segurança for usada, o que é por isso que o [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) especificado dentro de [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="22fa0-118">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="22fa0-119">O [ \<issuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) elemento da `ws2007FederationHttpBinding` dentro do [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Especifica o endereço e a identidade para um ponto de extremidade que pode ser usado para recuperar metadados para o STS.</span><span class="sxs-lookup"><span data-stu-id="22fa0-119">The [\<issuerMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>  
  
 <span data-ttu-id="22fa0-120">O comportamento para o serviço é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="22fa0-120">The behavior for the service is shown in the following code.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name ="ServiceBehaviour" >  
      <serviceDebug includeExceptionDetailInFaults ="true"/>  
      <serviceMetadata httpGetEnabled ="true"/>  
      <serviceCredentials>  
        <issuedTokenAuthentication>  
          <knownCertificates>  
            <add storeLocation ="LocalMachine"  
                 storeName="TrustedPeople"  
                 x509FindType="FindBySubjectDistinguishedName"  
                 findValue="CN=STS" />  
          </knownCertificates>  
        </issuedTokenAuthentication>  
        <serviceCertificate storeLocation ="LocalMachine"  
                            storeName ="My"  
                            x509FindType ="FindBySubjectDistinguishedName"  
                            findValue ="CN=localhost"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="22fa0-121">O [ \<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> permite que o serviço especificar restrições nos tokens que ele permite que os clientes presentes durante a autenticação.</span><span class="sxs-lookup"><span data-stu-id="22fa0-121">The [\<issuedTokenAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="22fa0-122">Essa configuração especifica que os tokens assinados por um certificado cujo nome de assunto é CN = STS são aceitos pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="22fa0-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="22fa0-123">STS disponibiliza um ponto de extremidade usando o padrão <xref:System.ServiceModel.WS2007HttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="22fa0-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="22fa0-124">O serviço responde às solicitações de clientes para tokens.</span><span class="sxs-lookup"><span data-stu-id="22fa0-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="22fa0-125">Se o cliente é autenticado usando uma conta do Windows, o serviço emite um token que contém o nome de usuário do cliente como uma declaração.</span><span class="sxs-lookup"><span data-stu-id="22fa0-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="22fa0-126">Como parte da criação de token, o STS assina o token usando a chave privada associada com o CN = certificado STS.</span><span class="sxs-lookup"><span data-stu-id="22fa0-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="22fa0-127">Além disso, ele cria uma chave simétrica e criptografa usando a chave pública associada com o CN = localhost certificate.</span><span class="sxs-lookup"><span data-stu-id="22fa0-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="22fa0-128">Retornar o token para o cliente, o STS também retorna a chave simétrica.</span><span class="sxs-lookup"><span data-stu-id="22fa0-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="22fa0-129">O cliente apresenta o token emitido para o `ICalculator` de serviço e comprova que ele saiba a chave simétrica inscrevendo-se a mensagem com essa chave.</span><span class="sxs-lookup"><span data-stu-id="22fa0-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
 <span data-ttu-id="22fa0-130">Quando você executar o exemplo, a solicitação de token de segurança é mostrada na janela do console do STS.</span><span class="sxs-lookup"><span data-stu-id="22fa0-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="22fa0-131">A operação solicitações e respostas são exibidas nas janelas do console de cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="22fa0-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="22fa0-132">Pressione ENTER em qualquer uma das janelas do console para fechar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="22fa0-132">Press ENTER in any of the console windows to shut down the application.</span></span>  

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="22fa0-133">O arquivo Setup bat incluído com este exemplo permite que você configure o servidor e o STS com os certificados relevantes para executar um aplicativo hospedado internamente.</span><span class="sxs-lookup"><span data-stu-id="22fa0-133">The Setup.bat file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="22fa0-134">O arquivo em lotes cria dois certificados no repositório de certificados LocalMachine/TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="22fa0-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="22fa0-135">O primeiro certificado tem um nome de assunto de CN = STS e é usado pelo STS para assinar os tokens de segurança que emite ao cliente.</span><span class="sxs-lookup"><span data-stu-id="22fa0-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="22fa0-136">O segundo certificado tem um nome de assunto de CN = localhost e é usada para criptografar uma chave de forma que o serviço pode descriptografar pelo STS.</span><span class="sxs-lookup"><span data-stu-id="22fa0-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="22fa0-137">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="22fa0-137">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="22fa0-138">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="22fa0-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="22fa0-139">Abra um Prompt de comando do desenvolvedor para Visual Studio com privilégios de administrador e execute o arquivo Setup. bat para criar os certificados necessários.</span><span class="sxs-lookup"><span data-stu-id="22fa0-139">Open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>  
  
 <span data-ttu-id="22fa0-140">Esse arquivo em lotes usa Certmgr.exe e Makecert.exe, que são distribuídos com o SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="22fa0-140">This batch file uses Certmgr.exe and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="22fa0-141">No entanto, você deve executar o Setup. bat de dentro de um prompt de comando do Visual Studio para habilitar o script localizar essas ferramentas.</span><span class="sxs-lookup"><span data-stu-id="22fa0-141">However, you must run Setup.bat from within a Visual Studio  command prompt to enable the script to find these tools.</span></span>  
  
1.  <span data-ttu-id="22fa0-142">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="22fa0-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="22fa0-143">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="22fa0-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="22fa0-144">Se você estiver usando [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], você deve executar Service.exe, Client.exe, e SecurityTokenService.exe com privilégios elevados (os arquivos com o botão direito e, em seguida, clique em **executar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="22fa0-144">If you are using [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must run Service.exe, Client.exe, and SecurityTokenService.exe with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="22fa0-145">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="22fa0-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="22fa0-146">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="22fa0-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="22fa0-147">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="22fa0-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="22fa0-148">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="22fa0-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
