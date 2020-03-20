---
title: Especificando transferência de dados em contratos de serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: e68ca46f9d2c562491063ae66754c469dbe0898e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184434"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Especificando transferência de dados em contratos de serviço
A Windows Communication Foundation (WCF) pode ser considerada como uma infra-estrutura de mensagens. As operações de serviço podem receber mensagens, processá-las e enviar mensagens. As mensagens são descritas usando contratos de operação. Por exemplo, considere o seguinte contrato.  
  
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
  
 Aqui, `GetAirfare` a operação aceita uma `fromCity` mensagem com informações sobre e `toCity`, em seguida, retorna uma mensagem que contém um número.  
  
 Este tópico explica as várias maneiras pelas quais um contrato de operação pode descrever mensagens.  
  
## <a name="describing-messages-by-using-parameters"></a>Descrevendo mensagens usando parâmetros  
 A maneira mais simples de descrever uma mensagem é usar uma lista de parâmetros e o valor de retorno. No exemplo anterior, `fromCity` `toCity` os parâmetros e string foram usados para descrever a mensagem de solicitação, e o valor de retorno flutuante foi usado para descrever a mensagem de resposta. Se o valor de retorno sozinho não for suficiente para descrever uma mensagem de resposta, os parâmetros de saída podem ser usados. Por exemplo, a `fromCity` seguinte `toCity` operação tem e em sua mensagem de solicitação, e um número juntamente com uma moeda em sua mensagem de resposta:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Além disso, você pode usar parâmetros de referência para fazer uma parte do parâmetro tanto da solicitação quanto da mensagem de resposta. Os parâmetros devem ser de tipos que podem ser serializados (convertidos em XML). Por padrão, o WCF <xref:System.Runtime.Serialization.DataContractSerializer> usa um componente chamado classe para realizar essa conversão. A maioria dos `int`tipos `string` `float`primitivos `DateTime`(como , , e .) são apoiados. Os tipos definidos pelo usuário devem normalmente ter um contrato de dados. Para obter mais informações, consulte [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
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
  
 Ocasionalmente, `DataContractSerializer` o não é adequado para serializar seus tipos. O WCF suporta um mecanismo <xref:System.Xml.Serialization.XmlSerializer>de serialização alternativo, o , que você também pode usar para serializar parâmetros. O <xref:System.Xml.Serialization.XmlSerializer> permite que você use mais controle sobre o XML resultante usando atributos como o `XmlAttributeAttribute`. Para mudar para <xref:System.Xml.Serialization.XmlSerializer> usar o para uma operação específica <xref:System.ServiceModel.XmlSerializerFormatAttribute> ou para todo o serviço, aplique o atributo a uma operação ou a um serviço. Por exemplo:   
  
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
  
 Para obter mais informações, consulte [Usando a classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md). Lembre-se que mudar <xref:System.Xml.Serialization.XmlSerializer> manualmente para o como mostrado aqui não é recomendado a menos que você tenha razões específicas para fazê-lo conforme detalhado nesse tópico.  
  
 Para isolar nomes de parâmetros .NET <xref:System.ServiceModel.MessageParameterAttribute> de nomes de `Name` contratos, você pode usar o atributo e usar a propriedade para definir o nome do contrato. Por exemplo, o contrato de operação a seguir é equivalente ao primeiro exemplo neste tópico.  
  
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
 Uma mensagem de solicitação vazia pode ser descrita sem parâmetros de entrada ou referência. Por exemplo, em C#:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Por exemplo, no Visual Basic:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Uma mensagem de resposta vazia `void` pode ser descrita com um tipo de retorno e sem parâmetros de saída ou referência. Por exemplo, em:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 Isto é diferente de uma operação unidirecional, como:  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 A `SetTemperatureStatus` operação retorna uma mensagem vazia. Ele pode retornar uma falha em vez disso se houver um problema no processamento da mensagem de entrada. A `SetLightbulbStatus` operação não devolve nada. Não há como comunicar uma condição de falha desta operação.  
  
## <a name="describing-messages-by-using-message-contracts"></a>Descrevendo mensagens usando contratos de mensagens  
 Você pode querer usar um único tipo para representar toda a mensagem. Embora seja possível usar um contrato de dados para esse fim, a maneira recomendada de fazer isso é usar um contrato de mensagem — isso evita níveis desnecessários de embrulho no XML resultante. Além disso, os contratos de mensagens permitem que você exerça mais controle sobre as mensagens resultantes. Por exemplo, você pode decidir quais informações devem estar no corpo da mensagem e quais devem estar nos cabeçalhos de mensagem. O exemplo a seguir mostra o uso de contratos de mensagem.  
  
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
  
 Para obter mais informações, consulte [Usando contratos de mensagem](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
 No exemplo anterior, <xref:System.Runtime.Serialization.DataContractSerializer> a classe ainda é usada por padrão. A <xref:System.Xml.Serialization.XmlSerializer> classe também pode ser usada com contratos de mensagens. Para isso, aplique <xref:System.ServiceModel.XmlSerializerFormatAttribute> o atributo à operação ou ao contrato <xref:System.Xml.Serialization.XmlSerializer> e use tipos compatíveis com a classe nos cabeçalhos de mensagem e membros do corpo.  
  
## <a name="describing-messages-by-using-streams"></a>Descrevendo mensagens usando fluxos  
 Outra maneira de descrever mensagens em <xref:System.IO.Stream> operações é usar a classe ou uma de suas classes derivadas em um contrato de operação ou como membro do corpo de contrato de mensagem (ele deve ser o único membro neste caso). Para mensagens recebidas, o `Stream`tipo deve ser — você não pode usar classes derivadas.  
  
 Em vez de invocar o serializador, o WCF recupera dados de um fluxo e os coloca diretamente em uma mensagem de saída, ou recupera dados de uma mensagem recebida e os coloca diretamente em um fluxo. A amostra a seguir mostra o uso de fluxos.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Você não `Stream` pode combinar e não transmitir dados em um único corpo de mensagem. Use um contrato de mensagem para colocar os dados extras em cabeçalhos de mensagem. O exemplo a seguir mostra o uso incorreto de fluxos na definição do contrato de operação.  
  
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
  
 A amostra a seguir mostra o uso correto dos fluxos ao definir um contrato de operação.  
  
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
  
 Para obter mais informações, consulte [Big Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>Usando a classe de mensagens  
 Para ter controle programático completo sobre mensagens enviadas <xref:System.ServiceModel.Channels.Message> ou recebidas, você pode usar a classe diretamente, como mostrado no código de exemplo a seguir.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Este é um cenário avançado, que é descrito em detalhes em [Usando a Classe de Mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>Descrevendo mensagens de falha  
 Além das mensagens descritas pelo valor de retorno e parâmetros de saída ou referência, qualquer operação que não seja unidirecional pode retornar pelo menos duas mensagens possíveis: sua mensagem de resposta normal e uma mensagem de falha. Considere o seguinte contrato de operação.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Esta operação pode retornar uma mensagem normal que contenha um `float` número ou uma mensagem de falha que contenha um código de falha e uma descrição. Você pode conseguir isso <xref:System.ServiceModel.FaultException> lançando um em sua implementação de serviço.  
  
 Você pode especificar mensagens de <xref:System.ServiceModel.FaultContractAttribute> falha possíveis adicionais usando o atributo. As falhas adicionais devem ser <xref:System.Runtime.Serialization.DataContractSerializer>serializáveis usando o , como mostrado no código de exemplo a seguir.  
  
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
  
 Essas falhas adicionais podem ser <xref:System.ServiceModel.FaultException%601> geradas jogando um do tipo de contrato de dados apropriado. Para obter mais informações, consulte [Manipulação de Exceções e Falhas](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
 Você não <xref:System.Xml.Serialization.XmlSerializer> pode usar a classe para descrever falhas. O <xref:System.ServiceModel.XmlSerializerFormatAttribute> não tem efeito sobre contratos de falha.  
  
## <a name="using-derived-types"></a>Usando tipos derivados  
 Você pode querer usar um tipo base em uma operação ou um contrato de mensagem e, em seguida, usar um tipo derivado ao invocar a operação. Neste caso, você deve <xref:System.ServiceModel.ServiceKnownTypeAttribute> usar o atributo ou algum mecanismo alternativo para permitir o uso de tipos derivados. Considere a seguinte operação.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 Assuma que `Book` `Magazine`dois tipos, e , derivam de `LibraryItem`. Para usar esses `IsLibraryItemAvailable` tipos na operação, você pode alterar a operação da seguinte forma:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Alternativamente, você pode <xref:System.Runtime.Serialization.KnownTypeAttribute> usar o <xref:System.Runtime.Serialization.DataContractSerializer> atributo quando o padrão estiver em uso, como mostrado no código de exemplo a seguir.  
  
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
  
 Você pode <xref:System.Xml.Serialization.XmlIncludeAttribute> usar o <xref:System.Xml.Serialization.XmlSerializer>atributo ao usar o .  
  
 Você pode <xref:System.ServiceModel.ServiceKnownTypeAttribute> aplicar o atributo a uma operação ou a todo o serviço. Ele aceita um tipo ou o nome do método para chamar para obter <xref:System.Runtime.Serialization.KnownTypeAttribute> uma lista de tipos conhecidos, assim como o atributo. Para obter mais informações, consulte [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Especificando o Uso e o Estilo  
 Ao descrever os serviços usando o Web Services Description Language (WSDL), os dois estilos comumente usados são A chamada de procedimento remoto (RPC). No estilo Documento, todo o corpo da mensagem é descrito usando o esquema, e o WSDL descreve as várias partes do corpo da mensagem, referindo-se a elementos dentro desse esquema. No estilo RPC, o WSDL refere-se a um tipo de esquema para cada parte da mensagem em vez de um elemento. Em alguns casos, você tem que selecionar manualmente um desses estilos. Você pode fazer isso <xref:System.ServiceModel.DataContractFormatAttribute> aplicando o `Style` atributo <xref:System.Runtime.Serialization.DataContractSerializer> e definindo a `Style` propriedade <xref:System.ServiceModel.XmlSerializerFormatAttribute> (quando o <xref:System.Xml.Serialization.XmlSerializer>está em uso), ou definindo o atributo (ao usar o ).  
  
 Além disso, <xref:System.Xml.Serialization.XmlSerializer> o suporte suporta duas formas de XML serializado: `Literal` e `Encoded`. `Literal`é a forma mais comumente aceita, e <xref:System.Runtime.Serialization.DataContractSerializer> é a única forma que os suportes suportam. `Encoded`é um formulário legado descrito na seção 5 da especificação SOAP, e não é recomendado para novos serviços. Para mudar `Encoded` para o `Use` modo, <xref:System.ServiceModel.XmlSerializerFormatAttribute> defina a propriedade no atributo para `Encoded`.  
  
 Na maioria dos casos, você não deve `Style` `Use` alterar as configurações padrão para as propriedades e.  
  
## <a name="controlling-the-serialization-process"></a>Controle do Processo de Serialização  
 Você pode fazer uma série de coisas para personalizar a forma como os dados são serializados.  
  
### <a name="changing-server-serialization-settings"></a>Alterando as configurações de serialização do servidor  
 Quando o <xref:System.Runtime.Serialization.DataContractSerializer> padrão está em uso, você pode controlar alguns aspectos do <xref:System.ServiceModel.ServiceBehaviorAttribute> processo de serialização no serviço aplicando o atributo ao serviço. Especificamente, você pode `MaxItemsInObjectGraph` usar a propriedade para definir a <xref:System.Runtime.Serialization.DataContractSerializer> cota que limita o número máximo de objetos que desserializa. Você pode `IgnoreExtensionDataObject` usar a propriedade para desativar o recurso de versão redonda. Para obter mais informações sobre cotas, confira [Considerações sobre segurança de dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Para obter mais informações sobre tropeços redondos, consulte [Contratos de dados compatíveis com o futuro](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
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
 Dois comportamentos estão disponíveis no <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> WCF, o e o <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> que são automaticamente conectados, dependendo de qual serializador está em uso para uma operação específica. Como esses comportamentos são aplicados automaticamente, você normalmente não precisa estar ciente deles.  
  
 No entanto, `DataContractSerializerOperationBehavior` o tem as `MaxItemsInObjectGraph` `IgnoreExtensionDataObject`propriedades que `DataContractSurrogate` você pode usar para personalizar o processo de serialização. As duas primeiras propriedades têm o mesmo significado discutido na seção anterior. Você pode `DataContractSurrogate` usar a propriedade para habilitar substitutos de contratos de dados, que são um mecanismo poderoso para personalizar e estender o processo de serialização. Para obter mais informações, consulte [Substitutos de Contratos de Dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
 Você pode `DataContractSerializerOperationBehavior` usar o para personalizar a serialização do cliente e do servidor. O exemplo a seguir `MaxItemsInObjectGraph` mostra como aumentar a cota no cliente.  
  
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
  
A seguir está o código equivalente no serviço, no caso auto-hospedado:
  
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
  
 No caso hospedado na Web, você `ServiceHost` deve criar uma nova classe derivada e usar uma fábrica de host de serviço para conectá-la.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Controlando configurações de serialização na configuração  
 E `MaxItemsInObjectGraph` `IgnoreExtensionDataObject` pode ser controlado através `dataContractSerializer` da configuração usando o endpoint ou o comportamento de serviço, como mostrado no exemplo a seguir.  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Serialização de tipo compartilhado, preservação de gráficos de objetos e serializadores personalizados  
 O <xref:System.Runtime.Serialization.DataContractSerializer> serializa usando nomes de contrato de dados e não nomes de tipo .NET. Isso é consistente com princípios de arquitetura orientados a serviços e permite um grande grau de flexibilidade — os tipos .NET podem mudar sem afetar o contrato de fio. Em casos raros, você pode querer serializar nomes reais do tipo .NET, introduzindo assim um acoplamento apertado entre o cliente e o servidor, semelhante à tecnologia de remoção .NET Framework. Esta não é uma prática recomendada, exceto em casos raros que geralmente ocorrem ao migrar para o WCF do .NET Framework remoting. Neste caso, você deve <xref:System.Runtime.Serialization.NetDataContractSerializer> usar a <xref:System.Runtime.Serialization.DataContractSerializer> classe em vez da classe.  
  
 O <xref:System.Runtime.Serialization.DataContractSerializer> normalmente serializa gráficos de objetos como árvores de objetos. Ou seja, se o mesmo objeto é referido mais de uma vez, ele é serializado mais de uma vez. Por exemplo, `PurchaseOrder` considere uma instância que tenha `billTo` `shipTo`dois campos de endereço tipo chamados e . Se ambos os campos estiverem definidos para a mesma instância de endereço, haverá duas instâncias de endereço idênticas após a serialização e a desserialização. Isso é feito porque não há uma maneira interoperável padrão de representar gráficos de objetos em XML (exceto para o padrão legado SOAP codificado disponível no <xref:System.Xml.Serialization.XmlSerializer>, como descrito na seção anterior em `Style` e `Use`). Serializar gráficos de objetos como árvores tem certas desvantagens, por exemplo, gráficos com referências circulares não podem ser serializados. Ocasionalmente, é necessário mudar para serialização de gráficos de objetos verdadeiros, mesmo que não seja interoperável. Isso pode ser feito <xref:System.Runtime.Serialization.DataContractSerializer> usando o `preserveObjectReferences` construído com `true`o parâmetro definido para .  
  
 Ocasionalmente, os serializadores embutidos não são suficientes para o seu cenário. Na maioria dos casos, <xref:System.Runtime.Serialization.XmlObjectSerializer> você ainda pode usar <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer> abstração da qual tanto o e o derivam.  
  
 Os três casos anteriores (preservação do tipo.NET, preservação de gráficos de objetos e serialização completamente personalizada) `XmlObjectSerializer`exigem que um serializador personalizado seja conectado. Para fazer isso, execute estas etapas:  
  
1. Escreva seu próprio comportamento <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>derivado do .  
  
2. Anular os `CreateSerializer` dois métodos para devolver seu <xref:System.Runtime.Serialization.NetDataContractSerializer>próprio <xref:System.Runtime.Serialization.DataContractSerializer> serializador `true`(seja o <xref:System.Runtime.Serialization.XmlObjectSerializer>, o com `preserveObjectReferences` set para , ou seu próprio costume ).  
  
3. Antes de abrir o host de serviço ou <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> criar um canal cliente, remova o comportamento existente e conecte a classe derivada personalizada que você criou nas etapas anteriores.  
  
 Para obter mais informações sobre conceitos avançados de serialização, consulte [Serialização e Desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Confira também

- [Usando a classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [Como habilitar transmissão](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [Como criar um contrato de dados básicos para uma classe ou estrutura](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
