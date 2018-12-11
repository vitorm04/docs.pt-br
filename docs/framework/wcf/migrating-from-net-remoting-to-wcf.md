---
title: Migrando de .NET Remoting para o WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: cca303cf9b906fd395e594111fae808ae4ab6435
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245672"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>Migrando de .NET Remoting para o WCF
Este artigo descreve como migrar um aplicativo que usa o .NET Remoting para usar o Windows Communication Foundation (WCF). Ele compara conceitos semelhantes entre esses produtos e, em seguida, descreve como realizar vários cenários comuns de comunicação remota no WCF.  
  
 Comunicação remota do .NET é um produto herdado que tem suporte apenas para compatibilidade com versões anteriores. Não é seguro em ambientes de confiança misto porque ele não é possível manter os níveis de confiança separados entre cliente e servidor. Por exemplo, você nunca deve expor um ponto de extremidade de comunicação remota do .NET para a Internet ou para clientes não confiáveis. Recomendamos que a comunicação remota existente aplicativos ser migrados para tecnologias mais novas e mais seguras. Se o design do aplicativo usa somente HTTP e RESTful, recomendamos a API Web do ASP.NET. Para obter mais informações, consulte a API Web do ASP.NET. Se o aplicativo é baseado em SOAP ou requer protocolos não Http como TCP, é recomendável WCF.  

## <a name="comparing-net-remoting-to-wcf"></a>Comparando a comunicação remota do .NET para WCF  
 Esta seção compara os blocos de construção básicos de comunicação remota do .NET com seus equivalentes do WCF. Posteriormente, usaremos esses blocos de construção para criar alguns cenários comuns de cliente-servidor no WCF. O gráfico a seguir resume as principais semelhanças e diferenças entre o WCF e o .NET Remoting.  
  
||Comunicação remota .NET|WCF|  
|-|-------------------|---------|  
|Tipo de servidor|Subclasse MarshalByRefObject|Marcar com o atributo [ServiceContract]|  
|Operações de serviço|Métodos públicos no tipo de servidor|Marcar com o atributo [OperationContract]|  
|Serialização|ISerializable ou [Serializable]|O DataContractSerializer ou o XmlSerializer|  
|Objetos passados|Por valor ou por referência|Por valor apenas|  
|Erros/exceções|Qualquer exceção serializável|FaultContract\<TDetail>|  
|Objetos de proxy de cliente|Com rigidez de tipos de proxies transparentes são criados automaticamente a partir MarshalByRefObjects|Os proxies com rigidez de tipos são gerados sob demanda usando o ChannelFactory\<TChannel >|  
|Plataforma necessária|Cliente e o servidor devem usar OS Microsoft e .NET|Plataforma cruzada|  
|Formato de mensagem|Particular|Padrões do setor (SOAP, WS-*, etc.)|  
  
### <a name="server-implementation-comparison"></a>Comparação de implementação de servidor  
  
#### <a name="creating-a-server-in-net-remoting"></a>Criando um servidor no .NET Remoting  
 Tipos de servidor de comunicação remota do .NET devem ser derivada de MarshalByRefObject e definir métodos que o cliente pode chamar, semelhante ao seguinte:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Os métodos públicos deste tipo de servidor se tornar disponível para clientes contrato público.  Não há nenhuma separação entre a interface do servidor público e sua implementação – um tipo lida com ambos.  
  
 Depois que o tipo de servidor tiver sido definido, ele pode ser disponibilizado aos clientes, como no exemplo a seguir:  
  
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
  
 Há várias maneiras de disponibilizar o tipo de comunicação remota como um servidor, incluindo o uso de arquivos de configuração. Isso é apenas um exemplo.  
  
#### <a name="creating-a-server-in-wcf"></a>Criando um servidor no WCF  
 A etapa equivalente no WCF envolve a criação de dois tipos – o público "contrato de serviço" e a implementação concreta. O primeiro é declarado como uma interface marcada com [ServiceContract]. Métodos disponíveis para os clientes são marcados com [OperationContract]:  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Implementação do servidor é definida em uma classe concreta separada, como no exemplo a seguir:  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Depois que esses tipos tiverem sido definidos, o servidor do WCF pode se tornar disponível a clientes, como no exemplo a seguir:  
  
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
>  TCP é usado em ambos os exemplos para mantê-los mais semelhante possível. Consulte a cenário instruções passo a passo neste tópico para obter exemplos usando HTTP.  
  
 Há várias maneiras para configurar e hospedar serviços WCF. Isso é apenas um exemplo, conhecido como "auto-hospedado". Para mais informações, consulte os seguintes tópicos:  
  
-   [Como: Definir um contrato de serviço](how-to-define-a-wcf-service-contract.md)  
  
-   [Configurando serviços usando arquivos de configuração](configuring-services-using-configuration-files.md)  
  
-   [Hospedando serviços](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>Comparação de implementação do cliente  
  
#### <a name="creating-a-client-in-net-remoting"></a>Criação de um cliente na comunicação remota do .NET  
 Depois que um objeto de servidor de comunicação remota do .NET foi disponibilizado, ele pode ser consumido por clientes, como no exemplo a seguir:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 A instância de RemotingServer retornada de Activator.GetObject() é conhecida como um "proxy transparente". Ele implementa a API pública para o tipo de RemotingServer no cliente, mas todos os métodos chamam o objeto de servidor em execução em um computador ou processo diferente.  
  
#### <a name="creating-a-client-in-wcf"></a>Criação de um cliente do WCF  
 A etapa equivalente no WCF envolve o uso de uma fábrica de canais para criar o proxy explicitamente. Como a comunicação remota, o objeto de proxy pode ser usado para invocar operações no servidor, como no exemplo a seguir:  
  
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
  
 Este exemplo mostra como ele é mais semelhante ao exemplo a comunicação remota de programação no nível do canal. Também está disponível de **adicionar referência de serviço** abordagem no Visual Studio que gera código para simplificar a programação do cliente. Para mais informações, consulte os seguintes tópicos:  
  
-   [Programação de nível de canal do cliente](./extending/client-channel-level-programming.md)  
  
-   [Como: Adicionar, atualizar ou remover uma referência de serviço](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Uso de serialização  
 Comunicação remota do .NET e o WCF usam a serialização para enviar objetos entre cliente e servidor, mas elas diferem das seguintes maneiras importantes:  
  
1.  Eles usam diferentes serializadores e convenções para indicar qual serializar.  
  
2.  Comunicação remota do .NET dá suporte à serialização "por referência" que permite o acesso de método ou propriedade em uma camada, para executar o código na camada que está entre limites de segurança. Essa funcionalidade expõe vulnerabilidades de segurança e é um dos principais motivos por que os pontos de extremidade de comunicação remota nunca devem ser expostos a clientes não confiáveis.  
  
3.  Serialização usada pela comunicação remota é uma recusa (excluir explicitamente para serializar o que não) e serialização do WCF é uma opção (marcar explicitamente quais membros para serializar).  
  
#### <a name="serialization-in-net-remoting"></a>Serialização no .NET Remoting  
 Comunicação remota do .NET dá suporte a duas maneiras para serializar e desserializar objetos entre o cliente e servidor:  
  
-   *Por valor* – os valores do objeto são serializados entre limites de camada e uma nova instância desse objeto é criada na outra camada. Todas as chamadas para métodos ou propriedades dessa instância nova executar apenas localmente e não afetam a camada ou o objeto original.  
  
-   *Por referência* – um "referência de objeto" especial é serializado entre limites de camada. Quando uma camada interage com métodos ou propriedades desse objeto, ele se comunica para o objeto original na camada original. Objetos por referência podem fluir em ambas as direções – servidor para o cliente ou o cliente para o servidor.  
  
 Tipos de valor by na comunicação remota são marcados com o atributo [Serializable] ou implementam ISerializable, como no exemplo a seguir:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Tipos por referência são derivadas da classe MarshalByRefObject, como no exemplo a seguir:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 É extremamente importante entender as implicações de objetos por referência do comunicação remota. Se qualquer camada (cliente ou servidor) envia um objeto por referência para a outra camada, todas as chamadas de método executar novamente na camada de proprietário do objeto. Por exemplo, um cliente chamar métodos em um objeto por referência retornado pelo servidor executará o código no servidor. Da mesma forma, um servidor de chamar métodos em um objeto por referência fornecido pelo cliente executará o código novamente no cliente. Por esse motivo, o uso de comunicação remota do .NET é recomendado somente dentro de ambientes totalmente confiáveis. Expor um ponto de extremidade público do .NET Remoting para clientes não confiáveis, um servidor de comunicação remota será tornar vulnerável a ataques.  
  
#### <a name="serialization-in-wcf"></a>Serialização no WCF  
 WCF oferece suporte somente a serialização de por valor. É a maneira mais comum para definir um tipo de troca entre cliente e servidor, como no exemplo a seguir:  
  
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
  
 O atributo [DataContract] identifica esse tipo como um que pode ser serializado e desserializado entre cliente e servidor. O atributo [DataMember] identifica as propriedades individuais ou campos para serializar.  
  
 Quando o WCF envia um objeto em camadas, ele serializa somente os valores e cria uma nova instância do objeto na camada de. Qualquer interação com os valores do objeto ocorre apenas localmente – eles não se comunicam com a outra camada de que fazer os forma como os objetos .NET Remoting por referência. Para mais informações, consulte os seguintes tópicos:  
  
-   [Serialização e desserialização](./feature-details/serialization-and-deserialization.md)  
  
-   [Serialização no Windows Communication Foundation](https://msdn.microsoft.com/magazine/cc163569.aspx)  
  
### <a name="exception-handling-capabilities"></a>Recursos de tratamento de exceção  
  
#### <a name="exceptions-in-net-remoting"></a>Exceções de comunicação remota do .NET  
 As exceções geradas por um servidor de comunicação remota são serializadas, enviadas ao cliente e geradas localmente no cliente, como qualquer outra exceção. Exceções personalizadas podem ser criadas por inferior classing o tipo de exceção e marcá-lo com [Serializable].   A maioria das exceções do framework já são marcados dessa forma, permitindo que a maioria dos gerada pelo servidor, serializada e gerada novamente no cliente. Embora esse design é conveniente durante o desenvolvimento, informações do lado do servidor podem ser divulgadas inadvertidamente ao cliente. Essa é uma das muitas razões, que comunicação remota deve ser usada somente em ambientes totalmente confiáveis.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>Exceções e falhas no WCF  
 O WCF não permite tipos de exceção arbitrários a serem retornadas do servidor para o cliente porque isso pode levar a divulgação acidental de informações. Se uma operação de serviço lança uma exceção inesperada, faz com que uma FaultException seja gerada no cliente de uso geral. Essa exceção não significa qualquer informação porque ou onde o problema ocorreu, e para alguns aplicativos, isso é suficiente. Aplicativos que precisam se comunicar informações mais detalhadas do erro para o cliente, faça isso definindo um contrato de falha.  
  
 Para fazer isso, primeiro crie um tipo de [DataContract] para conduzir as informações de falha.  
  
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
  
 O servidor de relatórios condições de erro lançando uma FaultException.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 E, sempre que o cliente faz uma solicitação ao servidor, ele pode capturar falhas como exceções normais.  
  
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
  
 Para obter mais informações sobre contratos de falha, consulte <xref:System.ServiceModel.FaultException>.  
  
### <a name="security-considerations"></a>Considerações sobre segurança  
  
#### <a name="security-in-net-remoting"></a>Segurança na comunicação remota do .NET  
 Alguns canais de comunicação remota do .NET dá suporte a recursos de segurança, como autenticação e criptografia na camada do canal (TCP e IPC). O canal HTTP se baseia em serviços de informações da Internet (IIS) para autenticação e criptografia. Apesar desse suporte, você deve considerar um protocolo de comunicação seguro de comunicação remota do .NET e usá-lo somente em ambientes totalmente confiáveis. Nunca exponha um ponto de extremidade de comunicação remota público à Internet ou clientes não confiáveis.  
  
#### <a name="security-in-wcf"></a>Segurança no WCF  
 O WCF foi projetado com segurança em mente, em parte para resolver os tipos de vulnerabilidades encontradas na comunicação remota do .NET. O WCF oferece segurança no nível de transporte e de mensagem e oferece muitas opções de autenticação, autorização, criptografia e assim por diante. Para mais informações, consulte os seguintes tópicos:  
  
-   [Segurança](./feature-details/security.md)  
  
-   [Diretrizes de segurança do WCF](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>Migrando para o WCF  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Por que migrar da comunicação remota do WCF?  
  
-   **Comunicação remota do .NET é um produto herdado.** Conforme descrito em [comunicação remota do .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), ele é considerado um produto herdado e não é recomendado para novo desenvolvimento. WCF ou API Web do ASP.NET são recomendados para aplicativos novos e existentes.  
  
-   **O WCF usa padrões de plataforma cruzada.** O WCF foi desenvolvido com a interoperabilidade entre plataformas em mente e dá suporte a muitos padrões do setor (SOAP, WS-Security, WS-Trust, etc.). Um serviço WCF pode interoperar com clientes em execução em sistemas operacionais diferentes do Windows. Comunicação remota foi projetada principalmente para ambientes em que aplicativos cliente e servidor executados usando o .NET framework em um sistema de operacional Windows.  
  
-   **O WCF possui segurança interna.** O WCF foi projetado tendo em mente a segurança e oferece muitas opções de autenticação, segurança em nível de transporte, segurança em nível de mensagem, etc. Comunicação remota foi projetada para tornar mais fácil para aplicativos interoperar, mas não foi projetada para ser seguro em ambientes não confiáveis. O WCF foi projetado para trabalhar em ambientes confiáveis e não confiáveis.  
  
### <a name="migration-recommendations"></a>Recomendações de migração  
 A seguir está as etapas recomendadas para migrar de comunicação remota do .NET para WCF:  
  
-   **Crie o contrato de serviço.** Definir seus tipos de interface de serviço e marcá-los com o atributo [ServiceContract]. Marca todos os métodos que os clientes terão permissão para chamar com [OperationContract].  
  
-   **Crie o contrato de dados.** Defina os tipos de dados que serão trocados entre cliente e servidor e marcá-los com o atributo [DataContract]. Marca todos os campos e propriedades que o cliente poderá usar com [DataMember].  
  
-   **Crie o contrato de falha (opcional).** Crie os tipos que serão trocados entre cliente e servidor quando forem encontrados erros. Marca esses tipos com [DataContract] e [DataMember] para torná-las serializável. Todas as operações de serviço que é marcado com [OperationContract], também marcá-los com [FaultContract] para indicar quais erros, eles podem retornar.  
  
-   **Configurar e hospedar o serviço.** Quando o contrato de serviço tiver sido criado, a próxima etapa é configurar uma associação para expor o serviço em um ponto de extremidade. Para obter mais informações, consulte [pontos de extremidade: Endereços, associações e contratos](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 Depois que um aplicativo de comunicação remota tiver sido migrado para o WCF, ele ainda é importante remover dependências em .NET Remoting. Isso garante que quaisquer vulnerabilidades de comunicação remota são removidas do aplicativo. Essas etapas incluem o seguinte:  
  
-   **Descontinuar o uso do MarshalByRefObject.** O tipo de MarshalByRefObject existe apenas para comunicação remota e não é usado pelo WCF. Qualquer tipo de aplicativo na subclasse MarshalByRefObject deve ser removido ou alterado. O tipo de MarshalByRefObject existe apenas para comunicação remota e não é usado pelo WCF. Qualquer tipo de aplicativo na subclasse MarshalByRefObject deve ser removido ou alterado.  
  
-   **Descontinuar o uso de [Serializable] e ISerializable.** O atributo [Serializable] e a interface ISerializable foram originalmente criados para serializar os tipos em ambientes confiáveis, e eles são usados pela comunicação remota. Serialização no WCF se baseia em tipos que estão sendo marcados com [DataContract] e [DataMember]. Tipos de dados usados por um aplicativo devem ser modificados para usar [DataContract] e não usar ISerializable ou [Serializable]. O atributo [Serializable] e a interface ISerializable foram originalmente criados para serializar os tipos em ambientes confiáveis, e eles são usados pela comunicação remota. Serialização no WCF se baseia em tipos que estão sendo marcados com [DataContract] e [DataMember]. Tipos de dados usados por um aplicativo devem ser modificados para usar [DataContract] e não usar ISerializable ou [Serializable].  
  
### <a name="migration-scenarios"></a>Cenários de migração  
 Agora vamos ver como realizar os seguintes cenários comuns de comunicação remota no WCF:  
  
1.  Servidor retorna um objeto por valor para o cliente  
  
2.  Servidor retorna um objeto por referência para o cliente  
  
3.  Cliente envia um objeto por valor para o servidor  
  
> [!NOTE]
>  Enviar um objeto por referência do cliente para o servidor não é permitido no WCF.  
  
 Ao ler por meio desses cenários, suponha que nossas interfaces de linha de base para comunicação remota do .NET se parecer com o exemplo a seguir. A implementação de comunicação remota do .NET não é importante aqui porque queremos ilustram só como usar o WCF para implementar a funcionalidade equivalente.  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a>Cenário 1: Serviço retorna um objeto por valor  
 Este cenário demonstra um servidor retornando um objeto para o cliente por valor. WCF sempre retorna objetos do servidor por valor, portanto, simplesmente, as etapas a seguir descrevem como criar um serviço WCF normal.  
  
1.  Comece definindo uma interface pública para o serviço WCF e marcá-lo com o atributo [ServiceContract]. Usamos [OperationContract] para identificar os métodos do lado do servidor que chamará nosso cliente.  
  
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
  
2.  A próxima etapa é criar o contrato de dados para este serviço. Fazemos isso criando classes (não interfaces) marcadas com o atributo [DataContract]. As propriedades individuais ou campos desejados visíveis para o cliente e servidor são marcados com [DataMember]. Se quisermos que tipos derivados para ser permitido, devemos usar o atributo [KnownType] para identificá-los. Os únicos tipos de WCF permitirá a ser serializado ou desserializado para esse serviço estão aqueles na interface de serviço e esses "tipos conhecidos". A tentativa de trocar de qualquer outro tipo não esteja na lista será rejeitada.  
  
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
  
3.  Em seguida, fornecemos a implementação da interface de serviço.  
  
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
  
4.  Para executar o serviço WCF, precisamos declarar um ponto de extremidade que expõe a interface de serviço em uma URL específica usando uma associação específica do WCF. Normalmente, isso é feito adicionando as seções a seguir ao arquivo de Web. config do projeto do servidor.  
  
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
  
5.  O serviço WCF, em seguida, pode ser iniciado com o código a seguir:  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Quando esse ServiceHost é iniciado, ele usa o arquivo Web. config para estabelecer o contrato adequado, a ligação e o ponto de extremidade. Para obter mais informações sobre arquivos de configuração, consulte [Configurando serviços usando arquivos de configuração](./configuring-services-using-configuration-files.md). Esse estilo de iniciar o servidor é conhecido como hospedagem interna. Para saber mais sobre outras opções para hospedar serviços WCF, consulte [serviços de hospedagem](./hosting-services.md).  
  
6.  App. config do projeto cliente deve declarar as informações de associação correspondentes do ponto de extremidade do serviço. A maneira mais fácil de fazer isso no Visual Studio é usar **adicionar referência de serviço**, que atualizará automaticamente o arquivo App. config. Como alternativa, essas mesmas alterações podem ser adicionadas manualmente.  
  
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
  
     Para obter mais informações sobre como usar **adicionar referência de serviço**, consulte [como: Adicionar, atualizar ou remover uma referência de serviço](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).  
  
7.  Agora podemos chamar o serviço WCF do cliente. Fazemos isso criando uma fábrica de canais para o serviço, solicitando que ele de um canal e chamar diretamente o método que queremos naquele canal. Podemos fazer isso porque o canal implementa a interface do serviço e manipula a lógica subjacente de solicitação/resposta para nós. O valor de retorno dessa chamada de método é a cópia desserializada da resposta do servidor.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 Os objetos retornados pelo WCF do servidor para o cliente são sempre por valor. Os objetos são cópias desserializadas dos dados enviados pelo servidor. O cliente pode chamar métodos nessas cópias locais sem qualquer perigo de invocar o código do servidor por meio de retornos de chamada.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Cenário 2: Servidor retorna um objeto por referência  
 Este cenário demonstra o servidor que fornece um objeto para o cliente por referência. No .NET Remoting, isso é manipulado automaticamente para qualquer tipo derivado de MarshalByRefObject, que é serializado por referência. Um exemplo desse cenário é permitir que vários clientes têm objetos independentes de sessão no servidor. Como mencionado anteriormente, os objetos retornados por um serviço WCF não são sempre por valor, portanto, não há nenhum equivalente direto de um objeto por referência, mas é possível obter algo semelhante ao uso de semântica por referência um <xref:System.ServiceModel.EndpointAddress10> objeto. Isso é um objeto serializável por valor que pode ser usado pelo cliente para obter um objeto por referência de sessão no servidor. Isso permite que o cenário de ter vários clientes com objetos de servidor de sessão independentes.  
  
1.  Primeiro, precisamos definir um contrato de serviço WCF que corresponde ao objeto de sessão.  
  
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
    >  Observe que o objeto de sessão é marcado com [ServiceContract], tornando-o uma interface de serviço WCF normal. Definindo o SessionMode propriedade indica que é um serviço de sessão. No WCF, uma sessão é uma maneira de correlacionar várias mensagens enviadas entre dois pontos de extremidade. Isso significa que, depois que um cliente obtiver uma conexão para esse serviço, uma sessão será estabelecida entre o cliente e o servidor. O cliente usará uma única instância exclusiva do objeto do lado do servidor para todas as interações dele nessa única sessão.  
  
2.  Em seguida, precisamos fornecer a implementação dessa interface de serviço. Denotando-la com [ServiceBehavior] e definindo o InstanceContextMode, Informaremos ao WCF que queremos usar uma instância exclusiva desse tipo para uma sessão de cada.  
  
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
  
3.  Agora precisamos de uma maneira de obter uma instância desse objeto de sessão. Fazemos isso criando outra interface de serviço do WCF que retorna um objeto EndpointAddress10. Isso é uma forma serializável de um ponto de extremidade que o cliente pode usar para criar o objeto de sessão.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     E podemos implementar esse serviço do WCF:  
  
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
  
     Essa implementação mantém uma fábrica de canais única para criar objetos de sessão. Quando GetInstanceAddress() é chamado, ele cria um canal e cria um objeto EndpointAddress10 que efetivamente aponta para o endereço remoto associado a esse canal. EndpointAddress10 é simplesmente um tipo de dados que pode ser retornado ao cliente por valor.  
  
4.  Precisamos modificar o arquivo de configuração do servidor ao fazer duas coisas a seguir, conforme mostrado no exemplo a seguir:  
  
    1.  Declarar um \<cliente > seção que descreve o ponto de extremidade para o objeto de sessão. Isso é necessário porque o servidor também atua como um cliente nessa situação.  
  
    2.  Declare pontos de extremidade para o objeto de fábrica e de sessão. Isso é necessário para permitir que o cliente para se comunicar com os pontos de extremidade de serviço para adquirir o EndpointAddress10 e criar o canal de sessão.  
  
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
  
     E, em seguida, podemos começar a esses serviços:  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5.  Declarando esses mesmos pontos de extremidade no arquivo de App. config do seu projeto, podemos configurar o cliente.  
  
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
  
6.  Para criar e usar esse objeto de sessão, o cliente deve fazer as seguintes etapas:  
  
    1.  Crie um canal para o serviço ISessionBoundFactory.  
  
    2.  Use esse canal para invocar esse serviço para obter um EndpointAddress10.  
  
    3.  Use o EndpointAddress10 para criar um canal para obter um objeto de sessão.  
  
    4.  Interagir com o objeto de sessão para demonstrar que ela permanece a mesma instância em várias chamadas.  
  
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
  
 O WCF sempre retorna objetos por valor, mas é possível suportar o equivalente a semântica por referência com o uso de EndpointAddress10. Isso permite que o cliente solicite uma instância de serviço WCF sessão, após o qual ele pode interagir com ele como qualquer outro serviço do WCF.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Cenário 3: O cliente envia ao servidor uma instância por valor  
 Este cenário demonstra o cliente enviar uma instância de objeto não primitivos para o servidor por valor. Porque o WCF envia apenas objetos por valor, este cenário demonstra o uso normal do WCF.  
  
1.  Use o mesmo serviço de WCF do cenário 1.  
  
2.  Use o cliente para criar um novo objeto por valor (cliente), criar um canal para se comunicar com o serviço ICustomerService e enviar o objeto para ele.  
  
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
  
     O objeto de cliente será serializado e enviado ao servidor, onde ele é desserializado em uma nova cópia desse objeto.  
  
    > [!NOTE]
    >  Esse código também ilustra o envio de um tipo derivado (PremiumCustomer). A interface de serviço espera um objeto do cliente, mas o atributo [KnownType] na classe Customer indicado que premiumcustomer também era permitido. O WCF irá falhar qualquer tentativa de serializar ou desserializar qualquer outro tipo por meio dessa interface de serviço.  
  
 Trocas de dados de WCF normais são por valor. Isso garante que a invocação de métodos em um desses objetos de dados é executado apenas localmente – não invocará código na camada de. Embora seja possível obter algo como objetos por referência retornada *partir* o servidor, não é possível que um cliente passar um objeto por referência *para* o servidor. Um cenário que requer uma conversa de ida e volta entre o cliente e o servidor pode ser obtido no WCF usando um serviço duplex. Para obter mais informações, consulte [serviços Duplex](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Resumo  
 Comunicação remota do .NET é uma estrutura de comunicação que se destina a ser usado apenas em ambientes totalmente confiáveis. Ele é um produto herdado e suporte somente para compatibilidade com versões anteriores. Ele não deve ser usado para criar novos aplicativos. Por outro lado, o WCF foi projetado tendo em mente a segurança e é recomendado para aplicativos novos e existentes. A Microsoft recomenda que os aplicativos de comunicação remota ser migrada para usar o WCF ou API Web ASP.NET em vez disso.