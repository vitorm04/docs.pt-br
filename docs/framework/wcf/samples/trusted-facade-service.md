---
title: "Serviço de fachada confiável"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4147f00b9396609ae80091a02c3f7d2450db34f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="trusted-facade-service"></a>Serviço de fachada confiável
Este exemplo de cenário demonstra como fluxo de informações de identidade do chamador, de um serviço para outro usando [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] infraestrutura de segurança.  
  
 É um padrão de design comum para expor a funcionalidade fornecida por um serviço de rede pública usando um serviço de fachada. O serviço de fachada geralmente reside na rede de perímetro (também conhecida como DMZ, zona desmilitarizada e sub-rede filtrada) e se comunica com um serviço de back-end que implementa a lógica de negócios e tem acesso aos dados internos. O canal de comunicação entre o serviço de fachada e o serviço de back-end passa por um firewall e geralmente é limitado para uma única finalidade.  
  
 Este exemplo consiste dos seguintes componentes:  
  
-   Cliente de cálculo  
  
-   Serviço de fachada de cálculo  
  
-   Serviço de back-end de cálculo  
  
 O serviço de fachada é responsável por validar a solicitação e autenticar o chamador. Após a autenticação bem-sucedida e validação, ele encaminha a solicitação para o serviço de back-end usando o canal de comunicação controlado de rede de perímetro com a rede interna. Como parte da solicitação encaminhada, o serviço de fachada inclui informações sobre a identidade do chamador, para que o serviço de back-end pode usar essas informações no seu processamento. A identidade do chamador é transmitida usando um `Username` token de segurança de mensagem `Security` cabeçalho. O exemplo usa o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura de segurança para transmitir e extrair essas informações do `Security` cabeçalho.  
  
> [!IMPORTANT]
>  O serviço de back-end confia que o serviço de fachada para autenticar o chamador. Por isso, o serviço de back-end não autentica o chamador novamente. Ele usa as informações de identidade fornecidas pelo serviço de fachada na solicitação encaminhada. Devido a essa relação de confiança, o serviço de back-end deve autenticar o serviço de fachada para garantir que a mensagem encaminhada vem de uma fonte confiável - nesse caso, o serviço de fachada.  
  
## <a name="implementation"></a>Implementação  
 Há dois caminhos de comunicação neste exemplo. A primeira é entre o cliente e o serviço de fachada, a segunda é entre o serviço de fachada e o serviço de back-end.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Caminho de comunicação entre cliente e serviço de fachada  
 O cliente para o caminho de comunicação do serviço de fachada usa `wsHttpBinding` com um `UserName` tipo de credencial de cliente. Isso significa que o cliente usa o nome de usuário e senha para autenticar para o serviço de fachada e o serviço de fachada usa o certificado x. 509 para autenticar o cliente. A configuração de associação se parece com o exemplo a seguir.  
  
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
  
 O serviço de fachada autentica o chamador usando personalizado `UserNamePasswordValidator` implementação. Para fins de demonstração, a autenticação apenas garante que o nome de usuário do chamador corresponde à senha apresentada. Em situações reais, o usuário provavelmente é autenticado usando o Active Directory ou o provedor de associação ASP.NET personalizado. A implementação de validador reside no `FacadeService.cs` arquivo.  
  
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
  
 O validador personalizado é configurado para ser usado dentro de `serviceCredentials` comportamento no arquivo de configuração de serviço de fachada. Esse comportamento também é usado para configurar o certificado de x. 509 do serviço.  
  
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
 O serviço de fachada para o caminho de comunicação do serviço de back-end usa um `customBinding` que consiste em vários elementos de associação. Essa associação faz duas coisas: Ele autentica o serviço de fachada e serviço de back-end para garantir que a comunicação segura e é proveniente de uma fonte confiável. Além disso, ele também transmite a identidade do chamador inicial dentro do `Username` token de segurança. Nesse caso, somente nome de usuário do chamador inicial é transmitida para o serviço de back-end, a senha não está incluída na mensagem. Isso ocorre porque o serviço de fachada para autenticar o chamador antes de encaminhar a solicitação de relações de confiança do serviço de back-end. Porque o serviço de fachada ele se autentica para o serviço de back-end, o serviço de back-end pode confiar as informações contidas na solicitação encaminhada.  
  
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
  
 O [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento de associação cuida da transmissão de nome de usuário e a extração inicial do chamador. O [ \<windowsstreamsecurity está >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) e [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) cuidar da autenticação de serviços de back-end e de fachada e proteção de mensagem.  
  
 Para encaminhar a solicitação, a implementação do serviço de fachada deve fornecer o nome de usuário do chamador inicial para que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura de segurança pode colocar isso em da mensagem encaminhada. Nome de usuário do chamador inicial é fornecido na implementação do serviço de fachada definindo- `ClientCredentials` desse serviço de fachada de propriedade na instância do proxy do cliente usa para se comunicar com o serviço de back-end.  
  
 O código a seguir mostra como `GetCallerIdentity` método é implementado no serviço de fachada. Outros métodos usam o mesmo padrão.  
  
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
  
 Conforme mostrado no código anterior, a senha não está definida no `ClientCredentials` , somente o nome de usuário está definida. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]infraestrutura de segurança cria um token de segurança do nome de usuário sem uma senha nesse caso, o que é exatamente o que é necessário neste cenário.  
  
 O serviço de back-end, as informações contidas no token de segurança de nome de usuário devem ser autenticadas. Por padrão, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] segurança tenta mapear o usuário para uma conta do Windows usando a senha fornecida. Nesse caso, não há nenhuma senha fornecida e o serviço de back-end não é necessário para autenticar o nome de usuário porque a autenticação já foi executada pelo serviço de fachada. Para implementar essa funcionalidade no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], um personalizado `UserNamePasswordValidator` for fornecido, que impõe somente se um nome de usuário é especificada no token e não realiza nenhuma autenticação adicional.  
  
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
  
 O validador personalizado é configurado para ser usado dentro de `serviceCredentials` comportamento no arquivo de configuração de serviço de fachada.  
  
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
  
 Para extrair as informações de nome de usuário e informações sobre a conta de serviço de fachada confiável, a implementação do serviço de back-end usa o `ServiceSecurityContext` classe. O código a seguir mostra como o `GetCallerIdentity` método é implementado.  
  
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
  
 As informações de conta de serviço de fachada são extraídas usando a `ServiceSecurityContext.Current.WindowsIdentity` propriedade. Para acessar as informações sobre o chamador inicial do serviço de back-end usa o `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` propriedade. Ele procura um `Identity` com um tipo de declaração `Name`. Esta declaração é automaticamente gerada pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura de segurança das informações contidas no `Username` token de segurança.  
  
## <a name="running-the-sample"></a>Executando o exemplo  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente. Você pode pressionar ENTER nas janelas do console de serviço back-end e de fachada para interromper os serviços.  
  
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
  
 Arquivo em lotes bat incluído com o exemplo de cenário de fachada confiável permite que você configure o servidor com um certificado apropriado para executar o serviço de fachada que exige a segurança baseada em certificado para se autenticar para o cliente. Consulte o procedimento de instalação no final deste tópico para obter detalhes.  
  
 O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote.  
  
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
  
     O `%SERVER_NAME%` variável Especifica o nome do servidor - o valor padrão é localhost. O certificado é armazenado no repositório de LocalMachine.  
  
-   Instalando o certificado do serviço de fachada no repositório de certificados confiáveis do cliente.  
  
     A linha a seguir copia o certificado do serviço de fachada no repositório de pessoas confiáveis do cliente. Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar o exemplo no mesmo computador  
  
1.  Certifique-se de que o caminho inclui a pasta onde Makecert.exe está localizado.  
  
2.  Execute bat da pasta de instalação do exemplo. Isso instala todos os certificados necessários para executar o exemplo.  
  
3.  Inicie o BackendService.exe do diretório \BackendService\bin em uma janela separada do console  
  
4.  Inicie o FacadeService.exe do diretório \FacadeService\bin em uma janela separada do console  
  
5.  Inicie Client.exe de \Client\Bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
6.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>A limpeza após a amostra  
  
1.  Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
  
## <a name="see-also"></a>Consulte também
