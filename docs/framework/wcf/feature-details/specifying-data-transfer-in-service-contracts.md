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
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="434c3-102">Especificando transferência de dados em contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="434c3-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="434c3-103">A Windows Communication Foundation (WCF) pode ser considerada como uma infra-estrutura de mensagens.</span><span class="sxs-lookup"><span data-stu-id="434c3-103">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="434c3-104">As operações de serviço podem receber mensagens, processá-las e enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="434c3-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="434c3-105">As mensagens são descritas usando contratos de operação.</span><span class="sxs-lookup"><span data-stu-id="434c3-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="434c3-106">Por exemplo, considere o seguinte contrato.</span><span class="sxs-lookup"><span data-stu-id="434c3-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="434c3-107">Aqui, `GetAirfare` a operação aceita uma `fromCity` mensagem com informações sobre e `toCity`, em seguida, retorna uma mensagem que contém um número.</span><span class="sxs-lookup"><span data-stu-id="434c3-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="434c3-108">Este tópico explica as várias maneiras pelas quais um contrato de operação pode descrever mensagens.</span><span class="sxs-lookup"><span data-stu-id="434c3-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="434c3-109">Descrevendo mensagens usando parâmetros</span><span class="sxs-lookup"><span data-stu-id="434c3-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="434c3-110">A maneira mais simples de descrever uma mensagem é usar uma lista de parâmetros e o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="434c3-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="434c3-111">No exemplo anterior, `fromCity` `toCity` os parâmetros e string foram usados para descrever a mensagem de solicitação, e o valor de retorno flutuante foi usado para descrever a mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="434c3-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="434c3-112">Se o valor de retorno sozinho não for suficiente para descrever uma mensagem de resposta, os parâmetros de saída podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="434c3-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="434c3-113">Por exemplo, a `fromCity` seguinte `toCity` operação tem e em sua mensagem de solicitação, e um número juntamente com uma moeda em sua mensagem de resposta:</span><span class="sxs-lookup"><span data-stu-id="434c3-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="434c3-114">Além disso, você pode usar parâmetros de referência para fazer uma parte do parâmetro tanto da solicitação quanto da mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="434c3-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="434c3-115">Os parâmetros devem ser de tipos que podem ser serializados (convertidos em XML).</span><span class="sxs-lookup"><span data-stu-id="434c3-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="434c3-116">Por padrão, o WCF <xref:System.Runtime.Serialization.DataContractSerializer> usa um componente chamado classe para realizar essa conversão.</span><span class="sxs-lookup"><span data-stu-id="434c3-116">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="434c3-117">A maioria dos `int`tipos `string` `float`primitivos `DateTime`(como , , e .) são apoiados.</span><span class="sxs-lookup"><span data-stu-id="434c3-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="434c3-118">Os tipos definidos pelo usuário devem normalmente ter um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="434c3-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="434c3-119">Para obter mais informações, consulte [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="434c3-119">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="434c3-120">Ocasionalmente, `DataContractSerializer` o não é adequado para serializar seus tipos.</span><span class="sxs-lookup"><span data-stu-id="434c3-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="434c3-121">O WCF suporta um mecanismo <xref:System.Xml.Serialization.XmlSerializer>de serialização alternativo, o , que você também pode usar para serializar parâmetros.</span><span class="sxs-lookup"><span data-stu-id="434c3-121">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="434c3-122">O <xref:System.Xml.Serialization.XmlSerializer> permite que você use mais controle sobre o XML resultante usando atributos como o `XmlAttributeAttribute`.</span><span class="sxs-lookup"><span data-stu-id="434c3-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="434c3-123">Para mudar para <xref:System.Xml.Serialization.XmlSerializer> usar o para uma operação específica <xref:System.ServiceModel.XmlSerializerFormatAttribute> ou para todo o serviço, aplique o atributo a uma operação ou a um serviço.</span><span class="sxs-lookup"><span data-stu-id="434c3-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="434c3-124">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="434c3-124">For example:</span></span>  
  
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
  
 <span data-ttu-id="434c3-125">Para obter mais informações, consulte [Usando a classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="434c3-125">For more information, see [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="434c3-126">Lembre-se que mudar <xref:System.Xml.Serialization.XmlSerializer> manualmente para o como mostrado aqui não é recomendado a menos que você tenha razões específicas para fazê-lo conforme detalhado nesse tópico.</span><span class="sxs-lookup"><span data-stu-id="434c3-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="434c3-127">Para isolar nomes de parâmetros .NET <xref:System.ServiceModel.MessageParameterAttribute> de nomes de `Name` contratos, você pode usar o atributo e usar a propriedade para definir o nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="434c3-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="434c3-128">Por exemplo, o contrato de operação a seguir é equivalente ao primeiro exemplo neste tópico.</span><span class="sxs-lookup"><span data-stu-id="434c3-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="434c3-129">Descrevendo mensagens vazias</span><span class="sxs-lookup"><span data-stu-id="434c3-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="434c3-130">Uma mensagem de solicitação vazia pode ser descrita sem parâmetros de entrada ou referência.</span><span class="sxs-lookup"><span data-stu-id="434c3-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="434c3-131">Por exemplo, em C#:</span><span class="sxs-lookup"><span data-stu-id="434c3-131">For example, in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="434c3-132">Por exemplo, no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="434c3-132">For example, in Visual Basic:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="434c3-133">Uma mensagem de resposta vazia `void` pode ser descrita com um tipo de retorno e sem parâmetros de saída ou referência.</span><span class="sxs-lookup"><span data-stu-id="434c3-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="434c3-134">Por exemplo, em:</span><span class="sxs-lookup"><span data-stu-id="434c3-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="434c3-135">Isto é diferente de uma operação unidirecional, como:</span><span class="sxs-lookup"><span data-stu-id="434c3-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="434c3-136">A `SetTemperatureStatus` operação retorna uma mensagem vazia.</span><span class="sxs-lookup"><span data-stu-id="434c3-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="434c3-137">Ele pode retornar uma falha em vez disso se houver um problema no processamento da mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="434c3-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="434c3-138">A `SetLightbulbStatus` operação não devolve nada.</span><span class="sxs-lookup"><span data-stu-id="434c3-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="434c3-139">Não há como comunicar uma condição de falha desta operação.</span><span class="sxs-lookup"><span data-stu-id="434c3-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="434c3-140">Descrevendo mensagens usando contratos de mensagens</span><span class="sxs-lookup"><span data-stu-id="434c3-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="434c3-141">Você pode querer usar um único tipo para representar toda a mensagem.</span><span class="sxs-lookup"><span data-stu-id="434c3-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="434c3-142">Embora seja possível usar um contrato de dados para esse fim, a maneira recomendada de fazer isso é usar um contrato de mensagem — isso evita níveis desnecessários de embrulho no XML resultante.</span><span class="sxs-lookup"><span data-stu-id="434c3-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="434c3-143">Além disso, os contratos de mensagens permitem que você exerça mais controle sobre as mensagens resultantes.</span><span class="sxs-lookup"><span data-stu-id="434c3-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="434c3-144">Por exemplo, você pode decidir quais informações devem estar no corpo da mensagem e quais devem estar nos cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="434c3-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="434c3-145">O exemplo a seguir mostra o uso de contratos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="434c3-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 <span data-ttu-id="434c3-146">Para obter mais informações, consulte [Usando contratos de mensagem](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="434c3-146">For more information, see [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="434c3-147">No exemplo anterior, <xref:System.Runtime.Serialization.DataContractSerializer> a classe ainda é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="434c3-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="434c3-148">A <xref:System.Xml.Serialization.XmlSerializer> classe também pode ser usada com contratos de mensagens.</span><span class="sxs-lookup"><span data-stu-id="434c3-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="434c3-149">Para isso, aplique <xref:System.ServiceModel.XmlSerializerFormatAttribute> o atributo à operação ou ao contrato <xref:System.Xml.Serialization.XmlSerializer> e use tipos compatíveis com a classe nos cabeçalhos de mensagem e membros do corpo.</span><span class="sxs-lookup"><span data-stu-id="434c3-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="434c3-150">Descrevendo mensagens usando fluxos</span><span class="sxs-lookup"><span data-stu-id="434c3-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="434c3-151">Outra maneira de descrever mensagens em <xref:System.IO.Stream> operações é usar a classe ou uma de suas classes derivadas em um contrato de operação ou como membro do corpo de contrato de mensagem (ele deve ser o único membro neste caso).</span><span class="sxs-lookup"><span data-stu-id="434c3-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="434c3-152">Para mensagens recebidas, o `Stream`tipo deve ser — você não pode usar classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="434c3-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="434c3-153">Em vez de invocar o serializador, o WCF recupera dados de um fluxo e os coloca diretamente em uma mensagem de saída, ou recupera dados de uma mensagem recebida e os coloca diretamente em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="434c3-153">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="434c3-154">A amostra a seguir mostra o uso de fluxos.</span><span class="sxs-lookup"><span data-stu-id="434c3-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="434c3-155">Você não `Stream` pode combinar e não transmitir dados em um único corpo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="434c3-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="434c3-156">Use um contrato de mensagem para colocar os dados extras em cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="434c3-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="434c3-157">O exemplo a seguir mostra o uso incorreto de fluxos na definição do contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="434c3-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="434c3-158">A amostra a seguir mostra o uso correto dos fluxos ao definir um contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="434c3-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 <span data-ttu-id="434c3-159">Para obter mais informações, consulte [Big Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="434c3-159">For more information, see [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="434c3-160">Usando a classe de mensagens</span><span class="sxs-lookup"><span data-stu-id="434c3-160">Using the Message Class</span></span>  
 <span data-ttu-id="434c3-161">Para ter controle programático completo sobre mensagens enviadas <xref:System.ServiceModel.Channels.Message> ou recebidas, você pode usar a classe diretamente, como mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="434c3-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="434c3-162">Este é um cenário avançado, que é descrito em detalhes em [Usando a Classe de Mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="434c3-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="434c3-163">Descrevendo mensagens de falha</span><span class="sxs-lookup"><span data-stu-id="434c3-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="434c3-164">Além das mensagens descritas pelo valor de retorno e parâmetros de saída ou referência, qualquer operação que não seja unidirecional pode retornar pelo menos duas mensagens possíveis: sua mensagem de resposta normal e uma mensagem de falha.</span><span class="sxs-lookup"><span data-stu-id="434c3-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="434c3-165">Considere o seguinte contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="434c3-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="434c3-166">Esta operação pode retornar uma mensagem normal que contenha um `float` número ou uma mensagem de falha que contenha um código de falha e uma descrição.</span><span class="sxs-lookup"><span data-stu-id="434c3-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="434c3-167">Você pode conseguir isso <xref:System.ServiceModel.FaultException> lançando um em sua implementação de serviço.</span><span class="sxs-lookup"><span data-stu-id="434c3-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="434c3-168">Você pode especificar mensagens de <xref:System.ServiceModel.FaultContractAttribute> falha possíveis adicionais usando o atributo.</span><span class="sxs-lookup"><span data-stu-id="434c3-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="434c3-169">As falhas adicionais devem ser <xref:System.Runtime.Serialization.DataContractSerializer>serializáveis usando o , como mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="434c3-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="434c3-170">Essas falhas adicionais podem ser <xref:System.ServiceModel.FaultException%601> geradas jogando um do tipo de contrato de dados apropriado.</span><span class="sxs-lookup"><span data-stu-id="434c3-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="434c3-171">Para obter mais informações, consulte [Manipulação de Exceções e Falhas](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="434c3-171">For more information, see [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="434c3-172">Você não <xref:System.Xml.Serialization.XmlSerializer> pode usar a classe para descrever falhas.</span><span class="sxs-lookup"><span data-stu-id="434c3-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="434c3-173">O <xref:System.ServiceModel.XmlSerializerFormatAttribute> não tem efeito sobre contratos de falha.</span><span class="sxs-lookup"><span data-stu-id="434c3-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="434c3-174">Usando tipos derivados</span><span class="sxs-lookup"><span data-stu-id="434c3-174">Using Derived Types</span></span>  
 <span data-ttu-id="434c3-175">Você pode querer usar um tipo base em uma operação ou um contrato de mensagem e, em seguida, usar um tipo derivado ao invocar a operação.</span><span class="sxs-lookup"><span data-stu-id="434c3-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="434c3-176">Neste caso, você deve <xref:System.ServiceModel.ServiceKnownTypeAttribute> usar o atributo ou algum mecanismo alternativo para permitir o uso de tipos derivados.</span><span class="sxs-lookup"><span data-stu-id="434c3-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="434c3-177">Considere a seguinte operação.</span><span class="sxs-lookup"><span data-stu-id="434c3-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="434c3-178">Assuma que `Book` `Magazine`dois tipos, e , derivam de `LibraryItem`.</span><span class="sxs-lookup"><span data-stu-id="434c3-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="434c3-179">Para usar esses `IsLibraryItemAvailable` tipos na operação, você pode alterar a operação da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="434c3-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="434c3-180">Alternativamente, você pode <xref:System.Runtime.Serialization.KnownTypeAttribute> usar o <xref:System.Runtime.Serialization.DataContractSerializer> atributo quando o padrão estiver em uso, como mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="434c3-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="434c3-181">Você pode <xref:System.Xml.Serialization.XmlIncludeAttribute> usar o <xref:System.Xml.Serialization.XmlSerializer>atributo ao usar o .</span><span class="sxs-lookup"><span data-stu-id="434c3-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="434c3-182">Você pode <xref:System.ServiceModel.ServiceKnownTypeAttribute> aplicar o atributo a uma operação ou a todo o serviço.</span><span class="sxs-lookup"><span data-stu-id="434c3-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="434c3-183">Ele aceita um tipo ou o nome do método para chamar para obter <xref:System.Runtime.Serialization.KnownTypeAttribute> uma lista de tipos conhecidos, assim como o atributo.</span><span class="sxs-lookup"><span data-stu-id="434c3-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="434c3-184">Para obter mais informações, consulte [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="434c3-184">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="434c3-185">Especificando o Uso e o Estilo</span><span class="sxs-lookup"><span data-stu-id="434c3-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="434c3-186">Ao descrever os serviços usando o Web Services Description Language (WSDL), os dois estilos comumente usados são A chamada de procedimento remoto (RPC).</span><span class="sxs-lookup"><span data-stu-id="434c3-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="434c3-187">No estilo Documento, todo o corpo da mensagem é descrito usando o esquema, e o WSDL descreve as várias partes do corpo da mensagem, referindo-se a elementos dentro desse esquema.</span><span class="sxs-lookup"><span data-stu-id="434c3-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="434c3-188">No estilo RPC, o WSDL refere-se a um tipo de esquema para cada parte da mensagem em vez de um elemento.</span><span class="sxs-lookup"><span data-stu-id="434c3-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="434c3-189">Em alguns casos, você tem que selecionar manualmente um desses estilos.</span><span class="sxs-lookup"><span data-stu-id="434c3-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="434c3-190">Você pode fazer isso <xref:System.ServiceModel.DataContractFormatAttribute> aplicando o `Style` atributo <xref:System.Runtime.Serialization.DataContractSerializer> e definindo a `Style` propriedade <xref:System.ServiceModel.XmlSerializerFormatAttribute> (quando o <xref:System.Xml.Serialization.XmlSerializer>está em uso), ou definindo o atributo (ao usar o ).</span><span class="sxs-lookup"><span data-stu-id="434c3-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="434c3-191">Além disso, <xref:System.Xml.Serialization.XmlSerializer> o suporte suporta duas formas de XML serializado: `Literal` e `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="434c3-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="434c3-192">`Literal`é a forma mais comumente aceita, e <xref:System.Runtime.Serialization.DataContractSerializer> é a única forma que os suportes suportam.</span><span class="sxs-lookup"><span data-stu-id="434c3-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="434c3-193">`Encoded`é um formulário legado descrito na seção 5 da especificação SOAP, e não é recomendado para novos serviços.</span><span class="sxs-lookup"><span data-stu-id="434c3-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="434c3-194">Para mudar `Encoded` para o `Use` modo, <xref:System.ServiceModel.XmlSerializerFormatAttribute> defina a propriedade no atributo para `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="434c3-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="434c3-195">Na maioria dos casos, você não deve `Style` `Use` alterar as configurações padrão para as propriedades e.</span><span class="sxs-lookup"><span data-stu-id="434c3-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="434c3-196">Controle do Processo de Serialização</span><span class="sxs-lookup"><span data-stu-id="434c3-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="434c3-197">Você pode fazer uma série de coisas para personalizar a forma como os dados são serializados.</span><span class="sxs-lookup"><span data-stu-id="434c3-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="434c3-198">Alterando as configurações de serialização do servidor</span><span class="sxs-lookup"><span data-stu-id="434c3-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="434c3-199">Quando o <xref:System.Runtime.Serialization.DataContractSerializer> padrão está em uso, você pode controlar alguns aspectos do <xref:System.ServiceModel.ServiceBehaviorAttribute> processo de serialização no serviço aplicando o atributo ao serviço.</span><span class="sxs-lookup"><span data-stu-id="434c3-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="434c3-200">Especificamente, você pode `MaxItemsInObjectGraph` usar a propriedade para definir a <xref:System.Runtime.Serialization.DataContractSerializer> cota que limita o número máximo de objetos que desserializa.</span><span class="sxs-lookup"><span data-stu-id="434c3-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="434c3-201">Você pode `IgnoreExtensionDataObject` usar a propriedade para desativar o recurso de versão redonda.</span><span class="sxs-lookup"><span data-stu-id="434c3-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="434c3-202">Para obter mais informações sobre cotas, confira [Considerações sobre segurança de dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="434c3-202">For more information about quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> <span data-ttu-id="434c3-203">Para obter mais informações sobre tropeços redondos, consulte [Contratos de dados compatíveis com o futuro](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="434c3-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="434c3-204">Comportamentos de serialização</span><span class="sxs-lookup"><span data-stu-id="434c3-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="434c3-205">Dois comportamentos estão disponíveis no <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> WCF, o e o <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> que são automaticamente conectados, dependendo de qual serializador está em uso para uma operação específica.</span><span class="sxs-lookup"><span data-stu-id="434c3-205">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="434c3-206">Como esses comportamentos são aplicados automaticamente, você normalmente não precisa estar ciente deles.</span><span class="sxs-lookup"><span data-stu-id="434c3-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="434c3-207">No entanto, `DataContractSerializerOperationBehavior` o tem as `MaxItemsInObjectGraph` `IgnoreExtensionDataObject`propriedades que `DataContractSurrogate` você pode usar para personalizar o processo de serialização.</span><span class="sxs-lookup"><span data-stu-id="434c3-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="434c3-208">As duas primeiras propriedades têm o mesmo significado discutido na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="434c3-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="434c3-209">Você pode `DataContractSurrogate` usar a propriedade para habilitar substitutos de contratos de dados, que são um mecanismo poderoso para personalizar e estender o processo de serialização.</span><span class="sxs-lookup"><span data-stu-id="434c3-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="434c3-210">Para obter mais informações, consulte [Substitutos de Contratos de Dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="434c3-210">For more information, see [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="434c3-211">Você pode `DataContractSerializerOperationBehavior` usar o para personalizar a serialização do cliente e do servidor.</span><span class="sxs-lookup"><span data-stu-id="434c3-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="434c3-212">O exemplo a seguir `MaxItemsInObjectGraph` mostra como aumentar a cota no cliente.</span><span class="sxs-lookup"><span data-stu-id="434c3-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
<span data-ttu-id="434c3-213">A seguir está o código equivalente no serviço, no caso auto-hospedado:</span><span class="sxs-lookup"><span data-stu-id="434c3-213">The following is the equivalent code on the service, in the self-hosted case:</span></span>
  
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
  
 <span data-ttu-id="434c3-214">No caso hospedado na Web, você `ServiceHost` deve criar uma nova classe derivada e usar uma fábrica de host de serviço para conectá-la.</span><span class="sxs-lookup"><span data-stu-id="434c3-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="434c3-215">Controlando configurações de serialização na configuração</span><span class="sxs-lookup"><span data-stu-id="434c3-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="434c3-216">E `MaxItemsInObjectGraph` `IgnoreExtensionDataObject` pode ser controlado através `dataContractSerializer` da configuração usando o endpoint ou o comportamento de serviço, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="434c3-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="434c3-217">Serialização de tipo compartilhado, preservação de gráficos de objetos e serializadores personalizados</span><span class="sxs-lookup"><span data-stu-id="434c3-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="434c3-218">O <xref:System.Runtime.Serialization.DataContractSerializer> serializa usando nomes de contrato de dados e não nomes de tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="434c3-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="434c3-219">Isso é consistente com princípios de arquitetura orientados a serviços e permite um grande grau de flexibilidade — os tipos .NET podem mudar sem afetar o contrato de fio.</span><span class="sxs-lookup"><span data-stu-id="434c3-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="434c3-220">Em casos raros, você pode querer serializar nomes reais do tipo .NET, introduzindo assim um acoplamento apertado entre o cliente e o servidor, semelhante à tecnologia de remoção .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="434c3-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="434c3-221">Esta não é uma prática recomendada, exceto em casos raros que geralmente ocorrem ao migrar para o WCF do .NET Framework remoting.</span><span class="sxs-lookup"><span data-stu-id="434c3-221">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="434c3-222">Neste caso, você deve <xref:System.Runtime.Serialization.NetDataContractSerializer> usar a <xref:System.Runtime.Serialization.DataContractSerializer> classe em vez da classe.</span><span class="sxs-lookup"><span data-stu-id="434c3-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="434c3-223">O <xref:System.Runtime.Serialization.DataContractSerializer> normalmente serializa gráficos de objetos como árvores de objetos.</span><span class="sxs-lookup"><span data-stu-id="434c3-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="434c3-224">Ou seja, se o mesmo objeto é referido mais de uma vez, ele é serializado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="434c3-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="434c3-225">Por exemplo, `PurchaseOrder` considere uma instância que tenha `billTo` `shipTo`dois campos de endereço tipo chamados e .</span><span class="sxs-lookup"><span data-stu-id="434c3-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="434c3-226">Se ambos os campos estiverem definidos para a mesma instância de endereço, haverá duas instâncias de endereço idênticas após a serialização e a desserialização.</span><span class="sxs-lookup"><span data-stu-id="434c3-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="434c3-227">Isso é feito porque não há uma maneira interoperável padrão de representar gráficos de objetos em XML (exceto para o padrão legado SOAP codificado disponível no <xref:System.Xml.Serialization.XmlSerializer>, como descrito na seção anterior em `Style` e `Use`).</span><span class="sxs-lookup"><span data-stu-id="434c3-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="434c3-228">Serializar gráficos de objetos como árvores tem certas desvantagens, por exemplo, gráficos com referências circulares não podem ser serializados.</span><span class="sxs-lookup"><span data-stu-id="434c3-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="434c3-229">Ocasionalmente, é necessário mudar para serialização de gráficos de objetos verdadeiros, mesmo que não seja interoperável.</span><span class="sxs-lookup"><span data-stu-id="434c3-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="434c3-230">Isso pode ser feito <xref:System.Runtime.Serialization.DataContractSerializer> usando o `preserveObjectReferences` construído com `true`o parâmetro definido para .</span><span class="sxs-lookup"><span data-stu-id="434c3-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="434c3-231">Ocasionalmente, os serializadores embutidos não são suficientes para o seu cenário.</span><span class="sxs-lookup"><span data-stu-id="434c3-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="434c3-232">Na maioria dos casos, <xref:System.Runtime.Serialization.XmlObjectSerializer> você ainda pode usar <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer> abstração da qual tanto o e o derivam.</span><span class="sxs-lookup"><span data-stu-id="434c3-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="434c3-233">Os três casos anteriores (preservação do tipo.NET, preservação de gráficos de objetos e serialização completamente personalizada) `XmlObjectSerializer`exigem que um serializador personalizado seja conectado.</span><span class="sxs-lookup"><span data-stu-id="434c3-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="434c3-234">Para fazer isso, execute estas etapas:</span><span class="sxs-lookup"><span data-stu-id="434c3-234">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="434c3-235">Escreva seu próprio comportamento <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>derivado do .</span><span class="sxs-lookup"><span data-stu-id="434c3-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="434c3-236">Anular os `CreateSerializer` dois métodos para devolver seu <xref:System.Runtime.Serialization.NetDataContractSerializer>próprio <xref:System.Runtime.Serialization.DataContractSerializer> serializador `true`(seja o <xref:System.Runtime.Serialization.XmlObjectSerializer>, o com `preserveObjectReferences` set para , ou seu próprio costume ).</span><span class="sxs-lookup"><span data-stu-id="434c3-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="434c3-237">Antes de abrir o host de serviço ou <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> criar um canal cliente, remova o comportamento existente e conecte a classe derivada personalizada que você criou nas etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="434c3-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="434c3-238">Para obter mais informações sobre conceitos avançados de serialização, consulte [Serialização e Desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="434c3-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="434c3-239">Confira também</span><span class="sxs-lookup"><span data-stu-id="434c3-239">See also</span></span>

- [<span data-ttu-id="434c3-240">Usando a classe XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="434c3-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [<span data-ttu-id="434c3-241">Como habilitar transmissão</span><span class="sxs-lookup"><span data-stu-id="434c3-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [<span data-ttu-id="434c3-242">Como criar um contrato de dados básicos para uma classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="434c3-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
