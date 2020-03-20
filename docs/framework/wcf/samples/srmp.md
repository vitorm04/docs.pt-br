---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: b1b61c18c801059e95cd0b13a3135132a583882f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183336"
---
# <a name="srmp"></a><span data-ttu-id="e3700-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="e3700-102">SRMP</span></span>
<span data-ttu-id="e3700-103">Esta amostra demonstra como executar a comunicação transacionada enfileirada usando a Fila de Mensagens (MSMQ) em HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3700-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="e3700-104">Na comunicação enfileirada, o cliente se comunica com o serviço usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="e3700-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="e3700-105">Mais precisamente, o cliente envia mensagens para uma fila.</span><span class="sxs-lookup"><span data-stu-id="e3700-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="e3700-106">O serviço recebe mensagens da fila.</span><span class="sxs-lookup"><span data-stu-id="e3700-106">The service receives messages from the queue.</span></span> <span data-ttu-id="e3700-107">O serviço e o cliente, portanto, não precisa estar funcionando ao mesmo tempo para se comunicar usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="e3700-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="e3700-108">O MSMQ permite o uso de HTTP (incluindo o uso de HTTPS) para enviar mensagens para uma fila.</span><span class="sxs-lookup"><span data-stu-id="e3700-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="e3700-109">Neste exemplo, demonstramos usando a comunicação enfileirada da Windows Communication Foundation (WCF) e como enviar mensagens através de HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3700-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="e3700-110">O MSMQ usa um protocolo chamado SRMP, que é um protocolo baseado em SOAP para comunicação via HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3700-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e3700-111">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e3700-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e3700-112">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e3700-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e3700-113">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e3700-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e3700-114">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e3700-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="e3700-115">Antes de executar a amostra em **Adicionar/Remover Componentes do Windows,** certifique-se de que o MSMQ esteja instalado com suporte http.</span><span class="sxs-lookup"><span data-stu-id="e3700-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="e3700-116">A instalação do suporte HTTP instala automaticamente o IIS (Internet Information Services, serviços de informação da Internet) e adiciona o suporte ao protocolo no IIS para MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e3700-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5. <span data-ttu-id="e3700-117">Se você quiser ter certeza de que http é usado para comunicação, você pode habilitar o MSMQ para executar no modo endurecido.</span><span class="sxs-lookup"><span data-stu-id="e3700-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="e3700-118">Isso garante que nenhuma mensagem para qualquer fila hospedada na máquina possa chegar usando qualquer transporte não-HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3700-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6. <span data-ttu-id="e3700-119">Depois de ter selecionado o MSMQ para ser executado no modo endurecido, a máquina requer uma reinicialização no Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="e3700-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on Windows Server 2003.</span></span>  
  
7. <span data-ttu-id="e3700-120">Executar o serviço.</span><span class="sxs-lookup"><span data-stu-id="e3700-120">Run the service.</span></span>  
  
8. <span data-ttu-id="e3700-121">Corra com o cliente.</span><span class="sxs-lookup"><span data-stu-id="e3700-121">Run the client.</span></span> <span data-ttu-id="e3700-122">Certifique-se de alterar o endereço do ponto final para apontar para o nome da máquina ou endereço IP em vez de localhost.</span><span class="sxs-lookup"><span data-stu-id="e3700-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="e3700-123">O cliente envia uma mensagem e sai.</span><span class="sxs-lookup"><span data-stu-id="e3700-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3700-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3700-124">Requirements</span></span>  
 <span data-ttu-id="e3700-125">Para executar esta amostra, o IIS deve ser instalado tanto no serviço quanto nas máquinas clientes, além do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e3700-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e3700-126">Demonstra</span><span class="sxs-lookup"><span data-stu-id="e3700-126">Demonstrates</span></span>  
 <span data-ttu-id="e3700-127">A amostra demonstra o envio de mensagens enfileiradas wcf usando MSMQ em HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3700-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="e3700-128">Isso também é chamado de mensagens SRMP.</span><span class="sxs-lookup"><span data-stu-id="e3700-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="e3700-129">Quando uma mensagem enfileirada é enviada, o MSMQ na máquina de envio transfere as mensagens para o gerenciador de fila saudosista sobre transporte TCP ou HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3700-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="e3700-130">Ao escolher o SRMP, o usuário indica a escolha do HTTP como um transporte para transferência de fila.</span><span class="sxs-lookup"><span data-stu-id="e3700-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="e3700-131">O SRMP Secure permite o uso de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e3700-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3700-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3700-132">Example</span></span>  
 <span data-ttu-id="e3700-133">O código amostral é baseado na amostra transacionada.</span><span class="sxs-lookup"><span data-stu-id="e3700-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="e3700-134">Como você envia uma mensagem para a fila e recebe uma mensagem da fila usando srmp é o mesmo que enviar e receber mensagens usando um protocolo Nativo.</span><span class="sxs-lookup"><span data-stu-id="e3700-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="e3700-135">A configuração para o cliente é alterada para indicar a escolha do protocolo de transferência de fila.</span><span class="sxs-lookup"><span data-stu-id="e3700-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="e3700-136">O protocolo de transferência de fila saem de nativo, SRMP ou SrmpSecure.</span><span class="sxs-lookup"><span data-stu-id="e3700-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="e3700-137">Por padrão, o protocolo de transferência é nativo.</span><span class="sxs-lookup"><span data-stu-id="e3700-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="e3700-138">O cliente e o serviço especificam na configuração para usar o SRMP neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="e3700-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="e3700-139">Existem limitações ao SRMP em relação à segurança do transporte.</span><span class="sxs-lookup"><span data-stu-id="e3700-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="e3700-140">O segurança de transporte MSMQ padrão requer o Active Directory que requer que o gerenciador de fila de envio e o gerenciador de fila socérea residam no mesmo domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="e3700-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="e3700-141">Isso não é possível ao enviar mensagens através do limite HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3700-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="e3700-142">Como tal, a segurança padrão do transporte não funciona.</span><span class="sxs-lookup"><span data-stu-id="e3700-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="e3700-143">A segurança do transporte deve ser definida como Certificado se a segurança do transporte for desejada.</span><span class="sxs-lookup"><span data-stu-id="e3700-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="e3700-144">A segurança das mensagens também pode ser usada para proteger a mensagem.</span><span class="sxs-lookup"><span data-stu-id="e3700-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="e3700-145">Nesta amostra, tanto o transporte quanto a segurança de mensagens são desligados para ilustrar as mensagens SRMP.</span><span class="sxs-lookup"><span data-stu-id="e3700-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"
           bindingConfiguration="srmpBinding"
           binding="netMsmqBinding"
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="e3700-146">A execução da amostra produz a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="e3700-146">Running the sample yields the following output.</span></span>  
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4
Customer: somecustomer.com
OrderDetails
    Order LineItem: 54 of Blue Widget @unit price: $29.99
    Order LineItem: 890 of Red Widget @unit price: $45.89
    Total cost of this order: $42461.56
    Order status: Pending  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="e3700-147">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e3700-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e3700-148">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e3700-148">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e3700-149">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="e3700-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e3700-150">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e3700-150">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
