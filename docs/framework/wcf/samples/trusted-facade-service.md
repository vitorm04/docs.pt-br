---
title: Serviço de fachada confiável
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 17901b7a68d4701287d02bc7ee3174683e777fd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143740"
---
# <a name="trusted-facade-service"></a>Serviço de fachada confiável
Esta amostra de cenário demonstra como fluir as informações de identidade do chamador de um serviço para outro usando a infra-estrutura de segurança da Windows Communication Foundation (WCF).  
  
 É um padrão de design comum para expor a funcionalidade fornecida por um serviço à rede pública usando um serviço de fachada. O serviço de fachada normalmente reside na rede de perímetro (também conhecida como DMZ, zona desmilitarizada e sub-rede rastreada) e se comunica com um serviço de back-end que implementa a lógica de negócios e tem acesso a dados internos. O canal de comunicação entre o serviço de fachada e o serviço de back-end passa por um firewall e geralmente é limitado apenas para um único propósito.  
  
 Esta amostra consiste nos seguintes componentes:  
  
- Cliente da calculadora  
  
- Serviço de fachada de calculadora  
  
- Serviço de backend da calculadora  
  
 O serviço de fachada é responsável por validar a solicitação e autenticar o chamador. Após autenticação e validação bem-sucedidas, ele encaminha a solicitação para o serviço backend usando o canal de comunicação controlado da rede de perímetro para a rede interna. Como parte da solicitação encaminhada, o serviço de fachada inclui informações sobre a identidade do chamador para que o serviço de back-end possa usar essas informações em seu processamento. A identidade do chamador é `Username` transmitida usando um `Security` token de segurança dentro do cabeçalho da mensagem. A amostra usa a infra-estrutura de segurança `Security` WCF para transmitir e extrair essas informações do cabeçalho.  
  
> [!IMPORTANT]
> O serviço backend confia no serviço de fachada para autenticar o chamador. Por causa disso, o serviço backend não autentica o chamador novamente; utiliza as informações de identidade fornecidas pelo serviço de fachada na solicitação encaminhada. Por causa dessa relação de confiança, o serviço de back-end deve autenticar o serviço de fachada para garantir que a mensagem encaminhada venha de uma fonte confiável - neste caso, o serviço de fachada.  
  
## <a name="implementation"></a>Implementação  
 Há dois caminhos de comunicação nesta amostra. Primeiro é entre o cliente e o serviço de fachada, o segundo é entre o serviço de fachada e o serviço back-end.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Caminho de Comunicação entre Cliente e Serviço de Fachada  
 O cliente para o caminho `wsHttpBinding` de `UserName` comunicação de serviço de fachada usa com um tipo de credencial do cliente. Isso significa que o cliente usa nome de usuário e senha para autenticar ao serviço de fachada e o serviço de fachada usa o certificado X.509 para autenticar ao cliente. A configuração de vinculação parece ser o exemplo a seguir.  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 O serviço de fachada autentica o `UserNamePasswordValidator` chamador usando a implementação personalizada. Para fins de demonstração, a autenticação apenas garante que o nome de usuário do chamador corresponda à senha apresentada. Na situação do mundo real, o usuário provavelmente é autenticado usando o Active Directory ou o provedor de associação de ASP.NET personalizado. A implementação do `FacadeService.cs` validador reside no arquivo.  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 O validador personalizado está configurado `serviceCredentials` para ser usado dentro do comportamento no arquivo de configuração do serviço de fachada. Esse comportamento também é usado para configurar o certificado X.509 do serviço.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate
               findValue="localhost"
               storeLocation="LocalMachine"
               storeName="My"
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Caminho de comunicação entre serviço de fachada e serviço backend  
 O serviço de fachada para o caminho `customBinding` de comunicação de serviço back-end utiliza um que consiste em vários elementos de ligação. Essa ligação realiza duas coisas. Ele autentica o serviço de fachada e o serviço de backend para garantir que a comunicação seja segura e venha de uma fonte confiável. Além disso, ele também transmite a identidade `Username` do chamador inicial dentro do token de segurança. Neste caso, apenas o nome de usuário do chamador inicial é transmitido para o serviço de back-end, a senha não está incluída na mensagem. Isso porque o serviço backend confia no serviço de fachada para autenticar o chamador antes de encaminhar a solicitação para ele. Como o serviço de fachada se autentica no serviço backend, o serviço de back-end pode confiar nas informações contidas na solicitação encaminhada.  
  
 A seguir está a configuração de vinculação para este caminho de comunicação.  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 O elemento [ \<de ligação de segurança>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) cuida da transmissão e extração do nome de usuário do chamador inicial. O [ \<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) e [ \<o tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) cuidar da autenticação dos serviços de fachada e back-end e proteção de mensagens.  
  
 Para encaminhar a solicitação, a implementação do serviço de fachada deve fornecer o nome de usuário do chamador inicial para que a infra-estrutura de segurança do WCF possa colocá-la na mensagem encaminhada. O nome de usuário do chamador inicial é fornecido na `ClientCredentials` implementação do serviço de fachada, definindo-o na propriedade na instância de proxy do cliente que o serviço de fachada usa para se comunicar com o serviço backend.  
  
 O código a `GetCallerIdentity` seguir mostra como o método é implementado no serviço de fachada. Outros métodos usam o mesmo padrão.  
  
```csharp  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 Como mostrado no código anterior, a senha `ClientCredentials` não está definida na propriedade, apenas o nome de usuário é definido. A infra-estrutura de segurança WCF cria um token de segurança de nome de usuário sem senha neste caso, que é exatamente o que é necessário neste cenário.  
  
 No serviço backend, as informações contidas no token de segurança do nome de usuário devem ser autenticadas. Por padrão, a segurança do WCF tenta mapear o usuário para uma conta do Windows usando a senha fornecida. Neste caso, não há senha fornecida e o serviço de back-end não é necessário para autenticar o nome de usuário porque a autenticação já foi realizada pelo serviço de fachada. Para implementar essa funcionalidade no WCF, é fornecido um personalizado `UserNamePasswordValidator` que apenas impõe que um nome de usuário seja especificado no token e não execute nenhuma autenticação adicional.  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 O validador personalizado está configurado `serviceCredentials` para ser usado dentro do comportamento no arquivo de configuração do serviço de fachada.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Para extrair as informações e informações sobre o nome de usuário e `ServiceSecurityContext` informações sobre a conta de serviço de fachada confiável, a implementação do serviço backend usa a classe. O código a `GetCallerIdentity` seguir mostra como o método é implementado.  
  
```csharp  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 As informações da conta de serviço `ServiceSecurityContext.Current.WindowsIdentity` de fachada são extraídas usando a propriedade. Para acessar as informações sobre o chamador `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` inicial, o serviço backend usa a propriedade. Ele procura `Identity` uma reivindicação `Name`com um tipo. Essa reclamação é gerada automaticamente pela infra-estrutura de `Username` segurança WCF a partir das informações contidas no token de segurança.  
  
## <a name="running-the-sample"></a>Executando o exemplo  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. Pressione ENTER na janela do cliente para desligar o cliente. Você pode pressionar ENTER nas janelas do console de serviço de fachada e back-end para desligar os serviços.  
  
```console  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 O arquivo de lote Setup.bat incluído na amostra de cenário Trusted Facade permite configurar o servidor com um certificado relevante para executar o serviço de fachada que requer segurança baseada em certificado para autenticar-se ao cliente. Consulte o procedimento de configuração no final deste tópico para obter detalhes.  
  
 O seguinte fornece uma breve visão geral das diferentes seções dos arquivos em lote.  
  
- Criando o certificado do servidor.  
  
     As seguintes linhas do arquivo setup.bat batch criam o certificado de servidor a ser usado.  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     A `%SERVER_NAME%` variável especifica o nome do servidor - o valor padrão é localhost. O certificado é armazenado na loja LocalMachine.  
  
- Instalando o certificado do serviço de fachada na loja de certificados confiáveis do cliente.  
  
     A linha a seguir copia o certificado do serviço de fachada na loja de pessoas confiáveis do cliente. Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema cliente. Se você já tiver um certificado enraizado em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de povoar a loja de certificados do cliente com o certificado do servidor não é necessária.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar a amostra na mesma máquina  
  
1. Certifique-se de que o caminho inclui a pasta onde o Makecert.exe está localizado.  
  
2. Executar Setup.bat da pasta de instalação de amostra. Isso instala todos os certificados necessários para a execução da amostra.  
  
3. Inicie o BackendService.exe do diretório \BackendService\bin em uma janela de console separada  
  
4. Inicie o Diretório FacadeService.exe de \FacadeService\bin em uma janela de console separada  
  
5. Inicie client.exe a partir de \client\bin. A atividade do cliente é exibida no aplicativo do console cliente.  
  
6. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Para limpar depois da amostra  
  
1. Executar Cleanup.bat na pasta amostras depois de terminar de executar a amostra.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
