---
title: Início rápido de solução de problemas do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: 2d835b055eba6ca66b64555b44cbde64134e743f
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442289"
---
# <a name="wcf-troubleshooting-quickstart"></a>Início rápido de solução de problemas do WCF
Este tópico lista diversos problemas conhecidos, os clientes têm executado até ao desenvolver clientes WCF e serviços. Se o problema que está ocorrendo não estiver nessa lista, é recomendável que configurar o rastreamento para seu serviço. Isso irá gerar um arquivo de rastreamento que você pode exibir com o Visualizador do arquivo de rastreamento e obter informações detalhadas sobre exceções que possam estar ocorrendo dentro do serviço. Para obter mais informações sobre como configurar o rastreamento, consulte: [Configurando o rastreamento](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Para obter mais informações sobre o Visualizador do arquivo de rastreamento, consulte: [Ferramenta de Visualizador de rastreamento (SvcTraceViewer.exe) de serviço](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1.  [Depois de instalar o Windows 7 e o IIS, quando eu tentar navegar para um serviço WCF, eu obtenho a seguinte mensagem de erro: Erro de HTTP 404.3 – não encontrado](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     Erro de HTTP 404.3 – não página FoundThe você está solicitando não pode ser servida devido à configuração da extensão. Se a página é um script, adicione um manipulador. Se o arquivo deve ser baixado, adicione um mapa MIME. InformationModule StaticFileModule de erro detalhada.  
  
2.  [Às vezes, recebo um MessageSecurityException na segunda solicitação se meu cliente está ocioso há algum tempo após a primeira solicitação. O que está acontecendo?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3.  [Meu serviço começa a rejeitar novos clientes depois de cerca de 10 clientes estão interagindo com ele. O que está acontecendo?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4.  [Pode carregar minha configuração de serviço do em outro lugar além do arquivo de configuração do aplicativo WCF?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5.  [Meu serviço e cliente funcionem bem, mas eu não é possível fazê-los funcionar quando o cliente está em outro computador? O que está acontecendo?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6.  [Quando eu gero uma FaultException\<exceção > em que o tipo é uma exceção, eu sempre recebem um tipo FaultException geral no cliente e não o tipo genérico. O que está acontecendo?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7.  [Aparentemente, unidirecional e operações de solicitação-resposta retornam com aproximadamente a mesma velocidade quando a resposta não contém nenhum dado. O que está acontecendo?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8.  [Estou usando um certificado X.509 com o serviço e obter um System.Security.Cryptography.CryptographicException. O que está acontecendo?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [Eu alterei o primeiro parâmetro de uma operação de letras maiusculas em minúsculas; Agora o meu cliente gera uma exceção. O que está acontecendo?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [Estou usando uma das Minhas ferramentas de rastreamento e obtenho um EndpointNotFoundException. O que está acontecendo?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [Ao chamar um aplicativo WCF Web HTTP de um aplicativo WCF SOAP o serviço retornará o seguinte erro: 405 método não permitido](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [O que é o endereço base? Como ele se relaciona a um endereço de ponto de extremidade?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Depois de instalar o Windows 7 e o IIS, quando eu tentar navegar para um serviço WCF, eu obtenho a seguinte mensagem de erro: Erro de HTTP 404.3 – não encontrado  
 A mensagem de erro completa é:  
  
 Erro de HTTP 404.3 – não página FoundThe você está solicitando não pode ser servida devido à configuração da extensão. Se a página é um script, adicione um manipulador. Se o arquivo deve ser baixado, adicione um mapa MIME. InformationModule StaticFileModule de erro detalhada.  
  
 Essa mensagem de erro ocorre quando o "Windows Communication Foundation HTTP Activation" não está definida explicitamente no painel de controle. Para definir isso, vá para painel de controle, clique em programas, no canto inferior esquerdo da janela. Clique em recursos do Windows ativar ou desativar. Expanda o Microsoft .NET Framework 3.5.1 e selecione Windows Communication Foundation HTTP Activation.  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>Às vezes, recebo um MessageSecurityException na segunda solicitação se meu cliente está ocioso há algum tempo após a primeira solicitação. O que está acontecendo?  
 A segunda solicitação pode falhar, principalmente por dois motivos: (1) a sessão tiver expirado ou (2) o servidor Web que está hospedando o serviço é reciclado. No primeiro caso, a sessão é válida até que o serviço de tempo limite. Quando o serviço recebe uma solicitação do cliente dentro do período de tempo especificado na associação do serviço (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), o serviço termina a sessão de segurança. Mensagens de cliente subsequentes resultam no <xref:System.ServiceModel.Security.MessageSecurityException>. O cliente novamente deve estabelecer uma sessão segura com o serviço para enviar as mensagens futuras ou usar um token de contexto de segurança com monitoração de estado. Tokens de contexto de segurança com monitoração de estado também permitem que uma sessão segura sobreviver a um servidor Web que está sendo reciclado. Para obter mais informações sobre como usar tokens de contexto seguro com monitoração de estado em uma sessão segura, consulte [como: Criar um contexto de segurança para uma sessão segura Token](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Como alternativa, você pode desabilitar sessões seguras. Quando você usa o [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) associação, você pode definir a `establishSecurityContext` propriedade `false` para desabilitar sessões seguras. Para desabilitar sessões seguras para outras associações, você deve criar uma associação personalizada. Para obter detalhes sobre como criar uma ligação personalizada, consulte [como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Antes de aplicar qualquer uma dessas opções, você deve entender os requisitos de segurança do seu aplicativo.  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Meu serviço começa a rejeitar novos clientes depois de cerca de 10 clientes estão interagindo com ele. O que está acontecendo?  
 Por padrão, os serviços podem ter apenas 10 sessões simultâneas. Portanto, se as associações de serviço usam sessões, o serviço aceita novas conexões de cliente até atingir esse número, após o qual ele se recusará a novas conexões de cliente até que uma das extremidades sessões atuais. Você pode dar suporte a mais clientes de várias maneiras. Se seu serviço exigir sessões, não use uma associação de sessão. (Para obter mais informações, consulte [sessões usando](../../../docs/framework/wcf/using-sessions.md).) Outra opção é aumentar o limite de sessão, alterando o valor da <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> propriedade para o número apropriado para o caso.  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Pode carregar minha configuração de serviço do em outro lugar além do arquivo de configuração do aplicativo WCF?  
 Sim, no entanto, você precisa criar um personalizado <xref:System.ServiceModel.ServiceHost> classe que substitui o <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> método. Dentro desse método, você pode chamar a base para carregar a configuração pela primeira vez (se você quiser carregar informações de configuração padrão), mas também inteiramente, você pode substituir a configuração de carregamento de sistema. Observe que, se você quiser carregar a configuração de um arquivo de configuração que é diferente do arquivo de configuração de aplicativo, você deve analisar o arquivo de configuração por conta própria e carregar a configuração.  
  
 O exemplo de código a seguir mostra como substituir o <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> método e configurar diretamente um ponto de extremidade.  
  
```csharp
public class MyServiceHost : ServiceHost  
{  
    public MyServiceHost(Type serviceType, params Uri[] baseAddresses)    
      : base(serviceType, baseAddresses)  
    {
        Console.WriteLine("MyServiceHost Constructor");
    }  
  
    protected override void ApplyConfiguration()  
    {  
        string straddress = GetAddress();  
        Uri address = new Uri(straddress);  
        Binding binding = GetBinding();  
        base.AddServiceEndpoint(typeof(IData), binding, address);  
    }  
  
    string GetAddress()  
    {
        return "http://MyMachine:7777/MyEndpointAddress/";
    }  
  
    Binding GetBinding()  
    {  
        WSHttpBinding binding = new WSHttpBinding();  
        binding.Security.Mode = SecurityMode.None;  
        return binding;  
    }  
}  
```  
  
<a name="BKMK_q4"></a>   
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Meu serviço e cliente funcionem bem, mas eu não é possível fazê-los funcionar quando o cliente está em outro computador? O que está acontecendo?  
 Dependendo da exceção, pode haver vários problemas:  
  
-   Talvez você precise alterar os endereços de ponto de extremidade do cliente para o nome de host e não "localhost".  
  
-   Talvez você precise abrir a porta para o aplicativo. Para obter detalhes, consulte [instruções do Firewall](../../../docs/framework/wcf/samples/firewall-instructions.md) de amostras do SDK.  
  
-   Para outros problemas possíveis, consulte o tópico de exemplos [executando os exemplos do Windows Communication Foundation](./samples/running-the-samples.md).  
  
-   Se o cliente está usando as credenciais do Windows e a exceção é um <xref:System.ServiceModel.Security.SecurityNegotiationException>, configure o Kerberos da seguinte maneira.  
  
    1.  Adicione as credenciais de identidade para o elemento de ponto de extremidade no arquivo de App. config do cliente:  
  
        ```xml
        <endpoint   
          address="http://MyServer:8000/MyService/"   
          binding="wsHttpBinding"   
          bindingConfiguration="WSHttpBinding_IServiceExample"   
          contract="IServiceExample"   
          behaviorConfiguration="ClientCredBehavior"   
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2.  Execute o serviço auto-hospedado na conta do sistema ou NetworkService. Você pode executar este comando para criar uma janela de comando na conta do sistema:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3.  Hospede o serviço no Internet Information Services (IIS), que, por padrão, usa a conta de serviço (SPN) nome da entidade.  
  
    4.  Registre um novo SPN com o domínio usando o SetSPN. Observe que você precisará ser um administrador de domínio para fazer isso.  
  
 Para obter mais informações sobre o protocolo Kerberos, consulte [conceitos de segurança utilizados no WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) e:  
  
-   [Depuração de erros de autenticação do Windows](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [Registrando nomes da entidade de serviço Kerberos usando HTTP. sys](https://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [Kerberos explicado](https://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Quando eu gero uma FaultException\<exceção > em que o tipo é uma exceção, eu sempre recebem um tipo FaultException geral no cliente e não o tipo genérico. O que está acontecendo?  
 É recomendável que você crie seu próprio erro personalizado do tipo de dados e declarar que como o tipo de detalhe no seu contrato de falha. O motivo é que, usando tipos de exceção fornecido pelo sistema:  
  
-   Cria uma dependência de tipo que remove uma das maiores vantagens de aplicativos orientados a serviço.  
  
-   Não podem depender de serialização de uma maneira padrão de exceções. Alguns — como <xref:System.Security.SecurityException>— pode não ser serializável em todos os.  
  
-   Expõe os detalhes de implementação interna para os clientes. Para obter mais informações, consulte [especificação e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Se você estiver depurando um aplicativo, no entanto, você pode serializar informações de exceção e retorná-lo para o cliente usando o <xref:System.ServiceModel.Description.ServiceDebugBehavior> classe.  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Aparentemente, unidirecional e operações de solicitação-resposta retornam com aproximadamente a mesma velocidade quando a resposta não contém nenhum dado. O que está acontecendo?  
 Especifica que uma operação é uma maneira de significa apenas que o contrato de operação aceita uma mensagem de entrada e não retorna uma mensagem de saída. No WCF, todas as invocações do cliente retornam quando os dados de saída foram gravados para a transmissão ou uma exceção será lançada. Operações unidirecionais funcionam da mesma forma, e eles podem gerar se o serviço não pode ser localizado ou bloqueie se o serviço não está preparado para aceitar os dados da rede. Normalmente no WCF, isso resulta em chamadas unidirecionais, retornando ao cliente mais rapidamente do que a solicitação-resposta; mas qualquer condição que retarda o envio de dados de saída pela rede diminui operações unidirecionais, bem como operações de solicitação-resposta. Para obter mais informações, consulte [Services unidirecional](../../../docs/framework/wcf/feature-details/one-way-services.md) e [serviços de acesso usando um cliente WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>Estou usando um certificado X.509 com o serviço e obter um System.Security.Cryptography.CryptographicException. O que está acontecendo?  
 Isso normalmente ocorre depois de alterar a conta de usuário sob a qual o IIS processo de trabalho é executado. Por exemplo, em [!INCLUDE[wxp](../../../includes/wxp-md.md)], se você alterar a conta de usuário padrão que o Aspnet_wp.exe é executado do ASPNET para uma conta de usuário personalizada, você poderá ver esse erro. Se usando uma chave privada, o processo que o utiliza será necessário ter permissões para acessar o arquivo armazenar essa chave.  
  
 Se esse for o caso, você deverá conceder privilégios de acesso de leitura à conta do processo para o arquivo que contém a chave privada. Por exemplo, se o processo de trabalho do IIS está em execução sob a conta de Bob, em seguida, você precisará conceder acesso de leitura de Bob para o arquivo que contém a chave privada.  
  
 Para obter mais informações sobre como conceder acesso à conta de usuário correto para o arquivo que contém a chave privada para um certificado x. 509 específico, consulte [como: Criar certificados X.509 acessíveis para o WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>Eu alterei o primeiro parâmetro de uma operação de letras maiusculas em minúsculas; Agora o meu cliente gera uma exceção. O que está acontecendo?  
 O valor de nomes de parâmetro na assinatura da operação são parte do contrato e diferenciam maiusculas de minúsculas. Use o <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> atributo quando você precisar distinguir entre o nome do parâmetro de local e os metadados que descrevem a operação para aplicativos cliente.  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>Estou usando uma das Minhas ferramentas de rastreamento e obtenho um EndpointNotFoundException. O que está acontecendo?  
 Se você estiver usando uma ferramenta de rastreamento não é o mecanismo de rastreamento do WCF fornecido pelo sistema e receber um <xref:System.ServiceModel.EndpointNotFoundException> que indica que houve uma incompatibilidade de filtro de endereço, você precisará usar o <xref:System.ServiceModel.Description.ClientViaBehavior> classe para direcionar as mensagens para o utilitário de rastreamento e ter o utilitário de redirecionar essas mensagens para o endereço do serviço. O <xref:System.ServiceModel.Description.ClientViaBehavior> classe altera o `Via` cabeçalho de endereçamento para especificar o próximo endereço de rede separadamente do receptor ultimate, indicada pela `To` cabeçalho de endereçamento. Ao fazer isso, no entanto, não altere o endereço do ponto de extremidade, o que é usado para estabelecer o `To` valor.  
  
 O exemplo de código a seguir mostra um exemplo de cliente de arquivo de configuração.  
  
```xml
<endpoint   
  address="http://localhost:8000/MyServer/"  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"   
  contract="IMyContract"   
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>   
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>O que é o endereço base? Como ele se relaciona a um endereço de ponto de extremidade?  
 Um endereço básico é o endereço de raiz para um <xref:System.ServiceModel.ServiceHost> classe. Por padrão, se você adicionar um <xref:System.ServiceModel.Description.ServiceMetadataBehavior> para todos os pontos de extremidade que publica o host são recuperados do endereço básico HTTP, além de qualquer endereço relativo fornecido para o comportamento dos metadados, de classe em sua configuração de serviço, a descrição de linguagem WSDL (Web Services) Além de "? wsdl". Se você estiver familiarizado com [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] e o IIS, o endereço base é equivalente ao diretório virtual.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>Compartilhar uma porta entre um ponto de extremidade de serviço e um ponto de extremidade de mex usando a NetTcpBinding  
 Se você especifica o endereço básico para um serviço como net.tcp://MyServer: 8080/MyService e adicione os seguintes pontos de extremidade:  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 E se você modificar uma das configurações de NetTcpBinding, conforme mostrado no trecho de configuração a seguir:  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
      <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 Você verá um erro semelhante ao seguinte: Exceção sem tratamento: System.ServiceModel.AddressAlreadyInUseException: Já existe um ouvinte 0.0.0.0:9000 de ponto de extremidade IP, que você pode contornar esse erro, especificando uma URL totalmente qualificada com uma porta diferente para o ponto de extremidade MEX conforme mostrado no trecho de configuração a seguir:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>Ao chamar um aplicativo WCF Web HTTP de um aplicativo WCF SOAP o serviço retornará o seguinte erro: 405 método não permitido  
 Chamar um aplicativo WCF Web HTTP (um serviço que usa o <xref:System.ServiceModel.WebHttpBinding> e <xref:System.ServiceModel.Description.WebHttpBehavior>) de um WCF serviço pode gerar a seguinte exceção: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: O servidor remoto retornou uma resposta inesperada: (405) método não permitido.' essa exceção ocorre porque o WCF substitui a saída <xref:System.ServiceModel.OperationContext> com a entrada <xref:System.ServiceModel.OperationContext>. Para resolver esse problema, crie um <xref:System.ServiceModel.OperationContextScope> dentro da operação de serviço WCF Web HTTP. Por exemplo:  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também
- [Depuração de erros de autenticação do Windows](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)
