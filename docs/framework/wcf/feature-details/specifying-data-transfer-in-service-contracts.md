---
title: Especificando transferência de dados em contratos de serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: 7423a44f7779c8e4ef75fc68e33eeb4ac48a660a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Especificando transferência de dados em contratos de serviço
O Windows Communication Foundation (WCF) pode ser pensada como uma infraestrutura de mensagens. Operações de serviço podem receber mensagens, processá-los e enviar mensagens. As mensagens são descritas usando contratos de operação. Por exemplo, considere o seguinte contrato.  
  
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
  
 Este tópico explica as várias maneiras em que um contrato de operação pode descrever mensagens.  
  
## <a name="describing-messages-by-using-parameters"></a>Descrevendo mensagens usando parâmetros  
 A maneira mais simples para descrever uma mensagem é usar uma lista de parâmetros e o valor de retorno. No exemplo anterior, o `fromCity` e `toCity` parâmetros de cadeia de caracteres que foram usados para descrever a mensagem de solicitação e o valor de retorno de float foi usado para descrever a mensagem de resposta. Se o valor de retorno sozinho não é suficiente para descrever uma mensagem de resposta, os parâmetros de saída podem ser usados. Por exemplo, a seguinte operação tem `fromCity` e `toCity` em sua mensagem de solicitação e um número junto com uma moeda na sua mensagem de resposta:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Além disso, você pode usar parâmetros de referência para fazer com que uma parte do parâmetro da solicitação e a mensagem de resposta. Os parâmetros devem ser de tipos que podem ser serializados (convertidos em XML). Por padrão, o WCF usa um componente chamado de <xref:System.Runtime.Serialization.DataContractSerializer> classe para realizar essa conversão. Tipos primitivos mais (como `int`, `string`, `float`, e `DateTime`.) têm suporte. Tipos definidos pelo usuário normalmente devem ter um contrato de dados. Para obter mais informações, consulte [usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
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
  
 Ocasionalmente, o `DataContractSerializer` não é adequado para serializar seus tipos. O WCF oferece suporte a um mecanismo de serialização alternativo, o <xref:System.Xml.Serialization.XmlSerializer>, que também pode ser usada para serializar os parâmetros. O <xref:System.Xml.Serialization.XmlSerializer> permite que você use mais controle sobre o XML resultante usando atributos, como o `XmlAttributeAttribute`. Para passar a usar o <xref:System.Xml.Serialization.XmlSerializer> para uma operação específica ou para todo o serviço, aplicar o <xref:System.ServiceModel.XmlSerializerFormatAttribute> de atributo para uma operação ou um serviço. Por exemplo:  
  
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
  
 Para obter mais informações, consulte [usando a classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md). Lembre-se de que alternar manualmente para o <xref:System.Xml.Serialization.XmlSerializer> conforme mostrado aqui não é recomendada a menos que você tenha motivos específicos para fazer assim como detalhado no tópico.  
  
 Para isolar os nomes de parâmetro .NET de nomes de contrato, você pode usar o <xref:System.ServiceModel.MessageParameterAttribute> de atributos e usar o `Name` propriedade para definir o nome do contrato. Por exemplo, o seguinte contrato de operação é equivalente ao primeiro exemplo neste tópico.  
  
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
 Uma mensagem de solicitação vazio pode ser descrita por não ter nenhum parâmetro de entrada ou referência. Por exemplo em c#:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Por exemplo, no VB:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Uma mensagem de resposta vazia pode ser descrita por ter uma `void` tipo de retorno e parâmetros de saída ou referência. Por exemplo, em:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 Isso é diferente de uma operação unidirecional, como:  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 O `SetTemperatureStatus` operação retorna uma mensagem vazia. Pode retornar uma falha em vez disso, se houver um problema ao processar a mensagem de entrada. O `SetLightbulbStatus` operação não retorna nada. Não há nenhuma maneira de comunicar-se uma condição de falha desta operação.  
  
## <a name="describing-messages-by-using-message-contracts"></a>Descrevendo mensagens por meio de contratos de mensagem  
 Você talvez queira usar um único tipo para representar a mensagem inteira. Embora seja possível usar um contrato de dados para essa finalidade, a maneira recomendada de fazer isso é usar um contrato de mensagem — Isso evita o desnecessários níveis de encapsulamento no XML resultante. Além disso, contratos de mensagem permitem que você tenha mais controle sobre mensagens resultantes. Por exemplo, você pode decidir quais informações devem estar no corpo da mensagem e que deve ser nos cabeçalhos da mensagem. O exemplo a seguir mostra o uso de contratos de mensagem.  
  
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
  
 Para obter mais informações, consulte [usando contratos de mensagem](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
 No exemplo anterior, a <xref:System.Runtime.Serialization.DataContractSerializer> classe ainda é usada por padrão. O <xref:System.Xml.Serialization.XmlSerializer> classe também pode ser usada com contratos de mensagem. Para fazer isso, aplique a <xref:System.ServiceModel.XmlSerializerFormatAttribute> de atributo para a operação ou o contrato e usar tipos compatíveis com o <xref:System.Xml.Serialization.XmlSerializer> classe nos cabeçalhos de mensagem e membros de corpo.  
  
## <a name="describing-messages-by-using-streams"></a>Descrevendo mensagens usando fluxos  
 Outra maneira de descrever as mensagens em operações é usar o <xref:System.IO.Stream> classe ou uma de suas classes derivadas em um contrato de operação ou como um membro de corpo de contrato de mensagem (deve ser o único membro nesse caso). Mensagens de entrada, o tipo deve ser `Stream`— não é possível usar as classes derivadas.  
  
 Em vez de invocar o serializador, WCF recupera dados de um fluxo e coloca diretamente em uma mensagem de saída, ou recupera dados de uma mensagem de entrada e coloca-o diretamente em um fluxo. O exemplo a seguir mostra o uso de fluxos.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Não é possível combinar `Stream` e não são de fluxo dados no corpo da mensagem única. Use um contrato de mensagem para colocar os dados extras em cabeçalhos de mensagem. O exemplo a seguir mostra o uso incorreto de fluxos quando o contrato de operação.  
  
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
 Para ter total controle programático sobre mensagens enviadas ou recebidas, você pode usar o <xref:System.ServiceModel.Channels.Message> classe diretamente, conforme mostrado no código de exemplo a seguir.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Este é um cenário avançado, que é descrito em detalhes em [usando a classe de mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>Que descreve mensagens de falha  
 As mensagens que são descritas pelo valor de retorno e parâmetros de saída ou referência, além de qualquer operação que não é unidirecional pode retornar pelo menos duas mensagens possíveis: a mensagem de resposta normal e uma mensagem de falha. Considere o seguinte contrato de operação.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Esta operação ou pode retornar uma mensagem normal que contém um `float` número ou uma mensagem de falha que contém um código de falha e uma descrição. Você pode fazer isso, lançando um <xref:System.ServiceModel.FaultException> em sua implementação de serviço.  
  
 Você pode especificar as mensagens de falha possíveis adicionais usando o <xref:System.ServiceModel.FaultContractAttribute> atributo. As falhas adicionais devem ser serializável usando o <xref:System.Runtime.Serialization.DataContractSerializer>, conforme mostrado no código de exemplo a seguir.  
  
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
  
 Essas falhas adicionais podem ser geradas, lançando um <xref:System.ServiceModel.FaultException%601> do tipo de contrato de dados apropriado. Para obter mais informações, consulte [tratamento de exceções e falhas](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
 Não é possível usar o <xref:System.Xml.Serialization.XmlSerializer> classe para descrever a falhas. O <xref:System.ServiceModel.XmlSerializerFormatAttribute> não tem efeito sobre contratos de falha.  
  
## <a name="using-derived-types"></a>Usando tipos derivados  
 Você talvez queira usar um tipo base em uma operação ou um contrato de mensagem e, em seguida, usar um tipo derivado quando realmente invocar a operação. Nesse caso, você deve usar o a <xref:System.ServiceModel.ServiceKnownTypeAttribute> atributo ou um mecanismo alternativo para permitir o uso de tipos derivados. Considere a seguinte operação.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 Suponha que dois tipos, `Book` e `Magazine`, derivam `LibraryItem`. Para usar estes tipos de `IsLibraryItemAvailable` operação, você pode alterar a operação da seguinte maneira:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Como alternativa, você pode usar o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo quando o padrão <xref:System.Runtime.Serialization.DataContractSerializer> está em uso, conforme mostrado no código de exemplo a seguir.  
  
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
  
 Você pode aplicar o <xref:System.ServiceModel.ServiceKnownTypeAttribute> atributo a uma operação ou todo o serviço. Ele aceita um tipo ou o nome do método para chamar para obter uma lista de tipos conhecidos, como o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo. Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Especificando o uso e o estilo  
 Ao descrever serviços usando WSDL Web Services Description Language (), as duas normalmente estilos usados são documento e a chamada de procedimento remoto (RPC). No estilo de documento, o corpo da mensagem inteira é descrito usando o esquema e o WSDL descreve as várias partes de corpo de mensagem referindo-se aos elementos no esquema. No estilo RPC, o WSDL se refere a um tipo de esquema para cada parte da mensagem em vez de um elemento. Em alguns casos, você precisa selecionar manualmente um desses estilos. Você pode fazer isso aplicando a <xref:System.ServiceModel.DataContractFormatAttribute> atributo e configuração o `Style` propriedade (quando o <xref:System.Runtime.Serialization.DataContractSerializer> está em uso), ou definindo `Style` no <xref:System.ServiceModel.XmlSerializerFormatAttribute> atributo (ao usar o <xref:System.Xml.Serialization.XmlSerializer>).  
  
 Além disso, o <xref:System.Xml.Serialization.XmlSerializer> dá suporte a duas formas de XML serializado: `Literal` e `Encoded`. `Literal` é o mais comumente aceito e é a única forma de <xref:System.Runtime.Serialization.DataContractSerializer> oferece suporte. `Encoded` é uma forma herdada descrita na seção 5 da especificação de SOAP e não é recomendado para novos serviços. Para alternar para `Encoded` modo, defina o `Use` propriedade o <xref:System.ServiceModel.XmlSerializerFormatAttribute> atributo `Encoded`.  
  
 Na maioria dos casos, você não deve alterar as configurações padrão para o `Style` e `Use` propriedades.  
  
## <a name="controlling-the-serialization-process"></a>Controlando o processo de serialização  
 Você pode fazer algumas coisas para personalizar a maneira como os dados são serializados.  
  
### <a name="changing-server-serialization-settings"></a>Alterando as definições de serialização do servidor  
 Quando o padrão <xref:System.Runtime.Serialization.DataContractSerializer> está em uso, você pode controlar alguns aspectos do processo de serialização no serviço aplicando o <xref:System.ServiceModel.ServiceBehaviorAttribute> de atributo para o serviço. Especificamente, você pode usar o `MaxItemsInObjectGraph` propriedade para definir a cota que limita o número máximo de objetos de <xref:System.Runtime.Serialization.DataContractSerializer> desserializa. Você pode usar o `IgnoreExtensionDataObject` propriedade para desativar o recurso de controle de versão de ciclo. Para obter mais informações sobre cotas, consulte [considerações de segurança para dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Para obter mais informações sobre o ciclo, consulte [contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
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
 Dois comportamentos estão disponíveis no WCF, o <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> e <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> que estão conectados automaticamente dependendo de qual serializador está em uso para uma operação específica. Como esses comportamentos são aplicados automaticamente, você normalmente não precisa estar ciente delas.  
  
 No entanto, o `DataContractSerializerOperationBehavior` tem o `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, e `DataContractSurrogate` propriedades que você pode usar para personalizar o processo de serialização. As duas primeiras propriedades têm o mesmo significado conforme discutido na seção anterior. Você pode usar o `DataContractSurrogate` propriedade para habilitar substitutos de contrato de dados, que são um mecanismo eficiente para personalizar e estender o processo de serialização. Para obter mais informações, consulte [substitutos de contrato de dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
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
  
 A seguir está o código equivalente do serviço, no caso de auto-hospedado.  
  
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
  
 No caso da Web hospedado, você deve criar um novo `ServiceHost` classe derivada e usar uma fábrica de host de serviço para conectá-lo.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Controlando a serialização de configurações em configuração  
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
            <endpoint address=http://example.com/myservice  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""   
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Serialização de tipo, preservação de gráfico de objeto e serializadores personalizados compartilhados  
 O <xref:System.Runtime.Serialization.DataContractSerializer> serializa usando nomes de contrato de dados e nomes de tipo do .NET. Isso é consistente com os princípios de arquitetura orientada a serviços e possibilita um alto grau de flexibilidade — podem alterar os tipos de .NET sem afetar o contrato de transmissão. Em casos raros, pode ser serializado nomes de tipo .NET reais, assim, apresentando uma grande união entre o cliente e o servidor, como a tecnologia de comunicação remota do .NET Framework. Isso não é uma prática recomendada, exceto em casos raros, que normalmente ocorrem quando migrar para o WCF de comunicação remota do .NET Framework. Nesse caso, você deve usar o <xref:System.Runtime.Serialization.NetDataContractSerializer> classe o <xref:System.Runtime.Serialization.DataContractSerializer> classe.  
  
 O <xref:System.Runtime.Serialization.DataContractSerializer> normalmente serializa os gráficos de objeto como árvores de objeto. Ou seja, se o mesmo objeto é referenciado mais de uma vez, ele é serializado mais de uma vez. Por exemplo, considere um `PurchaseOrder` instância que tem dois campos de tipo de endereço chamado `billTo` e `shipTo`. Se ambos os campos são definidos para a mesma instância de endereço, há duas instâncias idênticas de endereço após a serialização e desserialização. Isso é feito porque não há nenhuma maneira interoperável padrão para representar os gráficos de objeto em XML (exceto para o padrão SOAP codificado herdado disponível no <xref:System.Xml.Serialization.XmlSerializer>, conforme descrito na seção anterior no `Style` e `Use`). Serializando gráficos de objeto como árvores tem determinadas desvantagens, por exemplo, os gráficos com referências circulares não podem ser serializados. Ocasionalmente, é necessário alternar para a serialização do gráfico de objeto verdadeira, embora não seja interoperável. Isso pode ser feito usando o <xref:System.Runtime.Serialization.DataContractSerializer> construído com o `preserveObjectReferences` parâmetro definido como `true`.  
  
 Ocasionalmente, os serializadores internos não são suficientes para seu cenário. Na maioria dos casos, você ainda pode usar o <xref:System.Runtime.Serialization.XmlObjectSerializer> abstração do qual o <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.NetDataContractSerializer> derivar.  
  
 Os três casos anteriores (preservação de tipo do .NET, preservação de gráfico de objeto e totalmente personalizada `XmlObjectSerializer`-com base em serialização) exigem um serializador personalizado ser conectado. Para fazer isso, execute estas etapas:  
  
1.  Gravar seu próprio comportamento derivando de <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.  
  
2.  Substituir os dois `CreateSerializer` métodos para retornar o seu próprio serializador (ou o <xref:System.Runtime.Serialization.NetDataContractSerializer>, o <xref:System.Runtime.Serialization.DataContractSerializer> com `preserveObjectReferences` definida como `true`, ou seu próprio personalizado <xref:System.Runtime.Serialization.XmlObjectSerializer>).  
  
3.  Antes de abrir o host de serviço ou criar um canal de cliente, remova existente <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> comportamento e plug-in a classe personalizada derivada que você criou nas etapas anteriores.  
  
 Para obter mais informações sobre conceitos de serialização avançada, consulte [serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Consulte também  
 [Usando a classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 [Como habilitar o streaming](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)  
 [Como criar um contrato de dados básicos para uma classe ou estrutura](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
