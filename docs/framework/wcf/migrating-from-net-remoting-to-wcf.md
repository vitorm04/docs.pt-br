---
title: Migrando de .NET Remoting para o WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 8dcc019017195fd55231fbea3493d4c53d500cb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183958"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>Migrando de .NET Remoting para o WCF
Este artigo descreve como migrar um aplicativo que usa .NET Remoting para usar o Windows Communication Foundation (WCF). Ele compara conceitos semelhantes entre esses produtos e, em seguida, descreve como realizar vários cenários de Remoting comuns no WCF.  
  
 .NET Remoting é um produto legado suportado apenas para compatibilidade retrógrada. Ele não é seguro em ambientes de confiança mista porque não pode manter os níveis de confiança separados entre cliente e servidor. Por exemplo, você nunca deve expor um ponto final .NET Remoting à Internet ou a clientes não confiáveis. Recomendamos que os aplicativos de Remoting existentes sejam migrados para tecnologias mais novas e seguras. Se o design do aplicativo usa apenas HTTP e é RESTful, recomendamos ASP.NET API da Web. Para obter mais informações, consulte ASP.NET API web. Se o aplicativo for baseado em SOAP ou exigir protocolos não-Http, como o TCP, recomendamos o WCF.  

## <a name="comparing-net-remoting-to-wcf"></a>Comparando .NET Remoting com WCF  
 Esta seção compara os blocos básicos de construção do .NET Remoting com seus equivalentes WCF. Usaremos esses blocos de construção mais tarde para criar alguns cenários comuns de servidor de clientes no WCF. O gráfico a seguir resume as principais semelhanças e diferenças entre .NET Remoting e WCF.  
  
||Comunicação remota .NET|WCF|  
|-|-------------------|---------|  
|Tipo de servidor|Marechal de SubclasseByRefObject|Marcar com atributo [ServiceContract]|  
|Operações de serviço|Métodos públicos sobre o tipo de servidor|Marcar com atributo [OperaçãoContrato]|  
|Serialização|ISerializable ou [Serializable]|DataContractSerializer ou XmlSerializer|  
|Objetos passaram|Por valor ou por referência|Apenas por valor|  
|Erros/exceções|Qualquer exceção serializável|>\<de detalhes do contrato de falha|  
|Objetos proxy do cliente|Proxies transparentes fortemente digitados são criados automaticamente a partir de MarshalByRefObjects|Proxies fortemente digitados são gerados\<sob demanda usando o ChannelFactory TChannel>|  
|Plataforma necessária|Tanto o cliente quanto o servidor devem usar o Sistema Operacional Microsoft e o .NET|Multiplataforma|  
|Formato da mensagem|Privado|Padrões da indústria (SOAP, WS-*, etc.)|  
  
### <a name="server-implementation-comparison"></a>Comparação de implementação do servidor  
  
#### <a name="creating-a-server-in-net-remoting"></a>Criando um servidor em .NET Remoting  
 .NET Remoting tipos de servidor devem derivar do MarshalByRefObject e definir métodos que o cliente pode chamar, como o seguinte:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Os métodos públicos desse tipo de servidor tornam-se o contrato público disponível aos clientes.  Não há separação entre a interface pública do servidor e sua implementação – um tipo lida com ambos.  
  
 Uma vez definido o tipo de servidor, ele pode ser disponibilizado aos clientes, como no exemplo a seguir:  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),
    "RemotingServer",
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 Existem muitas maneiras de disponibilizar o tipo Remoting como servidor, inclusive usando arquivos de configuração. Este é apenas um exemplo.  
  
#### <a name="creating-a-server-in-wcf"></a>Criando um servidor no WCF  
 A etapa equivalente no WCF envolve a criação de dois tipos : o "contrato de serviço" público e a implementação concreta. O primeiro é declarado como uma interface marcada com [ServiceContract]. Os métodos disponíveis para os clientes são marcados com [OperationContract]:  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 A implementação do servidor é definida em uma classe de concreto separada, como no exemplo a seguir:  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Uma vez definidos esses tipos, o servidor WCF pode ser disponibilizado aos clientes, como no exemplo a seguir:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine($"The WCF server is ready at {baseAddress}.");
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
> TCP é usado em ambos os exemplos para mantê-los o mais semelhante possível. Consulte o cenário de passo-a-passo mais tarde neste tópico, por exemplo, usando HTTP.  
  
 Existem muitas maneiras de configurar e hospedar serviços WCF. Este é apenas um exemplo, conhecido como "auto-hospedado". Para obter mais informações, consulte estes tópicos:  
  
- [Como definir um contrato de serviço](how-to-define-a-wcf-service-contract.md)  
  
- [Configurando serviços usando arquivos de configuração](configuring-services-using-configuration-files.md)  
  
- [Hospedando serviços](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>Comparação de implementação do cliente  
  
#### <a name="creating-a-client-in-net-remoting"></a>Criando um Cliente em .NET Remoting  
 Uma vez que um objeto de servidor .NET Remoting tenha sido disponibilizado, ele pode ser consumido pelos clientes, como no exemplo a seguir:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 A instância RemotingServer retornada do Activator.GetObject() é conhecida como "proxy transparente". Ele implementa a API pública para o tipo RemotingServer no cliente, mas todos os métodos chamam o objeto do servidor em execução em um processo ou máquina diferente.  
  
#### <a name="creating-a-client-in-wcf"></a>Criando um cliente no WCF  
 A etapa equivalente no WCF envolve o uso de uma fábrica de canais para criar o proxy explicitamente. Assim como Remoting, o objeto proxy pode ser usado para invocar operações no servidor, como no exemplo a seguir:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 Este exemplo mostra a programação no nível do canal porque é mais semelhante ao exemplo de Remoting. Também está disponível a abordagem **Add Service Reference** no Visual Studio que gera código para simplificar a programação do cliente. Para obter mais informações, consulte estes tópicos:  
  
- [Programação de nível de canal do cliente](./extending/client-channel-level-programming.md)  
  
- [Como adicionar, atualizar ou remover uma referência de serviço](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Uso de serialização  
 Tanto o .NET Remoting quanto o WCF usam serialização para enviar objetos entre cliente e servidor, mas eles diferem destas maneiras importantes:  
  
1. Eles usam serializadores e convenções diferentes para indicar o que serializar.  
  
2. .NET Remoting suporta serialização "por referência" que permite que o método ou o acesso à propriedade em um nível execute o código no outro nível, que está além dos limites de segurança. Esse recurso expõe vulnerabilidades de segurança e é uma das principais razões pelas quais os pontos finais de Remoting nunca devem ser expostos a clientes não confiáveis.  
  
3. A serialização usada por Remoting é opt-out (exclua explicitamente o que não serializar) e a serialização do WCF é opt-in (marca explicitamente quais membros serializar).  
  
#### <a name="serialization-in-net-remoting"></a>Serialização em .NET Remoting  
 .NET Remoting suporta duas maneiras de serializar e desserializar objetos entre o cliente e o servidor:  
  
- *Por valor* – os valores do objeto são serializados através dos limites de nível, e uma nova instância desse objeto é criada no outro nível. Quaisquer chamadas para métodos ou propriedades dessa nova instância são executadas apenas localmente e não afetam o objeto ou nível original.  
  
- *Por referência* – uma "referência de objeto" especial é serializada através dos limites de nível. Quando um nível interage com métodos ou propriedades desse objeto, ele se comunica de volta ao objeto original no nível original. Objetos de referência podem fluir em qualquer direção – servidor para cliente ou cliente para servidor.  
  
 Os tipos de valor por valor em Remoting são marcados com o atributo [Serializable] ou implementam ISerializable, como no exemplo a seguir:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Os tipos de referência derivam da classe MarshalByRefObject, como no exemplo a seguir:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 É extremamente importante entender as implicações dos objetos de referência de Remoting. Se o nível (cliente ou servidor) enviar um objeto de referência para o outro nível, todas as chamadas do método são executadas de volta no nível que possui o objeto. Por exemplo, os métodos de chamada de cliente em um objeto de referência retornado pelo servidor executarão o código no servidor. Da mesma forma, um método de chamada de servidor em um objeto de referência fornecido pelo cliente executará o código de volta no cliente. Por essa razão, o uso do .NET Remoting é recomendado apenas em ambientes totalmente confiáveis. Expor um ponto final público .NET Remoting a clientes não confiáveis tornará um servidor Remoting vulnerável a ataques.  
  
#### <a name="serialization-in-wcf"></a>Serialização no WCF  
 O WCF suporta apenas a serialização por valor. A maneira mais comum de definir um tipo de troca entre cliente e servidor é como no exemplo a seguir:  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 O atributo [DataContract] identifica esse tipo como aquele que pode ser serializado e desserializado entre cliente e servidor. O atributo [DataMember] identifica as propriedades ou campos individuais para serializar.  
  
 Quando o WCF envia um objeto entre os níveis, ele serializa apenas os valores e cria uma nova instância do objeto no outro nível. Quaisquer interações com os valores do objeto ocorrem apenas localmente – elas não se comunicam com o outro nível da maneira que os objetos de referência .NET Remoting fazem. Para obter mais informações, consulte [Serialização e Desserialização](./feature-details/serialization-and-deserialization.md).  
  
### <a name="exception-handling-capabilities"></a>Recursos de manipulação de exceções  
  
#### <a name="exceptions-in-net-remoting"></a>Exceções em .NET Remoting  
 As exceções lançadas por um servidor Remoting são serializadas, enviadas ao cliente e jogadas localmente no cliente como qualquer outra exceção. Exceções personalizadas podem ser criadas subclassificando o tipo Exceção e marcando-a com [Serializable].   A maioria das exceções de quadro já estão marcadas dessa forma, permitindo que a maioria seja lançada pelo servidor, serializada e relançada no cliente. Embora este design seja conveniente durante o desenvolvimento, as informações do lado do servidor podem ser inadvertidamente divulgadas ao cliente. Esta é uma das muitas razões pelas quais remoting deve ser usado apenas em ambientes totalmente confiáveis.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>Exceções e Falhas no WCF  
 O WCF não permite que tipos de exceção arbitrária sejam devolvidos do servidor para o cliente porque isso pode levar à divulgação inadvertida de informações. Se uma operação de serviço lança uma exceção inesperada, isso faz com que uma falha exceção de propósito geral seja lançada sobre o cliente. Esta exceção não carrega nenhuma informação por que ou onde o problema ocorreu, e para algumas aplicações isso é suficiente. Aplicativos que precisam comunicar informações de erro mais ricas ao cliente fazem isso definindo um contrato de falha.  
  
 Para fazer isso, primeiro crie um tipo [DataContract] para transportar as informações de falha.  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 Especifique o contrato de falha a ser usado para cada operação de serviço.  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 O servidor relata condições de erro lançando uma FalhaExceto.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {
        CustomerId = customerId,
        ErrorMessage = "Illegal customer Id"
    });  
```  
  
 E sempre que o cliente faz uma solicitação ao servidor, ele pode pegar falhas como exceções normais.  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine($"Fault received: {fault.Detail.ErrorMessage}");
}  
```  
  
 Para obter mais informações <xref:System.ServiceModel.FaultException>sobre contratos de falha, consulte .  
  
### <a name="security-considerations"></a>Considerações de segurança  
  
#### <a name="security-in-net-remoting"></a>Segurança em .NET Remoting  
 Alguns canais .NET Remoting suportam recursos de segurança, como autenticação e criptografia na camada de canal (IPC e TCP). O canal HTTP conta com o IIS (Internet Information Services, serviços de informação à Internet) tanto para autenticação quanto para criptografia. Apesar desse suporte, você deve considerar .NET Remoting um protocolo de comunicação inseguro e usá-lo apenas em ambientes totalmente confiáveis. Nunca exponha um ponto final de Remoting público à Internet ou clientes não confiáveis.  
  
#### <a name="security-in-wcf"></a>Segurança no WCF  
 O WCF foi projetado com a segurança em mente, em parte para abordar os tipos de vulnerabilidades encontradas no .NET Remoting. O WCF oferece segurança tanto no nível de transporte quanto de mensagem, e oferece muitas opções de autenticação, autorização, criptografia e assim por diante. Para obter mais informações, consulte estes tópicos:  
  
- [Segurança](./feature-details/security.md)  
  
- [Orientação de segurança do WCF](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>Migrando para wcf  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Por que migrar de Remoting para WCF?  
  
- **.NET Remoting é um produto legado.** Como descrito em [.NET Remoting,](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29)é considerado um produto legado e não é recomendado para novos desenvolvimentos. O WCF ou ASP.NET API da Web são recomendados para aplicativos novos e existentes.  
  
- **O WCF usa padrões multiplataforma.** O WCF foi projetado com a interoperabilidade multiplataforma em mente e suporta muitos padrões do setor (SOAP, WS-Security, WS-Trust, etc.). Um serviço WCF pode interoperar com clientes em execução em sistemas operacionais diferentes do Windows. Remoting foi projetado principalmente para ambientes onde os aplicativos de servidor e cliente são executados usando o .NET Framework em um sistema operacional Windows.
  
- **A WCF tem segurança embutida.** O WCF foi projetado com a segurança em mente e oferece muitas opções de autenticação, segurança de nível de transporte, segurança de nível de mensagem, etc. Remoting foi projetado para facilitar a interoperação de aplicativos, mas não foi projetado para ser seguro em ambientes não confiáveis. O WCF foi projetado para funcionar em ambientes confiáveis e não confiáveis.  
  
### <a name="migration-recommendations"></a>Recomendações de migração  
 A seguir estão as etapas recomendadas para migrar de .NET Remoting para WCF:  
  
- **Crie o contrato de serviço.** Defina os tipos de interface de serviço e marque-os com o atributo [ServiceContract]. Marque todos os métodos que os clientes poderão ligar com [OperaçãoContrato].  
  
- **Crie o contrato de dados.** Defina os tipos de dados que serão trocados entre servidor e cliente e marque-os com o atributo [DataContract]. Marque todos os campos e propriedades que o cliente poderá usar com [DataMember].  
  
- **Crie o contrato de falha (opcional).** Crie os tipos que serão trocados entre servidor e cliente quando os erros forem encontrados. Marque esses tipos com [DataContract] e [DataMember] para torná-los serializáveis. Para todas as operações de serviço que você marcou com [OperaçãoContrato], também marque-as com [Contrato de falha] para indicar quais erros eles podem retornar.  
  
- **Configure e hospede o serviço.** Uma vez que o contrato de serviço tenha sido criado, o próximo passo é configurar uma vinculação para expor o serviço em um ponto final. Para obter mais informações, consulte [Endpoints: Endereços, Vinculações e Contratos](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 Uma vez que um aplicativo Remoting tenha sido migrado para o WCF, ainda é importante remover dependências do .NET Remoting. Isso garante que quaisquer vulnerabilidades remoting sejam removidas do aplicativo. Estas etapas incluem as seguintes:  
  
- **Descontinuar o uso do MarshalByRefObject.** O tipo MarshalByRefObject existe apenas para Remoting e não é usado pelo WCF. Todos os tipos de aplicativos que subclasse MarshalByRefObject devem ser removidos ou alterados.  
  
- **Descontinuar o uso de [Serializable] e ISerializable.** O atributo [Serializable] e a interface ISerializable foram originalmente projetados para serializar tipos em ambientes confiáveis, e eles são usados por Remoting. A serialização do WCF depende de tipos que estão sendo marcados com [DataContract] e [DataMember]. Os tipos de dados usados por um aplicativo devem ser modificados para usar [DataContract] e não para usar ISerializable ou [Serializable].  
  
### <a name="migration-scenarios"></a>Cenários de migração  
 Agora vamos ver como realizar os seguintes cenários comuns de Remoting no WCF:  
  
1. O servidor retorna um objeto por valor para o cliente  
  
2. O servidor retorna um objeto por referência ao cliente  
  
3. O cliente envia um objeto por valor para o servidor  
  
> [!NOTE]
> O envio de uma referência de objeto do cliente para o servidor não é permitido no WCF.  
  
 Ao ler esses cenários, assuma que nossas interfaces de linha de base para .NET Remoting se parecem com o exemplo a seguir. A implementação do .NET Remoting não é importante aqui porque queremos ilustrar apenas como usar o WCF para implementar funcionalidades equivalentes.  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a>Cenário 1: O serviço retorna um objeto por valor  
 Esse cenário demonstra um servidor devolvendo um objeto ao cliente por valor. O WCF sempre retorna objetos do servidor por valor, então as etapas a seguir simplesmente descrevem como construir um serviço WCF normal.  
  
1. Comece definindo uma interface pública para o serviço WCF e marque-a com o atributo [ServiceContract]. Usamos [OperationContract] para identificar os métodos do lado do servidor que nosso cliente chamará.  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2. O próximo passo é criar o contrato de dados para este serviço. Fazemos isso criando classes (não interfaces) marcadas com o atributo [DataContract]. As propriedades individuais ou campos que queremos visíveis para cliente e servidor são marcados com [DataMember]. Se quisermos que tipos derivados sejam permitidos, devemos usar o atributo [KnownType] para identificá-los. Os únicos tipos que o WCF permitirá ser serializado ou desserializado para este serviço são aqueles na interface de serviço e esses "tipos conhecidos". A tentativa de trocar qualquer outro tipo que não esteja nesta lista será rejeitada.  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3. Em seguida, fornecemos a implementação para a interface de serviço.  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4. Para executar o serviço WCF, precisamos declarar um ponto final que exponha essa interface de serviço em uma URL específica usando uma vinculação WCF específica. Isso é normalmente feito adicionando as seguintes seções ao arquivo web.config do projeto servidor.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5. O serviço WCF pode então ser iniciado com o seguinte código:  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Quando este ServiceHost é iniciado, ele usa o arquivo Web.config para estabelecer o contrato, vinculação e ponto final adequados. Para obter mais informações sobre arquivos de configuração, consulte [Configuração de serviços usando arquivos de configuração](./configuring-services-using-configuration-files.md). Este estilo de iniciar o servidor é conhecido como auto-hospedagem. Para saber mais sobre outras opções para hospedar serviços WCF, consulte [Serviços de hospedagem](./hosting-services.md).  
  
6. O aplicativo.config do projeto cliente deve declarar informações vinculativas correspondentes para o ponto final do serviço. A maneira mais fácil de fazer isso no Visual Studio é usar **o Add Service Reference**, que atualizará automaticamente o arquivo app.config. Alternativamente, essas mesmas alterações podem ser adicionadas manualmente.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Para obter mais informações sobre como usar **o Add Service Reference,** consulte [Como: Adicionar, Atualizar ou Remover uma Referência de Serviço](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).  
  
7. Agora podemos chamar o serviço WCF do cliente. Fazemos isso criando uma fábrica de canais para esse serviço, pedindo-lhe um canal, e ligando diretamente para o método que queremos naquele canal. Podemos fazer isso porque o canal implementa a interface do serviço e lida com a lógica de solicitação/resposta subjacente para nós. O valor de devolução dessa chamada de método é a cópia desserializada da resposta do servidor.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 Os objetos devolvidos pelo WCF do servidor para o cliente são sempre por valor. Os objetos são cópias desserializadas dos dados enviados pelo servidor. O cliente pode chamar métodos nessas cópias locais sem qualquer perigo de invocar o código do servidor através de retornos de chamada.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Cenário 2: Servidor retorna um objeto por referência  
 Esse cenário demonstra o servidor fornecendo um objeto ao cliente por referência. Em .NET Remoting, isso é tratado automaticamente para qualquer tipo derivado de MarshalByRefObject, que é serializado por referência. Um exemplo desse cenário é permitir que vários clientes tenham objetos independentes do lado do servidor. Como mencionado anteriormente, objetos retornados por um serviço WCF são sempre por valor, portanto não há equivalente direto de um objeto de <xref:System.ServiceModel.EndpointAddress10> referência, mas é possível alcançar algo semelhante à semântica de referência usando um objeto. Este é um objeto por valor serializável que pode ser usado pelo cliente para obter um objeto de referência por sessão no servidor. Isso permite o cenário de ter vários clientes com objetos independentes do lado do servidor.  
  
1. Primeiro, precisamos definir um contrato de serviço wcf que corresponda ao objeto em si.  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    > Observe que o objeto de sessão está marcado com [ServiceContract], tornando-o uma interface de serviço WCF normal. A configuração da propriedade SessionMode indica que será um serviço de sessão. No WCF, uma sessão é uma maneira de correlacionar várias mensagens enviadas entre dois pontos de extremidade. Isso significa que, depois que um cliente obtiver uma conexão para esse serviço, uma sessão será estabelecida entre o cliente e o servidor. O cliente usará uma única instância exclusiva do objeto do lado do servidor para todas as interações dele nessa única sessão.  
  
2. Em seguida, precisamos fornecer a implementação desta interface de serviço. Ao denotá-lo com [ServiceBehavior] e definir o InstanceContextMode, dizemos ao WCF que queremos usar uma instância única desse tipo para cada sessão.  
  
   ```csharp
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
       public class MySessionBoundObject : ISessionBoundObject  
       {  
           private string _value;  
  
           public string GetCurrentValue()  
           {  
               return _value;  
           }  
  
           public void SetCurrentValue(string val)  
           {  
               _value = val;  
           }  
  
       }  
   ```  
  
3. Agora precisamos de uma maneira de obter uma instância deste objeto de sessão. Fazemos isso criando outra interface de serviço WCF que retorna um objeto EndpointAddress10. Esta é uma forma serializável de um ponto final que o cliente pode usar para criar o objeto de sessão.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     E implementamos este serviço WCF:  
  
   ```csharp
   public class SessionBoundFactory : ISessionBoundFactory  
       {  
           public static ChannelFactory<ISessionBoundObject> _factory =
               new ChannelFactory<ISessionBoundObject>("sessionbound");  

           public SessionBoundFactory()  
           {  
           }  
  
           public EndpointAddress10 GetInstanceAddress()  
           {  
               IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
               return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
           }  
       }  
   ```  
  
     Essa implementação mantém uma fábrica de canais única para criar objetos de sessão. Quando getInstanceAddress() é chamado, ele cria um canal e cria um objeto EndpointAddress10 que efetivamente aponta para o endereço remoto associado a este canal. EndpointAddress10 é simplesmente um tipo de dados que pode ser devolvido ao cliente por valor.  
  
4. Precisamos modificar o arquivo de configuração do servidor fazendo as duas seguintes coisas, conforme mostrado no exemplo abaixo:  
  
    1. Declare \<uma seção de> cliente que descreva o ponto final para o objeto de sessão. Isso é necessário porque o servidor também atua como cliente nessa situação.  
  
    2. Declare pontos finais para o objeto de fábrica e sessão. Isso é necessário para permitir que o cliente se comunique com os pontos finais do serviço para adquirir o EndpointAddress10 e criar o canal de sessão.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
         <client>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
        </client>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
          <service name="Server.MySessionBoundObject">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundObject" />  
          </service>  
          <service name="Server.SessionBoundFactory">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundFactory" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     E então podemos iniciar esses serviços:  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. Configuramos o cliente declarando esses mesmos pontos finais no arquivo app.config do seu projeto.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
          <endpoint name="factory"  
                    address="net.tcp://localhost:8081/SessionBoundFactory"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundFactory"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
6. Para criar e usar este objeto de sessão, o cliente deve fazer as seguintes etapas:  
  
    1. Crie um canal para o serviço ISessionBoundFactory.  
  
    2. Use esse canal para invocar esse serviço para obter um EndpointAddress10.  
  
    3. Use o EndpointAddress10 para criar um canal para obter um objeto de sessão.  
  
    4. Interaja com o objeto de sessão para demonstrar que ele permanece a mesma instância em várias chamadas.  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 O WCF sempre retorna objetos por valor, mas é possível suportar o equivalente à semântica por referência através do uso do EndpointAddress10. Isso permite que o cliente solicite uma instância de serviço WCF em sessão, após a qual ele pode interagir com ele como qualquer outro serviço WCF.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Cenário 3: O cliente envia ao servidor uma instância de valor por valor  
 Esse cenário demonstra o cliente enviando uma instância de objeto não primitivo para o servidor por valor. Como o WCF envia apenas objetos por valor, esse cenário demonstra o uso normal do WCF.  
  
1. Use o mesmo Serviço WCF do Cenário 1.  
  
2. Use o cliente para criar um novo objeto por valor (Cliente), crie um canal para se comunicar com o serviço ICustomerService e envie o objeto para ele.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {
   FirstName = "Bob",
   LastName = "Jones",
   CustomerId = 43,
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine($"  Server returned {success}.");
   ```  
  
     O objeto do cliente será serializado e enviado para o servidor, onde é desserializado em uma nova cópia desse objeto.  
  
    > [!NOTE]
    > Este código também ilustra o envio de um tipo derivado (PremiumCustomer). A interface de serviço espera um objeto cliente, mas o atributo [KnownType] na classe Cliente indicado PremiumCustomer também foi permitido. O WCF falhará em qualquer tentativa de serializar ou desserializar qualquer outro tipo através desta interface de serviço.  
  
 As trocas normais de dados do WCF são por valor. Isso garante que a invocação de métodos em um desses objetos de dados seja executada apenas localmente – ele não invocará código no outro nível. Embora seja possível conseguir algo como objetos de referência retornados *do* servidor, não é possível que um cliente passe um objeto de referência *para* o servidor. Um cenário que requer uma conversa de ida e volta entre o cliente e o servidor pode ser obtido no WCF usando um serviço duplex. Para obter mais informações, consulte [Serviços Duplex](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Resumo  
 .NET Remoting é uma estrutura de comunicação destinada a ser usada apenas em ambientes totalmente confiáveis. É um produto legado e suportado apenas para compatibilidade retrógrada. Ele não deve ser usado para construir novas aplicações. Por outro lado, o WCF foi projetado com a segurança em mente e é recomendado para aplicativos novos e existentes. A Microsoft recomenda que os aplicativos remoting existentes sejam migrados para usar o WCF ou ASP.NET API da Web.
