---
title: WSHttpBinding
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8ff105c626f72d34cf6963586a84aba945b5af01
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="wshttpbinding"></a><span data-ttu-id="50df7-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="50df7-102">WSHttpBinding</span></span>
<span data-ttu-id="50df7-103">Este exemplo demonstra como implementar um serviço típico e um cliente típico usando [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50df7-103">This sample demonstrates how to implement a typical service and a typical client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="50df7-104">Este exemplo consiste em um programa de console de cliente (client.exe) e uma biblioteca de serviços hospedados pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="50df7-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="50df7-105">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="50df7-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="50df7-106">O contrato é definido pelo `ICalculator` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir).</span><span class="sxs-lookup"><span data-stu-id="50df7-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="50df7-107">O cliente faz solicitações síncronas para uma operação matemática determinado e as respostas do serviço com o resultado.</span><span class="sxs-lookup"><span data-stu-id="50df7-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="50df7-108">Atividade do cliente estiver visível na janela do console.</span><span class="sxs-lookup"><span data-stu-id="50df7-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="50df7-109">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="50df7-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="50df7-110">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="50df7-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="50df7-111">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="50df7-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="50df7-112">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="50df7-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  <span data-ttu-id="50df7-113">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="50df7-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="50df7-114">Este exemplo expõe o `ICalculator` contrato usando o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="50df7-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="50df7-115">A configuração desta associação foi expandida no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="50df7-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
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
  
 <span data-ttu-id="50df7-116">Na base de `binding` elemento, o `maxReceivedMessageSize` valor permite que você configure o tamanho máximo de uma mensagem de entrada (em bytes).</span><span class="sxs-lookup"><span data-stu-id="50df7-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="50df7-117">O `hostNameComparisonMode` valor permite que você configure se o nome do host é considerada quando eliminação multiplexação mensagens para o serviço.</span><span class="sxs-lookup"><span data-stu-id="50df7-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="50df7-118">O `messageEncoding` valor lhe permite configurar se deseja usar a codificação para mensagens de texto ou MTOM.</span><span class="sxs-lookup"><span data-stu-id="50df7-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="50df7-119">O `textEncoding` valor permite que você configure a codificação de caracteres para mensagens.</span><span class="sxs-lookup"><span data-stu-id="50df7-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="50df7-120">O `bypassProxyOnLocal` valor permite que você configure a possibilidade de usar um proxy HTTP para comunicação local.</span><span class="sxs-lookup"><span data-stu-id="50df7-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="50df7-121">O `transactionFlow` valor configura se a transação atual flui (se uma operação está configurada para fluxo de transações).</span><span class="sxs-lookup"><span data-stu-id="50df7-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="50df7-122">Sobre o [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) elemento, o valor booliano habilitado configura se sessões confiáveis estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="50df7-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="50df7-123">O `ordered` valor configura se a mensagem ordenação é preservada.</span><span class="sxs-lookup"><span data-stu-id="50df7-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="50df7-124">O `inactivityTimeout` valor configura quanto tempo uma sessão pode ficar ociosa antes que está sendo com defeito.</span><span class="sxs-lookup"><span data-stu-id="50df7-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="50df7-125">Sobre o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), o `mode` valor configura o modo de segurança deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="50df7-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="50df7-126">Neste exemplo, segurança de mensagens está sendo usada, que é por isso que o [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) é especificada dentro de [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="50df7-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="50df7-127">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="50df7-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="50df7-128">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="50df7-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="50df7-129">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="50df7-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="50df7-130">Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="50df7-130">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="50df7-131">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="50df7-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="50df7-132">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="50df7-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="50df7-133">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="50df7-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50df7-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50df7-134">See Also</span></span>
