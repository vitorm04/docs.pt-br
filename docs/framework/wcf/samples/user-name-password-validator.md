---
title: Validador de senha e nome de usuário
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 202c7bfc7f60afbad8220950e46c08c0a71eb001
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183247"
---
# <a name="user-name-password-validator"></a>Validador de senha e nome de usuário
Esta amostra demonstra como implementar um validador de senha de usuário personalizado. Isso é útil nos casos em que nenhum dos modos de validação de senha de usuário incorporado satisfaz os requisitos do aplicativo; por exemplo, quando os pares de nome de usuário/senha são armazenados em alguma loja externa, como um banco de dados. Esta amostra mostra um serviço que tem um validador personalizado que verifica dois pares de nome de usuário/senha específicos. O cliente usa esse par de nome de usuário/senha para autenticar o serviço.

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> Como qualquer pessoa pode construir uma credencial de nome de usuário que use os pares de nome de usuário/senha que o validador personalizado aceita, o serviço é menos seguro do que o comportamento padrão fornecido pelo Validador de senha de nome de usuário padrão. O Validador padrão UserNamePassword tenta mapear o par de nome de usuário/senha fornecido para uma conta do Windows e falha na autenticação se esse mapeamento falhar. O validador de senha de nome de usuário personalizado nesta amostra NÃO DEVE ser usado no código de produção, é apenas para fins de ilustração.

 Em resumo, esta amostra demonstra como:

- O cliente pode ser autenticado usando um Token de nome de usuário.

- O servidor valida as credenciais do cliente em um UsuárioNamePasswordValidator personalizado e como propagar falhas personalizadas da lógica de validação de nome de usuário e senha para o cliente.

- O servidor é autenticado usando o certificado X.509 do servidor.

 O serviço expõe um único ponto final para se comunicar com o serviço, definido usando o arquivo de configuração, App.config. O ponto final consiste em um endereço, um vinculativo e um contrato. A vinculação é configurada com um padrão `wsHttpBinding` que não usa o WS-Security e a autenticação do nome de usuário. O comportamento do `Custom` serviço especifica o modo de validação de pares de nome de usuário/senha do cliente, juntamente com o tipo da classe validador. O comportamento também especifica o `serviceCertificate` certificado de servidor usando o elemento. O certificado de servidor tem que `SubjectName` conter `findValue` o mesmo valor para o [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)de certificado no serviço .

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

 A configuração de ponto final do cliente consiste em um nome de configuração, um endereço absoluto para o ponto final do serviço, a vinculação e o contrato. A vinculação do cliente é configurada com o modo e a mensagem apropriados `clientCredentialType`.

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

 A implementação do cliente solicita ao usuário que digite um nome de usuário e senha.

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

 Esta amostra usa um UsuárioNamePasswordValidator personalizado para validar pares de nome de usuário/senha. Os implementos `CustomUserNamePasswordValidator`amostrais, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>derivados de . Consulte a <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> documentação para obter mais informações. Esta amostra de validador `Validate` personalizado em particular implementa o método para aceitar dois pares de nome de usuário/senha específicos, conforme mostrado no código a seguir.

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

 Uma vez que o validador seja implementado no código de serviço, o host de serviço deve ser informado sobre a instância do validador a ser usado. Isso é feito usando o seguinte código.

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 Ou você pode fazer a mesma coisa na configuração da seguinte forma.

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

 Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. O cliente deve chamar com sucesso todos os métodos. Pressione ENTER na janela do cliente para desligar o cliente.

## <a name="setup-batch-file"></a>Arquivo de lote de configuração
 O arquivo de lote Setup.bat incluído nesta amostra permite configurar o servidor com certificados relevantes para executar um aplicativo auto-hospedado que requer segurança baseada em certificados de servidor. Este arquivo em lote deve ser modificado para funcionar em máquinas ou para trabalhar em um caso não-auto-hospedado.

 O seguinte fornece uma breve visão geral das diferentes seções dos arquivos em lote para que eles possam ser modificados para serem executados na configuração apropriada.

- Criação do certificado de servidor:

     As seguintes linhas do arquivo setup.bat batch criam o certificado de servidor a ser usado. A variável %SERVER_NAME% especifica o nome do servidor. Altere essa variável para especificar o nome do seu próprio servidor. O valor padrão é localhost.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalando o certificado do servidor na loja de certificados confiáveis do cliente:

     As seguintes linhas no arquivo de lote Setup.bat copiam o certificado do servidor na loja de pessoas confiáveis do cliente. Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema cliente. Se você já tiver um certificado enraizado em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de povoar a loja de certificados do cliente com o certificado do servidor não é necessária.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Para configurar e construir a amostra

1. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Para executar a amostra em uma configuração de máquina única ou cruzada, use as seguintes instruções.

#### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar a amostra na mesma máquina

1. Executar Setup.bat a partir da pasta de instalação de amostra dentro de um prompt de comando Visual Studio 2012. Isso instala todos os certificados necessários para a execução da amostra.

    > [!NOTE]
    > O arquivo de lote Setup.bat foi projetado para ser executado a partir de um Prompt de comando do Visual Studio 2012. A variável de ambiente PATH definida no Prompt de comando do Visual Studio 2012 aponta para o diretório que contém executáveis exigidos pelo script Setup.bat.  
  
2. Launch Service.exe from service\bin.  
  
3. Inicie client.exe a partir de \client\bin. A atividade do cliente é exibida no aplicativo do console cliente.  
  
4. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-machines"></a>Para executar a amostra através de máquinas  
  
1. Crie um diretório na máquina de serviço para os binários de serviço.  
  
2. Copie o programa de serviço que arquiva o diretório de serviço na máquina de serviço. Copie também os arquivos Setup.bat e Cleanup.bat para a máquina de serviço.  
  
3. Você precisa de um certificado de servidor com o nome do assunto que contenha o nome de domínio totalmente qualificado da máquina. O arquivo de configuração do servidor deve ser atualizado para refletir este novo nome do certificado.  
  
4. Copie o certificado do servidor na loja CurrentUser-TrustedPeople do cliente. Você só precisa fazer isso se o certificado do servidor não for emitido por um emissor confiável.  
  
5. No arquivo App.config na máquina de serviço, altere o valor do endereço base para especificar um nome de máquina totalmente qualificado em vez de localhost.  
  
6. Na máquina de serviço, inicie Service.exe a partir de uma janela de solicitação de comando.  
  
7. Copie os arquivos do programa cliente da pasta \client\bin\\ na pasta específica do idioma para a máquina cliente.  
  
8. No arquivo Client.exe.config na máquina cliente, altere o valor do endereço do ponto final para corresponder ao novo endereço do seu serviço.  
  
9. Na máquina cliente, inicie client.exe a partir de uma janela de solicitação de comando.  
  
10. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Para limpar depois da amostra  
  
1. Executar Cleanup.bat na pasta amostras depois de terminar de executar a amostra. Isso remove o certificado do servidor da loja de certificados.  
