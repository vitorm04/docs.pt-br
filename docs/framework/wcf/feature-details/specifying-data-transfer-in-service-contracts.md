---
title: Especificando transferência de dados em contratos de serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: 47544cf74b4fa09fd8ee868ea940ef24a453840e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834643"
---
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="177d6-102">Especificando transferência de dados em contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="177d6-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="177d6-103">O Windows Communication Foundation (WCF) pode ser considerado uma infraestrutura de mensagens.</span><span class="sxs-lookup"><span data-stu-id="177d6-103">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="177d6-104">As operações de serviço podem receber mensagens, processá-las e enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="177d6-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="177d6-105">As mensagens são descritas usando contratos de operação.</span><span class="sxs-lookup"><span data-stu-id="177d6-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="177d6-106">Por exemplo, considere o contrato a seguir.</span><span class="sxs-lookup"><span data-stu-id="177d6-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="177d6-107">Aqui, a operação `GetAirfare` aceita uma mensagem com informações sobre `fromCity` e `toCity` e, em seguida, retorna uma mensagem que contém um número.</span><span class="sxs-lookup"><span data-stu-id="177d6-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="177d6-108">Este tópico explica as várias maneiras em que um contrato de operação pode descrever mensagens.</span><span class="sxs-lookup"><span data-stu-id="177d6-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="177d6-109">Descrevendo mensagens usando parâmetros</span><span class="sxs-lookup"><span data-stu-id="177d6-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="177d6-110">A maneira mais simples de descrever uma mensagem é usar uma lista de parâmetros e o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="177d6-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="177d6-111">No exemplo anterior, os parâmetros de cadeia de caracteres `fromCity` e `toCity` foram usados para descrever a mensagem de solicitação e o valor de retorno flutuante foi usado para descrever a mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="177d6-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="177d6-112">Se o valor de retorno sozinho não for suficiente para descrever uma mensagem de resposta, os parâmetros de saída poderão ser usados.</span><span class="sxs-lookup"><span data-stu-id="177d6-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="177d6-113">Por exemplo, a operação a seguir tem `fromCity` e `toCity` em sua mensagem de solicitação e um número junto com uma moeda em sua mensagem de resposta:</span><span class="sxs-lookup"><span data-stu-id="177d6-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="177d6-114">Além disso, você pode usar parâmetros de referência para fazer com que um parâmetro faça parte da solicitação e da mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="177d6-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="177d6-115">Os parâmetros devem ser de tipos que podem ser serializados (convertidos em XML).</span><span class="sxs-lookup"><span data-stu-id="177d6-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="177d6-116">Por padrão, o WCF usa um componente chamado classe <xref:System.Runtime.Serialization.DataContractSerializer> para executar essa conversão.</span><span class="sxs-lookup"><span data-stu-id="177d6-116">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="177d6-117">Há suporte para a maioria dos tipos primitivos (como `int`, `string`, `float` e `DateTime`.).</span><span class="sxs-lookup"><span data-stu-id="177d6-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="177d6-118">Os tipos definidos pelo usuário normalmente devem ter um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="177d6-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="177d6-119">Para obter mais informações, consulte [usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="177d6-119">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="177d6-120">Ocasionalmente, o `DataContractSerializer` não é adequado para serializar seus tipos.</span><span class="sxs-lookup"><span data-stu-id="177d6-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="177d6-121">O WCF dá suporte a um mecanismo de serialização alternativo, o <xref:System.Xml.Serialization.XmlSerializer>, que você também pode usar para serializar parâmetros.</span><span class="sxs-lookup"><span data-stu-id="177d6-121">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="177d6-122">O <xref:System.Xml.Serialization.XmlSerializer> permite que você use mais controle sobre o XML resultante usando atributos como o `XmlAttributeAttribute`.</span><span class="sxs-lookup"><span data-stu-id="177d6-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="177d6-123">Para alternar para o uso do <xref:System.Xml.Serialization.XmlSerializer> para uma operação específica ou para todo o serviço, aplique o atributo <xref:System.ServiceModel.XmlSerializerFormatAttribute> a uma operação ou um serviço.</span><span class="sxs-lookup"><span data-stu-id="177d6-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="177d6-124">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="177d6-124">For example:</span></span>  
  
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
  
 <span data-ttu-id="177d6-125">Para obter mais informações, consulte [usando a classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="177d6-125">For more information, see [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="177d6-126">Lembre-se de que alternar manualmente para o <xref:System.Xml.Serialization.XmlSerializer>, como mostrado aqui, não é recomendado, a menos que você tenha motivos específicos para fazer isso, conforme detalhado no tópico.</span><span class="sxs-lookup"><span data-stu-id="177d6-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="177d6-127">Para isolar os nomes de parâmetro do .NET dos nomes de contrato, você pode usar o atributo <xref:System.ServiceModel.MessageParameterAttribute> e usar a propriedade `Name` para definir o nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="177d6-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="177d6-128">Por exemplo, o contrato de operação a seguir é equivalente ao primeiro exemplo neste tópico.</span><span class="sxs-lookup"><span data-stu-id="177d6-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="177d6-129">Descrevendo mensagens vazias</span><span class="sxs-lookup"><span data-stu-id="177d6-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="177d6-130">Uma mensagem de solicitação vazia pode ser descrita por não ter parâmetros de entrada ou de referência.</span><span class="sxs-lookup"><span data-stu-id="177d6-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="177d6-131">Por exemplo, C#em:</span><span class="sxs-lookup"><span data-stu-id="177d6-131">For example in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="177d6-132">Por exemplo, no VB:</span><span class="sxs-lookup"><span data-stu-id="177d6-132">For example in VB:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="177d6-133">Uma mensagem de resposta vazia pode ser descrita por ter um tipo de retorno `void` e nenhum parâmetro de referência ou de saída.</span><span class="sxs-lookup"><span data-stu-id="177d6-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="177d6-134">Por exemplo, em:</span><span class="sxs-lookup"><span data-stu-id="177d6-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="177d6-135">Isso é diferente de uma operação unidirecional, como:</span><span class="sxs-lookup"><span data-stu-id="177d6-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="177d6-136">A operação `SetTemperatureStatus` retorna uma mensagem vazia.</span><span class="sxs-lookup"><span data-stu-id="177d6-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="177d6-137">Ele poderá retornar uma falha em vez disso, se houver um problema ao processar a mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="177d6-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="177d6-138">A operação `SetLightbulbStatus` não retorna nada.</span><span class="sxs-lookup"><span data-stu-id="177d6-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="177d6-139">Não é possível comunicar uma condição de falha dessa operação.</span><span class="sxs-lookup"><span data-stu-id="177d6-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="177d6-140">Descrevendo mensagens usando contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="177d6-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="177d6-141">Talvez você queira usar um único tipo para representar a mensagem inteira.</span><span class="sxs-lookup"><span data-stu-id="177d6-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="177d6-142">Embora seja possível usar um contrato de dados para essa finalidade, a maneira recomendada de fazer isso é usar um contrato de mensagem — isso evita níveis desnecessários de encapsulamento no XML resultante.</span><span class="sxs-lookup"><span data-stu-id="177d6-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="177d6-143">Além disso, os contratos de mensagem permitem que você exerça mais controle sobre as mensagens resultantes.</span><span class="sxs-lookup"><span data-stu-id="177d6-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="177d6-144">Por exemplo, você pode decidir quais partes de informações devem estar no corpo da mensagem e quais devem estar nos cabeçalhos da mensagem.</span><span class="sxs-lookup"><span data-stu-id="177d6-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="177d6-145">O exemplo a seguir mostra o uso de contratos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="177d6-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 <span data-ttu-id="177d6-146">Para obter mais informações, consulte [usando contratos de mensagem](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="177d6-146">For more information, see [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="177d6-147">No exemplo anterior, a classe <xref:System.Runtime.Serialization.DataContractSerializer> ainda é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="177d6-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="177d6-148">A classe <xref:System.Xml.Serialization.XmlSerializer> também pode ser usada com contratos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="177d6-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="177d6-149">Para fazer isso, aplique o atributo <xref:System.ServiceModel.XmlSerializerFormatAttribute> à operação ou ao contrato e use os tipos compatíveis com a classe <xref:System.Xml.Serialization.XmlSerializer> nos cabeçalhos e membros do corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="177d6-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="177d6-150">Descrevendo mensagens usando fluxos</span><span class="sxs-lookup"><span data-stu-id="177d6-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="177d6-151">Outra maneira de descrever as mensagens em operações é usar a classe <xref:System.IO.Stream> ou uma de suas classes derivadas em um contrato de operação ou como um membro do corpo do contrato de mensagem (ela deve ser o único membro nesse caso).</span><span class="sxs-lookup"><span data-stu-id="177d6-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="177d6-152">Para mensagens de entrada, o tipo deve ser `Stream` — você não pode usar classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="177d6-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="177d6-153">Em vez de invocar o serializador, o WCF recupera dados de um fluxo e os coloca diretamente em uma mensagem de saída ou recupera dados de uma mensagem de entrada e os coloca diretamente em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="177d6-153">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="177d6-154">O exemplo a seguir mostra o uso de fluxos.</span><span class="sxs-lookup"><span data-stu-id="177d6-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="177d6-155">Não é possível combinar dados `Stream` e não de fluxo em um único corpo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="177d6-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="177d6-156">Use um contrato de mensagem para colocar os dados adicionais em cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="177d6-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="177d6-157">O exemplo a seguir mostra o uso incorreto de fluxos ao definir o contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="177d6-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="177d6-158">O exemplo a seguir mostra o uso correto de fluxos ao definir um contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="177d6-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 <span data-ttu-id="177d6-159">Para obter mais informações, consulte [grandes dados e streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="177d6-159">For more information, see [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="177d6-160">Usando a classe de mensagens</span><span class="sxs-lookup"><span data-stu-id="177d6-160">Using the Message Class</span></span>  
 <span data-ttu-id="177d6-161">Para ter total controle programático sobre as mensagens enviadas ou recebidas, você pode usar a classe <xref:System.ServiceModel.Channels.Message> diretamente, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="177d6-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="177d6-162">Este é um cenário avançado, que é descrito em detalhes no [uso da classe Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="177d6-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="177d6-163">Descrevendo as mensagens de falha</span><span class="sxs-lookup"><span data-stu-id="177d6-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="177d6-164">Além das mensagens descritas pelo valor de retorno e parâmetros de saída ou de referência, qualquer operação que não seja unidirecional pode retornar pelo menos duas mensagens possíveis: sua mensagem de resposta normal e uma mensagem de falha.</span><span class="sxs-lookup"><span data-stu-id="177d6-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="177d6-165">Considere o contrato de operação a seguir.</span><span class="sxs-lookup"><span data-stu-id="177d6-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="177d6-166">Essa operação pode retornar uma mensagem normal que contém um número `float` ou uma mensagem de falha que contém um código de falha e uma descrição.</span><span class="sxs-lookup"><span data-stu-id="177d6-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="177d6-167">Você pode fazer isso lançando um <xref:System.ServiceModel.FaultException> em sua implementação de serviço.</span><span class="sxs-lookup"><span data-stu-id="177d6-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="177d6-168">Você pode especificar mensagens de falha adicionais possíveis usando o atributo <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="177d6-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="177d6-169">As falhas adicionais devem ser serializáveis usando o <xref:System.Runtime.Serialization.DataContractSerializer>, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="177d6-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="177d6-170">Essas falhas adicionais podem ser geradas lançando um <xref:System.ServiceModel.FaultException%601> do tipo de contrato de dados apropriado.</span><span class="sxs-lookup"><span data-stu-id="177d6-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="177d6-171">Para obter mais informações, consulte [tratamento de exceções e falhas](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="177d6-171">For more information, see [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="177d6-172">Você não pode usar a classe <xref:System.Xml.Serialization.XmlSerializer> para descrever as falhas.</span><span class="sxs-lookup"><span data-stu-id="177d6-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="177d6-173">O <xref:System.ServiceModel.XmlSerializerFormatAttribute> não tem nenhum efeito sobre os contratos de falha.</span><span class="sxs-lookup"><span data-stu-id="177d6-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="177d6-174">Usando tipos derivados</span><span class="sxs-lookup"><span data-stu-id="177d6-174">Using Derived Types</span></span>  
 <span data-ttu-id="177d6-175">Talvez você queira usar um tipo base em uma operação ou um contrato de mensagem e, em seguida, usar um tipo derivado ao invocar a operação de fato.</span><span class="sxs-lookup"><span data-stu-id="177d6-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="177d6-176">Nesse caso, você deve usar o atributo <xref:System.ServiceModel.ServiceKnownTypeAttribute> ou algum mecanismo alternativo para permitir o uso de tipos derivados.</span><span class="sxs-lookup"><span data-stu-id="177d6-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="177d6-177">Considere a seguinte operação.</span><span class="sxs-lookup"><span data-stu-id="177d6-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="177d6-178">Suponha que dois tipos, `Book` e `Magazine`, derivem de `LibraryItem`.</span><span class="sxs-lookup"><span data-stu-id="177d6-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="177d6-179">Para usar esses tipos na operação `IsLibraryItemAvailable`, você pode alterar a operação da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="177d6-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="177d6-180">Como alternativa, você pode usar o atributo <xref:System.Runtime.Serialization.KnownTypeAttribute> quando o padrão <xref:System.Runtime.Serialization.DataContractSerializer> estiver em uso, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="177d6-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="177d6-181">Você pode usar o atributo <xref:System.Xml.Serialization.XmlIncludeAttribute> ao usar o <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="177d6-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="177d6-182">Você pode aplicar o atributo <xref:System.ServiceModel.ServiceKnownTypeAttribute> a uma operação ou a todo o serviço.</span><span class="sxs-lookup"><span data-stu-id="177d6-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="177d6-183">Ele aceita um tipo ou o nome do método a ser chamado para obter uma lista de tipos conhecidos, assim como o atributo <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="177d6-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="177d6-184">Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="177d6-184">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="177d6-185">Especificando o uso e o estilo</span><span class="sxs-lookup"><span data-stu-id="177d6-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="177d6-186">Ao descrever serviços usando WSDL (Web Services Description Language), os dois estilos comumente usados são documento e RPC (chamada de procedimento remoto).</span><span class="sxs-lookup"><span data-stu-id="177d6-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="177d6-187">No estilo do documento, todo o corpo da mensagem é descrito usando o esquema, e o WSDL descreve as várias partes do corpo da mensagem referindo-se aos elementos dentro desse esquema.</span><span class="sxs-lookup"><span data-stu-id="177d6-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="177d6-188">No estilo RPC, o WSDL refere-se a um tipo de esquema para cada parte de mensagem, em vez de um elemento.</span><span class="sxs-lookup"><span data-stu-id="177d6-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="177d6-189">Em alguns casos, você precisa selecionar manualmente um desses estilos.</span><span class="sxs-lookup"><span data-stu-id="177d6-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="177d6-190">Você pode fazer isso aplicando o atributo <xref:System.ServiceModel.DataContractFormatAttribute> e definindo a propriedade `Style` (quando o <xref:System.Runtime.Serialization.DataContractSerializer> estiver em uso) ou definindo `Style` no atributo <xref:System.ServiceModel.XmlSerializerFormatAttribute> (ao usar o <xref:System.Xml.Serialization.XmlSerializer>).</span><span class="sxs-lookup"><span data-stu-id="177d6-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="177d6-191">Além disso, o <xref:System.Xml.Serialization.XmlSerializer> dá suporte a duas formas de XML serializado: `Literal` e `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="177d6-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="177d6-192">`Literal` é a forma mais aceita e é a única forma com a qual o <xref:System.Runtime.Serialization.DataContractSerializer> dá suporte.</span><span class="sxs-lookup"><span data-stu-id="177d6-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="177d6-193">`Encoded` é um formulário herdado descrito na seção 5 da especificação SOAP e não é recomendado para novos serviços.</span><span class="sxs-lookup"><span data-stu-id="177d6-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="177d6-194">Para alternar para o modo `Encoded`, defina a propriedade `Use` no atributo <xref:System.ServiceModel.XmlSerializerFormatAttribute> como `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="177d6-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="177d6-195">Na maioria dos casos, você não deve alterar as configurações padrão para as propriedades `Style` e `Use`.</span><span class="sxs-lookup"><span data-stu-id="177d6-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="177d6-196">Controlando o processo de serialização</span><span class="sxs-lookup"><span data-stu-id="177d6-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="177d6-197">Você pode fazer várias coisas para personalizar a maneira como os dados são serializados.</span><span class="sxs-lookup"><span data-stu-id="177d6-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="177d6-198">Alterando as configurações de serialização do servidor</span><span class="sxs-lookup"><span data-stu-id="177d6-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="177d6-199">Quando o padrão <xref:System.Runtime.Serialization.DataContractSerializer> está em uso, você pode controlar alguns aspectos do processo de serialização no serviço aplicando o atributo <xref:System.ServiceModel.ServiceBehaviorAttribute> ao serviço.</span><span class="sxs-lookup"><span data-stu-id="177d6-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="177d6-200">Especificamente, você pode usar a propriedade `MaxItemsInObjectGraph` para definir a cota que limita o número máximo de objetos que o <xref:System.Runtime.Serialization.DataContractSerializer> desserializa.</span><span class="sxs-lookup"><span data-stu-id="177d6-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="177d6-201">Você pode usar a propriedade `IgnoreExtensionDataObject` para desativar o recurso de controle de versão de ida e volta.</span><span class="sxs-lookup"><span data-stu-id="177d6-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="177d6-202">Para obter mais informações sobre cotas, confira [Considerações sobre segurança de dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="177d6-202">For more information about quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> <span data-ttu-id="177d6-203">Para obter mais informações sobre ida e volta, consulte [contratos de dados compatíveis com o encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="177d6-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="177d6-204">Comportamentos de serialização</span><span class="sxs-lookup"><span data-stu-id="177d6-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="177d6-205">Dois comportamentos estão disponíveis no WCF, o <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> e o <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> que são conectados automaticamente dependendo de qual serializador está em uso para uma operação específica.</span><span class="sxs-lookup"><span data-stu-id="177d6-205">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="177d6-206">Como esses comportamentos são aplicados automaticamente, você normalmente não precisa estar atento a eles.</span><span class="sxs-lookup"><span data-stu-id="177d6-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="177d6-207">No entanto, o `DataContractSerializerOperationBehavior` tem as propriedades `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject` e `DataContractSurrogate` que você pode usar para personalizar o processo de serialização.</span><span class="sxs-lookup"><span data-stu-id="177d6-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="177d6-208">As duas primeiras propriedades têm o mesmo significado, conforme discutido na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="177d6-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="177d6-209">Você pode usar a propriedade `DataContractSurrogate` para habilitar os substitutos de contrato de dados, que são um mecanismo poderoso para personalizar e estender o processo de serialização.</span><span class="sxs-lookup"><span data-stu-id="177d6-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="177d6-210">Para obter mais informações, consulte [substitutos de contrato de dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="177d6-210">For more information, see [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="177d6-211">Você pode usar o `DataContractSerializerOperationBehavior` para personalizar a serialização do cliente e do servidor.</span><span class="sxs-lookup"><span data-stu-id="177d6-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="177d6-212">O exemplo a seguir mostra como aumentar a cota de `MaxItemsInObjectGraph` no cliente.</span><span class="sxs-lookup"><span data-stu-id="177d6-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
<span data-ttu-id="177d6-213">Este é o código equivalente no serviço, no caso de hospedagem interna:</span><span class="sxs-lookup"><span data-stu-id="177d6-213">The following is the equivalent code on the service, in the self-hosted case:</span></span>
  
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
  
 <span data-ttu-id="177d6-214">No caso hospedado na Web, você deve criar uma nova classe derivada `ServiceHost` e usar uma fábrica de host de serviço para conectá-la.</span><span class="sxs-lookup"><span data-stu-id="177d6-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="177d6-215">Controlando as configurações de serialização na configuração</span><span class="sxs-lookup"><span data-stu-id="177d6-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="177d6-216">O `MaxItemsInObjectGraph` e o `IgnoreExtensionDataObject` podem ser controlados por meio da configuração usando o ponto de extremidade `dataContractSerializer` ou o comportamento do serviço, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="177d6-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="177d6-217">Serialização de tipo compartilhado, preservação de grafo de objeto e serializadores personalizados</span><span class="sxs-lookup"><span data-stu-id="177d6-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="177d6-218">O <xref:System.Runtime.Serialization.DataContractSerializer> serializa usando nomes de contrato de dados e não nomes de tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="177d6-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="177d6-219">Isso é consistente com as filosofias de arquitetura orientada a serviços e permite um grande grau de flexibilidade — os tipos .NET podem mudar sem afetar o contrato de fio.</span><span class="sxs-lookup"><span data-stu-id="177d6-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="177d6-220">Em casos raros, talvez você queira serializar nomes de tipo .NET reais, apresentando assim um forte acoplamento entre o cliente e o servidor, semelhante à tecnologia de comunicação remota .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="177d6-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="177d6-221">Essa não é uma prática recomendada, exceto em casos raros que geralmente ocorrem ao migrar para o WCF de .NET Framework comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="177d6-221">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="177d6-222">Nesse caso, você deve usar a classe <xref:System.Runtime.Serialization.NetDataContractSerializer> em vez da classe <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="177d6-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="177d6-223">O <xref:System.Runtime.Serialization.DataContractSerializer> normalmente serializa grafos de objeto como árvores de objeto.</span><span class="sxs-lookup"><span data-stu-id="177d6-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="177d6-224">Ou seja, se o mesmo objeto for referenciado mais de uma vez, ele será serializado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="177d6-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="177d6-225">Por exemplo, considere uma instância `PurchaseOrder` que tenha dois campos do tipo endereço chamado `billTo` e `shipTo`.</span><span class="sxs-lookup"><span data-stu-id="177d6-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="177d6-226">Se ambos os campos estiverem definidos para a mesma instância de endereço, haverá duas instâncias de endereço idênticas após a serialização e a desserialização.</span><span class="sxs-lookup"><span data-stu-id="177d6-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="177d6-227">Isso é feito porque não há uma maneira interoperável padrão para representar grafos de objeto em XML (exceto para o padrão codificado em SOAP herdado disponível no <xref:System.Xml.Serialization.XmlSerializer>, conforme descrito na seção anterior em `Style` e `Use`).</span><span class="sxs-lookup"><span data-stu-id="177d6-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="177d6-228">A serialização de grafos de objeto como árvores tem determinadas desvantagens, por exemplo, grafos com referências circulares não podem ser serializados.</span><span class="sxs-lookup"><span data-stu-id="177d6-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="177d6-229">Ocasionalmente, é necessário mudar para a serialização real do grafo de objetos, mesmo que ele não seja interoperável.</span><span class="sxs-lookup"><span data-stu-id="177d6-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="177d6-230">Isso pode ser feito usando o <xref:System.Runtime.Serialization.DataContractSerializer> construído com o parâmetro `preserveObjectReferences` definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="177d6-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="177d6-231">Ocasionalmente, os serializadores internos não são suficientes para seu cenário.</span><span class="sxs-lookup"><span data-stu-id="177d6-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="177d6-232">Na maioria dos casos, você ainda pode usar a abstração <xref:System.Runtime.Serialization.XmlObjectSerializer> da qual o <xref:System.Runtime.Serialization.DataContractSerializer> e o <xref:System.Runtime.Serialization.NetDataContractSerializer> derivam.</span><span class="sxs-lookup"><span data-stu-id="177d6-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="177d6-233">Os três casos anteriores (preservação de tipo .NET, preservação de grafo de objeto e completamente personalizado @no__t serialização baseada em-0) todos exigem que um serializador personalizado seja conectado.</span><span class="sxs-lookup"><span data-stu-id="177d6-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="177d6-234">Para fazer isso, execute estas etapas:</span><span class="sxs-lookup"><span data-stu-id="177d6-234">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="177d6-235">Escreva seu próprio comportamento derivando do <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="177d6-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="177d6-236">Substitua os dois métodos `CreateSerializer` para retornar seu próprio serializador (o <xref:System.Runtime.Serialization.NetDataContractSerializer>, o <xref:System.Runtime.Serialization.DataContractSerializer> com `preserveObjectReferences` definido como `true` ou seu próprio @no__t personalizado-5).</span><span class="sxs-lookup"><span data-stu-id="177d6-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="177d6-237">Antes de abrir o host de serviço ou criar um canal de cliente, remova o comportamento existente de <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> e conecte a classe derivada personalizada que você criou nas etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="177d6-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="177d6-238">Para obter mais informações sobre conceitos de serialização avançada, consulte [serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="177d6-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="177d6-239">Consulte também</span><span class="sxs-lookup"><span data-stu-id="177d6-239">See also</span></span>

- [<span data-ttu-id="177d6-240">Usando a classe XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="177d6-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [<span data-ttu-id="177d6-241">Como: Habilitar streaming</span><span class="sxs-lookup"><span data-stu-id="177d6-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- <span data-ttu-id="177d6-242">[Como: Criar um contrato de dados básico para uma classe ou estrutura @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="177d6-242">[How to: Create a Basic Data Contract for a Class or Structure](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)</span></span>
