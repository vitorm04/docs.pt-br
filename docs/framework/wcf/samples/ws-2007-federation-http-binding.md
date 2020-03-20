---
title: Associação HTTP de federação do WS 2007
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: bf61e64733859d96adf42fbacf08266eca1f5b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183181"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="59ea8-102">Associação HTTP de federação do WS 2007</span><span class="sxs-lookup"><span data-stu-id="59ea8-102">WS 2007 Federation HTTP Binding</span></span>

<span data-ttu-id="59ea8-103">Esta amostra demonstra <xref:System.ServiceModel.WS2007FederationHttpBinding>o uso de , uma vinculação padrão que você pode usar para construir cenários federados que suportam a versão 1.3 da especificação WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="59ea8-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>

> [!NOTE]
> <span data-ttu-id="59ea8-104">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="59ea8-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="59ea8-105">A amostra consiste em um programa de cliente baseado em console *(Client.exe),* um programa de serviço de token de segurança baseado em console *(Securitytokenservice.exe)* e um programa de serviço baseado em console *(Service.exe).*</span><span class="sxs-lookup"><span data-stu-id="59ea8-105">The sample consists of a console-based client program (*Client.exe*), a console-based security token service program (*Securitytokenservice.exe*), and a console-based service program (*Service.exe*).</span></span> <span data-ttu-id="59ea8-106">O serviço implementa um contrato que define um padrão de comunicação de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="59ea8-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="59ea8-107">O contrato é `ICalculator` definido pela interface, que`Add` `Subtract`expõe `Multiply`as `Divide`operações matemáticas ( , , e ).</span><span class="sxs-lookup"><span data-stu-id="59ea8-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="59ea8-108">O cliente obtém um token de segurança do Security Token Service (STS) e faz solicitações síncronas ao serviço para uma determinada operação matemática.</span><span class="sxs-lookup"><span data-stu-id="59ea8-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="59ea8-109">O serviço então responde com o resultado.</span><span class="sxs-lookup"><span data-stu-id="59ea8-109">The service then replies with the result.</span></span> <span data-ttu-id="59ea8-110">A atividade do cliente é visível na janela do console.</span><span class="sxs-lookup"><span data-stu-id="59ea8-110">Client activity is visible in the console window.</span></span>

<span data-ttu-id="59ea8-111">A amostra `ICalculator` disponibiliza o `ws2007FederationHttpBinding` contrato usando o elemento.</span><span class="sxs-lookup"><span data-stu-id="59ea8-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="59ea8-112">A configuração dessa vinculação no cliente é mostrada no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="59ea8-112">The configuration of this binding on the client is shown in the following code:</span></span>

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

<span data-ttu-id="59ea8-113">No [ \<>de ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` segurança , o valor especifica qual modo de segurança deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="59ea8-113">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="59ea8-114">Nesta amostra, `message` é usada a segurança, razão pela qual a [ \<mensagem>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) é especificada dentro do [ \<>de segurança ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="59ea8-114">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="59ea8-115">O [ \<emissor>](../../configure-apps/file-schema/wcf/issuer.md) elemento dentro da [ \<mensagem>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) especifica o endereço e a vinculação para o STS que emite um token de segurança para o cliente para que o cliente possa autenticar o `ICalculator` serviço.</span><span class="sxs-lookup"><span data-stu-id="59ea8-115">The [\<issuer>](../../configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>
  
<span data-ttu-id="59ea8-116">A configuração dessa vinculação no serviço é mostrada no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="59ea8-116">The configuration of this binding on the service is shown in the following code:</span></span>

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

<span data-ttu-id="59ea8-117">No [ \<>de ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` segurança , o valor especifica qual modo de segurança deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="59ea8-117">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="59ea8-118">Nesta amostra, `message` é usada a segurança, razão pela qual a [ \<mensagem>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) é especificada dentro do [ \<>de segurança ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="59ea8-118">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="59ea8-119">O [ \<emissorMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) `ws2007FederationHttpBinding` elemento de dentro da [ \<mensagem>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) especifica o endereço e a identidade para um ponto final que pode ser usado para recuperar metadados para o STS.</span><span class="sxs-lookup"><span data-stu-id="59ea8-119">The [\<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>

<span data-ttu-id="59ea8-120">O comportamento do serviço é mostrado no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="59ea8-120">The behavior for the service is shown in the following code:</span></span>

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
  
<span data-ttu-id="59ea8-121">O [ \<>de autenticação Token emitido](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> permite que o serviço especifique restrições nos tokens que permite que os clientes apresentem durante a autenticação.</span><span class="sxs-lookup"><span data-stu-id="59ea8-121">The [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="59ea8-122">Esta configuração especifica que os tokens assinados por um certificado cujo nome de assunto é CN=STS são aceitos pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="59ea8-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>

<span data-ttu-id="59ea8-123">O STS disponibiliza um único <xref:System.ServiceModel.WS2007HttpBinding>ponto final usando o padrão .</span><span class="sxs-lookup"><span data-stu-id="59ea8-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="59ea8-124">O serviço responde a pedidos de clientes por tokens.</span><span class="sxs-lookup"><span data-stu-id="59ea8-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="59ea8-125">Se o cliente for autenticado usando uma conta do Windows, o serviço emitirá um token que contém o nome de usuário do cliente como uma reclamação.</span><span class="sxs-lookup"><span data-stu-id="59ea8-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="59ea8-126">Como parte da criação do token, o STS assina o token usando a chave privada associada ao certificado CN=STS.</span><span class="sxs-lookup"><span data-stu-id="59ea8-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="59ea8-127">Além disso, ele cria uma chave simétrica e a criptografa usando a chave pública associada ao certificado CN=localhost.</span><span class="sxs-lookup"><span data-stu-id="59ea8-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="59ea8-128">Ao devolver o token ao cliente, o STS também retorna a chave simétrica.</span><span class="sxs-lookup"><span data-stu-id="59ea8-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="59ea8-129">O cliente apresenta o token `ICalculator` emitido para o serviço e prova que conhece a chave simétrica assinando a mensagem com essa chave.</span><span class="sxs-lookup"><span data-stu-id="59ea8-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>

<span data-ttu-id="59ea8-130">Quando você executa a amostra, a solicitação do token de segurança é mostrada na janela do console STS.</span><span class="sxs-lookup"><span data-stu-id="59ea8-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="59ea8-131">As solicitações e respostas da operação são exibidas nas janelas do cliente e do console de serviço.</span><span class="sxs-lookup"><span data-stu-id="59ea8-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="59ea8-132">Pressione ENTER em qualquer uma das janelas do console para desligar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="59ea8-132">Press ENTER in any of the console windows to shut down the application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

<span data-ttu-id="59ea8-133">O arquivo *Setup.bat* incluído nesta amostra permite configurar o servidor e o STS com os certificados relevantes para executar um aplicativo auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="59ea8-133">The *Setup.bat* file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="59ea8-134">O arquivo em lote cria dois certificados na loja de certificados LocalMachine/TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="59ea8-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="59ea8-135">O primeiro certificado tem um nome de assunto de CN=STS e é usado pela STS para assinar os tokens de segurança que ele emite ao cliente.</span><span class="sxs-lookup"><span data-stu-id="59ea8-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="59ea8-136">O segundo certificado tem um nome de assunto de CN=localhost e é usado pelo STS para criptografar uma chave de uma maneira que o serviço possa descriptografar.</span><span class="sxs-lookup"><span data-stu-id="59ea8-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="59ea8-137">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="59ea8-137">To set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="59ea8-138">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59ea8-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="59ea8-139">Abra um prompt de comando de desenvolvedor para o Visual Studio com privilégios de administrador e execute o arquivo Setup.bat para criar os certificados necessários.</span><span class="sxs-lookup"><span data-stu-id="59ea8-139">Open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>

 <span data-ttu-id="59ea8-140">Este arquivo em lote usa *Certmgr.exe* e Makecert.exe, que são distribuídos com o Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="59ea8-140">This batch file uses *Certmgr.exe* and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="59ea8-141">No entanto, você deve executar *Setup.bat* de dentro de um prompt de comando do Visual Studio para permitir que o script encontre essas ferramentas.</span><span class="sxs-lookup"><span data-stu-id="59ea8-141">However, you must run *Setup.bat* from within a Visual Studio command prompt to enable the script to find these tools.</span></span>

1. <span data-ttu-id="59ea8-142">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59ea8-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="59ea8-143">Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](running-the-samples.md)de Comunicação do Windows .</span><span class="sxs-lookup"><span data-stu-id="59ea8-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="59ea8-144">Se você estiver usando o Windows Vista, você deve executar *Service.exe*, *Client.exe*e *SecurityTokenService.exe* com privilégios elevados (clique com o botão direito do mouse nos arquivos e clique em **Executar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="59ea8-144">If you are using Windows Vista, you must run *Service.exe*, *Client.exe*, and *SecurityTokenService.exe* with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59ea8-145">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="59ea8-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="59ea8-146">Verificar o seguinte diretório (padrão) antes de continuar:</span><span class="sxs-lookup"><span data-stu-id="59ea8-146">Check for the following (default) directory before continuing:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="59ea8-147">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="59ea8-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="59ea8-148">Este exemplo está no seguinte diretório:</span><span class="sxs-lookup"><span data-stu-id="59ea8-148">This sample is located in the following directory:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
