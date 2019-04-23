---
title: Especificando transferência de dados em contratos de serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: 88bdfe6e659e6e83365b3d17c9067581f209d154
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331514"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Especificando transferência de dados em contratos de serviço
O Windows Communication Foundation (WCF) pode ser pensada como uma infraestrutura de mensagens. Operações de serviço podem receber mensagens, processá-los e enviar mensagens a eles. As mensagens são descritas usando contratos de operação. Por exemplo, considere o seguinte contrato.  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(string fromCity, string toCity);  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
  
    <OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
End Interface  
```  
  
 Aqui, o `GetAirfare` operação aceita uma mensagem com informações sobre `fromCity` e `toCity`e, em seguida, retorna uma mensagem que contém um número.  
  
 Este tópico explica as várias maneiras em que um contrato de operação pode descrever as mensagens.  
  
## <a name="describing-messages-by-using-parameters"></a>Descrevendo as mensagens usando parâmetros  
 A maneira mais simples para descrever uma mensagem é usar uma lista de parâmetros e o valor de retorno. No exemplo anterior, o `fromCity` e `toCity` parâmetros de cadeia de caracteres foram usados para descrever a mensagem de solicitação e o valor de retorno de float foi usado para descrever a mensagem de resposta. Se o valor de retorno sozinho não é suficiente para descrever uma mensagem de resposta, os parâmetros de saída podem ser usados. Por exemplo, a seguinte operação tem `fromCity` e `toCity` em sua mensagem de solicitação e um número junto com uma moeda em sua mensagem de resposta:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Além disso, você pode usar parâmetros de referência para tornar uma parte do parâmetro da solicitação e a mensagem de resposta. Os parâmetros devem ser dos tipos que podem ser serializados (convertidos em XML). Por padrão, o WCF usa um componente chamado de <xref:System.Runtime.Serialization.DataContractSerializer> classe para realizar essa conversão. Tipos mais primitivos (como `int`, `string`, `float`, e `DateTime`.) têm suporte. Tipos definidos pelo usuário normalmente devem ter um contrato de dados. Para obter mais informações, consulte [contratos de dados usando](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
```csharp
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
  
    [DataContract]  
    public class Itinerary  
    {  
        [DataMember]  
        public string fromCity;  
        [DataMember]  
        public string toCity;  
   }  
}  
```  
  
```vb  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
    <DataContract()>  
    Class Itinerary  
  
        <DataMember()>  
        Public fromCity As String  
        <DataMember()>  
        Public toCity As String  
    End Class  
End Interface  
```  
  
 Ocasionalmente, o `DataContractSerializer` não é adequada para serializar seus tipos. O WCF oferece suporte a um mecanismo de serialização alternativo, o <xref:System.Xml.Serialization.XmlSerializer>, que você também pode usar para serializar os parâmetros. O <xref:System.Xml.Serialization.XmlSerializer> permite que você use mais controle sobre o XML resultante usando atributos, como o `XmlAttributeAttribute`. Passar a usar o <xref:System.Xml.Serialization.XmlSerializer> de uma determinada operação ou o serviço inteiro, aplicar o <xref:System.ServiceModel.XmlSerializerFormatAttribute> de atributo a uma operação ou um serviço. Por exemplo:  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    [XmlSerializerFormat]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
}  
public class Itinerary  
{  
    public string fromCity;  
    public string toCity;  
    [XmlAttribute]  
    public bool isFirstClass;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    <XmlSerializerFormat>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
End Interface  
  
Class Itinerary  
  
    Public fromCity As String  
    Public toCity As String  
    <XmlSerializerFormat()>  
    Public isFirstClass As Boolean  
End Class  
```  
  
 Para obter mais informações, consulte [usando a classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md). Lembre-se de que trocar manualmente para o <xref:System.Xml.Serialization.XmlSerializer> conforme mostrado aqui não é recomendado a menos que você tenha motivos específicos para fazer assim como detalhado no tópico.  
  
 Para isolar os nomes de parâmetro do .NET dos nomes de contrato, você pode usar o <xref:System.ServiceModel.MessageParameterAttribute> de atributo e, em seguida, use o `Name` propriedade para definir o nome do contrato. Por exemplo, o seguinte contrato de operação é equivalente ao primeiro exemplo neste tópico.  
  
```csharp  
[OperationContract]  
public float GetAirfare(  
    [MessageParameter(Name="fromCity")] string originCity,  
    [MessageParameter(Name="toCity")] string destinationCity);  
```  
  
```vb  
<OperationContract()>  
  Function GetAirfare(<MessageParameter(Name := "fromCity")> fromCity As String, <MessageParameter(Name := "toCity")> toCity As String) As Double  
```  
  
## <a name="describing-empty-messages"></a>Descrevendo mensagens vazias  
 Uma mensagem de solicitação vazio pode ser descrita por não ter nenhum parâmetro de entrada ou de referência. Por exemplo, em C#:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Por exemplo, no VB:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Uma mensagem de resposta vazio pode ser descrita por ter um `void` tipo de retorno e parâmetros de saída ou de referência. Por exemplo, em:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 Isso é diferente de uma operação unidirecional, tais como:  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 O `SetTemperatureStatus` operação retorna uma mensagem vazia. Ele pode retornar uma falha em vez disso, se houver um problema ao processar a mensagem de entrada. O `SetLightbulbStatus` operação não retorna nada. Não há nenhuma maneira de comunicar-se uma condição de falha dessa operação.  
  
## <a name="describing-messages-by-using-message-contracts"></a>Descrevendo as mensagens por meio de contratos de mensagem  
 Você talvez queira usar um único tipo para representar a mensagem inteira. Embora seja possível usar um contrato de dados para essa finalidade, a maneira recomendada para fazer isso é usar um contrato de mensagem — Isso evita níveis desnecessários de encapsulamento no XML resultante. Além disso, os contratos de mensagem permitem que você tenha mais controle sobre mensagens resultantes. Por exemplo, você pode decidir quais informações devem estar no corpo da mensagem e que deve ser nos cabeçalhos da mensagem. O exemplo a seguir mostra o uso de contratos de mensagem.  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    GetAirfareResponse GetAirfare(GetAirfareRequest request);  
}  
  
[MessageContract]  
public class GetAirfareRequest  
{  
    [MessageHeader] public DateTime date;  
    [MessageBodyMember] public Itinerary itinerary;  
}  
  
[MessageContract]  
public class GetAirfareResponse  
{  
    [MessageBodyMember] public float airfare;  
    [MessageBodyMember] public string currency;  
}  
  
[DataContract]  
public class Itinerary  
{  
    [DataMember] public string fromCity;  
    [DataMember] public string toCity;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    Function GetAirfare(request As GetAirfareRequest) As GetAirfareResponse  
End Interface  
  
<MessageContract()>  
Public Class GetAirfareRequest  
    <MessageHeader()>   
    Public Property date as DateTime  
    <MessageBodyMember()>  
    Public Property itinerary As Itinerary  
End Class  
  
<MessageContract()>  
Public Class GetAirfareResponse  
    <MessageBodyMember()>  
    Public Property airfare As Double  
    <MessageBodyMember()> Public Property currency As String  
End Class  
  
<DataContract()>  
Public Class Itinerary  
    <DataMember()> Public Property fromCity As String  
    <DataMember()> Public Property toCity As String  
End Class  
```  
  
 Para obter mais informações, consulte [contratos de mensagem usando](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
 No exemplo anterior, o <xref:System.Runtime.Serialization.DataContractSerializer> classe ainda é usado por padrão. O <xref:System.Xml.Serialization.XmlSerializer> classe também pode ser usada com contratos de mensagem. Para fazer isso, aplicar a <xref:System.ServiceModel.XmlSerializerFormatAttribute> de atributo para a operação ou o contrato e usar tipos compatíveis com o <xref:System.Xml.Serialization.XmlSerializer> classe nos cabeçalhos de mensagem e os membros do corpo.  
  
## <a name="describing-messages-by-using-streams"></a>Descrevendo as mensagens por meio de fluxos  
 Outra maneira de descrever as mensagens em operações é usar o <xref:System.IO.Stream> classe ou uma de suas classes derivadas em um contrato de operação ou como um membro de corpo de contrato de mensagem (ele deve ser o único membro nesse caso). Mensagens de entrada, o tipo deve ser `Stream`— não é possível usar as classes derivadas.  
  
 Em vez de invocar o serializador, WCF recupera dados de um fluxo e coloca-o diretamente em uma mensagem de saída, ou recupera dados de uma mensagem de entrada e coloca-o diretamente em um fluxo. O exemplo a seguir mostra o uso de fluxos.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Não é possível combinar `Stream` e não são de fluxo dados no corpo de uma única mensagem. Use um contrato de mensagem para colocar os dados extras em cabeçalhos de mensagem. O exemplo a seguir mostra o uso incorreto de fluxos ao definir o contrato de operação.  
  
```csharp  
//Incorrect:  
// [OperationContract]  
// public void UploadFile (string fileName, Stream fileData);  
```  
  
```vb  
'Incorrect:  
    '<OperationContract()>  
    Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
```  
  
 O exemplo a seguir mostra o uso correto dos fluxos ao definir um contrato de operação.  
  
```csharp  
[OperationContract]  
public void UploadFile (UploadFileMessage message);  
//code omitted  
[MessageContract]  
public class UploadFileMessage  
{  
    [MessageHeader] public string fileName;  
    [MessageBodyMember] public Stream fileData;  
}  
```  
  
```vb  
<OperationContract()>  
Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
'Code Omitted  
<MessageContract()>  
Public Class UploadFileMessage  
   <MessageHeader()>  
    Public Property fileName As String  
    <MessageBodyMember()>  
    Public Property fileData As Stream  
End Class  
```  
  
 Para obter mais informações, consulte [dados grandes e Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>Usando a classe de mensagens  
 Para que o controle programático completo sobre mensagens enviadas ou recebidas, você pode usar o <xref:System.ServiceModel.Channels.Message> classe diretamente, conforme mostrado no código de exemplo a seguir.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Isso é um cenário avançado, que é descrito detalhadamente no [usando a classe de mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>Descrevendo as mensagens de falha  
 As mensagens que são descritas pelo valor de retorno e os parâmetros de saída ou de referência, além de qualquer operação que não seja unidirecional pode retornar pelo menos duas mensagens possíveis: sua mensagem de resposta normal e uma mensagem de falha. Considere o seguinte contrato de operação.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Essa operação também pode retornar uma mensagem normal que contém um `float` número ou uma mensagem de falha que contém um código de falha e uma descrição. Você pode fazer isso, lançando uma <xref:System.ServiceModel.FaultException> em sua implementação de serviço.  
  
 Você pode especificar mensagens de falha possíveis adicionais usando o <xref:System.ServiceModel.FaultContractAttribute> atributo. As falhas adicionais devem ser serializados usando a <xref:System.Runtime.Serialization.DataContractSerializer>, conforme mostrado no código de exemplo a seguir.  
  
```csharp  
[OperationContract]  
[FaultContract(typeof(ItineraryNotAvailableFault))]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
  
//code omitted  
  
[DataContract]  
public class ItineraryNotAvailableFault  
{  
    [DataMember]  
    public bool IsAlternativeDateAvailable;  
  
    [DataMember]  
    public DateTime alternativeSuggestedDate;  
}  
```  
  
```vb  
<OperationContract()>  
<FaultContract(GetType(ItineraryNotAvailableFault))>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime) As Double  
  
'Code Omitted  
<DataContract()>  
Public Class  
  <DataMember()>  
  Public Property IsAlternativeDateAvailable As Boolean  
  <DataMember()>  
  Public Property alternativeSuggestedDate As DateTime  
End Class  
```  
  
 Essas falhas adicionais podem ser geradas, lançando uma <xref:System.ServiceModel.FaultException%601> do tipo de contrato de dados apropriado. Para obter mais informações, consulte [tratamento de exceções e falhas de](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
 Não é possível usar o <xref:System.Xml.Serialization.XmlSerializer> classe para descrever a falhas. O <xref:System.ServiceModel.XmlSerializerFormatAttribute> não tem efeito sobre contratos de falha.  
  
## <a name="using-derived-types"></a>Usando tipos derivados  
 Você talvez queira usar um tipo base em uma operação ou um contrato de mensagem e, em seguida, usar um tipo derivado quando, na verdade, invocar a operação. Nesse caso, você deve usar qualquer um de <xref:System.ServiceModel.ServiceKnownTypeAttribute> tipos derivados do atributo ou algum mecanismo alternativo para permitir o uso de. Considere a seguinte operação.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 Suponha que dois tipos `Book` e `Magazine`, derivam `LibraryItem`. Para usar estes tipos de `IsLibraryItemAvailable` operação, você pode alterar a operação da seguinte maneira:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Como alternativa, você pode usar o <xref:System.Runtime.Serialization.KnownTypeAttribute> de atributo quando o padrão <xref:System.Runtime.Serialization.DataContractSerializer> está em uso, conforme mostrado no código de exemplo a seguir.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
  
// code omitted   
  
[DataContract]  
[KnownType(typeof(Book))]  
[KnownType(typeof(Magazine))]  
public class LibraryItem  
{  
    //code omitted  
}  
```  
  
```vb  
<OperationContract()>  
Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
  
'Code Omitted  
<DataContract()>  
<KnownType(GetType(Book))>  
<KnownType(GetType(Magazine))>  
Public Class LibraryItem  
  'Code Omitted  
End Class  
```  
  
 Você pode usar o <xref:System.Xml.Serialization.XmlIncludeAttribute> atributo ao usar o <xref:System.Xml.Serialization.XmlSerializer>.  
  
 Você pode aplicar o <xref:System.ServiceModel.ServiceKnownTypeAttribute> atributo a uma operação ou para todo o serviço. Ele aceita um tipo ou o nome do método para chamar para obter uma lista de tipos conhecidos, assim como o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo. Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Especificando o uso e estilo  
 Ao descrever serviços usando a descrição de linguagem WSDL (Web Services), as duas normalmente estilos usados são documentos e chamada de procedimento remoto (RPC). O estilo de documento, o corpo da mensagem inteira é descrito usando o esquema e o WSDL descreve as várias partes de corpo de mensagem referindo-se aos elementos dentro desse esquema. No estilo RPC, o WSDL se refere a um tipo de esquema para cada parte da mensagem em vez de um elemento. Em alguns casos, você precisa selecionar um desses estilos manualmente. Você pode fazer isso por meio da aplicação a <xref:System.ServiceModel.DataContractFormatAttribute> atributo e configuração o `Style` propriedade (quando o <xref:System.Runtime.Serialization.DataContractSerializer> está em uso), ou definindo `Style` no <xref:System.ServiceModel.XmlSerializerFormatAttribute> atributo (ao usar o <xref:System.Xml.Serialization.XmlSerializer>).  
  
 Além disso, o <xref:System.Xml.Serialization.XmlSerializer> dá suporte a duas formas de XML serializado: `Literal` e `Encoded`. `Literal` é a forma mais comumente aceita, e é a única forma de <xref:System.Runtime.Serialization.DataContractSerializer> dá suporte. `Encoded` é um formulário herdado descrito na seção 5 da especificação do SOAP e não é recomendado para novos serviços. Para alternar para o `Encoded` modo, defina a `Use` propriedade no <xref:System.ServiceModel.XmlSerializerFormatAttribute> atributo `Encoded`.  
  
 Na maioria dos casos, você não deve alterar as configurações padrão para o `Style` e `Use` propriedades.  
  
## <a name="controlling-the-serialization-process"></a>Controlando o processo de serialização  
 Você pode fazer várias coisas para personalizar a maneira como os dados são serializados.  
  
### <a name="changing-server-serialization-settings"></a>Alterando as definições de serialização do servidor  
 Quando o padrão <xref:System.Runtime.Serialization.DataContractSerializer> está em uso, você pode controlar alguns aspectos do processo de serialização no serviço aplicando o <xref:System.ServiceModel.ServiceBehaviorAttribute> de atributo para o serviço. Especificamente, você pode usar o `MaxItemsInObjectGraph` propriedade para definir a cota que limita o número máximo de objetos a <xref:System.Runtime.Serialization.DataContractSerializer> desserializa. Você pode usar o `IgnoreExtensionDataObject` propriedade para desativar o recurso de controle de versão do ciclo completo. Para obter mais informações sobre cotas, confira [Considerações sobre segurança de dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Para obter mais informações sobre o ciclo completo, consulte [contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
```csharp  
[ServiceBehavior(MaxItemsInObjectGraph=100000)]  
public class MyDataService:IDataService  
{  
    public DataPoint[] GetData()  
    {  
       // Implementation omitted  
    }  
}  
```  
  
```vb  
<ServiceBehavior(MaxItemsInObjectGraph:=100000)>  
Public Class MyDataService Implements IDataService  
  
    Function GetData() As DataPoint()  
         ‘ Implementation omitted  
    End Function  
End Interface  
```  
  
### <a name="serialization-behaviors"></a>Comportamentos de serialização  
 Dois comportamentos estão disponíveis no WCF, o <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> e o <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> que são conectados automaticamente dependendo de qual serializador é usado para uma determinada operação. Como esses comportamentos são aplicados automaticamente, você normalmente não precisa estar ciente deles.  
  
 No entanto, o `DataContractSerializerOperationBehavior` tem o `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, e `DataContractSurrogate` propriedades que você pode usar para personalizar o processo de serialização. As duas primeiras propriedades têm o mesmo significado conforme discutido na seção anterior. Você pode usar o `DataContractSurrogate` propriedade para habilitar substitutos de contrato de dados, que são um mecanismo poderoso para personalizar e estender o processo de serialização. Para obter mais informações, consulte [substitutos de contrato de dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
 Você pode usar o `DataContractSerializerOperationBehavior` para personalizar a serialização de cliente e servidor. O exemplo a seguir mostra como aumentar o `MaxItemsInObjectGraph` cota no cliente.  
  
```csharp  
ChannelFactory<IDataService> factory = new ChannelFactory<IDataService>(binding, address);  
foreach (OperationDescription op in factory.Endpoint.Contract.Operations)  
{  
    DataContractSerializerOperationBehavior dataContractBehavior =  
                op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
    if (dataContractBehavior != null)  
    {  
        dataContractBehavior.MaxItemsInObjectGraph = 100000;  
    }  
}  
IDataService client = factory.CreateChannel();  
```  
  
```vb  
Dim factory As ChannelFactory(Of IDataService) = New ChannelFactory(Of IDataService)(binding, address)  
For Each op As OperationDescription In factory.Endpoint.Contract.Operations  
        Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
        If dataContractBehavior IsNot Nothing Then  
            dataContractBehavior.MaxItemsInObjectGraph = 100000  
        End If  
     Next  
    Dim client As IDataService = factory.CreateChannel  
```  
  
 A seguir está o código equivalente no serviço, no caso de auto-hospedado.  
  
```csharp  
ServiceHost serviceHost = new ServiceHost(typeof(IDataService))  
foreach (ServiceEndpoint ep in serviceHost.Description.Endpoints)  
{  
foreach (OperationDescription op in ep.Contract.Operations)  
{  
        DataContractSerializerOperationBehavior dataContractBehavior =  
           op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
        if (dataContractBehavior != null)  
        {  
            dataContractBehavior.MaxItemsInObjectGraph = 100000;  
        }  
}  
}  
serviceHost.Open();  
```  
  
```vb  
Dim serviceHost As ServiceHost = New ServiceHost(GetType(IDataService))  
        For Each ep As ServiceEndpoint In serviceHost.Description.Endpoints  
            For Each op As OperationDescription In ep.Contract.Operations  
                Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
  
                If dataContractBehavior IsNot Nothing Then  
                    dataContractBehavior.MaxItemsInObjectGraph = 100000  
                End If  
            Next  
        Next  
        serviceHost.Open()  
```  
  
 No caso do hospedados na Web, você deve criar um novo `ServiceHost` classe derivada e usar uma fábrica do host de serviço para conectá-lo.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Configurações de serialização na configuração de controle  
 O `MaxItemsInObjectGraph` e `IgnoreExtensionDataObject` pode ser controlado pela configuração usando o `dataContractSerializer` comportamento de ponto de extremidade ou serviço, conforme mostrado no exemplo a seguir.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="LargeQuotaBehavior">  
                    <dataContractSerializer  
                      maxItemsInObjectGraph="100000" />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <client>  
            <endpoint address="http://example.com/myservice"  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""   
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Serialização de tipo, preservação do gráfico do objeto e os serializadores personalizados compartilhados  
 O <xref:System.Runtime.Serialization.DataContractSerializer> serializa usando nomes de contrato de dados e não os nomes de tipo do .NET. Isso é consistente com os princípios de arquitetura orientada a serviços e permite um alto grau de flexibilidade — os tipos do .NET podem alterar sem afetar o contrato de transmissão. Em casos raros, você talvez queira serializar os nomes de tipo .NET reais, apresentando assim um acoplamento rígido entre o cliente e servidor, semelhante à tecnologia de comunicação remota do .NET Framework. Isso não é uma prática recomendada, exceto em casos raros que normalmente ocorrem ao migrar para o WCF de comunicação remota do .NET Framework. Nesse caso, você deve usar o <xref:System.Runtime.Serialization.NetDataContractSerializer> classe, em vez do <xref:System.Runtime.Serialization.DataContractSerializer> classe.  
  
 O <xref:System.Runtime.Serialization.DataContractSerializer> normalmente serializa os gráficos de objeto como árvores de objetos. Ou seja, se o mesmo objeto é referenciado mais de uma vez, ele é serializado mais de uma vez. Por exemplo, considere uma `PurchaseOrder` instância que tem dois campos de tipo de endereço chamado `billTo` e `shipTo`. Se ambos os campos são definidos para a mesma instância de endereço, há duas instâncias idênticas de endereço após a serialização e desserialização. Isso é feito porque não há nenhuma maneira interoperável padrão para representar os gráficos de objeto no XML (exceto para o padrão SOAP codificado herdado disponível na <xref:System.Xml.Serialization.XmlSerializer>, conforme descrito na seção anterior sobre `Style` e `Use`). Serializando gráficos de objeto como árvores tem certas desvantagens, por exemplo, os gráficos com referências circulares não podem ser serializados. Ocasionalmente, é necessário alternar para a serialização de gráfico de objeto verdadeira, mesmo que não é interoperável. Isso pode ser feito usando o <xref:System.Runtime.Serialization.DataContractSerializer> construído com o `preserveObjectReferences` parâmetro definido como `true`.  
  
 Ocasionalmente, os serializadores internos não são suficientes para seu cenário. Na maioria dos casos, você ainda pode usar o <xref:System.Runtime.Serialization.XmlObjectSerializer> abstração do qual o <xref:System.Runtime.Serialization.DataContractSerializer> e o <xref:System.Runtime.Serialization.NetDataContractSerializer> derivar.  
  
 Os três casos anteriores (preservação de tipo do .NET, a preservação do gráfico do objeto e completamente personalizado `XmlObjectSerializer`-com base em serialização) exigem um serializador personalizado ser conectados. Para fazer isso, execute estas etapas:  
  
1. Escrever seu próprio comportamento derivando de <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.  
  
2. Substituir os dois `CreateSerializer` métodos para retornar a seu próprio serializador (ambos o <xref:System.Runtime.Serialization.NetDataContractSerializer>, o <xref:System.Runtime.Serialization.DataContractSerializer> com `preserveObjectReferences` definido como `true`, ou seu próprio custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).  
  
3. Antes de abrir o host de serviço ou criar um canal de cliente, remova existente <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> comportamento e plug-in a classe derivada personalizada que você criou nas etapas anteriores.  
  
 Para obter mais informações sobre os conceitos de serialização avançada, consulte [serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Consulte também

- [Usando a classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [Como: Habilitar o Streaming](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [Como: Criar um contrato de dados básicos para uma classe ou estrutura](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
