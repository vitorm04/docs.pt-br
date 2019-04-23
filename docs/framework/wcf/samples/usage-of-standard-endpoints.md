---
title: Uso de pontos de extremidade padrão
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 4ef0714acad12db1414e34fbb476b4ae7d1d9fb2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977074"
---
# <a name="usage-of-standard-endpoints"></a><span data-ttu-id="53237-102">Uso de pontos de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="53237-102">Usage of Standard Endpoints</span></span>

<span data-ttu-id="53237-103">Este exemplo demonstra como usar pontos de extremidade padrão em arquivos de configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="53237-103">This sample demonstrates how to use standard endpoints in service configuration files.</span></span> <span data-ttu-id="53237-104">Um ponto de extremidade padrão permite que o usuário simplificar as definições de ponto de extremidade por meio de uma única propriedade para descrever um endereço, ligação e contrato de combinação com propriedades adicionais associadas a ele.</span><span class="sxs-lookup"><span data-stu-id="53237-104">A standard endpoint allows the user to simplify endpoint definitions by using a single property to describe an address, binding and contract combination with additional properties associated to it.</span></span> <span data-ttu-id="53237-105">Este exemplo demonstra como definir e implementar um ponto de extremidade padrão personalizado e como definir propriedades específicas no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="53237-105">This sample demonstrates how to define and implement a custom standard endpoint and how to define specific properties in the endpoint.</span></span>

## <a name="sample-details"></a><span data-ttu-id="53237-106">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="53237-106">Sample Details</span></span>

<span data-ttu-id="53237-107">Pontos de extremidade de serviço podem ser especificados fornecendo três parâmetros: endereço, associação e contrato.</span><span class="sxs-lookup"><span data-stu-id="53237-107">Service endpoints can be specified by supplying three parameters: address, binding and contract.</span></span> <span data-ttu-id="53237-108">Outros parâmetros que podem ser fornecidos incluem a configuração de comportamento, cabeçalhos, URI de escuta e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="53237-108">Other parameters that can be supplied include behavior configuration, headers, listen URI, and so on.</span></span> <span data-ttu-id="53237-109">Em alguns casos, qualquer ou todos os endereços, associações e contratos têm valores que não é possível alterar.</span><span class="sxs-lookup"><span data-stu-id="53237-109">In some cases, any or all of addresses, bindings and contracts have values that cannot change.</span></span> <span data-ttu-id="53237-110">Por esse motivo, é possível usar pontos de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="53237-110">For this reason, it is possible to use standard endpoints.</span></span> <span data-ttu-id="53237-111">Alguns exemplos de tais pontos de extremidade incluem pontos de extremidade de troca de metadados e pontos de extremidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="53237-111">Some examples of such endpoints include metadata exchange endpoints and discovery endpoints.</span></span> <span data-ttu-id="53237-112">Pontos de extremidade padrão também melhoram a usabilidade, permitindo que a configuração de pontos de extremidade de serviço sem a necessidade de fornecer informações de natureza fixa ou criar seus próprios pontos de extremidade padrão, por exemplo, para melhorar a usabilidade, fornecendo um conjunto razoável de padrão os valores e reduzindo, assim, o detalhamento dos arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="53237-112">Standard endpoints also improve usability by allowing configuration of service endpoints without having to provide information of a fixed nature or to create their own standard endpoints, for example to improve usability by supplying a reasonable set of default values and thus reducing the verbosity of configuration files.</span></span>

<span data-ttu-id="53237-113">Esse exemplo consiste em dois projetos: o serviço que define dois pontos de extremidade padrão e o cliente que se comunica com o serviço.</span><span class="sxs-lookup"><span data-stu-id="53237-113">This sample consists of two projects: the service that defines two standard endpoints and the client that communicates with the service.</span></span> <span data-ttu-id="53237-114">A maneira como os pontos de extremidade padrão são definidos para o serviço no arquivo de configuração é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="53237-114">The way the standard endpoints are defined for the service in the configuration file is show in the following example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <extensions>
      <endpointExtensions>
        <add name="customEndpoint" type="Microsoft.Samples.StandardEndpoints.CustomEndpointCollectionElement, service" />
      </endpointExtensions>
    </extensions>
    <services>
      <service name="Microsoft.Samples.StandardEndpoints.CalculatorService">
        <endpoint address="http://localhost:8000/Samples/Service.svc/customEndpoint" contract="Microsoft.Samples.StandardEndpoints.ICalculator" kind="customEndpoint" />
        <endpoint kind="mexEndpoint" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="True"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <standardEndpoints>
      <customEndpoint>
        <standardEndpoint property="True" />
      </customEndpoint>
    </standardEndpoints>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="53237-115">O primeiro ponto de extremidade definido para o serviço é do tipo `customEndpoint`, cuja definição pode ser vista na `<standardEndpoints>` seção, no qual a propriedade `property` recebe o valor `true`.</span><span class="sxs-lookup"><span data-stu-id="53237-115">The first endpoint defined for the service is of kind `customEndpoint`, whose definition can be seen in the `<standardEndpoints>` section, in which the property `property` is given the value `true`.</span></span> <span data-ttu-id="53237-116">Esse é o caso de um ponto de extremidade personalizado com uma nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="53237-116">This is the case of an endpoint customized with a new property.</span></span> <span data-ttu-id="53237-117">O segundo ponto de extremidade corresponde a um ponto de extremidade de metadados, em que os valores de endereço, ligação e contrato são fixos.</span><span class="sxs-lookup"><span data-stu-id="53237-117">The second endpoint corresponds to a metadata endpoint, in which the values for address, binding and contract are fixed.</span></span>

<span data-ttu-id="53237-118">Para definir o elemento de ponto de extremidade padrão, uma classe que deriva de `StandardEndpointElement` deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="53237-118">To define the standard endpoint element, a class that derives from `StandardEndpointElement` must be created.</span></span> <span data-ttu-id="53237-119">Neste exemplo, no caso do `CustomEndpointElement` classe ter sido definida conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="53237-119">In the case of this sample, the `CustomEndpointElement` class has been defined as shown in the following example.</span></span>

```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```

<span data-ttu-id="53237-120">No `CreateServiceEndpoint` função, um `CustomEndpoint` objeto é criado.</span><span class="sxs-lookup"><span data-stu-id="53237-120">In the `CreateServiceEndpoint` function, a `CustomEndpoint` object is created.</span></span> <span data-ttu-id="53237-121">Sua definição é mostrada no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="53237-121">Its definition is shown in the following example:</span></span>

```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    {
    }

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    {
    }

    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    public bool Property
    {
        get;
        set;
    }
}
```

 <span data-ttu-id="53237-122">Para executar a comunicação entre cliente e de serviço, uma referência de serviço é criada no cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="53237-122">To perform the communication between service and client, a service reference is created in the client to the service.</span></span> <span data-ttu-id="53237-123">Quando o exemplo é compilado e executado, o serviço é executado e o cliente se comunica com ele.</span><span class="sxs-lookup"><span data-stu-id="53237-123">When the sample is built and executed, the service executes and the client communicates with it.</span></span> <span data-ttu-id="53237-124">Observe que a referência de serviço deve ser atualizada sempre que há alguma alteração no serviço.</span><span class="sxs-lookup"><span data-stu-id="53237-124">Note that the service reference should be updated every time there is some change in the service.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="53237-125">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="53237-125">To use this sample</span></span>

1. <span data-ttu-id="53237-126">Usando o Visual Studio 2012, abra o arquivo StandardEndpoints.sln.</span><span class="sxs-lookup"><span data-stu-id="53237-126">Using Visual Studio 2012, open the StandardEndpoints.sln file.</span></span>

2. <span data-ttu-id="53237-127">Habilite vários projetos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="53237-127">Enable multiple projects to start up.</span></span>

    1.  <span data-ttu-id="53237-128">Na **Gerenciador de soluções**, a solução de pontos de extremidade padrão com o botão direito e, em seguida, selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="53237-128">In **Solution Explorer**, right-click the Standard Endpoints solution and then select **Properties**.</span></span>

    2.  <span data-ttu-id="53237-129">Na **propriedades comuns**, selecione **projeto de inicialização**e, em seguida, clique em **vários projetos de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="53237-129">In **Common Properties**, select **Startup Project**, and then click **Multiple Startup Projects**.</span></span>

    3.  <span data-ttu-id="53237-130">Mover o projeto de serviço para o início da lista, com o **ação** definido como **iniciar**.</span><span class="sxs-lookup"><span data-stu-id="53237-130">Move the Service project to the beginning of the list, with the **Action** set to **Start**.</span></span>

    4.  <span data-ttu-id="53237-131">Mover o projeto do cliente após o projeto de serviço, também com o **ação** definido como **iniciar**.</span><span class="sxs-lookup"><span data-stu-id="53237-131">Move the Client project after the Service project, also with the **Action** set to **Start**.</span></span>

         <span data-ttu-id="53237-132">Isso especifica que o projeto do cliente é executado após o projeto de serviço.</span><span class="sxs-lookup"><span data-stu-id="53237-132">This specifies that the Client project is executed after the Service project.</span></span>

3. <span data-ttu-id="53237-133">Para executar a solução, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="53237-133">To run the solution, press F5.</span></span>

> [!NOTE]
> <span data-ttu-id="53237-134">Se essas etapas não funcionarem, em seguida, certifique-se de que seu ambiente foi corretamente configurado, usando as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="53237-134">If these steps don't work, then make sure that your environment has been properly set up, using the following steps:</span></span>
>
> 1. <span data-ttu-id="53237-135">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53237-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>
> 2. <span data-ttu-id="53237-136">Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53237-136">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>
> 3. <span data-ttu-id="53237-137">Para executar o exemplo em uma única ou várias configurações de computador, siga as instruções em [executando os exemplos do Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53237-137">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53237-138">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="53237-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="53237-139">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="53237-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="53237-140">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="53237-140">If this directory doesn't exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="53237-141">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="53237-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
