---
title: Fornecedor de token
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
author: BrucePerlerMS
ms.openlocfilehash: 9e9bc55c0596943739e7cbd46e78d2802906f30e
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580557"
---
# <a name="token-provider"></a><span data-ttu-id="7f512-102">Fornecedor de token</span><span class="sxs-lookup"><span data-stu-id="7f512-102">Token Provider</span></span>
<span data-ttu-id="7f512-103">Este exemplo demonstra como implementar um provedor de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="7f512-103">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="7f512-104">Um provedor de token no Windows Communication Foundation (WCF) é usado para fornecer credenciais para a infraestrutura de segurança.</span><span class="sxs-lookup"><span data-stu-id="7f512-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="7f512-105">O provedor de token em geral examina o destino e problemas apropriado as credenciais para que a infraestrutura de segurança pode proteger a mensagem.</span><span class="sxs-lookup"><span data-stu-id="7f512-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="7f512-106">O WCF é fornecido com o provedor de Token do Gerenciador de credenciais padrão.</span><span class="sxs-lookup"><span data-stu-id="7f512-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="7f512-107">O WCF também é fornecido com um [!INCLUDE[infocard](../../../../includes/infocard-md.md)] provedor de token.</span><span class="sxs-lookup"><span data-stu-id="7f512-107">WCF also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="7f512-108">Provedores de token personalizados são úteis nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="7f512-108">Custom token providers are useful in the following cases:</span></span>

-   <span data-ttu-id="7f512-109">Se você tiver um repositório de credenciais que esses provedores de token não podem operar com.</span><span class="sxs-lookup"><span data-stu-id="7f512-109">If you have a credential store that these token providers cannot operate with.</span></span>

-   <span data-ttu-id="7f512-110">Se você quiser fornecer seu próprio mecanismo personalizado para transformar as credenciais do ponto quando o usuário fornece os detalhes para quando a estrutura do cliente WCF usa as credenciais.</span><span class="sxs-lookup"><span data-stu-id="7f512-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

-   <span data-ttu-id="7f512-111">Se você estiver criando um token personalizado.</span><span class="sxs-lookup"><span data-stu-id="7f512-111">If you are building a custom token.</span></span>

 <span data-ttu-id="7f512-112">Este exemplo mostra como criar um provedor de token personalizado que transforma a entrada do usuário em um formato diferente.</span><span class="sxs-lookup"><span data-stu-id="7f512-112">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>

 <span data-ttu-id="7f512-113">Para resumir, este exemplo demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7f512-113">To summarize, this sample demonstrates the following:</span></span>

-   <span data-ttu-id="7f512-114">Como um cliente pode autenticar usando um par de nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="7f512-114">How a client can authenticate using a username/password pair.</span></span>

-   <span data-ttu-id="7f512-115">Como um cliente pode ser configurado com um provedor de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="7f512-115">How a client can be configured with a custom token provider.</span></span>

-   <span data-ttu-id="7f512-116">Como o servidor pode validar as credenciais do cliente usando uma senha com um personalizado <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> que valida o nome de usuário e a senha correspondem.</span><span class="sxs-lookup"><span data-stu-id="7f512-116">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>

-   <span data-ttu-id="7f512-117">Como o servidor é autenticado pelo cliente usando o certificado do servidor x. 509.</span><span class="sxs-lookup"><span data-stu-id="7f512-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="7f512-118">Este exemplo também mostra como a identidade do chamador está acessível após o processo de autenticação de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="7f512-118">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>

 <span data-ttu-id="7f512-119">O serviço expõe um ponto de extremidade para se comunicar com o serviço, definido usando o arquivo de configuração App. config.</span><span class="sxs-lookup"><span data-stu-id="7f512-119">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="7f512-120">O ponto de extremidade consiste em um endereço, uma ligação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="7f512-120">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="7f512-121">A associação está configurada com um padrão `wsHttpBinding`, que usa a segurança de mensagem por padrão.</span><span class="sxs-lookup"><span data-stu-id="7f512-121">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="7f512-122">Este exemplo define o padrão `wsHttpBinding` para usar a autenticação de nome de usuário do cliente.</span><span class="sxs-lookup"><span data-stu-id="7f512-122">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="7f512-123">O serviço também configura o certificado de serviço usando o comportamento de serviceCredentials.</span><span class="sxs-lookup"><span data-stu-id="7f512-123">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="7f512-124">O comportamento de serviceCredentials permite que você configure um certificado de serviço.</span><span class="sxs-lookup"><span data-stu-id="7f512-124">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="7f512-125">Um certificado de serviço é usado por um cliente para autenticar o serviço e fornecer proteção de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7f512-125">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="7f512-126">A configuração a seguir referencia o certificado do localhost instalado durante a instalação de exemplo conforme descrito nas instruções de instalação a seguir.</span><span class="sxs-lookup"><span data-stu-id="7f512-126">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>
          </baseAddresses>
        </host>
        <!-- use base address provided by host -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults="False" />
          <!--
        The serviceCredentials behavior allows one to define a service certificate.
        A service certificate is used by a client to authenticate the service and provide message protection.
        This configuration references the "localhost" certificate installed during the setup instructions.
        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
```

 <span data-ttu-id="7f512-127">A configuração do ponto de extremidade cliente consiste em um nome de configuração, um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="7f512-127">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="7f512-128">A associação de cliente é configurado com os devidos `Mode` e a mensagem `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="7f512-128">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
              address="http://localhost:8000/servicemodelsamples/service"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator">
    </endpoint>
  </client>

  <bindings>
    <wsHttpBinding>
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
</system.serviceModel>
```

 <span data-ttu-id="7f512-129">As etapas a seguir mostram como desenvolver um provedor de token personalizado e integrá-la com a estrutura de segurança do WCF:</span><span class="sxs-lookup"><span data-stu-id="7f512-129">The following steps show how to develop a custom token provider and integrate it with the WCF security framework:</span></span>

1.  <span data-ttu-id="7f512-130">Escreva um provedor de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="7f512-130">Write a custom token provider.</span></span>

     <span data-ttu-id="7f512-131">O exemplo implementa um provedor de token personalizado que obtém o nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="7f512-131">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="7f512-132">A senha deve corresponder a este nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="7f512-132">The password must match this username.</span></span> <span data-ttu-id="7f512-133">Este provedor de token personalizado é para fins de demonstração e não é recomendado para implantação do mundo para o real.</span><span class="sxs-lookup"><span data-stu-id="7f512-133">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>

     <span data-ttu-id="7f512-134">Para executar essa tarefa, o provedor de token personalizado é derivado de <xref:System.IdentityModel.Selectors.SecurityTokenProvider> classe e substitui o <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> método.</span><span class="sxs-lookup"><span data-stu-id="7f512-134">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="7f512-135">Esse método cria e retorna um novo `UserNameSecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="7f512-135">This method creates and returns a new `UserNameSecurityToken`.</span></span>

    ```
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
        // obtain username and password from the user using console window
        string username = GetUserName();
        string password = GetPassword();
        Console.WriteLine("username: {0}", username);

        // return new UserNameSecurityToken containing information obtained from user
        return new UserNameSecurityToken(username, password);
    }
    ```

2.  <span data-ttu-id="7f512-136">Escreva um Gerenciador de token de segurança personalizada.</span><span class="sxs-lookup"><span data-stu-id="7f512-136">Write custom security token manager.</span></span>

     <span data-ttu-id="7f512-137">O <xref:System.IdentityModel.Selectors.SecurityTokenManager> é usado para criar <xref:System.IdentityModel.Selectors.SecurityTokenProvider> para determinado <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> que é passado para ele no `CreateSecurityTokenProvider` método.</span><span class="sxs-lookup"><span data-stu-id="7f512-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="7f512-138">Gerenciador de token de segurança também é usado para criar um serializador de token e autenticadores de token, mas esses não são cobertos por este exemplo.</span><span class="sxs-lookup"><span data-stu-id="7f512-138">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="7f512-139">Neste exemplo, o Gerenciador de token de segurança personalizada herda <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe e substitui o `CreateSecurityTokenProvider` método para retornar o provedor de token de nome de usuário personalizada quando os requisitos de token passados indicam esse provedor de nome de usuário é solicitado.</span><span class="sxs-lookup"><span data-stu-id="7f512-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>

    ```
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        MyUserNameClientCredentials myUserNameClientCredentials;

        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)
            : base(myUserNameClientCredentials)
        {
            this.myUserNameClientCredentials = myUserNameClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // if token requirement matches username token return custom username token provider
            // otherwise use base implementation
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)
            {
                return new MyUserNameTokenProvider();
            }
            else
            {
                return base.CreateSecurityTokenProvider(tokenRequirement);
            }
        }
    }
    ```

3.  <span data-ttu-id="7f512-140">Grave uma credencial de cliente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="7f512-140">Write a custom client credential.</span></span>

     <span data-ttu-id="7f512-141">Classe de credenciais do cliente é usado para representar as credenciais que são configuradas para o proxy de cliente e cria o Gerenciador de token que é usado para obter os autenticadores de token, provedores de token e um serializador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="7f512-141">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>

    ```
    public class MyUserNameClientCredentials : ClientCredentials
    {
        public MyUserNameClientCredentials()
            : base()
        {
        }

        protected override ClientCredentials CloneCore()
        {
            return new MyUserNameClientCredentials();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            // return custom security token manager
            return new MyUserNameSecurityTokenManager(this);
        }
    }
    ```

4.  <span data-ttu-id="7f512-142">Configure o cliente para usar a credencial de cliente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="7f512-142">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="7f512-143">Em ordem para o cliente usar a credencial de cliente personalizado, o exemplo exclui a classe de credencial de cliente padrão e fornece a nova classe de credencial de cliente.</span><span class="sxs-lookup"><span data-stu-id="7f512-143">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>

    ```
    static void Main()
    {
        // ...
           // Create a client with given client endpoint configuration
          CalculatorClient client = new CalculatorClient();

          // set new credentials
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());
       // ...
    }
    ```

 <span data-ttu-id="7f512-144">No serviço, para exibir informações do chamador, use o <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7f512-144">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="7f512-145">O <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contém informações de declarações sobre o chamador atual.</span><span class="sxs-lookup"><span data-stu-id="7f512-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 <span data-ttu-id="7f512-146">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="7f512-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7f512-147">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="7f512-147">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="7f512-148">Arquivo de lote</span><span class="sxs-lookup"><span data-stu-id="7f512-148">Setup Batch File</span></span>
 <span data-ttu-id="7f512-149">O arquivo em lotes de Setup. bat incluído com este exemplo permite que você configure o servidor com o certificado apropriado para executar um aplicativo hospedado internamente que exige a segurança baseada em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="7f512-149">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="7f512-150">Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso de não hospedados.</span><span class="sxs-lookup"><span data-stu-id="7f512-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="7f512-151">O exemplo a seguir fornece uma visão geral das diferentes seções dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada:</span><span class="sxs-lookup"><span data-stu-id="7f512-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

-   <span data-ttu-id="7f512-152">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="7f512-152">Creating the server certificate.</span></span>

     <span data-ttu-id="7f512-153">As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="7f512-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="7f512-154">O `%SERVER_NAME%` variável Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="7f512-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="7f512-155">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="7f512-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="7f512-156">O valor padrão nesse arquivo em lotes é localhost.</span><span class="sxs-lookup"><span data-stu-id="7f512-156">The default value in this batch file is localhost.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="7f512-157">Instalando o certificado do servidor no repositório de certificados confiáveis do cliente:</span><span class="sxs-lookup"><span data-stu-id="7f512-157">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="7f512-158">As seguintes linhas na cópia de arquivo de lote o certificado do servidor Setup. bat as pessoas confiáveis do cliente ao repositório.</span><span class="sxs-lookup"><span data-stu-id="7f512-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="7f512-159">Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="7f512-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="7f512-160">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado da Microsoft emitido — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="7f512-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

> [!NOTE]
>  <span data-ttu-id="7f512-161">O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="7f512-161">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="7f512-162">Ele requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="7f512-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="7f512-163">Essa variável de ambiente é definido automaticamente dentro de um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="7f512-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="7f512-164">Para configurar e compilar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7f512-164">To set up and build the sample</span></span>

1.  <span data-ttu-id="7f512-165">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f512-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="7f512-166">Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f512-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="7f512-167">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="7f512-167">To run the sample on the same computer</span></span>

1.  <span data-ttu-id="7f512-168">Execute Setup. bat da pasta de instalação de exemplo dentro de um prompt de comando do Visual Studio 2012 aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="7f512-168">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="7f512-169">Essa opção instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="7f512-169">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="7f512-170">O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Visual Studio 2012 Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="7f512-170">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="7f512-171">A variável de ambiente PATH definido dentro de pontos de Prompt de comando do Visual Studio 2012 para o diretório que contém executáveis exigido pelo script de Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="7f512-171">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="7f512-172">Inicie o service.exe de service\bin.</span><span class="sxs-lookup"><span data-stu-id="7f512-172">Launch service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="7f512-173">Inicie o Client.exe no \client\bin.</span><span class="sxs-lookup"><span data-stu-id="7f512-173">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="7f512-174">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="7f512-174">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="7f512-175">No prompt de nome de usuário, digite um nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="7f512-175">At the username prompt, type a user name.</span></span>  
  
5.  <span data-ttu-id="7f512-176">No prompt de senha, use a mesma cadeia de caracteres que foi digitada para o prompt de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="7f512-176">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6.  <span data-ttu-id="7f512-177">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="7f512-177">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="7f512-178">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="7f512-178">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="7f512-179">Crie um diretório no computador do serviço para os binários de serviço.</span><span class="sxs-lookup"><span data-stu-id="7f512-179">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="7f512-180">Copie os arquivos de programa de serviço para o diretório de serviço no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="7f512-180">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="7f512-181">Também copie os arquivos Setup. bat e Cleanup para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="7f512-181">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="7f512-182">Você deve ter um certificado de servidor com o nome da entidade que contém o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="7f512-182">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="7f512-183">O arquivo Service.exe.config deve ser atualizado para refletir o novo nome de certificado.</span><span class="sxs-lookup"><span data-stu-id="7f512-183">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="7f512-184">Você pode criar o certificado do servidor, modificando o arquivo em lotes de Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="7f512-184">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="7f512-185">Observe que o arquivo Setup. bat deve ser executado em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="7f512-185">Note that the setup.bat file must be run from a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="7f512-186">Você deve definir `%SERVER_NAME%` variável ao nome de host totalmente qualificado do computador que é usado para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="7f512-186">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4.  <span data-ttu-id="7f512-187">Copie o certificado do servidor para o repositório CurrentUser TrustedPeople do cliente.</span><span class="sxs-lookup"><span data-stu-id="7f512-187">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="7f512-188">Você não precisa fazer isso quando o certificado do servidor é emitido por um emissor confiável do cliente.</span><span class="sxs-lookup"><span data-stu-id="7f512-188">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="7f512-189">No arquivo Service.exe.config no computador do serviço, altere o valor do endereço base para especificar um nome de computador totalmente qualificado em vez do localhost.</span><span class="sxs-lookup"><span data-stu-id="7f512-189">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="7f512-190">No computador do serviço, execute service.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="7f512-190">On the service computer, run service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="7f512-191">Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="7f512-191">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="7f512-192">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="7f512-192">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="7f512-193">No computador cliente, inicie o `Client.exe` em uma janela do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="7f512-193">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="7f512-194">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="7f512-194">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="7f512-195">Para limpar após a amostra</span><span class="sxs-lookup"><span data-stu-id="7f512-195">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="7f512-196">Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="7f512-196">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f512-197">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f512-197">See Also</span></span>
