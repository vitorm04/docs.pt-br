---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 62075cccfa8ff2c6a181d633756a5f9bc8969932
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858971"
---
# <a name="srmp"></a><span data-ttu-id="ef111-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="ef111-102">SRMP</span></span>
<span data-ttu-id="ef111-103">Este exemplo demonstra como executar transacionada comunicação em fila usando o serviço de enfileiramento de mensagens (MSMQ) em HTTP.</span><span class="sxs-lookup"><span data-stu-id="ef111-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="ef111-104">Comunicação em fila, o cliente se comunica com o serviço usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="ef111-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="ef111-105">Mais precisamente, o cliente envia mensagens a uma fila.</span><span class="sxs-lookup"><span data-stu-id="ef111-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="ef111-106">O serviço recebe mensagens da fila.</span><span class="sxs-lookup"><span data-stu-id="ef111-106">The service receives messages from the queue.</span></span> <span data-ttu-id="ef111-107">O serviço e o cliente, portanto, não precisa estar em execução ao mesmo tempo para se comunicar usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="ef111-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="ef111-108">MSMQ permite o uso de HTTP (incluindo o uso de HTTPS) para enviar mensagens para uma fila.</span><span class="sxs-lookup"><span data-stu-id="ef111-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="ef111-109">Neste exemplo, vamos demonstrar o usar o Windows Communication Foundation (WCF) na fila para a comunicação e como enviar mensagens via HTTP.</span><span class="sxs-lookup"><span data-stu-id="ef111-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="ef111-110">MSMQ usa um protocolo chamado SRMP, que é um protocolo baseado em SOAP para a comunicação por HTTP.</span><span class="sxs-lookup"><span data-stu-id="ef111-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ef111-111">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ef111-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ef111-112">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef111-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ef111-113">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef111-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ef111-114">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef111-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="ef111-115">Antes de executar a amostra **Adicionar/remover componentes do Windows**, certifique-se de que o MSMQ está instalado com o suporte a HTTP.</span><span class="sxs-lookup"><span data-stu-id="ef111-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="ef111-116">Instalando o suporte a HTTP automaticamente instala os serviços de informações da Internet (IIS) e adiciona o suporte de protocolo no IIS para o MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ef111-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5.  <span data-ttu-id="ef111-117">Se você quiser ter certeza de que o HTTP é usado para comunicação, você pode habilitar o MSMQ seja executado no modo protegido.</span><span class="sxs-lookup"><span data-stu-id="ef111-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="ef111-118">Isso garante que nenhuma mensagem para qualquer fila hospedada na máquina pode chegar usando qualquer transporte não HTTP.</span><span class="sxs-lookup"><span data-stu-id="ef111-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6.  <span data-ttu-id="ef111-119">Depois que você tiver selecionado o MSMQ seja executado no modo protegido, o computador requer a reinicialização do computador em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ef111-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
7.  <span data-ttu-id="ef111-120">Execute o serviço.</span><span class="sxs-lookup"><span data-stu-id="ef111-120">Run the service.</span></span>  
  
8.  <span data-ttu-id="ef111-121">Execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="ef111-121">Run the client.</span></span> <span data-ttu-id="ef111-122">Certifique-se de que você altere o endereço do ponto de extremidade para apontar para o nome do computador ou endereço IP em vez do localhost.</span><span class="sxs-lookup"><span data-stu-id="ef111-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="ef111-123">O cliente envia uma mensagem e sai.</span><span class="sxs-lookup"><span data-stu-id="ef111-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef111-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef111-124">Requirements</span></span>  
 <span data-ttu-id="ef111-125">Para executar este exemplo, o IIS deve ser instalado sobre o serviço e os computadores cliente, além de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ef111-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="ef111-126">Demonstra</span><span class="sxs-lookup"><span data-stu-id="ef111-126">Demonstrates</span></span>  
 <span data-ttu-id="ef111-127">O exemplo demonstra como enviar WCF usando o MSMQ em HTTP de mensagens na fila.</span><span class="sxs-lookup"><span data-stu-id="ef111-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="ef111-128">Isso também é chamado de mensagens SRMP.</span><span class="sxs-lookup"><span data-stu-id="ef111-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="ef111-129">Quando uma mensagem na fila foi enviada, MSMQ em transferências de máquina as mensagens de envio para o Gerenciador de fila de recebimento pelo transporte TCP ou HTTP.</span><span class="sxs-lookup"><span data-stu-id="ef111-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="ef111-130">Escolhendo SRMP, o usuário indica a escolha de HTTP como um transporte para a transferência da fila.</span><span class="sxs-lookup"><span data-stu-id="ef111-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="ef111-131">Proteger SRMP permite o uso de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ef111-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef111-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ef111-132">Example</span></span>  
 <span data-ttu-id="ef111-133">O código de exemplo se baseia na amostra transacionada.</span><span class="sxs-lookup"><span data-stu-id="ef111-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="ef111-134">Como você pode envia uma mensagem à fila e recebe uma mensagem da fila usando SRMP equivale a enviar e receber mensagens usando um protocolo nativo.</span><span class="sxs-lookup"><span data-stu-id="ef111-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="ef111-135">A configuração para o cliente é alterada para indicar que a opção de protocolo de transferência de fila.</span><span class="sxs-lookup"><span data-stu-id="ef111-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="ef111-136">O protocolo de transferência de fila pode ser um dos nativo, SRMP ou SrmpSecure.</span><span class="sxs-lookup"><span data-stu-id="ef111-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="ef111-137">Por padrão, o protocolo de transferência é nativo.</span><span class="sxs-lookup"><span data-stu-id="ef111-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="ef111-138">O cliente e o serviço especificam na configuração para usar SRMP neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="ef111-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="ef111-139">Há limitações para SRMP em relação à segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="ef111-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="ef111-140">A segurança do transporte MSMQ padrão requer o Active Directory que exige que o Gerenciador de fila de envio e o Gerenciador de fila de recebimento residam no mesmo domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="ef111-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="ef111-141">Isso não é possível quando o envio de mensagens por limites HTTP.</span><span class="sxs-lookup"><span data-stu-id="ef111-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="ef111-142">Como tal, a segurança de transporte padrão não funciona.</span><span class="sxs-lookup"><span data-stu-id="ef111-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="ef111-143">A segurança de transporte deve ser definida para o certificado se segurança de transporte é desejada.</span><span class="sxs-lookup"><span data-stu-id="ef111-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="ef111-144">Segurança de mensagem também pode ser usada para proteger a mensagem.</span><span class="sxs-lookup"><span data-stu-id="ef111-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="ef111-145">Neste exemplo, segurança de transporte e de mensagem é desativada para ilustrar SRMP de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ef111-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
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
          <security mode="None"></security>  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="ef111-146">Executar o exemplo produz a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="ef111-146">Running the sample yields the following output.</span></span>  
  
```  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="ef111-147">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ef111-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ef111-148">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ef111-148">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ef111-149">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ef111-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ef111-150">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ef111-150">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
  
## <a name="see-also"></a><span data-ttu-id="ef111-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef111-151">See Also</span></span>
