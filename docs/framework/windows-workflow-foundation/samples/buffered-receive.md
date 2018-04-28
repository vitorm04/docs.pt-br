---
title: Armazenados em buffer receber
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: abec64433d10a23dca6186c6c9a553bbed12a017
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="buffered-receive"></a><span data-ttu-id="9c88f-102">Armazenados em buffer receber</span><span class="sxs-lookup"><span data-stu-id="9c88f-102">Buffered Receive</span></span>
<span data-ttu-id="9c88f-103">Este exemplo demonstra como instalar e configurar o recurso de buffer de recebimento no Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="9c88f-103">This sample demonstrates how to set up and configure the buffered receive feature in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="9c88f-104">Armazenados em buffer receber permite que o autor de fluxo de trabalho crie um fluxo de trabalho sem ter que se preocupar na ordem em que as mensagens são recebidas.</span><span class="sxs-lookup"><span data-stu-id="9c88f-104">Buffered receive allows the workflow author to create a workflow without having to worry about the order in which messages are received.</span></span> <span data-ttu-id="9c88f-105">O armazenados em buffer recebe mensagens de buffers de recurso localmente e entrega-as quando o fluxo de trabalho está pronto para as receber.</span><span class="sxs-lookup"><span data-stu-id="9c88f-105">The buffered receive feature buffers messages locally and delivers them when the workflow is ready to receive them.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="9c88f-106">Demonstra</span><span class="sxs-lookup"><span data-stu-id="9c88f-106">Demonstrates</span></span>  
 <span data-ttu-id="9c88f-107">Como usar fora do serviço de processamento de mensagem armazenadas em buffer recebe com atividades de mensagem.</span><span class="sxs-lookup"><span data-stu-id="9c88f-107">Out-of-order message processing using buffered receive with messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c88f-108">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9c88f-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9c88f-109">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9c88f-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9c88f-110">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9c88f-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9c88f-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9c88f-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a><span data-ttu-id="9c88f-112">Discussão</span><span class="sxs-lookup"><span data-stu-id="9c88f-112">Discussion</span></span>  
 <span data-ttu-id="9c88f-113">Nesse exemplo, um serviço de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é implementado usando [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e tem uma sequência de atividades de <xref:System.ServiceModel.Activities.Receive> .</span><span class="sxs-lookup"><span data-stu-id="9c88f-113">In this sample, a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service is implemented using [!INCLUDE[wf1](../../../../includes/wf1-md.md)] and has a sequence of <xref:System.ServiceModel.Activities.Receive> activities.</span></span> <span data-ttu-id="9c88f-114">Este fluxo de trabalho modelos um processo de aprovação simples do empréstimo onde o fluxo de trabalho espere três notificações para um empréstimo é certo.</span><span class="sxs-lookup"><span data-stu-id="9c88f-114">This workflow models a simple loan approval process where the workflow expects three notifications for a loan to be approved.</span></span> <span data-ttu-id="9c88f-115">Um aplicativo cliente de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vem com três notificações correlacionadas em ordem inversa do serviço espera.</span><span class="sxs-lookup"><span data-stu-id="9c88f-115">A [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client application sends three correlated notifications in the reverse order of what the service expects.</span></span> <span data-ttu-id="9c88f-116">Porque o armazenados em buffer recebe o recurso é ativado no serviço, cada mensagem fora de serviço é armazenada em buffer no serviço e processadas como o fluxo de trabalho se torna pronto para receber.</span><span class="sxs-lookup"><span data-stu-id="9c88f-116">Because the buffered receive feature is turned on at the service, each out-of-order message is buffered at the service and processed as the workflow becomes ready to receive it.</span></span>  
  
 <span data-ttu-id="9c88f-117">O armazenados em buffer recebe o recurso exige o suporte de <xref:System.ServiceModel.Activities.ReceiveContent> de associação, portanto usos <xref:System.ServiceModel.NetMsmqBinding>de serviço.</span><span class="sxs-lookup"><span data-stu-id="9c88f-117">The buffered receive feature requires <xref:System.ServiceModel.Activities.ReceiveContent> support from the binding, therefore the service uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="9c88f-118">Qualquer configuração especial é necessária para associação, para que as opções são usadas.</span><span class="sxs-lookup"><span data-stu-id="9c88f-118">No special configuration is required for the binding, so the defaults are used.</span></span>  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 <span data-ttu-id="9c88f-119">O serviço também expõe metadados para o serviço usando <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="9c88f-119">The service also exposes metadata for the service using <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span></span>  
  
 <span data-ttu-id="9c88f-120">Da mesma forma, o ponto final do cliente é configurado usando <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="9c88f-120">Similarly, the client endpoint is configured using <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="9c88f-121">O código do cliente e a configuração é gerado usando o **adicionar referência de serviço** recurso do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c88f-121">The client code and configuration is generated by using the **Add Service Reference** feature of Visual Studio.</span></span> <span data-ttu-id="9c88f-122">O exemplo a seguir é o ponto final de cliente gerado no arquivo App.config.</span><span class="sxs-lookup"><span data-stu-id="9c88f-122">The following example is the generated client endpoint in the App.config file.</span></span>  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 <span data-ttu-id="9c88f-123">Esse exemplo requer que os seguintes componentes do Windows estão ativados:</span><span class="sxs-lookup"><span data-stu-id="9c88f-123">This sample requires that the following Windows components are enabled:</span></span>  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  <span data-ttu-id="9c88f-124">compatibilidade com gerenciamento de[!INCLUDE[iis60](../../../../includes/iis60-md.md)] , Metabase, e a compatibilidade de configuração</span><span class="sxs-lookup"><span data-stu-id="9c88f-124">[!INCLUDE[iis60](../../../../includes/iis60-md.md)] Management Compatibility, Metabase, and Configuration Compatibility</span></span>  
  
3.  <span data-ttu-id="9c88f-125">Serviços de World Wide Web, recursos de desenvolvimento de aplicativos, e o ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9c88f-125">World Wide Web Services, Application Development Features, and ASP.NET</span></span>  
  
4.  <span data-ttu-id="9c88f-126">Servidor das filas de mensagens da Microsoft (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="9c88f-126">Microsoft Message Queues (MSMQ) Server</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="9c88f-127">Para configurar, e compilar o exemplo</span><span class="sxs-lookup"><span data-stu-id="9c88f-127">To set up, and build the sample</span></span>  
  
1.  <span data-ttu-id="9c88f-128">Em um prompt de comando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] , o registro ASP.NET digitando `aspnet_regiis –I` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="9c88f-128">At a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by typing `aspnet_regiis –I` and press ENTER.</span></span>  
  
2.  <span data-ttu-id="9c88f-129">Execução [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] como um administrador.</span><span class="sxs-lookup"><span data-stu-id="9c88f-129">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an Administrator.</span></span>  
  
3.  <span data-ttu-id="9c88f-130">LoanService.sln aberto.</span><span class="sxs-lookup"><span data-stu-id="9c88f-130">Open LoanService.sln.</span></span>  
  
4.  <span data-ttu-id="9c88f-131">Quando for perguntado se você deseja criar os diretórios virtuais para o projeto LoanService, selecione **Sim**.</span><span class="sxs-lookup"><span data-stu-id="9c88f-131">When asked if you would like to create the virtual directories for the LoanService project, select **Yes**.</span></span>  
  
#### <a name="to-set-up-the-service-queues"></a><span data-ttu-id="9c88f-132">Para configurar as filas de serviço</span><span class="sxs-lookup"><span data-stu-id="9c88f-132">To set up the service queues</span></span>  
  
1.  <span data-ttu-id="9c88f-133">Pressione F5 para executar o aplicativo de LoanClient que cria as filas e ativa o serviço definido em Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="9c88f-133">Press F5 to run the LoanClient application that creates the queues and activates the service defined in Service1.xamlx.</span></span>  
  
2.  <span data-ttu-id="9c88f-134">Abra o **gerenciamento do computador** console executando Compmgmt.msc em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="9c88f-134">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
3.  <span data-ttu-id="9c88f-135">No **gerenciamento do computador** de console, expanda **Service**, **aplicativos**, **enfileiramento**, **filas particulares** .</span><span class="sxs-lookup"><span data-stu-id="9c88f-135">In the **Computer Management** console, expand **Service**, **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
4.  <span data-ttu-id="9c88f-136">A fila de loanservice/service1.xamlx e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="9c88f-136">Right-click the loanservice/service1.xamlx queue and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="9c88f-137">Selecione o **segurança** guia e adicionar **todos recebe mensagem**, **inspecionar mensagem** e **enviar mensagem** permissões.</span><span class="sxs-lookup"><span data-stu-id="9c88f-137">Select the **Security** tab, and add **Everyone Receives Message**, **Peek Message** and **Send Message** permissions.</span></span>  
  
6.  <span data-ttu-id="9c88f-138">Abra o gerenciador de [!INCLUDE[iis60](../../../../includes/iis60-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9c88f-138">Open the [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Manager.</span></span>  
  
7.  <span data-ttu-id="9c88f-139">Navegue até **servidor**, **Sites**, **site da Web padrão**, **privada**, **LoanService** e selecione  **Opções avançadas**</span><span class="sxs-lookup"><span data-stu-id="9c88f-139">Browse to **Server**, **Sites**, **Default Web site**, **Private**, **LoanService** and select **Advanced Options**</span></span>  
  
8.  <span data-ttu-id="9c88f-140">Alterar o **protocolos habilitados** ser **http**, **NET. MSMQ**.</span><span class="sxs-lookup"><span data-stu-id="9c88f-140">Change the **Enabled Protocols** to be **http**, **net.msmq**.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="9c88f-141">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="9c88f-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="9c88f-142">Navegue até http://localhost/private/loanservice/service1.xamlx para garantir que o serviço está em execução.</span><span class="sxs-lookup"><span data-stu-id="9c88f-142">Browse to http://localhost/private/loanservice/service1.xamlx to ensure that the service is running.</span></span>  
  
2.  <span data-ttu-id="9c88f-143">Pressione F5 para executar o aplicativo de LoanClient.</span><span class="sxs-lookup"><span data-stu-id="9c88f-143">Press F5 to run the LoanClient application.</span></span> <span data-ttu-id="9c88f-144">Uma vez que o fluxo de trabalho estiver concluída, um arquivo de out.txt deve ser salvo a C:\Inbox que contém o resultado de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="9c88f-144">Once the workflow is complete, an out.txt file should be saved to C:\Inbox that contains the result of the message exchange.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="9c88f-145">Para limpar</span><span class="sxs-lookup"><span data-stu-id="9c88f-145">To clean up</span></span>  
  
1.  <span data-ttu-id="9c88f-146">Abra o **gerenciamento do computador** console executando Compmgmt.msc em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="9c88f-146">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
2.  <span data-ttu-id="9c88f-147">Expanda **Service** e **aplicativos**, **enfileiramento**, **filas particulares**.</span><span class="sxs-lookup"><span data-stu-id="9c88f-147">Expand **Service** and **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="9c88f-148">Exclua a fila de loanservice/service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="9c88f-148">Delete the loanservice/service1.xamlx queue.</span></span>  
  
4.  <span data-ttu-id="9c88f-149">Remova o diretório de C:\Inbox.</span><span class="sxs-lookup"><span data-stu-id="9c88f-149">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c88f-150">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9c88f-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9c88f-151">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9c88f-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9c88f-152">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9c88f-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9c88f-153">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9c88f-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
