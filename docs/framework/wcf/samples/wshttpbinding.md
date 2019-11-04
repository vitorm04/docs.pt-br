---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 5a2d190fe7dfd5305b47da0e6e67de822cfd695b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424455"
---
# <a name="wshttpbinding"></a><span data-ttu-id="34738-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="34738-102">WSHttpBinding</span></span>
<span data-ttu-id="34738-103">Este exemplo demonstra como implementar um serviço típico e um cliente típico usando Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="34738-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="34738-104">Este exemplo consiste em um programa de console do cliente (Client. exe) e uma biblioteca de serviços hospedado pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="34738-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="34738-105">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="34738-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="34738-106">O contrato é definido pela interface `ICalculator`, que expõe operações matemáticas (adicionar, subtrair, multiplicar e dividir).</span><span class="sxs-lookup"><span data-stu-id="34738-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="34738-107">O cliente faz solicitações síncronas para uma determinada operação matemática e o serviço responde com o resultado.</span><span class="sxs-lookup"><span data-stu-id="34738-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="34738-108">A atividade do cliente fica visível na janela do console.</span><span class="sxs-lookup"><span data-stu-id="34738-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="34738-109">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="34738-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="34738-110">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="34738-110">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="34738-111">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="34738-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="34738-112">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="34738-112">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> <span data-ttu-id="34738-113">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="34738-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="34738-114">Este exemplo expõe o contrato de `ICalculator` usando o [> de wsHttpBinding\<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="34738-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="34738-115">A configuração dessa associação foi expandida no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="34738-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->   
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"   
              transactionFlow="false"   
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"   
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"   
              textEncoding="utf-8"   
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"   
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"   
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="34738-116">No elemento base `binding`, o valor `maxReceivedMessageSize` permite que você configure o tamanho máximo de uma mensagem de entrada (em bytes).</span><span class="sxs-lookup"><span data-stu-id="34738-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="34738-117">O valor `hostNameComparisonMode` permite que você configure se o nome de host é considerado ao Desmultiplexar mensagens para o serviço.</span><span class="sxs-lookup"><span data-stu-id="34738-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="34738-118">O valor `messageEncoding` permite que você configure se deseja usar a codificação de texto ou MTOM para mensagens.</span><span class="sxs-lookup"><span data-stu-id="34738-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="34738-119">O valor `textEncoding` permite configurar a codificação de caracteres para mensagens.</span><span class="sxs-lookup"><span data-stu-id="34738-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="34738-120">O valor `bypassProxyOnLocal` permite que você configure se deseja usar um proxy HTTP para comunicação local.</span><span class="sxs-lookup"><span data-stu-id="34738-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="34738-121">O valor `transactionFlow` define se a transação atual está fluindo (se uma operação estiver configurada para o fluxo de transações).</span><span class="sxs-lookup"><span data-stu-id="34738-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="34738-122">No elemento [\<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) , o valor booliano habilitado define se as sessões confiáveis estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="34738-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="34738-123">O valor `ordered` define se a ordenação da mensagem é preservada.</span><span class="sxs-lookup"><span data-stu-id="34738-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="34738-124">O valor `inactivityTimeout` define por quanto tempo uma sessão pode ficar ociosa antes de ter falhado.</span><span class="sxs-lookup"><span data-stu-id="34738-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="34738-125">No [\<segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), o valor `mode` configura qual modo de segurança deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="34738-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="34738-126">Neste exemplo, a segurança de mensagens está sendo usada, o que é o motivo pelo qual o [\<> de mensagem](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) é especificado dentro do [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="34738-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="34738-127">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="34738-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="34738-128">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="34738-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="34738-129">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="34738-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="34738-130">Instale o ASP.NET 4,0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="34738-130">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="34738-131">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="34738-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="34738-132">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="34738-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="34738-133">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="34738-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
