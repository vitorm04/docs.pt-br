---
title: Interceptor de mensagem personalizado
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 3b24535c67c1d16da63ec3b282d456e65ff8dd95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733266"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="08c74-102">Interceptor de mensagem personalizado</span><span class="sxs-lookup"><span data-stu-id="08c74-102">Custom Message Interceptor</span></span>
<span data-ttu-id="08c74-103">Este exemplo demonstra o uso do modelo de extensibilidade do canal.</span><span class="sxs-lookup"><span data-stu-id="08c74-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="08c74-104">Em particular, ele mostra como implementar um elemento de associação personalizado que cria as fábricas de canais e ouvintes de canais para interceptar todas as mensagens de entrada e saídas em um ponto específico na pilha de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="08c74-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="08c74-105">O exemplo também inclui um cliente e servidor que demonstram o uso dessas fábricas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="08c74-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="08c74-106">Neste exemplo, o cliente e o serviço são programas de console (.exe).</span><span class="sxs-lookup"><span data-stu-id="08c74-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="08c74-107">O cliente e o serviço que ambos fazer usam de uma biblioteca comum (. dll) que contém o elemento de associação personalizado e seus objetos de tempo de execução associados.</span><span class="sxs-lookup"><span data-stu-id="08c74-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08c74-108">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="08c74-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="08c74-109">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="08c74-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="08c74-110">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="08c74-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="08c74-111">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="08c74-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="08c74-112">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="08c74-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="08c74-113">O exemplo descreve o procedimento recomendado para a criação de um canal personalizado de em camadas no Windows Communication Foundation (WCF), usando a estrutura de canais e seguir as práticas recomendadas do WCF.</span><span class="sxs-lookup"><span data-stu-id="08c74-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="08c74-114">As etapas para criar um canal personalizado de em camadas são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="08c74-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1.  <span data-ttu-id="08c74-115">Decida quais das formas de canal oferecerá suporte a sua fábrica de canais e o ouvinte de canais.</span><span class="sxs-lookup"><span data-stu-id="08c74-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2.  <span data-ttu-id="08c74-116">Crie uma fábrica de canais e um ouvinte de canais que dão suporte a suas formas de canal.</span><span class="sxs-lookup"><span data-stu-id="08c74-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3.  <span data-ttu-id="08c74-117">Adicione um elemento de associação que adiciona o canal em camadas personalizado a uma pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="08c74-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4.  <span data-ttu-id="08c74-118">Adicione uma seção de extensão de elemento de associação para expor o novo elemento de associação para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="08c74-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="08c74-119">Formas de canal</span><span class="sxs-lookup"><span data-stu-id="08c74-119">Channel Shapes</span></span>  
 <span data-ttu-id="08c74-120">A primeira etapa ao escrever um canal personalizado de em camadas é decidir quais formas são necessárias para o canal.</span><span class="sxs-lookup"><span data-stu-id="08c74-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="08c74-121">Para nosso Inspetor de mensagens, há suporte para qualquer forma que a camada abaixo nos dá suporte a (por exemplo, se a camada abaixo nos pode compilar <xref:System.ServiceModel.Channels.IOutputChannel> e <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, em seguida, podemos também expor <xref:System.ServiceModel.Channels.IOutputChannel> e <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span><span class="sxs-lookup"><span data-stu-id="08c74-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="08c74-122">Fábrica de canais e fábrica de escuta</span><span class="sxs-lookup"><span data-stu-id="08c74-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="08c74-123">A próxima etapa na escrita de um canal personalizado de em camadas é criar uma implementação de <xref:System.ServiceModel.Channels.IChannelFactory> canais de cliente e de <xref:System.ServiceModel.Channels.IChannelListener> para canais de serviço.</span><span class="sxs-lookup"><span data-stu-id="08c74-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="08c74-124">Essas classes levar um alocador interno e um ouvinte e delegar tudo, exceto os `OnCreateChannel` e `OnAcceptChannel` chamadas para a fábrica interna e o ouvinte.</span><span class="sxs-lookup"><span data-stu-id="08c74-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="08c74-125">Adicionando um elemento de associação</span><span class="sxs-lookup"><span data-stu-id="08c74-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="08c74-126">O exemplo define um elemento de associação personalizada: `InterceptingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="08c74-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="08c74-127">`InterceptingBindingElement` leva um `ChannelMessageInterceptor` como uma entrada e usa isso `ChannelMessageInterceptor` para manipular as mensagens que passam por ela.</span><span class="sxs-lookup"><span data-stu-id="08c74-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="08c74-128">Isso é a única classe que deve ser pública.</span><span class="sxs-lookup"><span data-stu-id="08c74-128">This is the only class that must be public.</span></span> <span data-ttu-id="08c74-129">O factory, o ouvinte e canais podem ser internas implementações das interfaces públicas do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="08c74-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="08c74-130">Adicionando suporte à configuração</span><span class="sxs-lookup"><span data-stu-id="08c74-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="08c74-131">Para integrar com a configuração de associação, a biblioteca define um manipulador de seção de configuração como uma seção de extensão de elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="08c74-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="08c74-132">Os arquivos de configuração do cliente e o servidor devem registrar a extensão de elemento de associação com o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="08c74-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="08c74-133">Os implementadores que desejam expor seu elemento de associação para o sistema de configuração podem derivar dessa classe.</span><span class="sxs-lookup"><span data-stu-id="08c74-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a><span data-ttu-id="08c74-134">Adicionar política</span><span class="sxs-lookup"><span data-stu-id="08c74-134">Adding Policy</span></span>  
 <span data-ttu-id="08c74-135">Integrar com nosso sistema de política, `InterceptingBindingElement` implementa IPolicyExportExtension para sinalizar que podemos deve participar de geração de política.</span><span class="sxs-lookup"><span data-stu-id="08c74-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="08c74-136">Para dar suporte à importação de política em um cliente gerado, o usuário pode registrar uma classe derivada de `InterceptingBindingElementImporter` e substituir `CreateMessageInterceptor`() para gerar a sua política habilitada `ChannelMessageInterceptor` classe.</span><span class="sxs-lookup"><span data-stu-id="08c74-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="08c74-137">Exemplo: Inspetor de mensagens droppable</span><span class="sxs-lookup"><span data-stu-id="08c74-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="08c74-138">Incluído no exemplo é um exemplo de implementação de `ChannelMessageInspector` que descarta mensagens.</span><span class="sxs-lookup"><span data-stu-id="08c74-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="08c74-139">Você pode acessá-lo da configuração da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="08c74-139">You can access it from configuration as follows:</span></span>  
  
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
  
 <span data-ttu-id="08c74-140">O cliente e servidor usam esta seção de configuração recém-criada para inserir as fábricas personalizadas no nível mais baixo de suas pilhas de canal do tempo de execução (acima do nível de transporte).</span><span class="sxs-lookup"><span data-stu-id="08c74-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="08c74-141">O cliente usa o `MessageInterceptor` numerados de biblioteca para adicionar um cabeçalho personalizado para até mesmo mensagens.</span><span class="sxs-lookup"><span data-stu-id="08c74-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="08c74-142">O serviço por outro lado usa `MessageInterceptor` biblioteca para descartar todas as mensagens que não têm esse cabeçalho especial.</span><span class="sxs-lookup"><span data-stu-id="08c74-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="08c74-143">Você verá a seguinte saída de cliente depois de executar o serviço e, em seguida, o cliente.</span><span class="sxs-lookup"><span data-stu-id="08c74-143">You should see the following client output after running the service and then the client.</span></span>  
  
```  
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
  
 <span data-ttu-id="08c74-144">O cliente relata 10 velocidades de vento diferentes para o serviço, mas somente marcas metade com o cabeçalho especial.</span><span class="sxs-lookup"><span data-stu-id="08c74-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="08c74-145">No serviço, você deverá ver a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="08c74-145">On the service, you should see the following output:</span></span>  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="08c74-146">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="08c74-146">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="08c74-147">Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="08c74-147">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="08c74-148">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08c74-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="08c74-149">Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08c74-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="08c74-150">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08c74-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="08c74-151">Execute Service.exe primeiro, em seguida, executar Client.exe e assista a ambas as janelas do console de saída.</span><span class="sxs-lookup"><span data-stu-id="08c74-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c74-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08c74-152">See also</span></span>
