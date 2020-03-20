---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: c23bd3eddd49972b7083347fed88d4e70707ae58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183805"
---
# <a name="customchannelstester"></a>CustomChannelsTester
A `CustomChannelsTester` é uma ferramenta que você pode usar para testar suas implementações de canais personalizados contra um conjunto de contratos de serviço predefinidos. Você pode selecionar o conjunto de contratos de serviço e passá-lo para a ferramenta usando um arquivo XML. A ferramenta então gera o serviço e o cliente que exerce suas implementações personalizadas de canal durante a troca de mensagens.  
  
### <a name="to-build-the-tool"></a>Para construir a ferramenta  
  
1. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. A construção da solução gera três arquivos: CustomChannelsTester.exe, TestSpec.xml e SampleRun.cmd. O arquivo SampleRun.cmd tem uma linha de comando de amostra que mostra como usar esta ferramenta para testar a amostra [Transport: UDP.](../../../../docs/framework/wcf/samples/transport-udp.md)  
  
### <a name="to-run-the-tool"></a>Para executar a ferramenta  
  
- No prompt de comando digite o seguinte comando:  
  
    ```console  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     É `/binding` necessário usar a opção.  
  
     `/dll`é necessário se "vinculação" não for uma vinculação fornecida pelo sistema fornecida pela Windows Communication Foundation (WCF).  
  
     `/testspec` é opcional.  
  
     Isso cria servidores e clientes com base nas especificações do teste e na vinculação.  
  
     Executa o cliente e o servidor e retorna os resultados.  
  
     A seguir está a amostra XML para a descrição das especificações do teste (testspec.xml):  
  
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
