---
title: Host de serviço personalizado
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 80b2642fa202500aa22dc7d045476cb36677d47c
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928860"
---
# <a name="custom-service-host"></a><span data-ttu-id="0cf72-102">Host de serviço personalizado</span><span class="sxs-lookup"><span data-stu-id="0cf72-102">Custom Service Host</span></span>
<span data-ttu-id="0cf72-103">Este exemplo demonstra como usar um derivado personalizado da <xref:System.ServiceModel.ServiceHost> classe para alterar o comportamento de tempo de execução de um serviço.</span><span class="sxs-lookup"><span data-stu-id="0cf72-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="0cf72-104">Essa abordagem fornece uma alternativa reutilizável para configurar um grande número de serviços de maneira comum.</span><span class="sxs-lookup"><span data-stu-id="0cf72-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="0cf72-105">O exemplo também demonstra como usar a <xref:System.ServiceModel.Activation.ServiceHostFactory> classe para usar um ServiceHost personalizado no ambiente de hospedagem serviços de informações da Internet (IIS) ou serviço de ativação de processos do Windows (was).</span><span class="sxs-lookup"><span data-stu-id="0cf72-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0cf72-106">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0cf72-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0cf72-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0cf72-107">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="0cf72-108">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="0cf72-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0cf72-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0cf72-109">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="0cf72-110">Sobre o cenário</span><span class="sxs-lookup"><span data-stu-id="0cf72-110">About the Scenario</span></span>  
 <span data-ttu-id="0cf72-111">Para evitar a divulgação não intencional de metadados de serviço potencialmente confidenciais, a configuração padrão para Windows Communication Foundation (WCF) Services desabilita a publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="0cf72-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="0cf72-112">Esse comportamento é seguro por padrão, mas também significa que você não pode usar uma ferramenta de importação de metadados (como SvcUtil. exe) para gerar o código do cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço esteja explicitamente habilitado na configuração.</span><span class="sxs-lookup"><span data-stu-id="0cf72-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="0cf72-113">A habilitação da publicação de metadados para um grande número de serviços envolve a adição dos mesmos elementos de configuração a cada serviço individual, o que resulta em uma grande quantidade de informações de configuração que é essencialmente a mesma.</span><span class="sxs-lookup"><span data-stu-id="0cf72-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="0cf72-114">Como alternativa à configuração de cada serviço individualmente, é possível escrever o código imperativo que permite a publicação de metadados uma vez e, em seguida, reutilizar esse código em vários serviços diferentes.</span><span class="sxs-lookup"><span data-stu-id="0cf72-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="0cf72-115">Isso é feito pela criação de uma nova classe que deriva de <xref:System.ServiceModel.ServiceHost> e substitui o `ApplyConfiguration`método () para adicionar imperativamente o comportamento de publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="0cf72-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0cf72-116">Para maior clareza, este exemplo demonstra como criar um ponto de extremidade de publicação de metadados não seguro.</span><span class="sxs-lookup"><span data-stu-id="0cf72-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="0cf72-117">Esses pontos de extremidade estão potencialmente disponíveis para consumidores anônimos não autenticados e devem ser levados em vida antes da implantação desses pontos de extremidade para garantir que os metadados de um serviço sejam desmarcados publicamente.</span><span class="sxs-lookup"><span data-stu-id="0cf72-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="0cf72-118">Implementando um ServiceHost personalizado</span><span class="sxs-lookup"><span data-stu-id="0cf72-118">Implementing a Custom ServiceHost</span></span>  
 <span data-ttu-id="0cf72-119">A <xref:System.ServiceModel.ServiceHost> classe expõe vários métodos virtuais úteis que os herdeiros podem substituir para alterar o comportamento de tempo de execução de um serviço.</span><span class="sxs-lookup"><span data-stu-id="0cf72-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="0cf72-120">Por exemplo, o `ApplyConfiguration`método () lê as informações de configuração do serviço do repositório de configuração e altera o <xref:System.ServiceModel.Description.ServiceDescription> host de acordo.</span><span class="sxs-lookup"><span data-stu-id="0cf72-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="0cf72-121">A implementação padrão lê a configuração do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0cf72-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="0cf72-122">Implementações personalizadas podem `ApplyConfiguration`substituir () para alterar melhor <xref:System.ServiceModel.Description.ServiceDescription> o uso do código imperativo ou até mesmo substituir totalmente o repositório de configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="0cf72-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="0cf72-123">Por exemplo, para ler a configuração de ponto de extremidade de um serviço de um banco de dados em vez do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0cf72-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="0cf72-124">Neste exemplo, desejamos criar um ServiceHost personalizado que adiciona o ServiceMetadataBehavior, (que habilita a publicação de metadados), mesmo que esse comportamento não seja explicitamente adicionado ao arquivo de configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="0cf72-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="0cf72-125">Para fazer isso, criamos uma nova classe que herda de <xref:System.ServiceModel.ServiceHost> e substitui `ApplyConfiguration`().</span><span class="sxs-lookup"><span data-stu-id="0cf72-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="0cf72-126">Como não queremos ignorar nenhuma configuração que tenha sido fornecida no arquivo de configuração do aplicativo, a primeira coisa que nossa substituição de `ApplyConfiguration`() é chamar a implementação de base.</span><span class="sxs-lookup"><span data-stu-id="0cf72-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="0cf72-127">Depois que esse método é concluído, podemos adicionar imperativamente o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> à descrição usando o código imperativo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0cf72-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="0cf72-128">A última coisa que `ApplyConfiguration`nossa substituição () deve fazer é adicionar o ponto de extremidade de metadados padrão.</span><span class="sxs-lookup"><span data-stu-id="0cf72-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="0cf72-129">Por convenção, um ponto de extremidade de metadados é criado para cada URI na coleção do BaseAddress do host de serviço.</span><span class="sxs-lookup"><span data-stu-id="0cf72-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
```csharp  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="0cf72-130">Usando um ServiceHost personalizado no auto-host</span><span class="sxs-lookup"><span data-stu-id="0cf72-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="0cf72-131">Agora que concluímos nossa implementação de ServiceHost personalizada, podemos usá-la para adicionar o comportamento de publicação de metadados a qualquer serviço hospedando esse serviço dentro de uma `SelfDescribingServiceHost`instância do nosso.</span><span class="sxs-lookup"><span data-stu-id="0cf72-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="0cf72-132">O código a seguir mostra como usá-lo no cenário de hospedagem interna.</span><span class="sxs-lookup"><span data-stu-id="0cf72-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```csharp  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="0cf72-133">Nosso host personalizado ainda lê a configuração de ponto de extremidade do serviço do arquivo de configuração do aplicativo, assim como se tivéssemos usado <xref:System.ServiceModel.ServiceHost> a classe padrão para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="0cf72-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="0cf72-134">No entanto, como adicionamos a lógica para habilitar a publicação de metadados dentro de nosso host personalizado, não é mais necessário habilitar explicitamente o comportamento de publicação de metadados na configuração.</span><span class="sxs-lookup"><span data-stu-id="0cf72-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="0cf72-135">Essa abordagem tem uma vantagem distinta quando você está criando um aplicativo que contém vários serviços e deseja habilitar a publicação de metadados em cada um deles sem gravar os mesmos elementos de configuração várias vezes.</span><span class="sxs-lookup"><span data-stu-id="0cf72-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="0cf72-136">Usando um ServiceHost personalizado no IIS ou WAS</span><span class="sxs-lookup"><span data-stu-id="0cf72-136">Using a Custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="0cf72-137">Usar um host de serviço personalizado em cenários de hospedagem interna é simples, pois é o código do aplicativo que é, por fim, responsável pela criação e abertura da instância do host de serviço.</span><span class="sxs-lookup"><span data-stu-id="0cf72-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="0cf72-138">No entanto, no ambiente IIS ou WAS de hospedagem, a infraestrutura do WCF está instanciando dinamicamente o host do serviço em resposta às mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="0cf72-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="0cf72-139">Os hosts de serviço personalizados também podem ser usados nesse ambiente de hospedagem, mas exigem um código adicional na forma de um ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="0cf72-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="0cf72-140">O código a seguir mostra uma derivada <xref:System.ServiceModel.Activation.ServiceHostFactory> de que retorna instâncias de nosso `SelfDescribingServiceHost`personalizado.</span><span class="sxs-lookup"><span data-stu-id="0cf72-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="0cf72-141">Como você pode ver, a implementação de um ServiceHostFactory personalizado é muito simples.</span><span class="sxs-lookup"><span data-stu-id="0cf72-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="0cf72-142">Toda a lógica personalizada reside dentro da implementação do ServiceHost; a fábrica retorna uma instância da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="0cf72-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="0cf72-143">Para usar uma fábrica personalizada com uma implementação de serviço, devemos adicionar alguns metadados adicionais ao arquivo. svc do serviço.</span><span class="sxs-lookup"><span data-stu-id="0cf72-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 <span data-ttu-id="0cf72-144">Aqui, adicionamos um atributo `Factory` adicional `@ServiceHost` à diretiva e passamos o nome do tipo CLR de nossa fábrica personalizada como o valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="0cf72-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="0cf72-145">Quando o IIS ou o recebe uma mensagem para esse serviço, a infraestrutura de hospedagem do WCF primeiro cria uma instância do ServiceHostFactory e, em seguida, instancia o `ServiceHostFactory.CreateServiceHost()`próprio host de serviço chamando.</span><span class="sxs-lookup"><span data-stu-id="0cf72-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="0cf72-146">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="0cf72-146">Running the Sample</span></span>  
 <span data-ttu-id="0cf72-147">Embora este exemplo forneça uma implementação de cliente e de serviço totalmente funcional, o ponto do exemplo é ilustrar como alterar o comportamento de tempo de execução de um serviço por meio de um host personalizado. Execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="0cf72-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a><span data-ttu-id="0cf72-148">Para observar o efeito do host personalizado</span><span class="sxs-lookup"><span data-stu-id="0cf72-148">To observe the effect of the custom host</span></span>  
  
1. <span data-ttu-id="0cf72-149">Abra o arquivo Web. config do serviço e observe que não há nenhuma configuração habilitando explicitamente os metadados para o serviço.</span><span class="sxs-lookup"><span data-stu-id="0cf72-149">Open the service’s Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="0cf72-150">Abra o arquivo. svc do serviço e observe que sua @ServiceHost diretiva contém um atributo de fábrica que especifica o nome de um ServiceHostFactory personalizado.</span><span class="sxs-lookup"><span data-stu-id="0cf72-150">Open the service’s .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0cf72-151">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0cf72-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0cf72-152">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0cf72-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0cf72-153">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0cf72-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0cf72-154">Depois que a solução tiver sido criada, execute Setup. bat para configurar o aplicativo ServiceModelSamples no IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="0cf72-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="0cf72-155">O diretório ServiceModelSamples agora deve aparecer como um aplicativo IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="0cf72-155">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>  
  
4. <span data-ttu-id="0cf72-156">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0cf72-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="0cf72-157">Para remover o aplicativo IIS 7,0, execute Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="0cf72-157">To remove the IIS 7.0 application, run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf72-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cf72-158">See also</span></span>

- [<span data-ttu-id="0cf72-159">Como: Hospedar um serviço WCF no IIS</span><span class="sxs-lookup"><span data-stu-id="0cf72-159">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
