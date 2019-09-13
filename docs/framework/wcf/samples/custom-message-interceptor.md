---
title: Interceptor de mensagem personalizado
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: daa041bf63442dace0d33e1e3207d0857b6b7312
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928916"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="c244f-102">Interceptor de mensagem personalizado</span><span class="sxs-lookup"><span data-stu-id="c244f-102">Custom Message Interceptor</span></span>
<span data-ttu-id="c244f-103">Este exemplo demonstra o uso do modelo de extensibilidade do canal.</span><span class="sxs-lookup"><span data-stu-id="c244f-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="c244f-104">Em particular, ele mostra como implementar um elemento de ligação personalizado que cria fábricas de canal e ouvintes de canal para interceptar todas as mensagens recebidas e enviadas em um ponto específico na pilha de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c244f-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="c244f-105">O exemplo também inclui um cliente e um servidor que demonstram o uso dessas fábricas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="c244f-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="c244f-106">Neste exemplo, o cliente e o serviço são programas de console (. exe).</span><span class="sxs-lookup"><span data-stu-id="c244f-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="c244f-107">O cliente e o serviço fazem uso de uma biblioteca comum (. dll) que contém o elemento de associação personalizado e seus objetos de tempo de execução associados.</span><span class="sxs-lookup"><span data-stu-id="c244f-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c244f-108">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="c244f-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c244f-109">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c244f-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c244f-110">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c244f-110">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="c244f-111">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="c244f-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c244f-112">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c244f-112">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="c244f-113">O exemplo descreve o procedimento recomendado para criar um canal em camadas personalizado no Windows Communication Foundation (WCF), usando a estrutura de canal e as práticas recomendadas do WCF a seguir.</span><span class="sxs-lookup"><span data-stu-id="c244f-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="c244f-114">As etapas para criar um canal personalizado em camadas são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="c244f-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="c244f-115">Decida em quais formas de canal o Channel Factory e o ouvinte de canal irão dar suporte.</span><span class="sxs-lookup"><span data-stu-id="c244f-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="c244f-116">Crie uma fábrica de canais e um ouvinte de canal que ofereçam suporte às suas formas de canal.</span><span class="sxs-lookup"><span data-stu-id="c244f-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="c244f-117">Adicione um elemento Binding que adiciona o canal em camadas personalizado a uma pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="c244f-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="c244f-118">Adicione uma seção de extensão de elemento de associação para expor o novo elemento de associação ao sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="c244f-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="c244f-119">Formas de canal</span><span class="sxs-lookup"><span data-stu-id="c244f-119">Channel Shapes</span></span>  
 <span data-ttu-id="c244f-120">A primeira etapa na gravação de um canal personalizado em camadas é decidir quais formas são necessárias para o canal.</span><span class="sxs-lookup"><span data-stu-id="c244f-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="c244f-121">Para nosso Inspetor de mensagem, damos suporte a qualquer forma com a qual a camada abaixo dá suporte (por exemplo, se a camada <xref:System.ServiceModel.Channels.IOutputChannel> abaixo <xref:System.ServiceModel.Channels.IDuplexSessionChannel>pode criar e, além <xref:System.ServiceModel.Channels.IOutputChannel> disso <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, também expõe e).</span><span class="sxs-lookup"><span data-stu-id="c244f-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="c244f-122">Fábrica de canais e fábrica de ouvintes</span><span class="sxs-lookup"><span data-stu-id="c244f-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="c244f-123">A próxima etapa na gravação de um canal personalizado em camadas é criar uma implementação do <xref:System.ServiceModel.Channels.IChannelFactory> para canais de cliente e <xref:System.ServiceModel.Channels.IChannelListener> de para canais de serviço.</span><span class="sxs-lookup"><span data-stu-id="c244f-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="c244f-124">Essas classes usam uma fábrica interna e um ouvinte e delegam todas `OnCreateChannel` as `OnAcceptChannel` chamadas de e para a fábrica interna e o ouvinte.</span><span class="sxs-lookup"><span data-stu-id="c244f-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```csharp  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ 
    //... 
}

class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ 
    //...
}  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="c244f-125">Adicionando um elemento de associação</span><span class="sxs-lookup"><span data-stu-id="c244f-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="c244f-126">O exemplo define um elemento de associação personalizado `InterceptingBindingElement`:.</span><span class="sxs-lookup"><span data-stu-id="c244f-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="c244f-127">`InterceptingBindingElement`usa uma `ChannelMessageInterceptor` como entrada e `ChannelMessageInterceptor` a utiliza para manipular mensagens que passam por ela.</span><span class="sxs-lookup"><span data-stu-id="c244f-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="c244f-128">Essa é a única classe que deve ser pública.</span><span class="sxs-lookup"><span data-stu-id="c244f-128">This is the only class that must be public.</span></span> <span data-ttu-id="c244f-129">A fábrica, o ouvinte e os canais podem ser implementações internas das interfaces de tempo de execução públicas.</span><span class="sxs-lookup"><span data-stu-id="c244f-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```csharp
public class InterceptingBindingElement : BindingElement 
{
}
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="c244f-130">Adicionando suporte à configuração</span><span class="sxs-lookup"><span data-stu-id="c244f-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="c244f-131">Para integrar com a configuração de associação, a biblioteca define um manipulador de seção de configuração como uma seção de extensão de elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="c244f-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="c244f-132">Os arquivos de configuração do cliente e do servidor devem registrar a extensão do elemento de associação com o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="c244f-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="c244f-133">Os implementadores que desejam expor seu elemento de ligação para o sistema de configuração podem derivar dessa classe.</span><span class="sxs-lookup"><span data-stu-id="c244f-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement 
{ 
    //... 
}
```  
  
## <a name="adding-policy"></a><span data-ttu-id="c244f-134">Adicionando política</span><span class="sxs-lookup"><span data-stu-id="c244f-134">Adding Policy</span></span>  
 <span data-ttu-id="c244f-135">Para integrar com nosso sistema de política `InterceptingBindingElement` , implemente IPolicyExportExtension para sinalizar que devemos participar da geração de políticas.</span><span class="sxs-lookup"><span data-stu-id="c244f-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="c244f-136">Para dar suporte à política de importação em um cliente gerado, o usuário pode registrar uma `InterceptingBindingElementImporter` classe derivada `CreateMessageInterceptor`de e substituir () para gerar sua `ChannelMessageInterceptor` classe habilitada para política.</span><span class="sxs-lookup"><span data-stu-id="c244f-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="c244f-137">Exemplo: Inspetor de mensagem Dropper</span><span class="sxs-lookup"><span data-stu-id="c244f-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="c244f-138">Incluído no exemplo, há um exemplo de implementação `ChannelMessageInspector` de que descarta mensagens.</span><span class="sxs-lookup"><span data-stu-id="c244f-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```csharp  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="c244f-139">Você pode acessá-lo da configuração da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c244f-139">You can access it from configuration as follows:</span></span>  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"   
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="c244f-140">O cliente e o servidor usam essa seção de configuração recém-criada para inserir as fábricas personalizadas no nível mais baixo de suas pilhas de canal de tempo de execução (acima do nível de transporte).</span><span class="sxs-lookup"><span data-stu-id="c244f-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="c244f-141">O cliente usa a `MessageInterceptor` biblioteca para adicionar um cabeçalho personalizado a mensagens numeradas par.</span><span class="sxs-lookup"><span data-stu-id="c244f-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="c244f-142">O serviço, por outro lado, `MessageInterceptor` usa a biblioteca para descartar todas as mensagens que não têm esse cabeçalho especial.</span><span class="sxs-lookup"><span data-stu-id="c244f-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="c244f-143">Você deverá ver a seguinte saída do cliente depois de executar o serviço e, em seguida, o cliente.</span><span class="sxs-lookup"><span data-stu-id="c244f-143">You should see the following client output after running the service and then the client.</span></span>  
  
```console  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 <span data-ttu-id="c244f-144">O cliente relata 10 velocidades de vento diferentes para o serviço, mas apenas marca metade delas com o cabeçalho especial.</span><span class="sxs-lookup"><span data-stu-id="c244f-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="c244f-145">No serviço, você deve ver a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="c244f-145">On the service, you should see the following output:</span></span>  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c244f-146">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="c244f-146">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c244f-147">Instale o ASP.NET 4,0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="c244f-147">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="c244f-148">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c244f-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="c244f-149">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c244f-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="c244f-150">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c244f-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="c244f-151">Execute o Service. exe primeiro e, em seguida, execute Client. exe e observe as janelas do console para saída.</span><span class="sxs-lookup"><span data-stu-id="c244f-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
