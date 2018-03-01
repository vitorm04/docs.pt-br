---
title: "Especificando transferência de dados em contratos de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c650a59402099e1fe71a0292dd0ccfc409d3448d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="95bd6-102">Especificando transferência de dados em contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="95bd6-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="95bd6-103">O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pode ser pensada como uma infraestrutura de mensagens.</span><span class="sxs-lookup"><span data-stu-id="95bd6-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="95bd6-104">Operações de serviço podem receber mensagens, processá-los e enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="95bd6-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="95bd6-105">As mensagens são descritas usando contratos de operação.</span><span class="sxs-lookup"><span data-stu-id="95bd6-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="95bd6-106">Por exemplo, considere o seguinte contrato.</span><span class="sxs-lookup"><span data-stu-id="95bd6-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="95bd6-107">Aqui, o `GetAirfare` operação aceita uma mensagem com informações sobre `fromCity` e `toCity`e, em seguida, retorna uma mensagem que contém um número.</span><span class="sxs-lookup"><span data-stu-id="95bd6-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="95bd6-108">Este tópico explica as várias maneiras em que um contrato de operação pode descrever mensagens.</span><span class="sxs-lookup"><span data-stu-id="95bd6-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="95bd6-109">Descrevendo mensagens usando parâmetros</span><span class="sxs-lookup"><span data-stu-id="95bd6-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="95bd6-110">A maneira mais simples para descrever uma mensagem é usar uma lista de parâmetros e o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="95bd6-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="95bd6-111">No exemplo anterior, o `fromCity` e `toCity` parâmetros de cadeia de caracteres que foram usados para descrever a mensagem de solicitação e o valor de retorno de float foi usado para descrever a mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="95bd6-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="95bd6-112">Se o valor de retorno sozinho não é suficiente para descrever uma mensagem de resposta, os parâmetros de saída podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="95bd6-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="95bd6-113">Por exemplo, a seguinte operação tem `fromCity` e `toCity` em sua mensagem de solicitação e um número junto com uma moeda na sua mensagem de resposta:</span><span class="sxs-lookup"><span data-stu-id="95bd6-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="95bd6-114">Além disso, você pode usar parâmetros de referência para fazer com que uma parte do parâmetro da solicitação e a mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="95bd6-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="95bd6-115">Os parâmetros devem ser de tipos que podem ser serializados (convertidos em XML).</span><span class="sxs-lookup"><span data-stu-id="95bd6-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="95bd6-116">Por padrão, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa um componente chamado de <xref:System.Runtime.Serialization.DataContractSerializer> classe para realizar essa conversão.</span><span class="sxs-lookup"><span data-stu-id="95bd6-116">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="95bd6-117">Tipos primitivos mais (como `int`, `string`, `float`, e `DateTime`.) têm suporte.</span><span class="sxs-lookup"><span data-stu-id="95bd6-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="95bd6-118">Tipos definidos pelo usuário normalmente devem ter um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="95bd6-118">User-defined types must normally have a data contract.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="95bd6-119">[Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="95bd6-119"> [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="95bd6-120">Ocasionalmente, o `DataContractSerializer` não é adequado para serializar seus tipos.</span><span class="sxs-lookup"><span data-stu-id="95bd6-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="95bd6-121">oferece suporte a um mecanismo de serialização alternativo, o <xref:System.Xml.Serialization.XmlSerializer>, que também pode ser usada para serializar os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="95bd6-121"> supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="95bd6-122">O <xref:System.Xml.Serialization.XmlSerializer> permite que você use mais controle sobre o XML resultante usando atributos, como o `XmlAttributeAttribute`.</span><span class="sxs-lookup"><span data-stu-id="95bd6-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="95bd6-123">Para passar a usar o <xref:System.Xml.Serialization.XmlSerializer> para uma operação específica ou para todo o serviço, aplicar o <xref:System.ServiceModel.XmlSerializerFormatAttribute> de atributo para uma operação ou um serviço.</span><span class="sxs-lookup"><span data-stu-id="95bd6-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="95bd6-124">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="95bd6-124">For example:</span></span>  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="95bd6-125">[Usando a classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="95bd6-125"> [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="95bd6-126">Lembre-se de que alternar manualmente para o <xref:System.Xml.Serialization.XmlSerializer> conforme mostrado aqui não é recomendada a menos que você tenha motivos específicos para fazer assim como detalhado no tópico.</span><span class="sxs-lookup"><span data-stu-id="95bd6-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="95bd6-127">Para isolar os nomes de parâmetro .NET de nomes de contrato, você pode usar o <xref:System.ServiceModel.MessageParameterAttribute> de atributos e usar o `Name` propriedade para definir o nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="95bd6-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="95bd6-128">Por exemplo, o seguinte contrato de operação é equivalente ao primeiro exemplo neste tópico.</span><span class="sxs-lookup"><span data-stu-id="95bd6-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="95bd6-129">Descrevendo mensagens vazias</span><span class="sxs-lookup"><span data-stu-id="95bd6-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="95bd6-130">Uma mensagem de solicitação vazio pode ser descrita por não ter nenhum parâmetro de entrada ou referência.</span><span class="sxs-lookup"><span data-stu-id="95bd6-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="95bd6-131">Por exemplo em c#:</span><span class="sxs-lookup"><span data-stu-id="95bd6-131">For example in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="95bd6-132">Por exemplo, no VB:</span><span class="sxs-lookup"><span data-stu-id="95bd6-132">For example in VB:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="95bd6-133">Uma mensagem de resposta vazia pode ser descrita por ter uma `void` tipo de retorno e parâmetros de saída ou referência.</span><span class="sxs-lookup"><span data-stu-id="95bd6-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="95bd6-134">Por exemplo, em:</span><span class="sxs-lookup"><span data-stu-id="95bd6-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="95bd6-135">Isso é diferente de uma operação unidirecional, como:</span><span class="sxs-lookup"><span data-stu-id="95bd6-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="95bd6-136">O `SetTemperatureStatus` operação retorna uma mensagem vazia.</span><span class="sxs-lookup"><span data-stu-id="95bd6-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="95bd6-137">Pode retornar uma falha em vez disso, se houver um problema ao processar a mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="95bd6-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="95bd6-138">O `SetLightbulbStatus` operação não retorna nada.</span><span class="sxs-lookup"><span data-stu-id="95bd6-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="95bd6-139">Não há nenhuma maneira de comunicar-se uma condição de falha desta operação.</span><span class="sxs-lookup"><span data-stu-id="95bd6-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="95bd6-140">Descrevendo mensagens por meio de contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="95bd6-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="95bd6-141">Você talvez queira usar um único tipo para representar a mensagem inteira.</span><span class="sxs-lookup"><span data-stu-id="95bd6-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="95bd6-142">Embora seja possível usar um contrato de dados para essa finalidade, a maneira recomendada de fazer isso é usar um contrato de mensagem — Isso evita o desnecessários níveis de encapsulamento no XML resultante.</span><span class="sxs-lookup"><span data-stu-id="95bd6-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="95bd6-143">Além disso, contratos de mensagem permitem que você tenha mais controle sobre mensagens resultantes.</span><span class="sxs-lookup"><span data-stu-id="95bd6-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="95bd6-144">Por exemplo, você pode decidir quais informações devem estar no corpo da mensagem e que deve ser nos cabeçalhos da mensagem.</span><span class="sxs-lookup"><span data-stu-id="95bd6-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="95bd6-145">O exemplo a seguir mostra o uso de contratos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="95bd6-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="95bd6-146">[Usando contratos de mensagem](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="95bd6-146"> [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="95bd6-147">No exemplo anterior, a <xref:System.Runtime.Serialization.DataContractSerializer> classe ainda é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="95bd6-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="95bd6-148">O <xref:System.Xml.Serialization.XmlSerializer> classe também pode ser usada com contratos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="95bd6-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="95bd6-149">Para fazer isso, aplique a <xref:System.ServiceModel.XmlSerializerFormatAttribute> de atributo para a operação ou o contrato e usar tipos compatíveis com o <xref:System.Xml.Serialization.XmlSerializer> classe nos cabeçalhos de mensagem e membros de corpo.</span><span class="sxs-lookup"><span data-stu-id="95bd6-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="95bd6-150">Descrevendo mensagens usando fluxos</span><span class="sxs-lookup"><span data-stu-id="95bd6-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="95bd6-151">Outra maneira de descrever as mensagens em operações é usar o <xref:System.IO.Stream> classe ou uma de suas classes derivadas em um contrato de operação ou como um membro de corpo de contrato de mensagem (deve ser o único membro nesse caso).</span><span class="sxs-lookup"><span data-stu-id="95bd6-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="95bd6-152">Mensagens de entrada, o tipo deve ser `Stream`— não é possível usar as classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="95bd6-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="95bd6-153">Em vez de invocar o serializador [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recupera dados de um fluxo e coloca diretamente em uma mensagem de saída, ou recupera dados de uma mensagem de entrada e coloca-o diretamente em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="95bd6-153">Instead of invoking the serializer, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="95bd6-154">O exemplo a seguir mostra o uso de fluxos.</span><span class="sxs-lookup"><span data-stu-id="95bd6-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="95bd6-155">Não é possível combinar `Stream` e não são de fluxo dados no corpo da mensagem única.</span><span class="sxs-lookup"><span data-stu-id="95bd6-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="95bd6-156">Use um contrato de mensagem para colocar os dados extras em cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="95bd6-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="95bd6-157">O exemplo a seguir mostra o uso incorreto de fluxos quando o contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="95bd6-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="95bd6-158">O exemplo a seguir mostra o uso correto dos fluxos ao definir um contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="95bd6-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="95bd6-159">[Dados grandes e Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="95bd6-159"> [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="95bd6-160">Usando a classe de mensagens</span><span class="sxs-lookup"><span data-stu-id="95bd6-160">Using the Message Class</span></span>  
 <span data-ttu-id="95bd6-161">Para ter total controle programático sobre mensagens enviadas ou recebidas, você pode usar o <xref:System.ServiceModel.Channels.Message> classe diretamente, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="95bd6-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="95bd6-162">Este é um cenário avançado, que é descrito em detalhes em [usando a classe de mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="95bd6-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="95bd6-163">Que descreve mensagens de falha</span><span class="sxs-lookup"><span data-stu-id="95bd6-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="95bd6-164">As mensagens que são descritas pelo valor de retorno e parâmetros de saída ou referência, além de qualquer operação que não é unidirecional pode retornar pelo menos duas mensagens possíveis: a mensagem de resposta normal e uma mensagem de falha.</span><span class="sxs-lookup"><span data-stu-id="95bd6-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="95bd6-165">Considere o seguinte contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="95bd6-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="95bd6-166">Esta operação ou pode retornar uma mensagem normal que contém um `float` número ou uma mensagem de falha que contém um código de falha e uma descrição.</span><span class="sxs-lookup"><span data-stu-id="95bd6-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="95bd6-167">Você pode fazer isso, lançando um <xref:System.ServiceModel.FaultException> em sua implementação de serviço.</span><span class="sxs-lookup"><span data-stu-id="95bd6-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="95bd6-168">Você pode especificar as mensagens de falha possíveis adicionais usando o <xref:System.ServiceModel.FaultContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="95bd6-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="95bd6-169">As falhas adicionais devem ser serializável usando o <xref:System.Runtime.Serialization.DataContractSerializer>, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="95bd6-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="95bd6-170">Essas falhas adicionais podem ser geradas, lançando um <xref:System.ServiceModel.FaultException%601> do tipo de contrato de dados apropriado.</span><span class="sxs-lookup"><span data-stu-id="95bd6-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="95bd6-171">[Tratamento de exceções e falhas](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="95bd6-171"> [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="95bd6-172">Não é possível usar o <xref:System.Xml.Serialization.XmlSerializer> classe para descrever a falhas.</span><span class="sxs-lookup"><span data-stu-id="95bd6-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="95bd6-173">O <xref:System.ServiceModel.XmlSerializerFormatAttribute> não tem efeito sobre contratos de falha.</span><span class="sxs-lookup"><span data-stu-id="95bd6-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="95bd6-174">Usando tipos derivados</span><span class="sxs-lookup"><span data-stu-id="95bd6-174">Using Derived Types</span></span>  
 <span data-ttu-id="95bd6-175">Você talvez queira usar um tipo base em uma operação ou um contrato de mensagem e, em seguida, usar um tipo derivado quando realmente invocar a operação.</span><span class="sxs-lookup"><span data-stu-id="95bd6-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="95bd6-176">Nesse caso, você deve usar o a <xref:System.ServiceModel.ServiceKnownTypeAttribute> atributo ou um mecanismo alternativo para permitir o uso de tipos derivados.</span><span class="sxs-lookup"><span data-stu-id="95bd6-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="95bd6-177">Considere a seguinte operação.</span><span class="sxs-lookup"><span data-stu-id="95bd6-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="95bd6-178">Suponha que dois tipos, `Book` e `Magazine`, derivam `LibraryItem`.</span><span class="sxs-lookup"><span data-stu-id="95bd6-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="95bd6-179">Para usar estes tipos de `IsLibraryItemAvailable` operação, você pode alterar a operação da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="95bd6-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="95bd6-180">Como alternativa, você pode usar o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo quando o padrão <xref:System.Runtime.Serialization.DataContractSerializer> está em uso, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="95bd6-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="95bd6-181">Você pode usar o <xref:System.Xml.Serialization.XmlIncludeAttribute> atributo ao usar o <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="95bd6-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="95bd6-182">Você pode aplicar o <xref:System.ServiceModel.ServiceKnownTypeAttribute> atributo a uma operação ou todo o serviço.</span><span class="sxs-lookup"><span data-stu-id="95bd6-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="95bd6-183">Ele aceita um tipo ou o nome do método para chamar para obter uma lista de tipos conhecidos, como o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="95bd6-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="95bd6-184">[Tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="95bd6-184"> [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="95bd6-185">Especificando o uso e o estilo</span><span class="sxs-lookup"><span data-stu-id="95bd6-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="95bd6-186">Ao descrever serviços usando WSDL Web Services Description Language (), as duas normalmente estilos usados são documento e a chamada de procedimento remoto (RPC).</span><span class="sxs-lookup"><span data-stu-id="95bd6-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="95bd6-187">No estilo de documento, o corpo da mensagem inteira é descrito usando o esquema e o WSDL descreve as várias partes de corpo de mensagem referindo-se aos elementos no esquema.</span><span class="sxs-lookup"><span data-stu-id="95bd6-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="95bd6-188">No estilo RPC, o WSDL se refere a um tipo de esquema para cada parte da mensagem em vez de um elemento.</span><span class="sxs-lookup"><span data-stu-id="95bd6-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="95bd6-189">Em alguns casos, você precisa selecionar manualmente um desses estilos.</span><span class="sxs-lookup"><span data-stu-id="95bd6-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="95bd6-190">Você pode fazer isso aplicando a <xref:System.ServiceModel.DataContractFormatAttribute> atributo e configuração o `Style` propriedade (quando o <xref:System.Runtime.Serialization.DataContractSerializer> está em uso), ou definindo `Style` no <xref:System.ServiceModel.XmlSerializerFormatAttribute> atributo (ao usar o <xref:System.Xml.Serialization.XmlSerializer>).</span><span class="sxs-lookup"><span data-stu-id="95bd6-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="95bd6-191">Além disso, o <xref:System.Xml.Serialization.XmlSerializer> dá suporte a duas formas de XML serializado: `Literal` e `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="95bd6-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="95bd6-192">`Literal`é o mais comumente aceito e é a única forma de <xref:System.Runtime.Serialization.DataContractSerializer> oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="95bd6-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="95bd6-193">`Encoded`é uma forma herdada descrita na seção 5 da especificação de SOAP e não é recomendado para novos serviços.</span><span class="sxs-lookup"><span data-stu-id="95bd6-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="95bd6-194">Para alternar para `Encoded` modo, defina o `Use` propriedade o <xref:System.ServiceModel.XmlSerializerFormatAttribute> atributo `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="95bd6-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="95bd6-195">Na maioria dos casos, você não deve alterar as configurações padrão para o `Style` e `Use` propriedades.</span><span class="sxs-lookup"><span data-stu-id="95bd6-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="95bd6-196">Controlando o processo de serialização</span><span class="sxs-lookup"><span data-stu-id="95bd6-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="95bd6-197">Você pode fazer algumas coisas para personalizar a maneira como os dados são serializados.</span><span class="sxs-lookup"><span data-stu-id="95bd6-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="95bd6-198">Alterando as definições de serialização do servidor</span><span class="sxs-lookup"><span data-stu-id="95bd6-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="95bd6-199">Quando o padrão <xref:System.Runtime.Serialization.DataContractSerializer> está em uso, você pode controlar alguns aspectos do processo de serialização no serviço aplicando o <xref:System.ServiceModel.ServiceBehaviorAttribute> de atributo para o serviço.</span><span class="sxs-lookup"><span data-stu-id="95bd6-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="95bd6-200">Especificamente, você pode usar o `MaxItemsInObjectGraph` propriedade para definir a cota que limita o número máximo de objetos de <xref:System.Runtime.Serialization.DataContractSerializer> desserializa.</span><span class="sxs-lookup"><span data-stu-id="95bd6-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="95bd6-201">Você pode usar o `IgnoreExtensionDataObject` propriedade para desativar o recurso de controle de versão de ciclo.</span><span class="sxs-lookup"><span data-stu-id="95bd6-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="95bd6-202">cotas, consulte [considerações de segurança para dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="95bd6-202"> quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="95bd6-203">ciclo, consulte [contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="95bd6-203"> round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="95bd6-204">Comportamentos de serialização</span><span class="sxs-lookup"><span data-stu-id="95bd6-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="95bd6-205">Dois comportamentos estão disponíveis em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], o <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> e <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> que estão conectados automaticamente dependendo de qual serializador está em uso para uma operação específica.</span><span class="sxs-lookup"><span data-stu-id="95bd6-205">Two behaviors are available in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="95bd6-206">Como esses comportamentos são aplicados automaticamente, você normalmente não precisa estar ciente delas.</span><span class="sxs-lookup"><span data-stu-id="95bd6-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="95bd6-207">No entanto, o `DataContractSerializerOperationBehavior` tem o `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, e `DataContractSurrogate` propriedades que você pode usar para personalizar o processo de serialização.</span><span class="sxs-lookup"><span data-stu-id="95bd6-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="95bd6-208">As duas primeiras propriedades têm o mesmo significado conforme discutido na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="95bd6-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="95bd6-209">Você pode usar o `DataContractSurrogate` propriedade para habilitar substitutos de contrato de dados, que são um mecanismo eficiente para personalizar e estender o processo de serialização.</span><span class="sxs-lookup"><span data-stu-id="95bd6-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="95bd6-210">[Substitutos de contrato de dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="95bd6-210"> [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="95bd6-211">Você pode usar o `DataContractSerializerOperationBehavior` para personalizar a serialização de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="95bd6-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="95bd6-212">O exemplo a seguir mostra como aumentar o `MaxItemsInObjectGraph` cota no cliente.</span><span class="sxs-lookup"><span data-stu-id="95bd6-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
 <span data-ttu-id="95bd6-213">A seguir está o código equivalente do serviço, no caso de auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="95bd6-213">Following is the equivalent code on the service, in the self-hosted case.</span></span>  
  
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
  
 <span data-ttu-id="95bd6-214">No caso da Web hospedado, você deve criar um novo `ServiceHost` classe derivada e usar uma fábrica de host de serviço para conectá-lo.</span><span class="sxs-lookup"><span data-stu-id="95bd6-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="95bd6-215">Controlando a serialização de configurações em configuração</span><span class="sxs-lookup"><span data-stu-id="95bd6-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="95bd6-216">O `MaxItemsInObjectGraph` e `IgnoreExtensionDataObject` pode ser controlado pela configuração usando o `dataContractSerializer` comportamento de ponto de extremidade ou serviço, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="95bd6-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="95bd6-217">Serialização de tipo, preservação de gráfico de objeto e serializadores personalizados compartilhados</span><span class="sxs-lookup"><span data-stu-id="95bd6-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="95bd6-218">O <xref:System.Runtime.Serialization.DataContractSerializer> serializa usando nomes de contrato de dados e nomes de tipo do .NET.</span><span class="sxs-lookup"><span data-stu-id="95bd6-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="95bd6-219">Isso é consistente com os princípios de arquitetura orientada a serviços e possibilita um alto grau de flexibilidade — podem alterar os tipos de .NET sem afetar o contrato de transmissão.</span><span class="sxs-lookup"><span data-stu-id="95bd6-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="95bd6-220">Em casos raros, pode ser serializado nomes de tipo .NET reais, assim, apresentando uma grande união entre o cliente e o servidor, como a tecnologia de comunicação remota do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95bd6-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="95bd6-221">Isso não é uma prática recomendada, exceto em casos raros, que normalmente ocorrem durante a migração para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de comunicação remota do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95bd6-221">This is not a recommended practice, except in rare cases that usually occur when migrating to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] from .NET Framework remoting.</span></span> <span data-ttu-id="95bd6-222">Nesse caso, você deve usar o <xref:System.Runtime.Serialization.NetDataContractSerializer> classe o <xref:System.Runtime.Serialization.DataContractSerializer> classe.</span><span class="sxs-lookup"><span data-stu-id="95bd6-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="95bd6-223">O <xref:System.Runtime.Serialization.DataContractSerializer> normalmente serializa os gráficos de objeto como árvores de objeto.</span><span class="sxs-lookup"><span data-stu-id="95bd6-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="95bd6-224">Ou seja, se o mesmo objeto é referenciado mais de uma vez, ele é serializado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="95bd6-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="95bd6-225">Por exemplo, considere um `PurchaseOrder` instância que tem dois campos de tipo de endereço chamado `billTo` e `shipTo`.</span><span class="sxs-lookup"><span data-stu-id="95bd6-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="95bd6-226">Se ambos os campos são definidos para a mesma instância de endereço, há duas instâncias idênticas de endereço após a serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="95bd6-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="95bd6-227">Isso é feito porque não há nenhuma maneira interoperável padrão para representar os gráficos de objeto em XML (exceto para o padrão SOAP codificado herdado disponível no <xref:System.Xml.Serialization.XmlSerializer>, conforme descrito na seção anterior no `Style` e `Use`).</span><span class="sxs-lookup"><span data-stu-id="95bd6-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="95bd6-228">Serializando gráficos de objeto como árvores tem determinadas desvantagens, por exemplo, os gráficos com referências circulares não podem ser serializados.</span><span class="sxs-lookup"><span data-stu-id="95bd6-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="95bd6-229">Ocasionalmente, é necessário alternar para a serialização do gráfico de objeto verdadeira, embora não seja interoperável.</span><span class="sxs-lookup"><span data-stu-id="95bd6-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="95bd6-230">Isso pode ser feito usando o <xref:System.Runtime.Serialization.DataContractSerializer> construído com o `preserveObjectReferences` parâmetro definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="95bd6-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="95bd6-231">Ocasionalmente, os serializadores internos não são suficientes para seu cenário.</span><span class="sxs-lookup"><span data-stu-id="95bd6-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="95bd6-232">Na maioria dos casos, você ainda pode usar o <xref:System.Runtime.Serialization.XmlObjectSerializer> abstração do qual o <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.NetDataContractSerializer> derivar.</span><span class="sxs-lookup"><span data-stu-id="95bd6-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="95bd6-233">Os três casos anteriores (preservação de tipo do .NET, preservação de gráfico de objeto e totalmente personalizada `XmlObjectSerializer`-com base em serialização) exigem um serializador personalizado ser conectado.</span><span class="sxs-lookup"><span data-stu-id="95bd6-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="95bd6-234">Para fazer isso, execute estas etapas:</span><span class="sxs-lookup"><span data-stu-id="95bd6-234">To do this, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="95bd6-235">Gravar seu próprio comportamento derivando de <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="95bd6-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2.  <span data-ttu-id="95bd6-236">Substituir os dois `CreateSerializer` métodos para retornar o seu próprio serializador (ou o <xref:System.Runtime.Serialization.NetDataContractSerializer>, o <xref:System.Runtime.Serialization.DataContractSerializer> com `preserveObjectReferences` definida como `true`, ou seu próprio personalizado <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span><span class="sxs-lookup"><span data-stu-id="95bd6-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3.  <span data-ttu-id="95bd6-237">Antes de abrir o host de serviço ou criar um canal de cliente, remova existente <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> comportamento e plug-in a classe personalizada derivada que você criou nas etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="95bd6-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="95bd6-238">conceitos de serialização de avançados, consulte [serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="95bd6-238"> advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95bd6-239">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95bd6-239">See Also</span></span>  
 [<span data-ttu-id="95bd6-240">Usando a classe XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="95bd6-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 [<span data-ttu-id="95bd6-241">Como habilitar o streaming</span><span class="sxs-lookup"><span data-stu-id="95bd6-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)  
 [<span data-ttu-id="95bd6-242">Como criar um contrato de dados básicos para uma classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="95bd6-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
