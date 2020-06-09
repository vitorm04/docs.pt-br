---
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: 0b2b4d9b22f654fa433c7473160444b41a5adfa4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575141"
---
# <a name="operationcontextscope"></a><span data-ttu-id="cf8d6-102">OperationContextScope</span><span class="sxs-lookup"><span data-stu-id="cf8d6-102">OperationContextScope</span></span>
<span data-ttu-id="cf8d6-103">O exemplo OperationContextScope demonstra como enviar informações extras em uma chamada de Windows Communication Foundation (WCF) usando cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-103">The OperationContextScope sample demonstrates how to send extra information on a Windows Communication Foundation (WCF) call using headers.</span></span> <span data-ttu-id="cf8d6-104">Neste exemplo, o servidor e o cliente são aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-104">In this sample, both the server and client are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf8d6-105">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cf8d6-106">O exemplo demonstra como um cliente pode enviar informações adicionais como um <xref:System.ServiceModel.Channels.MessageHeader> usando <xref:System.ServiceModel.OperationContextScope> .</span><span class="sxs-lookup"><span data-stu-id="cf8d6-106">The sample demonstrates how a client can send additional information as a <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span></span> <span data-ttu-id="cf8d6-107">Um <xref:System.ServiceModel.OperationContextScope> objeto é criado com o escopo para um canal.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-107">An <xref:System.ServiceModel.OperationContextScope> object is created by scoping it to a channel.</span></span> <span data-ttu-id="cf8d6-108">Os cabeçalhos que devem ser convertidos no serviço remoto podem ser adicionados à <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-108">Headers that must be translated to the remote service can be added to the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="cf8d6-109">Os cabeçalhos adicionados a essa coleção podem ser recuperados no serviço acessando <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> .</span><span class="sxs-lookup"><span data-stu-id="cf8d6-109">Headers added to this collection can be retrieved on the service by accessing <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span></span> <span data-ttu-id="cf8d6-110">Suas chamadas são feitas em vários canais e, em seguida, os cabeçalhos adicionados ao cliente se aplicam somente ao canal que foi usado para criar o <xref:System.ServiceModel.OperationContextScope> .</span><span class="sxs-lookup"><span data-stu-id="cf8d6-110">Its calls are made on multiple channels and then the headers added to the client only apply to the channel that was used to create the <xref:System.ServiceModel.OperationContextScope>.</span></span>  
  
## <a name="messageheaderreader"></a><span data-ttu-id="cf8d6-111">MessageHeaderReader</span><span class="sxs-lookup"><span data-stu-id="cf8d6-111">MessageHeaderReader</span></span>  
 <span data-ttu-id="cf8d6-112">Esse é o serviço de exemplo que recebe uma mensagem do cliente e tenta pesquisar o cabeçalho na <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-112">This is the sample service that receives a message from the client and tries to look up the header in the <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="cf8d6-113">O cliente passa o GUID que ele enviou no cabeçalho e o serviço recupera o cabeçalho personalizado e, se presente, compara-o com o GUID passado como o argumento pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-113">The client passes the GUID that it sent in the header and the service retrieves the custom header and, if present, compares it with the GUID passed as the argument by the client.</span></span>  
  
```csharp
public bool RetrieveHeader(string guid)  
{  
     MessageHeaders messageHeaderCollection =
             OperationContext.Current.IncomingMessageHeaders;  
     String guidHeader = null;  
  
     Console.WriteLine("Trying to check if IncomingMessageHeader " +  
               " collection contains header with value {0}", guid);  
     if (messageHeaderCollection.FindHeader(  
                       CustomHeader.HeaderName,
                       CustomHeader.HeaderNamespace) != -1)  
     {  
          guidHeader = messageHeaderCollection.GetHeader<String>(  
           CustomHeader.HeaderName, CustomHeader.HeaderNamespace);  
     }  
     else  
     {  
          Console.WriteLine("No header was found");  
     }  
     if (guidHeader != null)  
     {  
          Console.WriteLine("Found header with value {0}. "+
         "Does it match with GUID sent as parameter: {1}",
          guidHeader, guidHeader.Equals(guid));  
      }  
  
      Console.WriteLine();  
      //Return true if header is present and equals the guid sent by  
      // client as argument  
      return (guidHeader != null && guidHeader.Equals(guid));  
}  
```  
  
## <a name="messageheaderclient"></a><span data-ttu-id="cf8d6-114">MessageHeaderClient</span><span class="sxs-lookup"><span data-stu-id="cf8d6-114">MessageHeaderClient</span></span>  
 <span data-ttu-id="cf8d6-115">Essa é a implementação do cliente que usa o proxy gerado pela [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) para se comunicar com o serviço remoto.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-115">This is the client implementation that uses the proxy generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to communicate with the remote service.</span></span> <span data-ttu-id="cf8d6-116">Primeiro, ele cria dois objetos proxy do `MessageHeaderReaderClient` .</span><span class="sxs-lookup"><span data-stu-id="cf8d6-116">It first creates two proxy objects of `MessageHeaderReaderClient`.</span></span>  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 <span data-ttu-id="cf8d6-117">Em seguida, o cliente cria um OperationContextScope e o escopo para `client1` .</span><span class="sxs-lookup"><span data-stu-id="cf8d6-117">Client then creates an OperationContextScope and scopes it to `client1`.</span></span> <span data-ttu-id="cf8d6-118">Ele adiciona um <xref:System.ServiceModel.Channels.MessageHeader> a <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> e invoca uma chamada em ambos os clientes.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-118">It adds a <xref:System.ServiceModel.Channels.MessageHeader> to <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> and invokes one call on both clients.</span></span> <span data-ttu-id="cf8d6-119">Ele garante que o cabeçalho seja enviado somente `client1` e não ativado `client2` , verificando o valor de retorno da `RetrieveHeader` chamada.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-119">It ensures that the header is sent only on `client1` and not on `client2` by checking the return value from the `RetrieveHeader` call.</span></span>  
  
```csharp
using (new OperationContextScope(client1.InnerChannel))  
{  
    //Create a new GUID that is sent as the header.  
    String guid = Guid.NewGuid().ToString();  
  
    //Create a MessageHeader for the GUID we just created.  
    MessageHeader customHeader = MessageHeader.CreateHeader(CustomHeader.HeaderName, CustomHeader.HeaderNamespace, guid);  
  
    //Add the header to the OutgoingMessageHeader collection.  
    OperationContext.Current.OutgoingMessageHeaders.Add(customHeader);  
  
    //Now call RetrieveHeader on both the proxies. Since the OperationContextScope is tied to
    //client1's InnerChannel, the header should only be added to calls made on that client.  
    //Calls made on client2 should not be sending the header across even though the call  
    //is made in the same OperationContextScope.  
    Console.WriteLine("Using client1 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: True", client1.RetrieveHeader(guid));  
  
    Console.WriteLine();  
    Console.WriteLine("Using client2 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: False", client2.RetrieveHeader(guid));  
}  
```  
  
 <span data-ttu-id="cf8d6-120">Este exemplo é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-120">This sample is self-hosted.</span></span> <span data-ttu-id="cf8d6-121">A seguinte saída de exemplo da execução do exemplo é fornecida:</span><span class="sxs-lookup"><span data-stu-id="cf8d6-121">The following sample output from running the sample is provided:</span></span>  
  
```console  
Prompt> Service.exe  
The service is ready.  
Press <ENTER> to terminate service.  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
Found header with value 2239da67-546f-42d4-89dc-8eb3c06215d8. Does it match with GUID sent as parameter: True  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
No header was found  
  
Prompt>Client.exe  
Using client1 to send message  
Did server retrieve the header? : Actual: True, Expected: True  
  
Using client2 to send message  
Did server retrieve the header? : Actual: False, Expected: False  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cf8d6-122">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="cf8d6-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cf8d6-123">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf8d6-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cf8d6-124">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf8d6-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cf8d6-125">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf8d6-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cf8d6-126">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cf8d6-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="cf8d6-128">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cf8d6-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cf8d6-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
