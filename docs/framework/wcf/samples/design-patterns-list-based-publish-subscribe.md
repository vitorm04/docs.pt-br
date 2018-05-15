---
title: 'Padrões de design: publicação-assinatura baseada em lista'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: ee05be76607975bd771c0e6f83c242ad944251df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="9c4eb-102">Padrões de design: publicação-assinatura baseada em lista</span><span class="sxs-lookup"><span data-stu-id="9c4eb-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="9c4eb-103">Este exemplo ilustra o padrão com base em lista de publicação-assinatura implementado como um programa do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9c4eb-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c4eb-104">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9c4eb-105">O padrão de design com base em lista de publicação-assinatura é descrito na publicação Microsoft Patterns & Practices, [padrões de integração](http://go.microsoft.com/fwlink/?LinkId=95894).</span><span class="sxs-lookup"><span data-stu-id="9c4eb-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](http://go.microsoft.com/fwlink/?LinkId=95894).</span></span> <span data-ttu-id="9c4eb-106">O padrão de publicação / assinatura passa informações para uma coleção de destinatários que assinaram um tópico de informações.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="9c4eb-107">Com base em lista de publicação / assinatura mantém uma lista de assinantes.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="9c4eb-108">Quando houver informações para compartilhar, uma cópia é enviada para cada assinante na lista.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="9c4eb-109">Este exemplo demonstra um dinâmico com base em lista de publicação / assinatura padrão, onde os clientes podem assinar ou cancelar a assinatura sempre que necessário.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="9c4eb-110">O exemplo de lista de publicação-assinatura baseada consiste em um cliente, um serviço e um programa de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="9c4eb-111">Pode haver mais de um cliente e mais de um programa de fonte de dados em execução.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="9c4eb-112">Os clientes assinarem o serviço, recebem notificações e cancelar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="9c4eb-113">Programas de fonte de dados enviam informações para o serviço para ser compartilhado com todos os assinantes atuais.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="9c4eb-114">Este exemplo, o cliente e fonte de dados são programas de console (.exe arquivos) e o serviço é uma biblioteca (. dll) hospedada no Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="9c4eb-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="9c4eb-115">Atividade de origem do cliente e os dados são visíveis na área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="9c4eb-116">O serviço usa comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-116">The service uses duplex communication.</span></span> <span data-ttu-id="9c4eb-117">O `ISampleContract` contrato de serviço é associado um `ISampleClientCallback` contrato de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="9c4eb-118">O serviço implementa Subscribe e Unsubscribe operações de serviço, quais clientes usam para ingressar ou sair da lista de assinantes.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="9c4eb-119">O serviço também implementa o `PublishPriceChange` operação de serviço, que chama o programa de origem de dados para fornecer o serviço com novas informações.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="9c4eb-120">O programa cliente implementa a `PriceChange` operação de serviço, que chama o serviço para notificar todos os assinantes de uma alteração de preços.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
```  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,   
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 <span data-ttu-id="9c4eb-121">O serviço usa um evento do .NET Framework como um mecanismo para informar a novas informações de todos os assinantes.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="9c4eb-122">Quando um cliente se associa o serviço por chamada de assinar, ele fornece um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="9c4eb-123">Quando um cliente sai, ele cancela a inscrição seu manipulador de eventos do evento.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="9c4eb-124">Quando uma fonte de dados chama o serviço de relatório a uma alteração de preços, o serviço gera o evento.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="9c4eb-125">Cada instância do serviço, uma para cada cliente que se inscreveu e faz com que seus manipuladores de eventos executar esse procedimento chama.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="9c4eb-126">Cada manipulador de eventos transmite as informações para o cliente por meio de sua função de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
```  
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is unregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 <span data-ttu-id="9c4eb-127">Quando você executar o exemplo, inicie vários clientes.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="9c4eb-128">Os clientes se inscrever no serviço.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-128">The clients subscribe to the service.</span></span> <span data-ttu-id="9c4eb-129">Em seguida, execute o programa de origem de dados, que envia informações ao serviço.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="9c4eb-130">O serviço passa as informações para todos os assinantes.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="9c4eb-131">Você pode ver a atividade em cada console de cliente confirmando que as informações foram recebidas.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="9c4eb-132">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="9c4eb-133">Para configurar e criar o exemplo</span><span class="sxs-lookup"><span data-stu-id="9c4eb-133">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="9c4eb-134">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c4eb-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9c4eb-135">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c4eb-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="9c4eb-136">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="9c4eb-136">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="9c4eb-137">Teste que você pode acessar o serviço usando um navegador, digitando o seguinte endereço: http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-137">Test that you can access the service using a browser by entering the following address: http://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="9c4eb-138">Uma página de confirmação deve ser exibida na resposta.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-138">A confirmation page should be displayed in response.</span></span>  
  
2.  <span data-ttu-id="9c4eb-139">Executar Client.exe de \Client\Bin.\\, sob a pasta de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="9c4eb-140">Atividade do cliente é exibida na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="9c4eb-141">Inicie a vários clientes.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-141">Launch several clients.</span></span>  
  
3.  <span data-ttu-id="9c4eb-142">Execute Datasource.exe de \datasource\bin\\, sob a pasta de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="9c4eb-143">Atividade de fonte de dados é exibida na janela do console.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="9c4eb-144">Depois que a fonte de dados envia informações ao serviço, que deve ser transmitidos para cada cliente.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4.  <span data-ttu-id="9c4eb-145">Se o cliente, fonte de dados e programas de serviço não são capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="9c4eb-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="9c4eb-146">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="9c4eb-146">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="9c4eb-147">Configure a máquina de serviço:</span><span class="sxs-lookup"><span data-stu-id="9c4eb-147">Set up the service machine:</span></span>  
  
    1.  <span data-ttu-id="9c4eb-148">No computador do serviço, crie um diretório virtual chamado ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="9c4eb-149">O lote de Setupvroot.bat de arquivo de [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) pode ser usado para criar o diretório de disco e o diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2.  <span data-ttu-id="9c4eb-150">Copie os arquivos de programa do serviço de %SystemDrive%\Inetpub\wwwroot\servicemodelsamples para o diretório virtual ServiceModelSamples no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="9c4eb-151">Certifique-se de incluir os arquivos no diretório \bin.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3.  <span data-ttu-id="9c4eb-152">Teste que você pode acessar o serviço do computador cliente usando um navegador.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2.  <span data-ttu-id="9c4eb-153">Configure os computadores cliente:</span><span class="sxs-lookup"><span data-stu-id="9c4eb-153">Set up the client machines:</span></span>  
  
    1.  <span data-ttu-id="9c4eb-154">Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para os computadores cliente.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2.  <span data-ttu-id="9c4eb-155">Em cada arquivo de configuração do cliente, altere o valor do endereço da definição do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="9c4eb-156">Substitua todas as referências a "localhost" com um nome de domínio totalmente qualificado no endereço.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3.  <span data-ttu-id="9c4eb-157">Configure o computador de origem de dados:</span><span class="sxs-lookup"><span data-stu-id="9c4eb-157">Set up the data source machine:</span></span>  
  
    1.  <span data-ttu-id="9c4eb-158">Copie os arquivos de programa da fonte de dados na pasta \datasource\bin\, sob a pasta de idioma específico, para o computador de origem de dados.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2.  <span data-ttu-id="9c4eb-159">No arquivo de configuração de fonte de dados, altere o valor do endereço da definição do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="9c4eb-160">Substitua todas as referências a "localhost" com um nome de domínio totalmente qualificado no endereço.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4.  <span data-ttu-id="9c4eb-161">Em computadores cliente, inicie Client.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="9c4eb-162">No computador de origem de dados, inicie Datasource.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c4eb-163">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9c4eb-164">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9c4eb-165">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9c4eb-166">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9c4eb-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
  
## <a name="see-also"></a><span data-ttu-id="9c4eb-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c4eb-167">See Also</span></span>
