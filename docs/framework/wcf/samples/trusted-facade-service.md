---
title: Serviço de fachada confiável
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 4921b2746b9df362a0bb3e6048602d41f3f2faaf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768183"
---
# <a name="trusted-facade-service"></a>Serviço de fachada confiável
Este exemplo de cenário demonstra como fluxo de informações de identidade do chamador de um serviço para outro usando o Windows Communication Foundation (WCF) infraestrutura de segurança.  
  
 É um padrão de design comum para expor a funcionalidade fornecida por um serviço para a rede pública usando um serviço de fachada. Normalmente, o serviço de fachada reside na rede de perímetro (também conhecida como DMZ, zona desmilitarizada e sub-rede filtrada) e se comunica com um serviço de back-end que implementa a lógica de negócios e tem acesso aos dados internos. O canal de comunicação entre o serviço de fachada e o serviço de back-end passa por um firewall e geralmente é limitado para somente uma única finalidade.  
  
 Esse exemplo consiste nos seguintes componentes:  
  
-   Cliente de Calculadora  
  
-   Serviço de fachada de Calculadora  
  
-   Serviço de back-end de Calculadora  
  
 O serviço de fachada é responsável por validar a solicitação e autenticar o chamador. Após a autenticação e validação, ele encaminha a solicitação para o serviço de back-end usando o canal de comunicação controlada da rede de perímetro para a rede interna. Como parte da solicitação encaminhada, o serviço de fachada inclui informações sobre a identidade do chamador para que o serviço de back-end pode usar essas informações no seu processamento. A identidade do chamador é transmitida usando um `Username` token de segurança dentro da mensagem `Security` cabeçalho. O exemplo usa a infraestrutura de segurança do WCF para transmitir e extrair essas informações do `Security` cabeçalho.  
  
> [!IMPORTANT]
>  O serviço de back-end confia que o serviço de fachada para autenticar o chamador. Por isso, o serviço de back-end não autentica o chamador novamente; Ele usa as informações de identidade fornecidas pelo serviço de fachada na solicitação encaminhada. Devido a essa relação de confiança, o serviço de back-end deve autenticar o serviço de fachada para garantir que a mensagem encaminhada vem de uma fonte confiável - nesse caso, o serviço de fachada.  
  
## <a name="implementation"></a>Implementação  
 Há dois caminhos de comunicação neste exemplo. Primeiro é entre o cliente e o serviço de fachada, a segunda é entre o serviço de fachada e o serviço de back-end.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Caminho de comunicação entre cliente e serviço de fachada  
 Usa o cliente para o caminho de comunicação do serviço de fachada `wsHttpBinding` com um `UserName` tipo de credencial de cliente. Isso significa que o cliente usa o nome de usuário e senha para autenticar para o serviço de fachada e o serviço de fachada usa o certificado x. 509 para autenticar o cliente. A configuração de associação é semelhante ao exemplo a seguir.  
  
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
  
 O serviço de fachada autentica o chamador usar custom `UserNamePasswordValidator` implementação. Para fins de demonstração, a autenticação apenas garante que o nome de usuário do chamador corresponde à senha apresentada. A situação de mundo real, o usuário provavelmente é autenticado usando o Active Directory ou o provedor de associação do ASP.NET personalizado. A implementação de validador reside no `FacadeService.cs` arquivo.  
  
```  
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
  
 O validador personalizado está configurado para ser usado dentro de `serviceCredentials` comportamento no arquivo de configuração de serviço de fachada. Esse comportamento também é usado para configurar o certificado do serviço x. 509.  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Caminho de comunicação entre o serviço de fachada e serviço de back-end  
 O serviço de fachada para o caminho de comunicação do serviço de back-end usa um `customBinding` que consiste em vários elementos de associação. Essa associação faz duas coisas: Ele autentica o serviço de fachada e o serviço de back-end para garantir que a comunicação seja segura e é proveniente de uma fonte confiável. Além disso, ele também transmite a identidade do chamador inicial dentro de `Username` token de segurança. Nesse caso, somente nome de usuário do chamador inicial é transmitida para o serviço de back-end, a senha não está incluída na mensagem. Isso ocorre porque o serviço de fachada para autenticar o chamador antes de encaminhar a solicitação para ele de relações de confiança do serviço de back-end. Porque o serviço de fachada se autentica para o serviço de back-end, o serviço de back-end pode confiar as informações contidas na solicitação encaminhada.  
  
 A seguir está a configuração de associação para este caminho de comunicação.  
  
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
  
 O [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento de associação se encarrega de transmissão de nome de usuário e a extração do chamador inicial. O [ \<windowsStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) e [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) cuidar da autenticação dos serviços de fachada e de back-end e a proteção da mensagem.  
  
 Para encaminhar a solicitação, a implementação do serviço de fachada deve fornecer o nome de usuário do chamador inicial para que essa infraestrutura de segurança do WCF pode colocá-la para a mensagem encaminhada. Nome de usuário do chamador inicial é fornecido na implementação do serviço de fachada definindo-o `ClientCredentials` desse serviço de fachada de propriedade na instância do proxy do cliente usa para se comunicar com o serviço de back-end.  
  
 O seguinte código mostra como `GetCallerIdentity` método é implementado no serviço de fachada. Outros métodos usem o mesmo padrão.  
  
```  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 Conforme mostrado no código anterior, a senha não está definida no `ClientCredentials` , somente o nome de usuário estiver definida. Infraestrutura de segurança do WCF cria um token de segurança do nome de usuário sem uma senha nesse caso, o que é exatamente o que é necessária nesse cenário.  
  
 No serviço de back-end, as informações contidas no token de segurança de nome de usuário devem ser autenticadas. Por padrão, a segurança do WCF tenta mapear o usuário a uma conta do Windows usando a senha fornecida. Nesse caso, não há nenhuma senha fornecida e o serviço de back-end não é necessária para autenticar o nome de usuário porque a autenticação já foi executada pelo serviço de fachada. Para implementar essa funcionalidade no WCF, um personalizado `UserNamePasswordValidator` for fornecido, que impõe apenas que um nome de usuário é especificada no token e não executa nenhuma autenticação adicional.  
  
```  
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
  
 O validador personalizado está configurado para ser usado dentro de `serviceCredentials` comportamento no arquivo de configuração de serviço de fachada.  
  
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
  
 Para extrair as informações de nome de usuário e informações sobre a conta de serviço de fachada confiável, a implementação do serviço de back-end usa o `ServiceSecurityContext` classe. O seguinte código mostra como o `GetCallerIdentity` método é implementado.  
  
```  
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
  
 As informações de conta de serviço de fachada são extraídas usando o `ServiceSecurityContext.Current.WindowsIdentity` propriedade. Para acessar as informações sobre o chamador inicial o serviço de back-end usa o `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` propriedade. Ele procura por um `Identity` com um tipo de declaração `Name`. Essa declaração é gerada automaticamente pela infraestrutura de segurança do WCF das informações contidas no `Username` token de segurança.  
  
## <a name="running-the-sample"></a>Executando o exemplo  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente. Você pode pressionar ENTER nas janelas do console de serviço fachada e de back-end para desligar os serviços.  
  
```  
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
  
 O arquivo em lotes de Setup. bat incluído no exemplo de cenário de fachada confiável permite que você configure o servidor com um certificado apropriado para executar o serviço de fachada que exija segurança baseada em certificado para autenticar-se com o cliente. Consulte o procedimento de instalação no final deste tópico para obter detalhes.  
  
 O exemplo a seguir fornece uma visão geral sobre as diferentes seções dos arquivos de lote.  
  
-   Criando o certificado do servidor.  
  
     As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     O `%SERVER_NAME%` variável Especifica o nome do servidor, o valor padrão é localhost. O certificado é armazenado no repositório de LocalMachine.  
  
-   Instalando o certificado do serviço de fachada no repositório de certificados confiáveis do cliente.  
  
     A linha a seguir copia o certificado do serviço de fachada para o repositório de pessoas confiáveis do cliente. Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar o exemplo na mesma máquina  
  
1. Certifique-se de que o caminho inclui a pasta onde se encontra Makecert.exe.  
  
2. Execute Setup. bat da pasta de instalação de exemplo. Essa opção instala todos os certificados necessários para executar o exemplo.  
  
3. Inicie o BackendService.exe do diretório \BackendService\bin em uma janela separada do console  
  
4. Inicie o FacadeService.exe do diretório \FacadeService\bin em uma janela separada do console  
  
5. Inicie o Client.exe no \client\bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
6. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Para limpar após a amostra  
  
1. Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
