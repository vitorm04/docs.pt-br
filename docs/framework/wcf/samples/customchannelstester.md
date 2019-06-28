---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: 1517a2eb73da778c9b84ff857f4b8ad2b4334498
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425001"
---
# <a name="customchannelstester"></a><span data-ttu-id="96a07-102">CustomChannelsTester</span><span class="sxs-lookup"><span data-stu-id="96a07-102">CustomChannelsTester</span></span>
<span data-ttu-id="96a07-103">O `CustomChannelsTester` é uma ferramenta que você pode usar para testar suas implementações de canal personalizado em um conjunto de contratos de serviço predefinido.</span><span class="sxs-lookup"><span data-stu-id="96a07-103">The `CustomChannelsTester` is a tool that you can use to test your custom channel implementations against a set of predefined service contracts.</span></span> <span data-ttu-id="96a07-104">Você pode selecionar o conjunto de contratos de serviço e passá-lo para a ferramenta usando um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="96a07-104">You can select the set of service contracts and pass it to the tool using an XML file.</span></span> <span data-ttu-id="96a07-105">A ferramenta gera, em seguida, o serviço e o cliente que exercite suas implementações de canal personalizado durante a troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="96a07-105">The tool then generates the service and client that exercises your custom channel implementations during message exchange.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="96a07-106">Para a ferramenta de compilação</span><span class="sxs-lookup"><span data-stu-id="96a07-106">To build the tool</span></span>  
  
1. <span data-ttu-id="96a07-107">Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="96a07-107">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="96a07-108">Compilando a solução gera três arquivos: CustomChannelsTester.exe, TestSpec.xml e SampleRun.cmd.</span><span class="sxs-lookup"><span data-stu-id="96a07-108">Building the solution generates three files: CustomChannelsTester.exe, TestSpec.xml and SampleRun.cmd.</span></span> <span data-ttu-id="96a07-109">O arquivo SampleRun.cmd tem uma linha de comando de exemplo que mostra como usar essa ferramenta para testar o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="96a07-109">The file SampleRun.cmd has a sample command line that shows how to use this tool to test the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="96a07-110">Para executar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="96a07-110">To run the tool</span></span>  
  
- <span data-ttu-id="96a07-111">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="96a07-111">At the command prompt type the following command:</span></span>  
  
    ```  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     <span data-ttu-id="96a07-112">Usando o `/binding` opção é necessária.</span><span class="sxs-lookup"><span data-stu-id="96a07-112">Using the `/binding` option is required.</span></span>  
  
     <span data-ttu-id="96a07-113">`/dll` é necessário se "binding" não é uma associação fornecida pelo sistema fornecida pelo Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="96a07-113">`/dll` is required if "binding" is not a system-provided binding provided by Windows Communication Foundation (WCF).</span></span>  
  
     <span data-ttu-id="96a07-114">`/testspec` é opcional.</span><span class="sxs-lookup"><span data-stu-id="96a07-114">`/testspec` is optional.</span></span>  
  
     <span data-ttu-id="96a07-115">Isso cria o servidor e clientes com base nas especificações de teste e a associação.</span><span class="sxs-lookup"><span data-stu-id="96a07-115">This creates server and clients based on the test specifications and the binding.</span></span>  
  
     <span data-ttu-id="96a07-116">Executa o cliente e servidor e retorna os resultados.</span><span class="sxs-lookup"><span data-stu-id="96a07-116">Executes the client and server and returns the results.</span></span>  
  
     <span data-ttu-id="96a07-117">Este é o XML de exemplo para a descrição das especificações de teste (testspec.xml):</span><span class="sxs-lookup"><span data-stu-id="96a07-117">The following is the sample XML for the description of the test specifications (testspec.xml):</span></span>  
  
    ```xml  
    <TestSpec xmlns="http://WCF/TestSpec" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" >  
    <ServiceContract>  
    <!-- Test a contract which has oneway / twoway operations. If you set ExpandAll = true, both types of contracts are tested -->    <IsOneWay ExpandAll="true">true</IsOneWay>  
    <!-- Test a contract with Asynchronous / Synchronous Operations-->  
        <IsAsync>false</IsAsync>   
    <!-- Test a sessionful / sessionless contract-->      
        <IsSession ExpandAll="true">true</IsSession>  
    <!-- If the Service Contract includes a CallBack Contract-->      
        <IsCallBack ExpandAll="true">true</IsCallBack>  
    </ServiceContract>  
    <TestDetails>  
    <!-- Name of the machine that runs the server - required if you want to run the test crossmachine-->  
        <ServerName>ReplaceThisWithTheServerMachineName</ServerName>  
    <!-- Port Number - Optional-->  
        <Port>8000</Port>  
    <!--URI for the callBack address for the client. The client will receive the messages from the server on this address in case of a CallBack Contract-->  
        <ClientCallBackAddress/>      
    <!-- Duration (in sec) after the server has started, it times out - optional(default = 300sec) -->  
        <ServerTimeout>300</ServerTimeout>  
    <!-- Duration (in sec) before the Client initializes -optional(default = 60sec) -->  
        <ClientTimeout>60</ClientTimeout>  
    <!-- Number of clients for each service - optional(default = 1) -->  
        <NumberOfClients>1</NumberOfClients>  
    <!-- Number of messages each client sends to the service - optional(default = 1) -->  
        <MessagesPerClient>1</MessagesPerClient>  
    </TestDetails>  
    </TestSpec>  
    ```  
