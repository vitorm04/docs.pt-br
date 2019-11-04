---
title: Validador de senha e nome de usuário
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 553ccd69a02e057c5131128378611a19502e713d
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424157"
---
# <a name="user-name-password-validator"></a><span data-ttu-id="2c1c3-102">Validador de senha e nome de usuário</span><span class="sxs-lookup"><span data-stu-id="2c1c3-102">User Name Password Validator</span></span>
<span data-ttu-id="2c1c3-103">Este exemplo demonstra como implementar um validador UserNamePassword personalizado.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="2c1c3-104">Isso é útil em casos em que nenhum dos modos de validação internos do UserNamePassword é apropriado para os requisitos do aplicativo; por exemplo, quando os pares de nome de usuário/senha são armazenados em algum repositório externo, como um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="2c1c3-105">Este exemplo mostra um serviço que tem um validador personalizado que verifica dois pares de nome de usuário/senha específicos.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="2c1c3-106">O cliente usa um par de nome de usuário/senha para se autenticar no serviço.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-106">The client uses such a username/password pair to authenticate to the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c1c3-107">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2c1c3-108">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-108">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="2c1c3-109">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2c1c3-110">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-110">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> <span data-ttu-id="2c1c3-111">Como qualquer pessoa pode construir uma credencial de nome de usuário que usa os pares de nome de usuário/senha que o validador personalizado aceita, o serviço é menos seguro do que o comportamento padrão fornecido pelo validador UserNamePassword padrão.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="2c1c3-112">O validador UserNamePassword padrão tenta mapear o par de nome de usuário/senha fornecido para uma conta do Windows e falha na autenticação se esse mapeamento falhar.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="2c1c3-113">O validador UserNamePassword personalizado neste exemplo não deve ser usado no código de produção; ele é apenas para fins ilustrativos.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>

 <span data-ttu-id="2c1c3-114">Em resumo, este exemplo demonstra como:</span><span class="sxs-lookup"><span data-stu-id="2c1c3-114">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="2c1c3-115">O cliente pode ser autenticado usando um token de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-115">The client can be authenticated using a Username Token.</span></span>

- <span data-ttu-id="2c1c3-116">O servidor valida as credenciais do cliente em relação a um UserNamePasswordValidator personalizado e como propagar falhas personalizadas da lógica de validação de nome de usuário e senha para o cliente.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>

- <span data-ttu-id="2c1c3-117">O servidor é autenticado usando o certificado X. 509 do servidor.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-117">The server is authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="2c1c3-118">O serviço expõe um único ponto de extremidade para se comunicar com o serviço, definido usando o arquivo de configuração, app. config. O ponto de extremidade consiste em um endereço, uma associação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="2c1c3-119">A associação é configurada com um padrão `wsHttpBinding` que usa o WS-Security e a autenticação de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Security and username authentication.</span></span> <span data-ttu-id="2c1c3-120">O comportamento do serviço especifica o modo de `Custom` para validar pares de nome de usuário/senha do cliente junto com o tipo da classe do validador.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="2c1c3-121">O comportamento também especifica o certificado do servidor usando o elemento `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="2c1c3-122">O certificado do servidor deve conter o mesmo valor para o `SubjectName` como o `findValue` no [> do\<de certificados](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="2c1c3-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <!-- use host/baseAddresses to configure base address provided by host -->
      <host>
        <baseAddresses>
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service" />
        </baseAddresses>
      </host>
      <!-- use base address specified above, provide one endpoint -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- username binding -->
      <binding name="Binding">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceDebug includeExceptionDetailInFaults ="true"/>
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to
          specify a custom validator for username/password
          combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom"
                                  customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate. A service certificate is used by a client to authenticate the service and provide message protection. You must specify a server certificate when passing username/passwords to encrypt the information as it is sent on the wire. Otherwise the username and password information would be sent as clear text. This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

 <span data-ttu-id="2c1c3-123">A configuração de ponto de extremidade do cliente consiste em um nome de configuração, um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="2c1c3-124">A associação de cliente é configurada com o modo e a mensagem `clientCredentialType`apropriados.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
address="http://localhost:8001/servicemodelsamples/service/username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
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
```

 <span data-ttu-id="2c1c3-125">A implementação do cliente solicita que o usuário insira um nome de usuário e uma senha.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-125">The client implementation prompts the user to enter a username and password.</span></span>

```csharp
// Get the username and password
Console.WriteLine("Username authentication required.");
Console.WriteLine("Provide a username.");
Console.WriteLine("   Enter username: (test1)");
string username = Console.ReadLine();
Console.WriteLine("   Enter password:");
string password = "";
ConsoleKeyInfo info = Console.ReadKey(true);
while (info.Key != ConsoleKey.Enter)
{
    if (info.Key != ConsoleKey.Backspace)
    {
        if (info.KeyChar != '\0')
        {
            password += info.KeyChar;
        }
        info = Console.ReadKey(true);
    }
    else if (info.Key == ConsoleKey.Backspace)
    {
        if (password != "")
        {
            password = password.Substring(0, password.Length - 1);
        }
        info = Console.ReadKey(true);
    }
}
for (int i = 0; i < password.Length; i++)
{
    Console.Write("*");
}
Console.WriteLine();
// Create a proxy with Certificate endpoint configuration
CalculatorProxy proxy = new CalculatorProxy("Username")
try
{
  proxy.ClientCredentials.Username.Username = username;
  proxy.ClientCredentials.Username.Password = password;
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = proxy.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
  }
  catch (Exception e)
  {
      Console.WriteLine("Call failed:");
      while (e != null)
      {
          Console.WriteLine("\t{0}", e.Message);
          e = e.InnerException;
      }
      proxy.Abort();
  }
}
```

 <span data-ttu-id="2c1c3-126">Este exemplo usa um UserNamePasswordValidator personalizado para validar os pares de nome de usuário/senha.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="2c1c3-127">O exemplo implementa `CustomUserNamePasswordValidator`, derivado de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="2c1c3-128">Consulte a documentação para obter <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="2c1c3-129">Este exemplo de validador personalizado específico implementa o método `Validate` para aceitar dois pares de nome de usuário/senha específicos, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>

```csharp
public class CustomUserNameValidator : UserNamePasswordValidator
{
 // This method validates users. It allows in two users,
 // test1 and test2 with passwords 1tset and 2tset respectively.
 // This code is for illustration purposes only and
 // MUST NOT be used in a production environment because it
 // is NOT secure.
 public override void Validate(string userName, string password)
 {
  if (null == userName || null == password)
  {
   throw new ArgumentNullException();
  }

  if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))
  {
   throw new FaultException("Unknown Username or Incorrect Password");
   }
  }
 }
```

 <span data-ttu-id="2c1c3-130">Depois que o validador for implementado no código de serviço, o host de serviço deverá ser informado sobre a instância do validador a ser usada.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="2c1c3-131">Isso é feito usando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-131">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 <span data-ttu-id="2c1c3-132">Ou você pode fazer a mesma coisa na configuração da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-132">Or you can do the same thing in configuration as follows.</span></span>

```xml
<behaviors>
 <serviceBehaviors>
  <behavior name="CalculatorServiceBehavior">
  ...
   <serviceCredentials>
    <!--
    The serviceCredentials behavior allows one to specify authentication constraints on username / password combinations.
    -->
    <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+CustomUserNameValidator, service" />
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="2c1c3-133">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2c1c3-134">O cliente deve chamar com êxito todos os métodos.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="2c1c3-135">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-135">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="2c1c3-136">Arquivo em lotes de instalação</span><span class="sxs-lookup"><span data-stu-id="2c1c3-136">Setup Batch File</span></span>
 <span data-ttu-id="2c1c3-137">O arquivo em lotes setup. bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar um aplicativo auto-hospedado que requer segurança baseada em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="2c1c3-138">Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para funcionar em um caso não hospedado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>

 <span data-ttu-id="2c1c3-139">Veja a seguir uma breve visão geral das diferentes seções dos arquivos em lotes para que eles possam ser modificados para serem executados na configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="2c1c3-140">Criando o certificado do servidor:</span><span class="sxs-lookup"><span data-stu-id="2c1c3-140">Creating the server certificate:</span></span>

     <span data-ttu-id="2c1c3-141">As linhas a seguir do arquivo em lotes setup. bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="2c1c3-142">A variável% SERVER_NAME% especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="2c1c3-143">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="2c1c3-144">O valor padrão é localhost.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-144">The default value is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="2c1c3-145">Instalando o certificado do servidor no repositório de certificados confiáveis do cliente:</span><span class="sxs-lookup"><span data-stu-id="2c1c3-145">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="2c1c3-146">As linhas a seguir no arquivo em lotes setup. bat copiam o certificado do servidor no repositório de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="2c1c3-147">Essa etapa é necessária porque os certificados gerados pelo MakeCert. exe não são implicitamente confiáveis pelo sistema cliente.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="2c1c3-148">Se você já tiver um certificado com raiz em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — esta etapa de popular o repositório de certificados do cliente com o certificado do servidor não será necessária.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="2c1c3-149">Para configurar e compilar o exemplo</span><span class="sxs-lookup"><span data-stu-id="2c1c3-149">To set up and build the sample</span></span>

1. <span data-ttu-id="2c1c3-150">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2c1c3-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="2c1c3-151">Para executar o exemplo em uma configuração de computador único ou cruzado, use as instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="2c1c3-152">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="2c1c3-152">To run the sample on the same machine</span></span>

1. <span data-ttu-id="2c1c3-153">Execute setup. bat da pasta de instalação de exemplo dentro de um prompt de comando do Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-153">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt.</span></span> <span data-ttu-id="2c1c3-154">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-154">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2c1c3-155">O arquivo em lotes setup. bat foi projetado para ser executado em um prompt de comando do Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-155">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="2c1c3-156">A variável de ambiente PATH definida no prompt de comando do Visual Studio 2012 aponta para o diretório que contém os executáveis exigidos pelo script setup. bat.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-156">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="2c1c3-157">Inicie o Service. exe em service\bin.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-157">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="2c1c3-158">Inicie o Client. exe em \client\bin.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="2c1c3-159">A atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-159">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="2c1c3-160">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2c1c3-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="2c1c3-161">Para executar o exemplo entre computadores</span><span class="sxs-lookup"><span data-stu-id="2c1c3-161">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="2c1c3-162">Crie um diretório no computador de serviço para os binários de serviço.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="2c1c3-163">Copie os arquivos de programa de serviço no diretório de serviço no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="2c1c3-164">Copie também os arquivos Setup. bat e Cleanup. bat para o computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="2c1c3-165">Você precisa de um certificado de servidor com o nome da entidade que contém o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="2c1c3-166">O arquivo de configuração do servidor deve ser atualizado para refletir esse novo nome de certificado.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4. <span data-ttu-id="2c1c3-167">Copie o certificado do servidor no repositório CurrentUser-TrustedPeople do cliente.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="2c1c3-168">Você precisará fazer isso somente se o certificado do servidor não for emitido por um emissor confiável.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="2c1c3-169">No arquivo app. config no computador do serviço, altere o valor do endereço base para especificar um nome de máquina totalmente qualificado em vez de localhost.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6. <span data-ttu-id="2c1c3-170">Na máquina de serviço, inicie o Service. exe em uma janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7. <span data-ttu-id="2c1c3-171">Copie os arquivos de programas do cliente da pasta \client\bin\, na pasta específica do idioma, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8. <span data-ttu-id="2c1c3-172">No arquivo client. exe. config no computador cliente, altere o valor de endereço do ponto de extremidade para corresponder ao novo endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="2c1c3-173">No computador cliente, inicie o Client. exe em uma janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="2c1c3-174">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2c1c3-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="2c1c3-175">Para limpar após o exemplo</span><span class="sxs-lookup"><span data-stu-id="2c1c3-175">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="2c1c3-176">Execute o Cleanup. bat na pasta Samples depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="2c1c3-177">Isso remove o certificado do servidor do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-177">This removes the server certificate from the certificate store.</span></span>  
