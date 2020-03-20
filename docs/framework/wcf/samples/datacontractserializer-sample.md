---
title: Exemplo de DataContractSerializer
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: 5e1a471cc4cc43b2aa36143eeecc18f7ec17b81a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183783"
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="83de8-102">Exemplo de DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="83de8-102">DataContractSerializer Sample</span></span>
<span data-ttu-id="83de8-103">A amostra DataContractSerializer <xref:System.Runtime.Serialization.DataContractSerializer>demonstra o , que realiza serviços gerais de serialização e desserialização para as classes de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="83de8-103">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="83de8-104">A amostra `Record` cria um objeto, serializa-o em um fluxo de memória `Record` e desserializa <xref:System.Runtime.Serialization.DataContractSerializer>o fluxo de memória de volta para outro objeto para demonstrar o uso do .</span><span class="sxs-lookup"><span data-stu-id="83de8-104">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="83de8-105">A amostra então serializa o `Record` objeto usando um escritor binário para demonstrar como o escritor afeta a serialização.</span><span class="sxs-lookup"><span data-stu-id="83de8-105">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83de8-106">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="83de8-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="83de8-107">O contrato `Record` de dados para é mostrado no seguinte código de amostra.</span><span class="sxs-lookup"><span data-stu-id="83de8-107">The data contract for `Record` is shown in the following sample code.</span></span>  
  
```csharp  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
internal class Record  
{  
    private double n1;  
    private double n2;  
    private string operation;  
    private double result;  
  
    internal Record(double n1, double n2, string operation, double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    [DataMember]  
    internal double OperandNumberOne  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [DataMember]  
    internal double OperandNumberTwo  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [DataMember]  
    internal string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]  
    internal double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
  
    public override string ToString()  
    {  
        return $"Record: {n1} {operation} {n2} = {result}";
    }  
}  
```  
  
 <span data-ttu-id="83de8-108">O código de `Record` amostra `record1` cria um objeto chamado e exibe o objeto.</span><span class="sxs-lookup"><span data-stu-id="83de8-108">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="83de8-109">A amostra então <xref:System.Runtime.Serialization.DataContractSerializer> usa `record1` o para serializar em um fluxo de memória.</span><span class="sxs-lookup"><span data-stu-id="83de8-109">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="83de8-110">Em seguida, a <xref:System.Runtime.Serialization.DataContractSerializer> amostra usa o para desserializar o fluxo de memória de volta em um novo `Record` objeto e exibi-lo.</span><span class="sxs-lookup"><span data-stu-id="83de8-110">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="83de8-111">Por padrão, `DataContractSerializer` os codificaobjetos em um fluxo usando uma representação textual de XML.</span><span class="sxs-lookup"><span data-stu-id="83de8-111">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="83de8-112">No entanto, você pode influenciar a codificação do XML passando em um escritor diferente.</span><span class="sxs-lookup"><span data-stu-id="83de8-112">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="83de8-113">A amostra cria um escritor <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>binário chamando .</span><span class="sxs-lookup"><span data-stu-id="83de8-113">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="83de8-114">Em seguida, passa o objeto de gravação e <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>o autor para o serializador quando ele chama .</span><span class="sxs-lookup"><span data-stu-id="83de8-114">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="83de8-115">Finalmente, a amostra libera o escritor e relata a extensão dos córregos.</span><span class="sxs-lookup"><span data-stu-id="83de8-115">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="83de8-116">Quando você executa a amostra, o registro original e o registro desserializado são exibidos, seguido pela comparação entre o comprimento da codificação de texto e a codificação binária.</span><span class="sxs-lookup"><span data-stu-id="83de8-116">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="83de8-117">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="83de8-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="83de8-118">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="83de8-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="83de8-119">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="83de8-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="83de8-120">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="83de8-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="83de8-121">Para executar a amostra, inicie o cliente a partir do prompt de comando digitando client\bin\client.exe.</span><span class="sxs-lookup"><span data-stu-id="83de8-121">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="83de8-122">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="83de8-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="83de8-123">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="83de8-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="83de8-124">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="83de8-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83de8-125">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="83de8-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
