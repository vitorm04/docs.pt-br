---
title: Host de serviço personalizado
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 2aed557d1d045c08aed206660aa7b4b75ffe0e2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145066"
---
# <a name="custom-service-host"></a><span data-ttu-id="f05e7-102">Host de serviço personalizado</span><span class="sxs-lookup"><span data-stu-id="f05e7-102">Custom Service Host</span></span>
<span data-ttu-id="f05e7-103">Esta amostra demonstra como usar um <xref:System.ServiceModel.ServiceHost> derivado personalizado da classe para alterar o comportamento de tempo de execução de um serviço.</span><span class="sxs-lookup"><span data-stu-id="f05e7-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="f05e7-104">Essa abordagem fornece uma alternativa reutilizável para configurar um grande número de serviços de forma comum.</span><span class="sxs-lookup"><span data-stu-id="f05e7-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="f05e7-105">A amostra também demonstra <xref:System.ServiceModel.Activation.ServiceHostFactory> como usar a classe para usar um ServiceHost personalizado no ambiente de hospedagem IIS (Internet Information Services, serviço de ativação de processos da Internet) ou do Windows Process Activation Service (WAS).</span><span class="sxs-lookup"><span data-stu-id="f05e7-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f05e7-106">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f05e7-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f05e7-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f05e7-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f05e7-108">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="f05e7-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f05e7-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f05e7-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="f05e7-110">Sobre o cenário</span><span class="sxs-lookup"><span data-stu-id="f05e7-110">About the scenario</span></span>
 <span data-ttu-id="f05e7-111">Para evitar a divulgação não intencional de metadados de serviços potencialmente sensíveis, a configuração padrão dos serviços do Windows Communication Foundation (WCF) desativa a publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="f05e7-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="f05e7-112">Esse comportamento é seguro por padrão, mas também significa que você não pode usar uma ferramenta de importação de metadados (como svcutil.exe) para gerar o código do cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço esteja explicitamente ativado na configuração.</span><span class="sxs-lookup"><span data-stu-id="f05e7-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="f05e7-113">Habilitar a publicação de metadados para um grande número de serviços envolve adicionar os mesmos elementos de configuração a cada serviço individual, o que resulta em uma grande quantidade de informações de configuração que são essencialmente as mesmas.</span><span class="sxs-lookup"><span data-stu-id="f05e7-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="f05e7-114">Como alternativa à configuração individual de cada serviço, é possível escrever o código imperativo que permite a publicação de metadados uma vez e, em seguida, reutilizar esse código em vários serviços diferentes.</span><span class="sxs-lookup"><span data-stu-id="f05e7-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="f05e7-115">Isso é feito criando uma nova <xref:System.ServiceModel.ServiceHost> classe que `ApplyConfiguration`deriva e substitui o método () para adicionar imperativamente o comportamento de publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="f05e7-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f05e7-116">Para obter clareza, esta amostra demonstra como criar um ponto final de publicação de metadados não seguro.</span><span class="sxs-lookup"><span data-stu-id="f05e7-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="f05e7-117">Esses pontos finais estão potencialmente disponíveis para consumidores anônimos não autenticados e os cuidados devem ser tomados antes de implantar tais pontos finais para garantir que a divulgação pública dos metadados de um serviço seja apropriada.</span><span class="sxs-lookup"><span data-stu-id="f05e7-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="f05e7-118">Implementando um ServiceHost personalizado</span><span class="sxs-lookup"><span data-stu-id="f05e7-118">Implementing a custom ServiceHost</span></span>
 <span data-ttu-id="f05e7-119">A <xref:System.ServiceModel.ServiceHost> classe expõe vários métodos virtuais úteis que os herdeiros podem substituir para alterar o comportamento de tempo de execução de um serviço.</span><span class="sxs-lookup"><span data-stu-id="f05e7-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="f05e7-120">Por exemplo, `ApplyConfiguration`o método () lê informações de configuração de <xref:System.ServiceModel.Description.ServiceDescription> serviço do armazenamento de configuração e altera o host de acordo.</span><span class="sxs-lookup"><span data-stu-id="f05e7-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="f05e7-121">A implementação padrão lê a configuração do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f05e7-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="f05e7-122">Implementações personalizadas `ApplyConfiguration`podem substituir () <xref:System.ServiceModel.Description.ServiceDescription> alterar ainda mais o código imperativo de uso ou até mesmo substituir totalmente o armazenamento de configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="f05e7-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="f05e7-123">Por exemplo, para ler a configuração de ponto final de um serviço a partir de um banco de dados em vez do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f05e7-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="f05e7-124">Nesta amostra, queremos criar um ServiceHost personalizado que adiciona o ServiceMetadataBehavior (que permite a publicação de metadados), mesmo que esse comportamento não seja explicitamente adicionado no arquivo de configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="f05e7-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="f05e7-125">Para isso, criamos uma nova classe <xref:System.ServiceModel.ServiceHost> que herda e substitui `ApplyConfiguration`().</span><span class="sxs-lookup"><span data-stu-id="f05e7-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
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
  
 <span data-ttu-id="f05e7-126">Como não queremos ignorar qualquer configuração que tenha sido fornecida no arquivo de configuração do aplicativo, a primeira coisa que `ApplyConfiguration`nossa substituição faz é chamar a implementação base.</span><span class="sxs-lookup"><span data-stu-id="f05e7-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="f05e7-127">Uma vez que este método seja <xref:System.ServiceModel.Description.ServiceMetadataBehavior> concluído, podemos adicionar a descrição da descrição usando o seguinte código imperativo.</span><span class="sxs-lookup"><span data-stu-id="f05e7-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
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
  
 <span data-ttu-id="f05e7-128">A última `ApplyConfiguration`coisa que nossa () substituição deve fazer é adicionar o ponto final de metadados padrão.</span><span class="sxs-lookup"><span data-stu-id="f05e7-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="f05e7-129">Por convenção, um ponto final de metadados é criado para cada URI na coleção BaseAddresses do host de serviço.</span><span class="sxs-lookup"><span data-stu-id="f05e7-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="f05e7-130">Usando um ServiceHost personalizado no self-host</span><span class="sxs-lookup"><span data-stu-id="f05e7-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="f05e7-131">Agora que concluímos nossa implementação personalizada do ServiceHost, podemos usá-lo para adicionar comportamento de publicação `SelfDescribingServiceHost`de metadados a qualquer serviço, hospedando esse serviço dentro de uma instância do nosso .</span><span class="sxs-lookup"><span data-stu-id="f05e7-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="f05e7-132">O código a seguir mostra como usá-lo no cenário de auto-host.</span><span class="sxs-lookup"><span data-stu-id="f05e7-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="f05e7-133">Nosso host personalizado ainda lê a configuração de ponto final do serviço a partir <xref:System.ServiceModel.ServiceHost> do arquivo de configuração do aplicativo, como se tivéssemos usado a classe padrão para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="f05e7-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="f05e7-134">No entanto, como adicionamos a lógica para permitir a publicação de metadados dentro do nosso host personalizado, não devemos mais habilitar explicitamente o comportamento de publicação de metadados na configuração.</span><span class="sxs-lookup"><span data-stu-id="f05e7-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="f05e7-135">Essa abordagem tem uma vantagem distinta quando você está construindo um aplicativo que contém vários serviços e você deseja permitir a publicação de metadados em cada um deles sem escrever os mesmos elementos de configuração várias vezes.</span><span class="sxs-lookup"><span data-stu-id="f05e7-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="f05e7-136">Usando um ServiceHost personalizado no IIS ou WAS</span><span class="sxs-lookup"><span data-stu-id="f05e7-136">Using a custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="f05e7-137">O uso de um host de serviço personalizado em cenários de auto-host é simples, porque é o código do aplicativo que é responsável pela criação e abertura da instância de host do serviço.</span><span class="sxs-lookup"><span data-stu-id="f05e7-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="f05e7-138">No ambiente de hospedagem IIS ou WAS, no entanto, a infra-estrutura WCF está instanciando o host do seu serviço em resposta às mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="f05e7-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="f05e7-139">Hosts de serviço personalizados também podem ser usados neste ambiente de hospedagem, mas eles requerem algum código adicional na forma de um ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="f05e7-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="f05e7-140">O código a seguir <xref:System.ServiceModel.Activation.ServiceHostFactory> mostra uma derivada de que retorna instâncias do nosso costume `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="f05e7-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
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
  
 <span data-ttu-id="f05e7-141">Como você pode ver, implementar um ServiceHostFactory personalizado é muito simples.</span><span class="sxs-lookup"><span data-stu-id="f05e7-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="f05e7-142">Toda a lógica personalizada reside dentro da implementação do ServiceHost; a fábrica retorna uma instância da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="f05e7-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="f05e7-143">Para usar uma fábrica personalizada com uma implementação de serviço, devemos adicionar alguns metadados adicionais ao arquivo .svc do serviço.</span><span class="sxs-lookup"><span data-stu-id="f05e7-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```xml
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 <span data-ttu-id="f05e7-144">Aqui adicionamos um `Factory` atributo `@ServiceHost` adicional à diretiva, e passamos o nome do tipo CLR da nossa fábrica personalizada como o valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="f05e7-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="f05e7-145">Quando o IIS ou WAS recebe uma mensagem para este serviço, a infra-estrutura de hospedagem `ServiceHostFactory.CreateServiceHost()`WCF cria primeiro uma instância do ServiceHostFactory e, em seguida, instancia o próprio host do serviço, chamando .</span><span class="sxs-lookup"><span data-stu-id="f05e7-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="f05e7-146">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="f05e7-146">Running the sample</span></span>  
 <span data-ttu-id="f05e7-147">Embora esta amostra forneça uma implementação de serviço e cliente totalmente funcional, o objetivo da amostra é ilustrar como alterar o comportamento de tempo de execução de um serviço por meio de um host personalizado., faça as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="f05e7-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
### <a name="observe-the-effect-of-the-custom-host"></a><span data-ttu-id="f05e7-148">Observe o efeito do host personalizado</span><span class="sxs-lookup"><span data-stu-id="f05e7-148">Observe the effect of the custom host</span></span>
  
1. <span data-ttu-id="f05e7-149">Abra o arquivo Web.config do serviço e observe que não há configuração que habilite metadados explicitamente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f05e7-149">Open the service's Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="f05e7-150">Abra o arquivo .svc do serviço @ServiceHost e observe que sua diretiva contém um atributo Factory que especifica o nome de um ServiceHostFactory personalizado.</span><span class="sxs-lookup"><span data-stu-id="f05e7-150">Open the service's .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="f05e7-151">Configurar, construir e executar a amostra</span><span class="sxs-lookup"><span data-stu-id="f05e7-151">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="f05e7-152">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f05e7-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="f05e7-153">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f05e7-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="f05e7-154">Depois que a solução for construída, execute Setup.bat para configurar o aplicativo ServiceModelSamples no IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="f05e7-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="f05e7-155">O diretório ServiceModelSamples agora deve aparecer como um aplicativo IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="f05e7-155">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="f05e7-156">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f05e7-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="f05e7-157">Para remover o aplicativo IIS 7.0, execute *Cleanup.bat*.</span><span class="sxs-lookup"><span data-stu-id="f05e7-157">To remove the IIS 7.0 application, run *Cleanup.bat*.</span></span>

## <a name="see-also"></a><span data-ttu-id="f05e7-158">Confira também</span><span class="sxs-lookup"><span data-stu-id="f05e7-158">See also</span></span>

- [<span data-ttu-id="f05e7-159">Como hospedar um serviço WCF no IIS</span><span class="sxs-lookup"><span data-stu-id="f05e7-159">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
