---
title: Serialização JSON
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: bb38005c02e9b3e850282d2a81c2e17143657025
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305280"
---
# <a name="json-serialization"></a><span data-ttu-id="0b4b6-102">Serialização JSON</span><span class="sxs-lookup"><span data-stu-id="0b4b6-102">JSON Serialization</span></span>
<span data-ttu-id="0b4b6-103">Este exemplo demonstra como usar o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> para serializar e desserializar dados no formato JSON (JavaScript Object Notation).</span><span class="sxs-lookup"><span data-stu-id="0b4b6-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="0b4b6-104">Esse mecanismo de serialização converte dados JSON em instâncias de tipos [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] e de volta em dados JSON.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-104">This serialization engine converts JSON data into instances of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and back into JSON data.</span></span> <span data-ttu-id="0b4b6-105">O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> dá suporte aos mesmos tipos que o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="0b4b6-106">O formato de dados JSON é especialmente útil ao escrever aplicativos Web de estilo AJAX (Asynchronous JavaScript and XML).</span><span class="sxs-lookup"><span data-stu-id="0b4b6-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="0b4b6-107">Suporte a AJAX no Windows Communication Foundation (WCF) é otimizado para uso com o ASP.NET AJAX por meio do controle ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="0b4b6-108">Para obter exemplos de como usar o Windows Communication Foundation (WCF) com o ASP.NET AJAX, consulte o [amostras do AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="0b4b6-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b4b6-109">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0b4b6-110">Este exemplo usa um contrato de dados `Person` para demonstrar a serialização e a desserialização.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 <span data-ttu-id="0b4b6-111">Para serializar uma instância do tipo `Person` para JSON, crie primeiro o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e use o método `WriteObject` para gravar dados JSON em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="0b4b6-112">O fluxo de memória contém dados JSON válidos.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="0b4b6-113">O exemplo demonstra a desserialização de dados JSON em um objeto.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="0b4b6-114">Em seguida, você volta o fluxo e chama `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="0b4b6-115">Examinar o objeto `p2` revela que os dados JSON foram desserializados corretamente.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0b4b6-116">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0b4b6-117">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0b4b6-118">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0b4b6-119">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0b4b6-120">Para configurar, compilar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0b4b6-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="0b4b6-121">Compile a solução jsonSerialization, conforme descrito em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0b4b6-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="0b4b6-122">Execute o aplicativo de console resultante.</span><span class="sxs-lookup"><span data-stu-id="0b4b6-122">Run the resulting console application.</span></span>  
