---
title: Host de serviço personalizado
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: c02ceb114a5346ea2a851f711f1ab9b50373cb75
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="custom-service-host"></a><span data-ttu-id="f7750-102">Host de serviço personalizado</span><span class="sxs-lookup"><span data-stu-id="f7750-102">Custom Service Host</span></span>
<span data-ttu-id="f7750-103">Este exemplo demonstra como usar um personalizado derivado do <xref:System.ServiceModel.ServiceHost> classe para alterar o comportamento de tempo de execução de um serviço.</span><span class="sxs-lookup"><span data-stu-id="f7750-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="f7750-104">Essa abordagem fornece uma alternativa reutilizável para configurar um grande número de serviços de uma maneira comum.</span><span class="sxs-lookup"><span data-stu-id="f7750-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="f7750-105">O exemplo também demonstra como usar o <xref:System.ServiceModel.Activation.ServiceHostFactory> classe para usar um ServiceHost personalizado no ambiente de hospedagem de serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="f7750-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f7750-106">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f7750-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f7750-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f7750-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f7750-108">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="f7750-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f7750-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f7750-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="f7750-110">Sobre o cenário</span><span class="sxs-lookup"><span data-stu-id="f7750-110">About the Scenario</span></span>  
 <span data-ttu-id="f7750-111">Para evitar a divulgação acidental de metadados de serviço potencialmente confidenciais, a configuração padrão para serviços do Windows Communication Foundation (WCF) desabilita a publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="f7750-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="f7750-112">Esse comportamento é seguro por padrão, mas também significa que você não pode usar metadados importa ferramenta (como Svcutil.exe) para gerar o código de cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço é explicitamente habilitado na configuração.</span><span class="sxs-lookup"><span data-stu-id="f7750-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="f7750-113">Habilitar a publicação de metadados para um grande número de serviços envolve a adição os mesmos elementos de configuração para cada serviço, que resulta em uma grande quantidade de informações de configuração que é essencialmente o mesmo.</span><span class="sxs-lookup"><span data-stu-id="f7750-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="f7750-114">Como alternativa à configuração de cada serviço individualmente, é possível gravar o código obrigatório que permite que os metadados de publicação de uma vez e, em seguida, reutilizar esse código em vários serviços diferentes.</span><span class="sxs-lookup"><span data-stu-id="f7750-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="f7750-115">Isso é feito criando uma nova classe que deriva de <xref:System.ServiceModel.ServiceHost> e substitui o `ApplyConfiguration`método () para adicionar imperativa o comportamento de publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="f7750-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f7750-116">Para maior clareza, este exemplo demonstra como criar um ponto de extremidade de publicação de metadados não segura.</span><span class="sxs-lookup"><span data-stu-id="f7750-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="f7750-117">Esses pontos de extremidade são potencialmente disponíveis para consumidores não autenticados anônimos e deve ter cuidado antes de implantar esses pontos de extremidade para garantir que publicamente destinatária metadados do serviço são apropriado.</span><span class="sxs-lookup"><span data-stu-id="f7750-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="f7750-118">Implementando um ServiceHost personalizado</span><span class="sxs-lookup"><span data-stu-id="f7750-118">Implementing a Custom ServiceHost</span></span>  
 <span data-ttu-id="f7750-119">O <xref:System.ServiceModel.ServiceHost> classe expõe vários métodos virtuais útil que herdeiros podem substituir para alterar o comportamento de tempo de execução de um serviço.</span><span class="sxs-lookup"><span data-stu-id="f7750-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="f7750-120">Por exemplo, o `ApplyConfiguration`método () lê informações de configuração do serviço de repositório de configuração e altera o host <xref:System.ServiceModel.Description.ServiceDescription> adequadamente.</span><span class="sxs-lookup"><span data-stu-id="f7750-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="f7750-121">A implementação padrão lê a configuração do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7750-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="f7750-122">Implementações personalizadas podem substituir `ApplyConfiguration`() para alterar ainda mais o <xref:System.ServiceModel.Description.ServiceDescription> usando o código obrigatório ou até mesmo substituir o repositório de configuração padrão inteiramente.</span><span class="sxs-lookup"><span data-stu-id="f7750-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="f7750-123">Por exemplo, para ler a configuração de ponto de extremidade do serviço de banco de dados em vez do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7750-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="f7750-124">Neste exemplo, queremos desenvolver um ServiceHost personalizado que adiciona ServiceMetadataBehavior, (que permite a publicação de metadados), mesmo se esse comportamento não for explicitamente adicionado no arquivo de configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="f7750-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="f7750-125">Para fazer isso, podemos criar uma nova classe que herda de <xref:System.ServiceModel.ServiceHost> e substituições `ApplyConfiguration`().</span><span class="sxs-lookup"><span data-stu-id="f7750-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
```  
class SelfDescribingServiceHost : ServiceHost  
{  
    public SelfDescribingServiceHost(Type serviceType, params Uri[] baseAddresses)  
        : base(serviceType, baseAddresses) { }  
  
    //Overriding ApplyConfiguration() allows us to   
    //alter the ServiceDescription prior to opening  
    //the service host.   
    protected override void ApplyConfiguration()  
    {  
        //First, we call base.ApplyConfiguration()  
        //to read any configuration that was provided for  
        //the service we're hosting. After this call,  
        //this.Description describes the service  
        //as it was configured.  
        base.ApplyConfiguration();       
  
        //(rest of implementation elided for clarity)  
    }  
}  
```  
  
 <span data-ttu-id="f7750-126">Porque não queremos ignorar qualquer configuração que foi fornecida no arquivo de configuração do aplicativo, a primeira coisa que nosso substituição de `ApplyConfiguration`() é chamada a implementação base.</span><span class="sxs-lookup"><span data-stu-id="f7750-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="f7750-127">Quando esse método é concluído, podemos imperativa adicionar o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> a descrição usando o seguinte código obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f7750-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
```  
ServiceMetadataBehavior mexBehavior = this.Description.Behaviors.Find<ServiceMetadataBehavior>();  
if (mexBehavior == null)  
{  
    mexBehavior = new ServiceMetadataBehavior();  
    this.Description.Behaviors.Add(mexBehavior);  
}  
else  
{  
    //Metadata behavior has already been configured,   
    //so we do not have any work to do.  
    return;  
}  
```  
  
 <span data-ttu-id="f7750-128">A última coisa que nosso `ApplyConfiguration`substituição () deve fazer é adicionar o ponto de extremidade de metadados padrão.</span><span class="sxs-lookup"><span data-stu-id="f7750-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="f7750-129">Por convenção, um ponto de extremidade de metadados é criado para cada URI na coleção de BaseAddresses do host de serviço.</span><span class="sxs-lookup"><span data-stu-id="f7750-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
```  
//Add a metadata endpoint at each base address  
//using the "/mex" addressing convention  
foreach (Uri baseAddress in this.BaseAddresses)  
{  
    if (baseAddress.Scheme == Uri.UriSchemeHttp)  
    {  
        mexBehavior.HttpGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeHttps)  
    {  
        mexBehavior.HttpsGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpsBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetPipe)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexNamedPipeBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetTcp)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexTcpBinding(),  
                                "mex");  
    }  
}  
```  
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="f7750-130">Usando um ServiceHost personalizado no próprio host</span><span class="sxs-lookup"><span data-stu-id="f7750-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="f7750-131">Agora que já foram concluídos nossa implementação personalizada de ServiceHost, podemos usá-lo para adicionar o comportamento de publicação de metadados para qualquer serviço hospedam o serviço dentro de uma instância do nosso `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="f7750-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="f7750-132">O código a seguir mostra como usá-lo no cenário de hospedagem interna.</span><span class="sxs-lookup"><span data-stu-id="f7750-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="f7750-133">Nosso host personalizado ainda lê configuração de ponto de extremidade do serviço de arquivo de configuração do aplicativo, como se tivéssemos usado o padrão <xref:System.ServiceModel.ServiceHost> classe para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="f7750-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="f7750-134">No entanto, como adicionamos a lógica para habilitar metadados de publicação dentro de nosso host personalizado, não deve explicitamente habilitamos o comportamento de publicação na configuração de metadados.</span><span class="sxs-lookup"><span data-stu-id="f7750-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="f7750-135">Essa abordagem tem uma vantagem quando você estiver criando um aplicativo que contém vários serviços e você deseja habilitar a publicação de metadados em cada um sem gravar os mesmos elementos de configuração diversas vezes.</span><span class="sxs-lookup"><span data-stu-id="f7750-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="f7750-136">Usando um ServiceHost personalizado no IIS ou do WAS</span><span class="sxs-lookup"><span data-stu-id="f7750-136">Using a Custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="f7750-137">Uso de um host de serviço personalizado em cenários de hospedagem interna é simples, porque ele é o código do aplicativo que é responsável por criar e abrir a instância de host do serviço.</span><span class="sxs-lookup"><span data-stu-id="f7750-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="f7750-138">No ambiente de hospedagem do WAS ou IIS, no entanto, a infraestrutura WCF é dinamicamente instanciação de host do serviço em resposta a mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="f7750-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="f7750-139">Hosts de serviço personalizada também podem ser usados nesse ambiente de hospedagem, mas elas exigem algum código adicional na forma de um ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="f7750-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="f7750-140">O código a seguir mostra um derivativo de <xref:System.ServiceModel.Activation.ServiceHostFactory> que retorna instâncias do nosso personalizado `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="f7750-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
```  
public class SelfDescribingServiceHostFactory : ServiceHostFactory  
{  
    protected override ServiceHost CreateServiceHost(Type serviceType,   
     Uri[] baseAddresses)  
    {  
        //All the custom factory does is return a new instance  
        //of our custom host class. The bulk of the custom logic should  
        //live in the custom host (as opposed to the factory)   
        //for maximum  
        //reuse value outside of the IIS/WAS hosting environment.  
        return new SelfDescribingServiceHost(serviceType,     
                                             baseAddresses);  
    }  
}  
```  
  
 <span data-ttu-id="f7750-141">Como você pode ver, implementar um ServiceHostFactory personalizado é muito simples.</span><span class="sxs-lookup"><span data-stu-id="f7750-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="f7750-142">Toda a lógica personalizada reside dentro a implementação do ServiceHost; a fábrica retorna uma instância da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="f7750-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="f7750-143">Para usar uma fábrica personalizada com uma implementação de serviço, devemos adicionar alguns metadados adicionais para o arquivo do serviço. svc.</span><span class="sxs-lookup"><span data-stu-id="f7750-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 <span data-ttu-id="f7750-144">Aqui, adicionamos mais `Factory` de atributo para o `@ServiceHost` diretiva e passado o tipo CLR nome de nossa fábrica personalizada como o valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="f7750-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="f7750-145">Quando o IIS ou do WAS recebe uma mensagem para esse serviço, a infraestrutura de hospedagem do WCF primeiro cria uma instância do ServiceHostFactory e, em seguida, instanciar o host de serviço chamando `ServiceHostFactory.CreateServiceHost()`.</span><span class="sxs-lookup"><span data-stu-id="f7750-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="f7750-146">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="f7750-146">Running the Sample</span></span>  
 <span data-ttu-id="f7750-147">Embora este exemplo fornece uma implementação de serviço e cliente totalmente funcional, o objetivo do exemplo é para ilustrar como alterar o comportamento de tempo de execução do serviço por meio de um host personalizado., execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="f7750-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a><span data-ttu-id="f7750-148">Para observar o efeito do host personalizado</span><span class="sxs-lookup"><span data-stu-id="f7750-148">To observe the effect of the custom host</span></span>  
  
1.  <span data-ttu-id="f7750-149">Abra o arquivo do serviço Web. config e observe que não há nenhuma configuração habilitando explicitamente os metadados para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f7750-149">Open the service’s Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2.  <span data-ttu-id="f7750-150">Abra o arquivo do serviço. svc e observe que seu @ServiceHost diretiva contém um atributo de fábrica que especifica o nome de um ServiceHostFactory personalizado.</span><span class="sxs-lookup"><span data-stu-id="f7750-150">Open the service’s .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f7750-151">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f7750-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f7750-152">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7750-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f7750-153">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7750-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f7750-154">Depois que a solução foi criada, execute bat para configurar o aplicativo ServiceModelSamples em [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7750-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="f7750-155">O diretório ServiceModelSamples agora deve aparecer como um [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7750-155">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="f7750-156">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7750-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="f7750-157">Para remover o [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Cleanup.bat de execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7750-157">To remove the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] application, run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7750-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7750-158">See Also</span></span>  
 [<span data-ttu-id="f7750-159">Como hospedar um serviço WCF no IIS</span><span class="sxs-lookup"><span data-stu-id="f7750-159">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
