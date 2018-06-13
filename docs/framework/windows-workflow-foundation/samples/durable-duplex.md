---
title: Frente e verso durável
ms.date: 03/30/2017
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
ms.openlocfilehash: 3df5ba962ef33594df1eaebc20789fa9e2d35244
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809421"
---
# <a name="durable-duplex"></a><span data-ttu-id="58d82-102">Frente e verso durável</span><span class="sxs-lookup"><span data-stu-id="58d82-102">Durable Duplex</span></span>
<span data-ttu-id="58d82-103">Este exemplo demonstra como instalar e configurar o exchange mensagem duplex durável usando as atividades de mensagens no Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="58d82-103">This sample demonstrates how to set up and configure durable duplex message exchange using the messaging activities in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="58d82-104">Uma troca frente e verso durável de mensagem é uma troca bidirecional de mensagem que ocorra um longo período de tempo.</span><span class="sxs-lookup"><span data-stu-id="58d82-104">A durable duplex message exchange is a two-way message exchange that takes place over a long period of time.</span></span> <span data-ttu-id="58d82-105">O tempo de vida de troca de mensagem pode ser maior que o tempo de vida do canal de comunicação e o tempo de vida de memória das instâncias de serviço.</span><span class="sxs-lookup"><span data-stu-id="58d82-105">The lifetime of the message exchange may be longer than the lifetime of the communication channel and the in-memory lifetime of the service instances.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="58d82-106">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="58d82-106">Sample Details</span></span>  
 <span data-ttu-id="58d82-107">Neste exemplo, dois serviços do Windows Communication Foundation (WCF) implementados usando o Windows Workflow Foundation são configurados para ter uma troca de mensagens duplex durável.</span><span class="sxs-lookup"><span data-stu-id="58d82-107">In this sample, two Windows Communication Foundation (WCF) services implemented using Windows Workflow Foundation are configured to have a durable duplex message exchange.</span></span> <span data-ttu-id="58d82-108">A troca de mensagens duplex durável é composta de duas mensagens unidirecionais enviadas através de MSMQ e correlacionados usando [.NET contexto Exchange](http://go.microsoft.com/fwlink/?LinkID=166059).</span><span class="sxs-lookup"><span data-stu-id="58d82-108">The durable duplex message exchange is composed from two one-way messages sent over MSMQ and correlated using [.NET Context Exchange](http://go.microsoft.com/fwlink/?LinkID=166059).</span></span> <span data-ttu-id="58d82-109">As mensagens são enviadas usando as atividades de mensagem de <xref:System.ServiceModel.Activities.Send> e de <xref:System.ServiceModel.Activities.Receive> .</span><span class="sxs-lookup"><span data-stu-id="58d82-109">The messages are sent using the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.Receive> messaging activities.</span></span> <span data-ttu-id="58d82-110">O contexto - .NET é usado especificar o endereço de retorno de chamada nas mensagens enviadas.</span><span class="sxs-lookup"><span data-stu-id="58d82-110">.NET Context Exchange is use to specify the callback address on the sent messages.</span></span> <span data-ttu-id="58d82-111">Ambos os serviços são hospedados usando serviços de ativação de processo do Windows (WAS) e configurados para ativar persistência de instâncias de serviços.</span><span class="sxs-lookup"><span data-stu-id="58d82-111">Both services are hosted using Windows Process Activation Services (WAS) and are configured to enable persistence of the services instances.</span></span>  
  
 <span data-ttu-id="58d82-112">O primeiro serviço (Service1.xamlx) envia uma solicitação para o serviço de enviar (Service2.xamlx) fazer qualquer trabalho.</span><span class="sxs-lookup"><span data-stu-id="58d82-112">The first service (Service1.xamlx) sends a request to the send service (Service2.xamlx) to do some work.</span></span> <span data-ttu-id="58d82-113">O trabalho é concluído uma vez, envia de Service2.xamlx uma notificação de volta a Service1.xamlx para indicar que o trabalho foi concluído.</span><span class="sxs-lookup"><span data-stu-id="58d82-113">Once the work is completed, Service2.xamlx sends a notification back to Service1.xamlx to indicate that the work has been completed.</span></span> <span data-ttu-id="58d82-114">Um aplicativo de console do fluxo de trabalho configura as filas que os serviços são escuta sobre e envia a mensagem inicial de Início para ativar Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="58d82-114">A workflow console application sets up the queues that the services are listening on and sends the initial Start message to activate Service1.xamlx.</span></span> <span data-ttu-id="58d82-115">Uma vez que Service1.xamlx recebe notificação de Service2.xamlx que o aplicativo trabalho foi concluído, Service1.xamlx salva o resultado a um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="58d82-115">Once Service1.xamlx receives the notification from Service2.xamlx that the requested work has been completed, Service1.xamlx saves the result to an XML file.</span></span> <span data-ttu-id="58d82-116">Enquanto aguarda a mensagem de retorno de chamada, Service1.xamlx mantém o estado da instância que usa <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>padrão.</span><span class="sxs-lookup"><span data-stu-id="58d82-116">While waiting for the callback message, Service1.xamlx persists its instance state using the default <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>.</span></span> <span data-ttu-id="58d82-117">Service2.xamlx mantém o estado da instância como parte de concluir o trabalho solicitado por Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="58d82-117">Service2.xamlx persists its instance state as part of completing the work requested by Service1.xamlx.</span></span>  
  
 <span data-ttu-id="58d82-118">Para configurar os serviços para usar o contexto - .NET sobre MSMQ, ambos os serviços são configurados para usar uma associação personalizado que consiste em <xref:System.ServiceModel.Channels.ContextBindingElement> e em <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="58d82-118">To configure the services to use .NET Context Exchange over MSMQ, both services are configured to use a custom binding that consists of the <xref:System.ServiceModel.Channels.ContextBindingElement> and the <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span></span> <span data-ttu-id="58d82-119">Um endereço de retorno de chamada é especificado com <xref:System.ServiceModel.Channels.ContextBindingElement> e incluído em um cabeçalho de contexto de retorno de chamada com todas as mensagens enviadas usando uma associação personalizado.</span><span class="sxs-lookup"><span data-stu-id="58d82-119">A callback address is specified with the <xref:System.ServiceModel.Channels.ContextBindingElement> and is included in a callback context header with all messages sent using a custom binding.</span></span> <span data-ttu-id="58d82-120">O exemplo a seguir define a associação personalizado.</span><span class="sxs-lookup"><span data-stu-id="58d82-120">The following code example defines the custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="58d82-121">A associação usada por este exemplo não é seguro.</span><span class="sxs-lookup"><span data-stu-id="58d82-121">The binding used by this sample is not secure.</span></span> <span data-ttu-id="58d82-122">Para implantar seu aplicativo você deve configurar a associação com base nos requisitos de segurança do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58d82-122">When deploying your application you should configure your binding based on the security requirements of your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58d82-123">Filas usadas neste exemplo não são transacionais.</span><span class="sxs-lookup"><span data-stu-id="58d82-123">The queues used in this sample are not transactional.</span></span> <span data-ttu-id="58d82-124">Para obter um exemplo que mostra como configurar o uso de filas de transação trocas de mensagens do WCF, consulte o [ativação MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="58d82-124">For a sample that shows how to set up WCF message exchanges using transaction queues, see the [MSMQ Activation](../../../../docs/framework/wcf/samples/msmq-activation.md) sample.</span></span>  
  
 <span data-ttu-id="58d82-125">A mensagem enviada por Service1.xamlx a Service2.xamlx é enviada usando um ponto final do cliente configurado com o endereço de Service2.xamlx e associação personalizado definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="58d82-125">The message sent by Service1.xamlx to Service2.xamlx is sent using a client endpoint configured with the address of Service2.xamlx and the custom binding defined previously.</span></span> <span data-ttu-id="58d82-126">O retorno de chamada de Service2.xamlx a Service1.xamlx é enviado usando um ponto final do cliente sem o endereço explicitamente configurado como o endereço é tirado de contexto de retorno de chamada enviado por Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="58d82-126">The callback from Service2.xamlx to Service1.xamlx is sent using a client endpoint with no explicitly configured address because the address is taken from the callback context sent by Service1.xamlx.</span></span> <span data-ttu-id="58d82-127">O exemplo de código a seguir define os pontos de extremidade de cliente.</span><span class="sxs-lookup"><span data-stu-id="58d82-127">The following code example defines the client endpoints.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="58d82-128">O exemplo de código expõe pontos de extremidade usando essa associação personalizado modificar o mapeamento padrão de protocolo para que os endereços de base de net.msmq usar essa associação personalizado.</span><span class="sxs-lookup"><span data-stu-id="58d82-128">The following code example exposes endpoints using this custom binding by changing the default protocol mapping for net.msmq base addresses to use this custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="58d82-129">O exemplo de código permite a persistência para ambos os serviços adicionando o comportamento de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> a ambos os serviços e especificando a cadeia de conexão para o base de dados de persistência.</span><span class="sxs-lookup"><span data-stu-id="58d82-129">The following code example enables persistence for both services by adding the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior to both services and specifying the connection string for the persistence database.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
```  
  
## <a name="system-requirements"></a><span data-ttu-id="58d82-130">Requisitos de sistema</span><span class="sxs-lookup"><span data-stu-id="58d82-130">System Requirements</span></span>  
 <span data-ttu-id="58d82-131">Este exemplo requer os seguintes componentes.</span><span class="sxs-lookup"><span data-stu-id="58d82-131">This sample requires the following components.</span></span>  
  
1.  <span data-ttu-id="58d82-132">Serviços de Informações da Internet.</span><span class="sxs-lookup"><span data-stu-id="58d82-132">Internet Information Services.</span></span>  
  
2.  <span data-ttu-id="58d82-133">Serviços de Informações da Internet -> de gerenciamento do IIS 6.0 -> compatibilidade IIS Metabase e a compatibilidade de configuração do IIS 6.0.</span><span class="sxs-lookup"><span data-stu-id="58d82-133">Internet Information Services -> IIS 6.0 Management Compatibility -> IIS Metabase and IIS 6.0 configuration compatibility.</span></span>  
  
3.  <span data-ttu-id="58d82-134">O World Wide Web serviços -> recursos de desenvolvimento de aplicativos -> ao ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="58d82-134">World Wide Web Services -> Application Development Features -> ASP.NET.</span></span>  
  
4.  <span data-ttu-id="58d82-135">Servidor das filas de mensagens da Microsoft (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="58d82-135">Microsoft Message Queues (MSMQ) Server.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="58d82-136">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="58d82-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="58d82-137">Configurar o base de dados de persistência e o diretório de resultados.</span><span class="sxs-lookup"><span data-stu-id="58d82-137">Set up the persistence database and the results directory.</span></span>  
  
    1.  <span data-ttu-id="58d82-138">Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58d82-138">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="58d82-139">Navegue até a pasta para esse exemplo e Setup.cmd executado.</span><span class="sxs-lookup"><span data-stu-id="58d82-139">Navigate to the folder for this sample and run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="58d82-140">Configurar o aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="58d82-140">Set up the virtual application.</span></span>  
  
    1.  <span data-ttu-id="58d82-141">De um prompt de comando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] , registrar o ASP.NET executando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="58d82-141">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by running the following command.</span></span>  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  <span data-ttu-id="58d82-142">Executar [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com permissões de administrador clicando com o [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e selecionando **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="58d82-142">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator permissions by right-clicking [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and selecting **Run as administrator**.</span></span>  
  
    3.  <span data-ttu-id="58d82-143">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de DurableDuplex.sln.</span><span class="sxs-lookup"><span data-stu-id="58d82-143">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DurableDuplex.sln file.</span></span>  
  
3.  <span data-ttu-id="58d82-144">Configurar as filas do serviço.</span><span class="sxs-lookup"><span data-stu-id="58d82-144">Set up the service queues.</span></span>  
  
    1.  <span data-ttu-id="58d82-145">Para executar o cliente de DurableDuplex, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="58d82-145">To run the DurableDuplex client, press F5.</span></span>  
  
    2.  <span data-ttu-id="58d82-146">Abra o **gerenciamento do computador** console executando `Compmgmt.msc` em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="58d82-146">Open the **Computer Management** console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    3.  <span data-ttu-id="58d82-147">Expanda **serviços e aplicativos**, **enfileiramento**.</span><span class="sxs-lookup"><span data-stu-id="58d82-147">Expand **Service and Applications**, **Message Queuing**.</span></span> <span data-ttu-id="58d82-148">**Filas particulares**.</span><span class="sxs-lookup"><span data-stu-id="58d82-148">**Private Queues**.</span></span>  
  
    4.  <span data-ttu-id="58d82-149">As filas de durableduplex/service1.xamlx e durableduplex/service2.xamlx e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="58d82-149">Right-click the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues and select **Properties**.</span></span>  
  
    5.  <span data-ttu-id="58d82-150">Selecione o **segurança** guia e permitir **todos receber mensagem**, **inspecionar mensagem** e **enviar mensagem** permissões para ambas as filas.</span><span class="sxs-lookup"><span data-stu-id="58d82-150">Select the **Security** tab and allow **Everyone Receive Message**, **Peek Message** and **Send Message** permissions for both queues.</span></span>  
  
    6.  <span data-ttu-id="58d82-151">Abra o Gerenciador do IIS (Serviços de Informações da Internet).</span><span class="sxs-lookup"><span data-stu-id="58d82-151">Open Internet Information Services (IIS) Manager.</span></span>  
  
    7.  <span data-ttu-id="58d82-152">Navegue até **servidor**, **Sites**, **site da Web padrão**, **privada**, **Duplex durável** e selecione **Opções avançadas**.</span><span class="sxs-lookup"><span data-stu-id="58d82-152">Browse to **Server**, **Sites**, **Default Web site**, **private**, **Durable Duplex** and select **Advanced Options**.</span></span>  
  
    8.  <span data-ttu-id="58d82-153">Alterar o **protocolos habilitados** para **http,net.msmq**.</span><span class="sxs-lookup"><span data-stu-id="58d82-153">Change the **Enabled Protocols** to **http,net.msmq**.</span></span>  
  
4.  <span data-ttu-id="58d82-154">Executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="58d82-154">Run the sample.</span></span>  
  
    1.  <span data-ttu-id="58d82-155">Navegue até http://localhost/private/durableduplex/service1.xamlx e http://localhost/private/durableduplex/service2.xamlx para garantir que os dois serviços estão em execução.</span><span class="sxs-lookup"><span data-stu-id="58d82-155">Browse to http://localhost/private/durableduplex/service1.xamlx and http://localhost/private/durableduplex/service2.xamlx to ensure that both services are running.</span></span>  
  
    2.  <span data-ttu-id="58d82-156">Pressione F5 para executar DurableDuplexClient.</span><span class="sxs-lookup"><span data-stu-id="58d82-156">Press F5 to run DurableDuplexClient.</span></span>  
  
         <span data-ttu-id="58d82-157">Quando a troca de dois lados durável de mensagem concluir um arquivo de result.xml é salvo para a pasta de C:\Inbox e contém o resultado de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="58d82-157">When the durable duplex message exchange completes a result.xml file is saved to the C:\Inbox folder and contains the result of the message exchange.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="58d82-158">A limpeza (opcional)</span><span class="sxs-lookup"><span data-stu-id="58d82-158">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="58d82-159">Execução Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="58d82-159">Run Cleanup.cmd.</span></span>  
  
    1.  <span data-ttu-id="58d82-160">Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58d82-160">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="58d82-161">Navegue até a pasta para esse exemplo e Cleanup.cmd executado.</span><span class="sxs-lookup"><span data-stu-id="58d82-161">Navigate to the folder for this sample and run Cleanup.cmd.</span></span>  
  
2.  <span data-ttu-id="58d82-162">Remova o aplicativo virtual para os serviços.</span><span class="sxs-lookup"><span data-stu-id="58d82-162">Remove the virtual application for the services.</span></span>  
  
    1.  <span data-ttu-id="58d82-163">Abra o Gerenciador de serviços de informações da Internet (IIS) executando `Inetmgr.exe` em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="58d82-163">Open the Internet Information Services (IIS) Manager by running `Inetmgr.exe` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="58d82-164">Navegue até o site da Web padrão e remover o **privada** diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="58d82-164">Browse to the default Web site and remove the **private** virtual directory.</span></span>  
  
3.  <span data-ttu-id="58d82-165">Remover a configuração das filas para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="58d82-165">Remove the queues set up for this sample.</span></span>  
  
    1.  <span data-ttu-id="58d82-166">Abra o console de gerenciamento do computador executando `Compmgmt.msc` em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="58d82-166">Open the Computer Management console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="58d82-167">Expanda **serviços e aplicativos**, **enfileiramento**, **filas particulares**.</span><span class="sxs-lookup"><span data-stu-id="58d82-167">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    3.  <span data-ttu-id="58d82-168">Excluir o durableduplex/service1.xamlx e filas de durableduplex/service2.xamlx.</span><span class="sxs-lookup"><span data-stu-id="58d82-168">Delete the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues.</span></span>  
  
4.  <span data-ttu-id="58d82-169">Remova o diretório de C:\Inbox.</span><span class="sxs-lookup"><span data-stu-id="58d82-169">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="58d82-170">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="58d82-170">The samples may already be installed on your machine.</span></span> <span data-ttu-id="58d82-171">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="58d82-171">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="58d82-172">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="58d82-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="58d82-173">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="58d82-173">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`