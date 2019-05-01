---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: d8453d85afb92c69bdf3066ccb8b31e26a34c6d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006480"
---
# <a name="wshttpbinding"></a><span data-ttu-id="ad673-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="ad673-102">WSHttpBinding</span></span>
<span data-ttu-id="ad673-103">Este exemplo demonstra como implementar um serviço típico e um cliente típico usando o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ad673-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="ad673-104">Esse exemplo consiste em um programa de console de cliente (client.exe) e uma biblioteca de serviço hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="ad673-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="ad673-105">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="ad673-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="ad673-106">O contrato é definido o `ICalculator` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir).</span><span class="sxs-lookup"><span data-stu-id="ad673-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="ad673-107">O cliente faz solicitações síncronas para uma operação matemática determinado e as respostas de serviço com o resultado.</span><span class="sxs-lookup"><span data-stu-id="ad673-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="ad673-108">Atividade do cliente está visível na janela do console.</span><span class="sxs-lookup"><span data-stu-id="ad673-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ad673-109">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ad673-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ad673-110">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ad673-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ad673-111">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ad673-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ad673-112">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ad673-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  <span data-ttu-id="ad673-113">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ad673-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ad673-114">Este exemplo exibe a `ICalculator` contrato usando o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ad673-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="ad673-115">A configuração desta associação foi expandida no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="ad673-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
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
  
 <span data-ttu-id="ad673-116">Na base `binding` elemento, o `maxReceivedMessageSize` valor permite que você configure o tamanho máximo de uma mensagem de entrada (em bytes).</span><span class="sxs-lookup"><span data-stu-id="ad673-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="ad673-117">O `hostNameComparisonMode` valor permite que você configure se o nome do host é considerado ao demultiplexação mensagens para o serviço.</span><span class="sxs-lookup"><span data-stu-id="ad673-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="ad673-118">O `messageEncoding` valor permite que você configure se é necessário usar a codificação para mensagens de texto ou MTOM.</span><span class="sxs-lookup"><span data-stu-id="ad673-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="ad673-119">O `textEncoding` valor permite que você configure a codificação de caracteres de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ad673-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="ad673-120">O `bypassProxyOnLocal` valor lhe permite configurar se deseja usar um proxy HTTP para comunicação local.</span><span class="sxs-lookup"><span data-stu-id="ad673-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="ad673-121">O `transactionFlow` valor configura se flui a transação atual (se uma operação está configurada para o fluxo de transações).</span><span class="sxs-lookup"><span data-stu-id="ad673-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="ad673-122">Sobre o [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) elemento, o valor booliano habilitado configura se sessões confiáveis são habilitadas.</span><span class="sxs-lookup"><span data-stu-id="ad673-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="ad673-123">O `ordered` valor configura se a mensagem de ordenação é preservada.</span><span class="sxs-lookup"><span data-stu-id="ad673-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="ad673-124">O `inactivityTimeout` valor configura quanto tempo uma sessão pode ficar ociosa antes que está sendo com defeito.</span><span class="sxs-lookup"><span data-stu-id="ad673-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="ad673-125">Sobre o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), o `mode` valor configura o modo de segurança deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="ad673-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="ad673-126">Neste exemplo, segurança de mensagens está sendo usada, que é por isso que o [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) especificado dentro de [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ad673-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="ad673-127">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="ad673-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ad673-128">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="ad673-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ad673-129">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ad673-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ad673-130">Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="ad673-130">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="ad673-131">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ad673-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="ad673-132">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ad673-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="ad673-133">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ad673-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
