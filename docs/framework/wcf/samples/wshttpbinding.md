---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: c54cbf1fe881ef2ce5dffb0bc0c6dac4049135b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143363"
---
# <a name="wshttpbinding"></a><span data-ttu-id="78e03-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="78e03-102">WSHttpBinding</span></span>
<span data-ttu-id="78e03-103">Esta amostra demonstra como implementar um serviço típico e um cliente típico usando o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="78e03-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="78e03-104">Esta amostra consiste em um programa de console cliente (client.exe) e uma biblioteca de serviços hospedada pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="78e03-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="78e03-105">O serviço implementa um contrato que define um padrão de comunicação solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="78e03-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="78e03-106">O contrato é `ICalculator` definido pela interface, que expõe as operações matemáticas (adicionar, subtrair, multiplicar e dividir).</span><span class="sxs-lookup"><span data-stu-id="78e03-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="78e03-107">O cliente faz solicitações síncronas para uma determinada operação matemática e o serviço responde com o resultado.</span><span class="sxs-lookup"><span data-stu-id="78e03-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="78e03-108">A atividade do cliente é visível na janela do console.</span><span class="sxs-lookup"><span data-stu-id="78e03-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="78e03-109">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="78e03-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="78e03-110">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="78e03-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="78e03-111">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="78e03-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="78e03-112">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="78e03-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> <span data-ttu-id="78e03-113">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="78e03-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="78e03-114">Esta amostra expõe `ICalculator` o contrato usando o [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="78e03-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="78e03-115">A configuração desta vinculação foi expandida no arquivo Web.config.</span><span class="sxs-lookup"><span data-stu-id="78e03-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
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
  
 <span data-ttu-id="78e03-116">No elemento `binding` base, `maxReceivedMessageSize` o valor permite configurar o tamanho máximo de uma mensagem recebida (em bytes).</span><span class="sxs-lookup"><span data-stu-id="78e03-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="78e03-117">O `hostNameComparisonMode` valor permite configurar se o nome do host é considerado ao desmultiplelizar mensagens para o serviço.</span><span class="sxs-lookup"><span data-stu-id="78e03-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="78e03-118">O `messageEncoding` valor permite configurar se deve usar a codificação Texto ou MTOM para mensagens.</span><span class="sxs-lookup"><span data-stu-id="78e03-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="78e03-119">O `textEncoding` valor permite configurar a codificação de caracteres para mensagens.</span><span class="sxs-lookup"><span data-stu-id="78e03-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="78e03-120">O `bypassProxyOnLocal` valor permite configurar se deve usar um proxy HTTP para comunicação local.</span><span class="sxs-lookup"><span data-stu-id="78e03-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="78e03-121">O `transactionFlow` valor configura se a transação atual é fluída (se uma operação está configurada para o fluxo de transações).</span><span class="sxs-lookup"><span data-stu-id="78e03-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="78e03-122">No elemento [ \<>de Sessão confiável,](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) o valor booleano ativado configura se as sessões confiáveis estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="78e03-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="78e03-123">O `ordered` valor configura se o pedido de mensagem é preservado.</span><span class="sxs-lookup"><span data-stu-id="78e03-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="78e03-124">O `inactivityTimeout` valor configura quanto tempo uma sessão pode ficar ociosa antes de ser defeituosa.</span><span class="sxs-lookup"><span data-stu-id="78e03-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="78e03-125">No [ \<>de ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` segurança , o valor configura qual modo de segurança deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="78e03-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="78e03-126">Nesta amostra, a segurança das mensagens está sendo usada, e [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)é por isso que a [ \<mensagem>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) é especificada dentro do>de segurança .</span><span class="sxs-lookup"><span data-stu-id="78e03-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="78e03-127">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="78e03-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="78e03-128">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="78e03-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="78e03-129">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="78e03-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="78e03-130">Instale ASP.NET 4.0 usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="78e03-130">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="78e03-131">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="78e03-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="78e03-132">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="78e03-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="78e03-133">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="78e03-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
