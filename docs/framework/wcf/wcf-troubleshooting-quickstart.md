---
title: Início rápido de solução de problemas do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: f85d37fde19767d7fd1e3002776b4816666cc7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183051"
---
# <a name="wcf-troubleshooting-quickstart"></a>Início rápido de solução de problemas do WCF
Este tópico lista uma série de problemas conhecidos que os clientes tiveram ao desenvolver clientes e serviços wcf. Se o problema que você está correndo não estiver nesta lista, recomendamos que você configure rastreamento para o seu serviço. Isso gerará um arquivo de rastreamento que você pode visualizar com o visualizador de arquivos de rastreamento e obter informações detalhadas sobre exceções que podem estar ocorrendo dentro do serviço. Para obter mais informações sobre a configuração do rastreamento, consulte: [Configurando o rastreamento](./diagnostics/tracing/configuring-tracing.md). Para obter mais informações sobre o visualizador de arquivos de rastreamento, consulte: [Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1. [Depois de instalar o Windows 7 e o IIS, quando tento navegar para um serviço WCF, recebo a seguinte mensagem de erro: ERRO HTTP 404.3 – Não Encontrado](#bkmk_0)  
  
     Erro HTTP 404.3 – Não EncontradoA página que você está solicitando não pode ser atendida devido à configuração da extensão. Se a página for um script, adicione um manipulador. Se o arquivo deve ser baixado, adicione um mapa MIME. Informações detalhadas de erroMódulo estáticoDearquivo.  
  
2. [Às vezes, recebo uma MensagemSecurityException na segunda solicitação se meu cliente estiver ocioso por um tempo após a primeira solicitação. O que está acontecendo?](#BKMK_q1)  
  
3. [Meu serviço começa a rejeitar novos clientes depois que cerca de 10 clientes estão interagindo com ele. O que está acontecendo?](#BKMK_q2)  
  
4. [Posso carregar minha configuração de serviço de outro lugar que não seja o arquivo de configuração do aplicativo WCF?](#BKMK_q3)  
  
5. [Meu serviço e meu cliente funcionam muito bem, mas não consigo fazê-los trabalhar quando o cliente está em outro computador? O que está acontecendo?](#BKMK_q4)  
  
6. [Quando eu jogo\<uma exceção de falha exceção> onde o tipo é uma exceção, eu sempre recebo um tipo geral de FalhaExceções no cliente e não no tipo genérico. O que está acontecendo?](#BKMK_q5)  
  
7. [Parece que as operações de mão única e solicitação de resposta retornam aproximadamente na mesma velocidade quando a resposta não contém dados. O que está acontecendo?](#BKMK_q6)  
  
8. [Estou usando um certificado X.509 com meu serviço e recebo um System.Security.Cryptography.CryptographicException. O que está acontecendo?](#BKMK_q77)  
  
9. [Mudei o primeiro parâmetro de uma operação de maiúsculas para minúsculas; Agora meu cliente abre uma exceção. O que está acontecendo?](#BKMK_q88)  
  
10. [Estou usando uma das minhas ferramentas de rastreamento e recebo um EndpointNotFoundException. O que está acontecendo?](#BKMK_q99)  
  
11. [Ao chamar um aplicativo WCF Web HTTP de um aplicativo WCF SOAP, o serviço retorna o seguinte erro: 405 Método Não Permitido](#BK_MK99)  
  
 [Qual é o endereço base? Como ele se relaciona com um endereço de ponto final?](#BKMK_q10)  
  
<a name="bkmk_0"></a>
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Depois de instalar o Windows 7 e o IIS, quando tento navegar para um serviço WCF, recebo a seguinte mensagem de erro: ERRO HTTP 404.3 – Não Encontrado  
 A mensagem de erro completa é:  
  
 Erro HTTP 404.3 – Não EncontradoA página que você está solicitando não pode ser atendida devido à configuração da extensão. Se a página for um script, adicione um manipulador. Se o arquivo deve ser baixado, adicione um mapa MIME. Informações detalhadas de erroMódulo estáticoDearquivo.  
  
 Esta mensagem de erro ocorre quando "Ativação HTTP da Windows Communication Foundation" não é explicitamente definida no Painel de Controle. Para definir isso vá para o Painel de Controle, clique em Programas no canto inferior esquerdo da janela. Clique em Ativar ou desativar os recursos do Windows. Expanda o Microsoft .NET Framework 3.5.1 e selecione a ativação HTTP da Windows Communication Foundation.  
  
<a name="BKMK_q1"></a>
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>Às vezes, recebo uma MensagemSecurityException na segunda solicitação se meu cliente estiver ocioso por um tempo após a primeira solicitação. O que está acontecendo?  
 A segunda solicitação pode falhar principalmente por dois motivos: (1) a sessão tem tempo de saída ou (2) o servidor Web que está hospedando o serviço é reciclado. No primeiro caso, a sessão é válida até o horário de serviço. Quando o serviço não recebe uma solicitação do cliente dentro do prazo especificado na vinculação do serviço (),<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>o serviço encerra a sessão de segurança. Mensagens de cliente <xref:System.ServiceModel.Security.MessageSecurityException>subseqüentes resultam no . O cliente deve restabelecer uma sessão segura com o serviço para enviar mensagens futuras ou usar um token de contexto de segurança de estado. Os tokens de contexto de segurança de estado também permitem que uma sessão segura sobreviva a um servidor Web sendo reciclado. Para obter mais informações sobre o uso de tokens de contexto seguro estatal em uma sessão segura, consulte [Como: Criar um Token de Contexto de Segurança para uma Sessão Segura](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Alternativamente, você pode desativar sessões seguras. Quando você usa a `establishSecurityContext` `false` [ \<vinculação wsHttpBinding>,](../configure-apps/file-schema/wcf/wshttpbinding.md) você pode definir a propriedade para desativar sessões seguras. Para desativar sessões seguras para outras vinculações, você deve criar uma vinculação personalizada. Para obter detalhes sobre a criação de uma vinculação personalizada, consulte [Como: Criar uma vinculação personalizada usando o SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Antes de aplicar qualquer uma dessas opções, você deve entender os requisitos de segurança do seu aplicativo.  
  
<a name="BKMK_q2"></a>
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Meu serviço começa a rejeitar novos clientes depois que cerca de 10 clientes estão interagindo com ele. O que está acontecendo?  
 Por padrão, os serviços podem ter apenas 10 sessões simultâneas. Portanto, se as vinculações de serviço usarem sessões, o serviço aceita novas conexões com clientes até atingir esse número, após o qual ele recusa novas conexões com clientes até que uma das sessões atuais termine. Você pode apoiar mais clientes de várias maneiras. Se o seu serviço não exigir sessões, não use uma vinculação de sessão. (Para obter mais informações, consulte [Usando sessões](using-sessions.md).) Outra opção é aumentar o limite da <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> sessão alterando o valor do imóvel para o número apropriado à sua circunstância.  
  
<a name="BKMK_q3"></a>
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Posso carregar minha configuração de serviço de outro lugar que não seja o arquivo de configuração do aplicativo WCF?  
 Sim, no entanto, você <xref:System.ServiceModel.ServiceHost> tem que <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> criar uma classe personalizada que substitui o método. Dentro desse método, você pode chamar a base para carregar a configuração primeiro (se você quiser carregar as informações de configuração padrão também), mas você também pode substituir inteiramente o sistema de carregamento de configuração. Se você quiser carregar a configuração de um arquivo de configuração diferente do arquivo de configuração do aplicativo, você deve analisar o arquivo de configuração você mesmo e carregar a configuração.  
  
 O exemplo de código a <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> seguir mostra como substituir o método e configurar diretamente um ponto final.  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Meu serviço e meu cliente funcionam muito bem, mas não consigo fazê-los trabalhar quando o cliente está em outro computador? O que está acontecendo?  
 Dependendo da exceção, pode haver vários problemas:  
  
- Você pode precisar alterar os endereços de ponto final do cliente para o nome do host e não "localhost".  
  
- Você pode precisar abrir a porta para o aplicativo. Para obter detalhes, consulte [as instruções](./samples/firewall-instructions.md) de firewall das amostras de SDK.  
  
- Para outros problemas possíveis, consulte o tópico amostras [executando o Windows Communication Foundation Samples](./samples/running-the-samples.md).  
  
- Se o seu cliente estiver usando <xref:System.ServiceModel.Security.SecurityNegotiationException>credenciais do Windows e a exceção for um , configure Kerberos da seguinte forma.  
  
    1. Adicione as credenciais de identidade ao elemento ponto final no arquivo App.config do cliente:  
  
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
  
    2. Execute o serviço auto-hospedado na conta System ou NetworkService. Você pode executar este comando para criar uma janela de comando a conta do sistema:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. Hospede o serviço em Serviços de Informação da Internet (IIS), que, por padrão, usa a conta spn (nome principal do serviço).  
  
    4. Registre um novo SPN com o domínio usando SetSPN. Você precisa ser um administrador de domínio para fazer isso.  
  
 Para obter mais informações sobre o protocolo Kerberos, consulte [Conceitos de segurança usados no WCF](./feature-details/security-concepts-used-in-wcf.md) e:  
  
- [Depurando erros de autenticação do Windows](./feature-details/debugging-windows-authentication-errors.md)  
  
- [Registrando nomes da entidade de serviço Kerberos usando Http.sys](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))  
  
- [Kerberos Explicado](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))  
  
<a name="BKMK_q5"></a>
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Quando eu jogo\<uma exceção de falha exceção> onde o tipo é uma exceção, eu sempre recebo um tipo geral de FalhaExceções no cliente e não no tipo genérico. O que está acontecendo?  
 É altamente recomendável que você crie seu próprio tipo de dados de erro personalizado e declare isso como o tipo de detalhe em seu contrato de falha. A razão é que usando tipos de exceção fornecidos pelo sistema:  
  
- Cria uma dependência de tipo que remove um dos maiores pontos fortes dos aplicativos orientados ao serviço.  
  
- Não pode depender de exceções serializando de forma padrão. Alguns <xref:System.Security.SecurityException>, como - pode não ser serializável em tudo.  
  
- Expõe detalhes de implementação interna aos clientes. Para obter mais informações, consulte [Especificar e Lidar com Falhas em Contratos e Serviços](specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Se você estiver depurando um aplicativo, no entanto, você pode serializar informações de exceção e devolvê-la ao cliente usando a <xref:System.ServiceModel.Description.ServiceDebugBehavior> classe.  
  
<a name="BKMK_q6"></a>
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Parece que as operações de mão única e solicitação de resposta retornam aproximadamente na mesma velocidade quando a resposta não contém dados. O que está acontecendo?  
 Especificar que uma operação é uma maneira significa apenas que o contrato de operação aceita uma mensagem de entrada e não retorna uma mensagem de saída. No WCF, todas as invocações do cliente retornam quando os dados de saída foram gravados no fio ou uma exceção é lançada. As operações unidirecionais funcionam da mesma maneira, e podem ser lançadas se o serviço não puder ser localizado ou bloquear se o serviço não estiver preparado para aceitar os dados da rede. Normalmente, no WCF, isso resulta em chamadas unidirecionais retornando ao cliente mais rapidamente do que solicitação-resposta; mas qualquer condição que atrase o envio dos dados de saída pela rede retarda as operações unidirecionais, bem como as operações de solicitação e resposta. Para obter mais informações, consulte [Serviços unidirecionais](./feature-details/one-way-services.md) e [serviços de acesso usando um cliente WCF](./feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>Estou usando um certificado X.509 com meu serviço e recebo um System.Security.Cryptography.CryptographicException. O que está acontecendo?  
 Isso geralmente ocorre após a alteração da conta de usuário a qual o processo do trabalhador do IIS é executado. Por exemplo, no Windows XP, se você alterar a conta de usuário padrão que o Aspnet_wp.exe é executado abaixo do ASPNET para uma conta de usuário personalizada, você poderá ver esse erro. Se usar uma chave privada, o processo que a utiliza precisará de permissões para acessar o arquivo armazenando essa chave.  
  
 Se este for o caso, você deve dar privilégios de acesso à conta do processo para o arquivo que contém a chave privada. Por exemplo, se o processo do trabalhador IIS estiver sendo executado a conta Bob, então você precisará dar a Bob acesso de leitura ao arquivo que contém a chave privada.  
  
 Para obter mais informações sobre como dar à conta de usuário correta acesso ao arquivo que contém a chave privada para um certificado X.509 específico, consulte [Como: Tornar os Certificados X.509 Acessíveis ao WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>Mudei o primeiro parâmetro de uma operação de maiúsculas para minúsculas; Agora meu cliente abre uma exceção. O que está acontecendo?  
 Os valores dos nomes dos parâmetros na assinatura da operação fazem parte do contrato e são sensíveis a maiúsculas e minúsculas. Use <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> o atributo quando precisar distinguir entre o nome do parâmetro local e os metadados que descrevem a operação para aplicativos clientes.  
  
<a name="BKMK_q99"></a>
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>Estou usando uma das minhas ferramentas de rastreamento e recebo um EndpointNotFoundException. O que está acontecendo?  
 Se você estiver usando uma ferramenta de rastreamento que não seja o mecanismo <xref:System.ServiceModel.EndpointNotFoundException> de rastreamento WCF fornecido pelo sistema e receber <xref:System.ServiceModel.Description.ClientViaBehavior> um que indique que houve uma incompatibilidade de filtro de endereço, você precisa usar a classe para direcionar as mensagens para o utilitário de rastreamento e fazer com que o utilitário redirecione essas mensagens para o endereço de serviço. A <xref:System.ServiceModel.Description.ClientViaBehavior> classe altera `Via` o cabeçalho de endereçamento para especificar o `To` próximo endereço de rede separadamente do receptor final, indicado pelo cabeçalho endereçado. Ao fazer isso, no entanto, não altere o `To` endereço de ponto final, que é usado para estabelecer o valor.  
  
 O exemplo de código a seguir mostra um arquivo de configuração do cliente de exemplo.  
  
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
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>Qual é o endereço base? Como ele se relaciona com um endereço de ponto final?  
 Um endereço base é o <xref:System.ServiceModel.ServiceHost> endereço raiz de uma classe. Por padrão, se <xref:System.ServiceModel.Description.ServiceMetadataBehavior> você adicionar uma classe à configuração do serviço, o WSDL (Web Services Description Language, linguagem de descrição de serviços da Web) para todos os pontos finais que o host publica são recuperados do endereço base HTTP, além de qualquer endereço relativo fornecido ao comportamento de metadados, além de "?wsdl". Se você está familiarizado com ASP.NET e IIS, o endereço base é equivalente ao diretório virtual.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>Compartilhando uma porta entre um ponto final de serviço e um ponto final mex usando o NetTcpBinding  
 Se você especificar o endereço base de um serviço como net.tcp://MyServer:8080/MyService e adicionar os seguintes pontos finais:  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 E se você modificar uma das configurações do NetTcpBinding como mostrado no seguinte trecho de configuração:  
  
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
  
 Você verá um erro como o seguinte: Exceção não manipulada: System.ServiceModel.AddressJáInUseException: Já existe um ouvinte no ponto final IP 0.0.0.9000 Você pode contornar esse erro especificando uma URL totalmente qualificada com uma porta diferente para o ponto final do MEX, conforme mostrado no seguinte trecho de configuração:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>Ao chamar um aplicativo WCF Web HTTP de um aplicativo WCF SOAP, o serviço retorna o seguinte erro: 405 Método Não Permitido  
 Chamar um aplicativo WCF Web HTTP <xref:System.ServiceModel.WebHttpBinding> (um serviço que usa o <xref:System.ServiceModel.Description.WebHttpBehavior>e ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` ) de um serviço WCF <xref:System.ServiceModel.OperationContext> pode gerar <xref:System.ServiceModel.OperationContext>a seguinte exceção: Essa exceção ocorre porque o WCF substitui a saída com a entrada . Para resolver esse problema, crie uma <xref:System.ServiceModel.OperationContextScope> operação de serviço Sc. Http do WCF Web. Por exemplo:   
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a>Confira também

- [Depurando erros de autenticação do Windows](./feature-details/debugging-windows-authentication-errors.md)
