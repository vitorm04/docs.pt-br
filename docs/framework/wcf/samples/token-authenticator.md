---
title: Autenticador de token
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d635a1d5122319e228feb4d8a362b7609129c9de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="token-authenticator"></a>Autenticador de token
Este exemplo demonstra como implementar um autenticador de token personalizado. Um autenticador de token em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é usado para validar o token usado com a mensagem, verificar se ele é consistente e autenticar a identidade associada ao token.  
  
 Autenticadores de token personalizados são úteis em uma variedade de casos, como:  
  
-   Quando você deseja substituir o mecanismo de autenticação padrão associado a um token.  
  
-   Quando você está criando um token personalizado.  
  
 Este exemplo demonstra o seguinte:  
  
-   Como um cliente pode autenticar usando um par de nome de usuário e senha.  
  
-   Como o servidor pode validar as credenciais do cliente usando um autenticador de token personalizado.  
  
-   Como o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] código de serviço está associado com o autenticador de token personalizado.  
  
-   Como o servidor pode ser autenticado usando o certificado do servidor x. 509.  
  
 Este exemplo também mostra como a identidade do chamador é acessível de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] após o processo de autenticação de token personalizado.  
  
 O serviço expõe um ponto de extremidade de comunicação com o serviço, definido usando o arquivo de configuração App. config. O ponto de extremidade consiste em um endereço, uma ligação e um contrato. A associação está configurada com um padrão `wsHttpBinding`, com o modo de segurança definido para a mensagem - o modo padrão da `wsHttpBinding`. Este exemplo define o padrão de `wsHttpBinding` para usar a autenticação de nome de usuário do cliente. O serviço também configura o certificado de serviço usando `serviceCredentials` comportamento. O `securityCredentials` comportamento permite que você especifique um certificado de serviço. Um certificado de serviço é usado por um cliente para autenticar o serviço e fornecer proteção de mensagem. A configuração a seguir faz referência ao certificado de localhost instalado durante a configuração de exemplo, conforme descrito nas instruções de instalação a seguir.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- configure base address provided by host -->  
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />  
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
....        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 A configuração do ponto de extremidade cliente consiste em um nome de configuração, um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato. A ligação do cliente é configurado com as `Mode` e `clientCredentialType`.  
  
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
  
 A implementação de cliente define o nome de usuário e senha a ser usada.  
  
```  
static void Main()  
{  
     ...  
     client.ClientCredentials.UserNamePassword.UserName = username;  
     client.ClientCredentials.UserNamePassword.Password = password;  
     ...  
}  
```  
  
## <a name="custom-token-authenticator"></a>Autenticador de Token personalizado  
 Use as etapas a seguir para criar um autenticador de token personalizado:  
  
1.  Grave um autenticador de token personalizado.  
  
     O exemplo implementa um autenticador de token personalizado que valida o nome de usuário tem um formato de email válido. Ele é derivado de <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>. O método mais importante dessa classe é <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>. Nesse método, o autenticador valida o formato do nome de usuário e também que o nome do host não é de um domínio autorizado. Se ambas as condições forem atendidas, ele retorna uma coleção somente leitura de <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instâncias que é usado para fornecer declarações que representam as informações armazenadas dentro do token de nome de usuário.  
  
    ```  
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)  
    {  
        if (!ValidateUserNameFormat(userName))  
            throw new SecurityTokenValidationException("Incorrect UserName format");  
  
        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));  
        List<IIdentity> identities = new List<IIdentity>(1);  
        identities.Add(new GenericIdentity(userName));  
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);  
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));  
        return policies.AsReadOnly();  
    }  
    ```  
  
2.  Forneça uma diretiva de autorização que é retornada pelo autenticador de token personalizado.  
  
     Este exemplo fornece sua própria implementação de <xref:System.IdentityModel.Policy.IAuthorizationPolicy> chamado `UnconditionalPolicy` que retorna o conjunto de declarações e as identidades que foram passadas para ele em seu construtor.  
  
    ```  
    class UnconditionalPolicy : IAuthorizationPolicy  
    {  
        String id = Guid.NewGuid().ToString();  
        ClaimSet issuer;  
        ClaimSet issuance;  
        DateTime expirationTime;  
        IList<IIdentity> identities;  
  
        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)  
        {  
            if (issuer == null)  
                throw new ArgumentNullException("issuer");  
            if (issuance == null)  
                throw new ArgumentNullException("issuance");  
  
            this.issuer = issuer;  
            this.issuance = issuance;  
            this.identities = identities;  
            this.expirationTime = expirationTime;  
        }  
  
        public string Id  
        {  
            get { return this.id; }  
        }  
  
        public ClaimSet Issuer  
        {  
            get { return this.issuer; }  
        }  
  
        public DateTime ExpirationTime  
        {  
            get { return this.expirationTime; }  
        }  
  
        public bool Evaluate(EvaluationContext evaluationContext, ref object state)  
        {  
            evaluationContext.AddToTarget(this, this.issuance);  
  
            if (this.identities != null)  
            {  
                object value;  
                IList<IIdentity> contextIdentities;  
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))  
                {  
                    contextIdentities = new List<IIdentity>(this.identities.Count);  
                    evaluationContext.Properties.Add("Identities", contextIdentities);  
                }  
                else  
                {  
                    contextIdentities = value as IList<IIdentity>;  
                }  
                foreach (IIdentity identity in this.identities)  
                {  
                    contextIdentities.Add(identity);  
                }  
            }  
  
            evaluationContext.RecordExpirationTime(this.expirationTime);  
            return true;  
        }  
    }  
    ```  
  
3.  Grave um Gerenciador de token de segurança personalizada.  
  
     O <xref:System.IdentityModel.Selectors.SecurityTokenManager> é usado para criar um <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> para determinado <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objetos que são passados para ele no `CreateSecurityTokenAuthenticator` método. O Gerenciador de token de segurança também é usado para criar provedores de token e serializadores de token, mas aqueles não são cobertas por este exemplo. Neste exemplo, o Gerenciador de token de segurança personalizada herda de <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> classe e substituições de `CreateSecurityTokenAuthenticator` método para retornar o autenticador de token de nome de usuário personalizada quando os requisitos de token passados indicam que autenticador de nome de usuário é solicitado.  
  
    ```  
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager  
    {  
        MyUserNameCredential myUserNameCredential;  
  
        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)  
            : base(myUserNameCredential)  
        {  
            this.myUserNameCredential = myUserNameCredential;  
        }  
  
        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)  
        {  
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)  
            {  
                outOfBandTokenResolver = null;  
                return new MyTokenAuthenticator();  
            }  
            else  
            {  
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);  
            }  
        }  
    }  
    ```  
  
4.  Grave uma credencial de serviço personalizado.  
  
     A classe de credenciais de serviço é usada para representar as credenciais que são configuradas para o serviço e cria o Gerenciador de token que é usado para obter autenticadores de token, provedores de token e serializadores de token de segurança.  
  
    ```  
    public class MyUserNameCredential : ServiceCredentials  
    {  
  
        public MyUserNameCredential()  
            : base()  
        {  
        }  
  
        protected override ServiceCredentials CloneCore()  
        {  
            return new MyUserNameCredential();  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            return new MySecurityTokenManager(this);  
        }  
  
    }  
    ```  
  
5.  Configure o serviço para usar a credencial de serviço personalizado.  
  
     Em ordem para o serviço para usar a credencial de serviço personalizado, podemos excluir a classe de credencial de serviço padrão depois de capturar o certificado de serviço já está pré-configurado na credencial de serviço padrão e configurar a nova credencial de serviço instância para usar os certificados de serviço pré-configurado e adicionar essa nova instância de credencial de serviço a comportamentos de serviço.  
  
    ```  
    ServiceCredentials sc = serviceHost.Credentials;  
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;  
    MyUserNameCredential serviceCredential = new MyUserNameCredential();  
    serviceCredential.ServiceCertificate.Certificate = cert;  
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));  
    serviceHost.Description.Behaviors.Add(serviceCredential);  
    ```  
  
 Para exibir informações do chamador, você pode usar o <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> conforme mostrado no código a seguir. O <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contém informações de declarações sobre o chamador atual.  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
            ServiceSecurityContext.Current.PrimaryIdentity.Name);  
     return;  
}  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
## <a name="setup-batch-file"></a>Arquivo de lote  
 Arquivo em lotes bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar um aplicativo auto-hospedado que requer um servidor de segurança baseada em certificado. Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso não hospedado.  
  
 O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada.  
  
-   Criando o certificado do servidor.  
  
     As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado. O `%SERVER_NAME%` variável Especifica o nome do servidor. Altere essa variável para especificar seu próprio nome de servidor. O padrão, esse arquivo em lotes é localhost.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalando o certificado de servidor no repositório de certificados confiáveis do cliente.  
  
     Armazenam as linhas a seguir na cópia de arquivo de lote o certificado do servidor bat para as pessoas confiáveis do cliente. Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado da Microsoft emitido — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  O arquivo de lote é projetado para ser executado de um Prompt de comando do SDK do Windows. Isso requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado. Essa variável de ambiente é definida automaticamente em um Prompt de comando do SDK do Windows.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Para configurar e criar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador  
  
1.  Execute bat da pasta de instalação de exemplo dentro de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prompt de comando aberto com privilégios de administrador. Isso instala todos os certificados necessários para executar o exemplo.  
  
    > [!NOTE]
    >  O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando. Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat.  
  
2.  Inicie service.exe de service\bin.  
  
3.  Inicie client.exe de \Client\Bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
4.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  Crie um diretório no computador de serviço para os binários de serviço.  
  
2.  Copie os arquivos de programa do serviço para o diretório de serviço no computador de serviço. Também copie os arquivos. bat e Cleanup.bat para o computador do serviço.  
  
3.  Você deve ter um certificado de servidor com o nome da entidade que contém o nome de domínio totalmente qualificado do computador. O arquivo App. config do serviço deve ser atualizado para refletir o novo nome de certificado. Você pode criar uma usando o bat se você definir o `%SERVER_NAME%` variável ao nome de host totalmente qualificado do computador no qual o serviço será executado. Observe que o arquivo bat deve ser executado em um prompt de comando do Visual Studio aberto com privilégios de administrador.  
  
4.  Copie o certificado do servidor para o armazenamento CurrentUser TrustedPeople do cliente. Você não precisa fazer isso, exceto quando o certificado do servidor é emitido por um emissor confiável do cliente.  
  
5.  No arquivo App. config no computador de serviço, altere o valor do endereço base para especificar um nome de computador totalmente qualificado em vez de localhost.  
  
6.  No computador do serviço, execute service.exe em um prompt de comando.  
  
7.  Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.  
  
8.  No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.  
  
9. No computador cliente, inicie o Client.exe em um prompt de comando.  
  
10. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>A limpeza após a amostra  
  
1.  Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.  
  
## <a name="see-also"></a>Consulte também
