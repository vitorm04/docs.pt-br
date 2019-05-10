---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: dbd10d1bd08529d11e86c3d9296e68264564a21d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650146"
---
# <a name="customchannelstester"></a>CustomChannelsTester
O `CustomChannelsTester` é uma ferramenta que você pode usar para testar suas implementações de canal personalizado em um conjunto de contratos de serviço predefinido. Você pode selecionar o conjunto de contratos de serviço e passá-lo para a ferramenta usando um arquivo XML. A ferramenta gera, em seguida, o serviço e o cliente que exercite suas implementações de canal personalizado durante a troca de mensagens.  
  
### <a name="to-build-the-tool"></a>Para a ferramenta de compilação  
  
1. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Compilando a solução gera três arquivos: CustomChannelsTester.exe, TestSpec.xml e SampleRun.cmd. O arquivo SampleRun.cmd tem uma linha de comando de exemplo que mostra como usar essa ferramenta para testar o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.  
  
### <a name="to-run-the-tool"></a>Para executar a ferramenta  
  
- No prompt de comando, digite o seguinte comando:  
  
    ```  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     Usando o `/binding` opção é necessária.  
  
     `/dll` é necessário se "binding" não é uma associação fornecida pelo sistema fornecida pelo Windows Communication Foundation (WCF).  
  
     `/testspec` é opcional.  
  
     Isso cria o servidor e clientes com base nas especificações de teste e a associação.  
  
     Executa o cliente e servidor e retorna os resultados.  
  
     Este é o XML de exemplo para a descrição das especificações de teste (testspec.xml):  
  
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
    <!--URI for the callBack address for the CLient. The client will receive the messages from the server on this address in case of a CallBack Contract-->  
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
