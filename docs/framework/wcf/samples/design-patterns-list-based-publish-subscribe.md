---
title: 'Padrões de design: publicação-assinatura baseada em lista'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 7342b3702338d5cd1fcc27d80e4e70cee019cc22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144754"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="23348-102">Padrões de design: publicação-assinatura baseada em lista</span><span class="sxs-lookup"><span data-stu-id="23348-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="23348-103">Esta amostra ilustra o padrão Publish-Subscribe baseado em lista implementado como um programa da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="23348-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23348-104">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="23348-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="23348-105">O padrão de design Publish-Subscribe baseado em lista é descrito na publicação Microsoft Patterns & Practices, [Integration Patterns](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="23348-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span></span> <span data-ttu-id="23348-106">O padrão Publish-Subscribe passa informações para uma coleção de destinatários que se inscreveram em um tópico de informação.</span><span class="sxs-lookup"><span data-stu-id="23348-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="23348-107">A assinatura de publicação baseada em listas mantém uma lista de assinantes.</span><span class="sxs-lookup"><span data-stu-id="23348-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="23348-108">Quando há informações a serem compartilhadas, uma cópia é enviada a cada assinante da lista.</span><span class="sxs-lookup"><span data-stu-id="23348-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="23348-109">Esta amostra demonstra um padrão dinâmico de assinatura de publicação baseado em lista, onde os clientes podem assinar ou cancelar a inscrição quantas vezes necessário.</span><span class="sxs-lookup"><span data-stu-id="23348-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="23348-110">A amostra Publish-Subscribe baseada em lista consiste em um cliente, um serviço e um programa de origem de dados.</span><span class="sxs-lookup"><span data-stu-id="23348-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="23348-111">Pode haver mais de um cliente e mais de um programa de fonte de dados em execução.</span><span class="sxs-lookup"><span data-stu-id="23348-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="23348-112">Os clientes assinam o serviço, recebem notificações e cancelam a inscrição.</span><span class="sxs-lookup"><span data-stu-id="23348-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="23348-113">Os programas de fonte de dados enviam informações para o serviço para serem compartilhadas com todos os assinantes atuais.</span><span class="sxs-lookup"><span data-stu-id="23348-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="23348-114">Nesta amostra, o cliente e a fonte de dados são programas de console (.exe files) e o serviço é uma biblioteca (.dll) hospedada no Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="23348-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="23348-115">A atividade do cliente e da fonte de dados são visíveis na área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="23348-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="23348-116">O serviço usa comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="23348-116">The service uses duplex communication.</span></span> <span data-ttu-id="23348-117">O `ISampleContract` contrato de serviço é `ISampleClientCallback` emparelhado com um contrato de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="23348-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="23348-118">O serviço implementa operações de serviço de Assinatura e Cancelamento, que os clientes usam para participar ou sair da lista de assinantes.</span><span class="sxs-lookup"><span data-stu-id="23348-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="23348-119">O serviço também `PublishPriceChange` implementa a operação do serviço, que o programa de fonte de dados chama para fornecer ao serviço novas informações.</span><span class="sxs-lookup"><span data-stu-id="23348-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="23348-120">O programa cliente `PriceChange` implementa a operação do serviço, que o serviço chama para notificar todos os assinantes de uma mudança de preço.</span><span class="sxs-lookup"><span data-stu-id="23348-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="23348-121">O serviço usa um evento .NET Framework como mecanismo para informar todos os assinantes sobre novas informações.</span><span class="sxs-lookup"><span data-stu-id="23348-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="23348-122">Quando um cliente entra no serviço ligando para Assinar, ele fornece um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="23348-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="23348-123">Quando um cliente sai, ele cancela a inscrição de seu manipulador de eventos do evento.</span><span class="sxs-lookup"><span data-stu-id="23348-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="23348-124">Quando uma fonte de dados liga para o serviço para relatar uma mudança de preço, o serviço aumenta o evento.</span><span class="sxs-lookup"><span data-stu-id="23348-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="23348-125">Isso chama cada instância do serviço, uma para cada cliente que se inscreveu e faz com que seus manipuladores de eventos executem.</span><span class="sxs-lookup"><span data-stu-id="23348-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="23348-126">Cada manipulador de eventos passa as informações ao seu cliente através de sua função de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="23348-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="23348-127">Quando você executar a amostra, lance vários clientes.</span><span class="sxs-lookup"><span data-stu-id="23348-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="23348-128">Os clientes assinam o serviço.</span><span class="sxs-lookup"><span data-stu-id="23348-128">The clients subscribe to the service.</span></span> <span data-ttu-id="23348-129">Em seguida, execute o programa de origem de dados, que envia informações para o serviço.</span><span class="sxs-lookup"><span data-stu-id="23348-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="23348-130">O serviço repassa as informações a todos os assinantes.</span><span class="sxs-lookup"><span data-stu-id="23348-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="23348-131">Você pode ver a atividade em cada console do cliente confirmando que as informações foram recebidas.</span><span class="sxs-lookup"><span data-stu-id="23348-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="23348-132">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="23348-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="23348-133">Para configurar e construir a amostra</span><span class="sxs-lookup"><span data-stu-id="23348-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="23348-134">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="23348-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="23348-135">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="23348-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="23348-136">Para executar a amostra na mesma máquina</span><span class="sxs-lookup"><span data-stu-id="23348-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="23348-137">Teste que você pode acessar o serviço usando `http://localhost/servicemodelsamples/service.svc`um navegador inserindo o seguinte endereço: .</span><span class="sxs-lookup"><span data-stu-id="23348-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="23348-138">Uma página de confirmação deve ser exibida em resposta.</span><span class="sxs-lookup"><span data-stu-id="23348-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="23348-139">Executar Client.exe a partir\\de \client\bin , a partir da pasta específica do idioma.</span><span class="sxs-lookup"><span data-stu-id="23348-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="23348-140">A atividade do cliente é exibida na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="23348-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="23348-141">Lançar vários clientes.</span><span class="sxs-lookup"><span data-stu-id="23348-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="23348-142">Executar Datasource.exe a partir\\de \datasource\bin , a partir da pasta específica do idioma.</span><span class="sxs-lookup"><span data-stu-id="23348-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="23348-143">A atividade de origem de dados é exibida na janela do console.</span><span class="sxs-lookup"><span data-stu-id="23348-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="23348-144">Uma vez que a fonte de dados envia informações para o serviço, ela deve ser repassada a cada cliente.</span><span class="sxs-lookup"><span data-stu-id="23348-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="23348-145">Se o cliente, a fonte de dados e os programas de serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="23348-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="23348-146">Para executar a amostra através de máquinas</span><span class="sxs-lookup"><span data-stu-id="23348-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="23348-147">Configure a máquina de serviço:</span><span class="sxs-lookup"><span data-stu-id="23348-147">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="23348-148">Na máquina de serviço, crie um diretório virtual chamado ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="23348-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="23348-149">O arquivo em lote Setupvroot.bat do [Procedimento de Configuração Única para a Fundação de Comunicação do Windows Amostras](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) pode ser usado para criar o diretório de disco e o diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="23348-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="23348-150">Copie os arquivos do programa de serviço de %SystemDrive%\Inetpub\wwwroot\servicemodelsamples para o diretório virtual ServiceModelSamples na máquina de serviço.</span><span class="sxs-lookup"><span data-stu-id="23348-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="23348-151">Certifique-se de incluir os arquivos no diretório \bin.</span><span class="sxs-lookup"><span data-stu-id="23348-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="23348-152">Teste que você pode acessar o serviço a partir da máquina cliente usando um navegador.</span><span class="sxs-lookup"><span data-stu-id="23348-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="23348-153">Configure as máquinas clientes:</span><span class="sxs-lookup"><span data-stu-id="23348-153">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="23348-154">Copie os arquivos do programa cliente da pasta \client\bin\\ na pasta específica do idioma para as máquinas clientes.</span><span class="sxs-lookup"><span data-stu-id="23348-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="23348-155">Em cada arquivo de configuração do cliente, altere o valor de endereço da definição de ponto final para corresponder ao novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="23348-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="23348-156">Substitua quaisquer referências a "localhost" por um nome de domínio totalmente qualificado no endereço.</span><span class="sxs-lookup"><span data-stu-id="23348-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="23348-157">Configure a máquina de origem de dados:</span><span class="sxs-lookup"><span data-stu-id="23348-157">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="23348-158">Copie os arquivos do programa de origem de dados da pasta \datasource\bin\\ na pasta específica do idioma para a máquina de origem de dados.</span><span class="sxs-lookup"><span data-stu-id="23348-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="23348-159">No arquivo de configuração de origem de dados, altere o valor de endereço da definição de ponto final para corresponder ao novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="23348-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="23348-160">Substitua quaisquer referências a "localhost" por um nome de domínio totalmente qualificado no endereço.</span><span class="sxs-lookup"><span data-stu-id="23348-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="23348-161">Nas máquinas clientes, inicie client.exe a partir de um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="23348-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="23348-162">Na máquina de origem de dados, inicie Datasource.exe a partir de um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="23348-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="23348-163">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="23348-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="23348-164">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="23348-164">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="23348-165">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="23348-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="23348-166">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="23348-166">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
