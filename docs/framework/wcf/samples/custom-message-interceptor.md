---
title: Interceptor de mensagem personalizado
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 433b14433a7e2dd6edad551a2732e9049a9861ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145080"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="08be1-102">Interceptor de mensagem personalizado</span><span class="sxs-lookup"><span data-stu-id="08be1-102">Custom Message Interceptor</span></span>
<span data-ttu-id="08be1-103">Esta amostra demonstra o uso do modelo de extensibilidade do canal.</span><span class="sxs-lookup"><span data-stu-id="08be1-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="08be1-104">Em particular, ele mostra como implementar um elemento de vinculação personalizado que cria fábricas de canais e ouvintes de canais para interceptar todas as mensagens recebidas e de saída em um determinado ponto da pilha de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="08be1-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="08be1-105">A amostra também inclui um cliente e um servidor que demonstram o uso dessas fábricas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="08be1-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="08be1-106">Nesta amostra, tanto o cliente quanto o serviço são programas de console (.exe).</span><span class="sxs-lookup"><span data-stu-id="08be1-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="08be1-107">O cliente e o serviço fazem uso de uma biblioteca comum (.dll) que contém o elemento de vinculação personalizado e seus objetos de tempo de execução associados.</span><span class="sxs-lookup"><span data-stu-id="08be1-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08be1-108">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="08be1-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="08be1-109">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="08be1-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="08be1-110">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="08be1-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="08be1-111">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="08be1-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="08be1-112">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="08be1-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="08be1-113">A amostra descreve o procedimento recomendado para criar um canal em camadas personalizado na Windows Communication Foundation (WCF), usando a estrutura do canal e seguindo as práticas recomendadas do WCF.</span><span class="sxs-lookup"><span data-stu-id="08be1-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="08be1-114">As etapas para criar um canal em camadas personalizado sao as seguintes:</span><span class="sxs-lookup"><span data-stu-id="08be1-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="08be1-115">Decida qual dos canais molda sua fábrica de canais e o ouvinte do canal suportará.</span><span class="sxs-lookup"><span data-stu-id="08be1-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="08be1-116">Crie uma fábrica de canais e um ouvinte de canal que suporte as formas do seu canal.</span><span class="sxs-lookup"><span data-stu-id="08be1-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="08be1-117">Adicione um elemento de vinculação que adiciona o canal em camadas personalizado a uma pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="08be1-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="08be1-118">Adicione uma seção de extensão de elemento de vinculação para expor o novo elemento de vinculação ao sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="08be1-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="08be1-119">Formas de canal</span><span class="sxs-lookup"><span data-stu-id="08be1-119">Channel Shapes</span></span>  
 <span data-ttu-id="08be1-120">O primeiro passo para escrever um canal em camadas personalizado é decidir quais formas são necessárias para o canal.</span><span class="sxs-lookup"><span data-stu-id="08be1-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="08be1-121">Para nosso inspetor de mensagens, apoiamos qualquer forma que a camada abaixo <xref:System.ServiceModel.Channels.IOutputChannel> de <xref:System.ServiceModel.Channels.IDuplexSessionChannel>nós suporta <xref:System.ServiceModel.Channels.IOutputChannel> (por exemplo, se a camada abaixo de nós pode construir e , então também expõe e <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span><span class="sxs-lookup"><span data-stu-id="08be1-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="08be1-122">Fábrica de Canais e Fábrica de Ouvintes</span><span class="sxs-lookup"><span data-stu-id="08be1-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="08be1-123">O próximo passo na criação de um canal <xref:System.ServiceModel.Channels.IChannelFactory> em camadas <xref:System.ServiceModel.Channels.IChannelListener> personalizado é criar uma implementação para canais de clientes e de canais de serviço.</span><span class="sxs-lookup"><span data-stu-id="08be1-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="08be1-124">Essas aulas tomam uma fábrica interna e ouvinte, e delegam tudo, menos as `OnCreateChannel` chamadas `OnAcceptChannel` para a fábrica interna e ouvinte.</span><span class="sxs-lookup"><span data-stu-id="08be1-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
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
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="08be1-125">Adicionando um elemento de vinculação</span><span class="sxs-lookup"><span data-stu-id="08be1-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="08be1-126">A amostra define um elemento `InterceptingBindingElement`de ligação personalizado: .</span><span class="sxs-lookup"><span data-stu-id="08be1-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="08be1-127">`InterceptingBindingElement`toma `ChannelMessageInterceptor` uma entrada, e `ChannelMessageInterceptor` usa isso para manipular mensagens que passam por ela.</span><span class="sxs-lookup"><span data-stu-id="08be1-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="08be1-128">Esta é a única classe que deve ser pública.</span><span class="sxs-lookup"><span data-stu-id="08be1-128">This is the only class that must be public.</span></span> <span data-ttu-id="08be1-129">A fábrica, o ouvinte e os canais podem ser implementações internas das interfaces públicas de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="08be1-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="08be1-130">Adicionando suporte à configuração</span><span class="sxs-lookup"><span data-stu-id="08be1-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="08be1-131">Para integrar-se à configuração de vinculação, a biblioteca define um manipulador de seção de configuração como uma seção de extensão de elemento de vinculação.</span><span class="sxs-lookup"><span data-stu-id="08be1-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="08be1-132">Os arquivos de configuração cliente e servidor devem registrar a extensão do elemento de vinculação com o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="08be1-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="08be1-133">Os implementadores que desejam expor seu elemento de vinculação ao sistema de configuração podem derivar dessa classe.</span><span class="sxs-lookup"><span data-stu-id="08be1-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement
{
    //...
}
```  
  
## <a name="adding-policy"></a><span data-ttu-id="08be1-134">Adicionando política</span><span class="sxs-lookup"><span data-stu-id="08be1-134">Adding Policy</span></span>  
 <span data-ttu-id="08be1-135">Para integrar-se ao `InterceptingBindingElement` nosso sistema de políticas, implementa o IPolicyExportExtension para sinalizar que devemos participar na política de geração.</span><span class="sxs-lookup"><span data-stu-id="08be1-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="08be1-136">Para suportar a política de importação em um cliente gerado, o `CreateMessageInterceptor`usuário pode registrar uma `ChannelMessageInterceptor` classe derivada de `InterceptingBindingElementImporter` e substituir () para gerar sua classe habilitada para políticas.</span><span class="sxs-lookup"><span data-stu-id="08be1-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="08be1-137">Exemplo: Inspetor de mensagens droppable</span><span class="sxs-lookup"><span data-stu-id="08be1-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="08be1-138">Incluído na amostra é um `ChannelMessageInspector` exemplo de implementação de que as mensagens soltam.</span><span class="sxs-lookup"><span data-stu-id="08be1-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="08be1-139">Você pode acessá-lo a partir da configuração da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="08be1-139">You can access it from configuration as follows:</span></span>  
  
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
  
 <span data-ttu-id="08be1-140">O cliente e o servidor usam essa seção de configuração recém-criada para inserir as fábricas personalizadas no nível mais baixo de suas pilhas de canais de tempo de execução (acima do nível de transporte).</span><span class="sxs-lookup"><span data-stu-id="08be1-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="08be1-141">O cliente `MessageInterceptor` usa a biblioteca para adicionar um cabeçalho personalizado até mesmo mensagens numeradas.</span><span class="sxs-lookup"><span data-stu-id="08be1-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="08be1-142">O serviço, por `MessageInterceptor` outro lado, usa biblioteca para soltar quaisquer mensagens que não tenham esse cabeçalho especial.</span><span class="sxs-lookup"><span data-stu-id="08be1-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="08be1-143">Você deve ver a seguinte saída do cliente após executar o serviço e, em seguida, o cliente.</span><span class="sxs-lookup"><span data-stu-id="08be1-143">You should see the following client output after running the service and then the client.</span></span>  
  
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
  
 <span data-ttu-id="08be1-144">O cliente relata 10 velocidades de vento diferentes para o serviço, mas apenas marca metade deles com o cabeçalho especial.</span><span class="sxs-lookup"><span data-stu-id="08be1-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="08be1-145">No serviço, você deve ver a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="08be1-145">On the service, you should see the following output:</span></span>  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="08be1-146">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="08be1-146">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="08be1-147">Instale ASP.NET 4.0 usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="08be1-147">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="08be1-148">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08be1-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="08be1-149">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08be1-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="08be1-150">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08be1-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="08be1-151">Executar Service.exe primeiro, em seguida, executar Client.exe e assistir ambas as janelas do console para saída.</span><span class="sxs-lookup"><span data-stu-id="08be1-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
