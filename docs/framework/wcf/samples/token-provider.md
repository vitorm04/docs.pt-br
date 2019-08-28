---
title: Fornecedor de token
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: 9f008204c6ff8d3d134dbb17fc445b460f757f13
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038744"
---
# <a name="token-provider"></a><span data-ttu-id="e7e95-102">Fornecedor de token</span><span class="sxs-lookup"><span data-stu-id="e7e95-102">Token Provider</span></span>
<span data-ttu-id="e7e95-103">Este exemplo demonstra como implementar um provedor de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="e7e95-103">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="e7e95-104">Um provedor de token no Windows Communication Foundation (WCF) é usado para fornecer credenciais para a infraestrutura de segurança.</span><span class="sxs-lookup"><span data-stu-id="e7e95-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="e7e95-105">O provedor de token em geral examina o destino e emite as credenciais apropriadas para que a infraestrutura de segurança possa proteger a mensagem.</span><span class="sxs-lookup"><span data-stu-id="e7e95-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="e7e95-106">O WCF é fornecido com o provedor de token padrão do Credential Manager.</span><span class="sxs-lookup"><span data-stu-id="e7e95-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="e7e95-107">O WCF também é fornecido com um provedor de token do CardSpace.</span><span class="sxs-lookup"><span data-stu-id="e7e95-107">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="e7e95-108">Os provedores de token personalizados são úteis nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="e7e95-108">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="e7e95-109">Se você tiver um repositório de credenciais para o qual esses provedores de token não podem operar.</span><span class="sxs-lookup"><span data-stu-id="e7e95-109">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="e7e95-110">Se você quiser fornecer seu próprio mecanismo personalizado para transformar as credenciais do ponto em que o usuário fornece os detalhes quando a estrutura do cliente WCF usa as credenciais.</span><span class="sxs-lookup"><span data-stu-id="e7e95-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="e7e95-111">Se você estiver criando um token personalizado.</span><span class="sxs-lookup"><span data-stu-id="e7e95-111">If you are building a custom token.</span></span>

 <span data-ttu-id="e7e95-112">Este exemplo mostra como criar um provedor de token personalizado que transforma a entrada do usuário em um formato diferente.</span><span class="sxs-lookup"><span data-stu-id="e7e95-112">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>

 <span data-ttu-id="e7e95-113">Para resumir, este exemplo demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e7e95-113">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="e7e95-114">Como um cliente pode se autenticar usando um par de nome de usuário/senha.</span><span class="sxs-lookup"><span data-stu-id="e7e95-114">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="e7e95-115">Como um cliente pode ser configurado com um provedor de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="e7e95-115">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="e7e95-116">Como o servidor pode validar as credenciais do cliente usando uma senha com um <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> personalizado que valida a correspondência entre o nome de usuário e a senha.</span><span class="sxs-lookup"><span data-stu-id="e7e95-116">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>

- <span data-ttu-id="e7e95-117">Como o servidor é autenticado pelo cliente usando o certificado X. 509 do servidor.</span><span class="sxs-lookup"><span data-stu-id="e7e95-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="e7e95-118">Este exemplo também mostra como a identidade do chamador pode ser acessada após o processo de autenticação de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="e7e95-118">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>

 <span data-ttu-id="e7e95-119">O serviço expõe um único ponto de extremidade para se comunicar com o serviço, definido usando o arquivo de configuração app. config.</span><span class="sxs-lookup"><span data-stu-id="e7e95-119">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="e7e95-120">O ponto de extremidade consiste em um endereço, uma associação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="e7e95-120">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="e7e95-121">A associação é configurada com `wsHttpBinding`um padrão, que usa a segurança de mensagem por padrão.</span><span class="sxs-lookup"><span data-stu-id="e7e95-121">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="e7e95-122">Este exemplo define o padrão `wsHttpBinding` para usar a autenticação de nome de usuário do cliente.</span><span class="sxs-lookup"><span data-stu-id="e7e95-122">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="e7e95-123">O serviço também configura o certificado de serviço usando o comportamento serviceCredentials.</span><span class="sxs-lookup"><span data-stu-id="e7e95-123">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="e7e95-124">O comportamento serviceCredentials permite que você configure um certificado de serviço.</span><span class="sxs-lookup"><span data-stu-id="e7e95-124">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="e7e95-125">Um certificado de serviço é usado por um cliente para autenticar o serviço e fornecer proteção de mensagem.</span><span class="sxs-lookup"><span data-stu-id="e7e95-125">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="e7e95-126">A configuração a seguir faz referência ao certificado localhost instalado durante a configuração de exemplo, conforme descrito nas instruções de instalação a seguir.</span><span class="sxs-lookup"><span data-stu-id="e7e95-126">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

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

 <span data-ttu-id="e7e95-127">A configuração de ponto de extremidade do cliente consiste em um nome de configuração, um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="e7e95-127">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="e7e95-128">A associação de cliente é configurada `Mode` com a `clientCredentialType`mensagem e apropriada.</span><span class="sxs-lookup"><span data-stu-id="e7e95-128">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="e7e95-129">As etapas a seguir mostram como desenvolver um provedor de token personalizado e integrá-lo com a estrutura de segurança do WCF:</span><span class="sxs-lookup"><span data-stu-id="e7e95-129">The following steps show how to develop a custom token provider and integrate it with the WCF security framework:</span></span>

1. <span data-ttu-id="e7e95-130">Escreva um provedor de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="e7e95-130">Write a custom token provider.</span></span>

     <span data-ttu-id="e7e95-131">O exemplo implementa um provedor de token personalizado que obtém o nome de usuário e a senha.</span><span class="sxs-lookup"><span data-stu-id="e7e95-131">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="e7e95-132">A senha deve corresponder a este nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="e7e95-132">The password must match this username.</span></span> <span data-ttu-id="e7e95-133">Esse provedor de token personalizado é apenas para fins de demonstração e não é recomendado para implantação do mundo real.</span><span class="sxs-lookup"><span data-stu-id="e7e95-133">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>

     <span data-ttu-id="e7e95-134">Para executar essa tarefa, o provedor de token personalizado deriva a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> classe e substitui o <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> método.</span><span class="sxs-lookup"><span data-stu-id="e7e95-134">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="e7e95-135">Esse método cria e retorna um novo `UserNameSecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="e7e95-135">This method creates and returns a new `UserNameSecurityToken`.</span></span>

    ```csharp
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

2. <span data-ttu-id="e7e95-136">Gravar Gerenciador de token de segurança personalizado.</span><span class="sxs-lookup"><span data-stu-id="e7e95-136">Write custom security token manager.</span></span>

     <span data-ttu-id="e7e95-137">O <xref:System.IdentityModel.Selectors.SecurityTokenManager> é usado para criar <xref:System.IdentityModel.Selectors.SecurityTokenProvider> para o <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> específico que é passado para ele `CreateSecurityTokenProvider` no método.</span><span class="sxs-lookup"><span data-stu-id="e7e95-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="e7e95-138">O Gerenciador de token de segurança também é usado para criar autenticadores de token e um serializador de token, mas eles não são cobertos por esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="e7e95-138">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="e7e95-139">Neste exemplo, o Gerenciador de token de segurança personalizado herda <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> da classe e substitui `CreateSecurityTokenProvider` o método para retornar o provedor de token de nome de usuário personalizado quando os requisitos de token passados indicam que o provedor de nome de usuário é solicitado.</span><span class="sxs-lookup"><span data-stu-id="e7e95-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>

    ```csharp
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

3. <span data-ttu-id="e7e95-140">Grave uma credencial de cliente personalizada.</span><span class="sxs-lookup"><span data-stu-id="e7e95-140">Write a custom client credential.</span></span>

     <span data-ttu-id="e7e95-141">A classe de credenciais de cliente é usada para representar as credenciais que são configuradas para o proxy do cliente e cria o Gerenciador de token de segurança que é usado para obter autenticadores de token, provedores de token e um serializador de token.</span><span class="sxs-lookup"><span data-stu-id="e7e95-141">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>

    ```csharp
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

4. <span data-ttu-id="e7e95-142">Configure o cliente para usar a credencial de cliente personalizada.</span><span class="sxs-lookup"><span data-stu-id="e7e95-142">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="e7e95-143">Para que o cliente use a credencial de cliente personalizada, o exemplo exclui a classe de credencial do cliente padrão e fornece a nova classe de credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="e7e95-143">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>

    ```csharp
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

 <span data-ttu-id="e7e95-144">No serviço, para exibir as informações do chamador, use o <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e7e95-144">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="e7e95-145">O <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contém informações de declarações sobre o chamador atual.</span><span class="sxs-lookup"><span data-stu-id="e7e95-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 <span data-ttu-id="e7e95-146">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="e7e95-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e7e95-147">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e7e95-147">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="e7e95-148">Arquivo em lotes de instalação</span><span class="sxs-lookup"><span data-stu-id="e7e95-148">Setup Batch File</span></span>
 <span data-ttu-id="e7e95-149">O arquivo em lotes setup. bat incluído com este exemplo permite que você configure o servidor com o certificado relevante para executar um aplicativo auto-hospedado que requer segurança baseada em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="e7e95-149">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="e7e95-150">Esse arquivo em lotes deve ser modificado para funcionar em computadores ou para funcionar em um caso não hospedado.</span><span class="sxs-lookup"><span data-stu-id="e7e95-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="e7e95-151">Veja a seguir uma breve visão geral das diferentes seções dos arquivos em lotes para que eles possam ser modificados para serem executados na configuração apropriada:</span><span class="sxs-lookup"><span data-stu-id="e7e95-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="e7e95-152">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="e7e95-152">Creating the server certificate.</span></span>

     <span data-ttu-id="e7e95-153">As linhas a seguir do arquivo em lotes setup. bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="e7e95-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="e7e95-154">A `%SERVER_NAME%` variável especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="e7e95-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="e7e95-155">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="e7e95-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="e7e95-156">O valor padrão nesse arquivo em lotes é localhost.</span><span class="sxs-lookup"><span data-stu-id="e7e95-156">The default value in this batch file is localhost.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="e7e95-157">Instalando o certificado do servidor no repositório de certificados confiáveis do cliente:</span><span class="sxs-lookup"><span data-stu-id="e7e95-157">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="e7e95-158">As linhas a seguir no arquivo em lotes setup. bat copiam o certificado do servidor no repositório de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="e7e95-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="e7e95-159">Essa etapa é necessária porque os certificados gerados pelo MakeCert. exe não são implicitamente confiáveis pelo sistema cliente.</span><span class="sxs-lookup"><span data-stu-id="e7e95-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="e7e95-160">Se você já tiver um certificado com raiz em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — esta etapa de popular o repositório de certificados do cliente com o certificado do servidor não será necessária.</span><span class="sxs-lookup"><span data-stu-id="e7e95-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

> [!NOTE]
> <span data-ttu-id="e7e95-161">O arquivo em lotes setup. bat foi projetado para ser executado em um prompt de comando SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="e7e95-161">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="e7e95-162">Ele requer que a variável de ambiente MSSDK aponte para o diretório em que o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="e7e95-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="e7e95-163">Essa variável de ambiente é definida automaticamente em um prompt de comando SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="e7e95-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="e7e95-164">Para configurar e compilar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e7e95-164">To set up and build the sample</span></span>

1. <span data-ttu-id="e7e95-165">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e7e95-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e7e95-166">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e7e95-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="e7e95-167">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="e7e95-167">To run the sample on the same computer</span></span>

1. <span data-ttu-id="e7e95-168">Execute setup. bat da pasta de instalação de exemplo dentro de um prompt de comando do Visual Studio 2012 aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="e7e95-168">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="e7e95-169">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="e7e95-169">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e7e95-170">O arquivo em lotes setup. bat foi projetado para ser executado em um prompt de comando do Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="e7e95-170">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="e7e95-171">A variável de ambiente PATH definida no prompt de comando do Visual Studio 2012 aponta para o diretório que contém os executáveis exigidos pelo script setup. bat.</span><span class="sxs-lookup"><span data-stu-id="e7e95-171">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="e7e95-172">Inicie o Service. exe em service\bin.</span><span class="sxs-lookup"><span data-stu-id="e7e95-172">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="e7e95-173">Inicie o Client.exe no \client\bin.</span><span class="sxs-lookup"><span data-stu-id="e7e95-173">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="e7e95-174">A atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="e7e95-174">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="e7e95-175">Na solicitação de nome de usuário, digite um nome de utilizador.</span><span class="sxs-lookup"><span data-stu-id="e7e95-175">At the username prompt, type a user name.</span></span>  
  
5. <span data-ttu-id="e7e95-176">No prompt de senha, use a mesma cadeia de caracteres que foi digitada para o prompt de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="e7e95-176">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6. <span data-ttu-id="e7e95-177">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e7e95-177">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="e7e95-178">Para executar o exemplo entre computadores</span><span class="sxs-lookup"><span data-stu-id="e7e95-178">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="e7e95-179">Crie um diretório no computador de serviço para os binários de serviço.</span><span class="sxs-lookup"><span data-stu-id="e7e95-179">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="e7e95-180">Copie os arquivos de programa do serviço para o diretório de serviço no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="e7e95-180">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="e7e95-181">Copie também os arquivos Setup. bat e Cleanup. bat para o computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="e7e95-181">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="e7e95-182">Você deve ter um certificado de servidor com o nome da entidade que contém o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="e7e95-182">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="e7e95-183">O arquivo Service. exe. config deve ser atualizado para refletir esse novo nome de certificado.</span><span class="sxs-lookup"><span data-stu-id="e7e95-183">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="e7e95-184">Você pode criar um certificado de servidor modificando o arquivo em lotes setup. bat.</span><span class="sxs-lookup"><span data-stu-id="e7e95-184">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="e7e95-185">Observe que o arquivo setup. bat deve ser executado de um Prompt de Comando do Desenvolvedor para o Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="e7e95-185">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="e7e95-186">Você deve definir `%SERVER_NAME%` a variável para o nome de host totalmente qualificado do computador que é usado para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="e7e95-186">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="e7e95-187">Copie o certificado do servidor no repositório CurrentUser-TrustedPeople do cliente.</span><span class="sxs-lookup"><span data-stu-id="e7e95-187">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="e7e95-188">Você não precisa fazer isso quando o certificado do servidor é emitido por um emissor confiável do cliente.</span><span class="sxs-lookup"><span data-stu-id="e7e95-188">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="e7e95-189">No arquivo Service. exe. config no computador do serviço, altere o valor do endereço base para especificar um nome de computador totalmente qualificado em vez de localhost.</span><span class="sxs-lookup"><span data-stu-id="e7e95-189">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="e7e95-190">No computador do serviço, execute o Service. exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e7e95-190">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="e7e95-191">Copie os arquivos de programas do cliente da pasta \client\bin\, na pasta específica do idioma, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="e7e95-191">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="e7e95-192">No arquivo client. exe. config no computador cliente, altere o valor de endereço do ponto de extremidade para corresponder ao novo endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="e7e95-192">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="e7e95-193">No computador cliente, inicie `Client.exe` a partir de uma janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e7e95-193">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="e7e95-194">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e7e95-194">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="e7e95-195">Para limpar após o exemplo</span><span class="sxs-lookup"><span data-stu-id="e7e95-195">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="e7e95-196">Execute o Cleanup. bat na pasta Samples depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="e7e95-196">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
