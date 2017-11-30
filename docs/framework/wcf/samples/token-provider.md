---
title: Fornecedor de token
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 87965b8802dd770d6977154ab805889838e9c5e4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="token-provider"></a>Fornecedor de token
Este exemplo demonstra como implementar um provedor do token. Um provedor de token em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é usado para fornecer credenciais para a infraestrutura de segurança. O provedor de token em geral examina o destino e problemas apropriada credenciais para que a infraestrutura de segurança possa proteger a mensagem. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]é fornecido com o provedor de Token do Gerenciador de credenciais padrão. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]também é fornecida com um [!INCLUDE[infocard](../../../../includes/infocard-md.md)] provedor de token. Provedores de token personalizados são úteis nos seguintes casos:  
  
-   Se você tiver um repositório de credenciais que esses provedores de token não podem operar com.  
  
-   Se desejar fornecer seu próprio mecanismo personalizado para transformar as credenciais do ponto quando o usuário fornece os detalhes para quando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estrutura do cliente usa as credenciais.  
  
-   Se você estiver criando um token personalizado.  
  
 Este exemplo mostra como criar um provedor de token personalizado que transforma a entrada do usuário em um formato diferente.  
  
 Para resumir, este exemplo demonstra o seguinte:  
  
-   Como um cliente pode autenticar usando um par de nome de usuário e senha.  
  
-   Como um cliente pode ser configurado com um provedor do token.  
  
-   Como o servidor pode validar as credenciais do cliente usando uma senha com um personalizado <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> que valida o nome de usuário e a senha correspondem.  
  
-   Como o servidor é autenticado pelo cliente usando o certificado do servidor x. 509.  
  
 Este exemplo também mostra como a identidade do chamador é acessível após o processo de autenticação de token personalizado.  
  
 O serviço expõe um ponto de extremidade de comunicação com o serviço, definido usando o arquivo de configuração App. config. O ponto de extremidade consiste em um endereço, uma ligação e um contrato. A associação está configurada com um padrão `wsHttpBinding`, que usa a segurança de mensagem por padrão. Este exemplo define o padrão de `wsHttpBinding` para usar a autenticação de nome de usuário do cliente. O serviço também configura o certificado de serviço usando o comportamento de serviceCredentials. O comportamento de serviceCredentials permite configurar um certificado de serviço. Um certificado de serviço é usado por um cliente para autenticar o serviço e fornecer proteção de mensagem. A configuração a seguir faz referência ao certificado de localhost instalado durante a configuração de exemplo, conforme descrito nas instruções de instalação a seguir.  
  
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
  
 A configuração do ponto de extremidade cliente consiste em um nome de configuração, um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato. A ligação do cliente é configurado com as `Mode` e mensagem `clientCredentialType`.  
  
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
  
 As etapas a seguir mostram como desenvolver um provedor do token e integrá-lo com o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estrutura de segurança:  
  
1.  Grave um provedor do token.  
  
     O exemplo implementa um provedor de token personalizado que obtém o nome de usuário e senha. A senha deve corresponder a esse nome de usuário. Este provedor do token é para fins de demonstração e não é recomendado para implantação do mundo real para.  
  
     Para executar essa tarefa, o provedor de token personalizado derivado de <xref:System.IdentityModel.Selectors.SecurityTokenProvider> classe e substituições de <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> método. Esse método cria e retorna um novo `UserNameSecurityToken`.  
  
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
  
2.  Grave o Gerenciador de token de segurança personalizada.  
  
     O <xref:System.IdentityModel.Selectors.SecurityTokenManager> é usado para criar <xref:System.IdentityModel.Selectors.SecurityTokenProvider> para determinado <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> que é passado para ele no `CreateSecurityTokenProvider` método. Gerenciador de token de segurança também é usado para criar um serializador de token e autenticadores de token, mas aqueles não são cobertas por este exemplo. Neste exemplo, o Gerenciador de token de segurança personalizada herda de <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe e substituições de `CreateSecurityTokenProvider` método para retornar o provedor de token de nome de usuário personalizada quando os requisitos de token passados indicam esse provedor de nome de usuário é solicitado.  
  
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
  
3.  Grave uma credencial de cliente personalizadas.  
  
     Classe de credenciais de cliente é usado para representar as credenciais que são configuradas para o proxy de cliente e cria o Gerenciador de token que é usado para obter um serializador de token, provedores de token e autenticadores de token de segurança.  
  
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
  
4.  Configure o cliente para usar a credencial de cliente personalizadas.  
  
     Em ordem para o cliente usar a credencial de cliente personalizado, o exemplo exclui a classe de credencial de cliente padrão e fornece a nova classe de credencial de cliente.  
  
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
  
 Sobre o serviço, para exibir informações do chamador, use o <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> conforme mostrado no exemplo de código a seguir. O <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contém informações de declarações sobre o chamador atual.  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
        ServiceSecurityContext.Current.PrimaryIdentity.Name);  
}  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
## <a name="setup-batch-file"></a>Arquivo de lote  
 Arquivo em lotes bat incluído com este exemplo permite que você configure o servidor com o certificado apropriado para executar um aplicativo auto-hospedado que exige a segurança baseada em certificado do servidor. Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso não hospedado.  
  
 O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada:  
  
-   Criando o certificado do servidor.  
  
     As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado. O `%SERVER_NAME%` variável Especifica o nome do servidor. Altere essa variável para especificar seu próprio nome de servidor. O valor padrão, esse arquivo em lotes é localhost.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalando o certificado do servidor no repositório de certificados confiáveis do cliente:  
  
     Armazenam as linhas a seguir na cópia de arquivo de lote o certificado do servidor bat para as pessoas confiáveis do cliente. Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado da Microsoft emitido — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
> [!NOTE]
>  O arquivo em lotes bat é projetado para ser executado de um Prompt de comando do SDK do Windows. Isso requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado. Essa variável de ambiente é definida automaticamente em um Prompt de comando do SDK do Windows.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Para configurar e criar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador  
  
1.  Execute bat da pasta de instalação de exemplo dentro de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prompt de comando aberto com privilégios de administrador. Isso instala todos os certificados necessários para executar o exemplo.  
  
    > [!NOTE]
    >  O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando. Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat.  
  
2.  Inicie service.exe de service\bin.  
  
3.  Inicie Client.exe de \Client\Bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
4.  No prompt de nome de usuário, digite um nome de usuário.  
  
5.  No prompt de senha, use a mesma cadeia de caracteres que foi digitada para o prompt de nome de usuário.  
  
6.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  Crie um diretório no computador de serviço para os binários de serviço.  
  
2.  Copie os arquivos de programa do serviço para o diretório de serviço no computador de serviço. Também copie os arquivos. bat e Cleanup.bat para o computador do serviço.  
  
3.  Você deve ter um certificado de servidor com o nome da entidade que contém o nome de domínio totalmente qualificado do computador. O arquivo Service.exe.config deve ser atualizado para refletir o novo nome de certificado. Você pode criar o certificado do servidor, modificando o arquivo em lotes bat. Observe que o arquivo bat deve ser executado em um prompt de comando do Visual Studio aberto com privilégios de administrador. Você deve definir `%SERVER_NAME%` variável ao nome de host totalmente qualificado do computador que é usado para hospedar o serviço.  
  
4.  Copie o certificado do servidor para o armazenamento CurrentUser TrustedPeople do cliente. Você não precisa fazer isso quando o certificado do servidor é emitido por um emissor confiável do cliente.  
  
5.  No arquivo Service.exe.config no computador de serviço, altere o valor do endereço base para especificar um nome de computador totalmente qualificado em vez de localhost.  
  
6.  No computador do serviço, execute service.exe em um prompt de comando.  
  
7.  Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.  
  
8.  No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.  
  
9. No computador cliente, inicie o `Client.exe` em uma janela de prompt de comando.  
  
10. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>A limpeza após a amostra  
  
1.  Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.  
  
## <a name="see-also"></a>Consulte também
