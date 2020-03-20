---
title: Validação de segurança
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 17e6e250c6b345477f7c9b377eb8e16ff4331ca7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183375"
---
# <a name="security-validation"></a><span data-ttu-id="a59cb-102">Validação de segurança</span><span class="sxs-lookup"><span data-stu-id="a59cb-102">Security Validation</span></span>
<span data-ttu-id="a59cb-103">Esta amostra demonstra como usar um comportamento personalizado para validar serviços em um computador para garantir que eles atendam a critérios específicos.</span><span class="sxs-lookup"><span data-stu-id="a59cb-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="a59cb-104">Nesta amostra, os serviços são validados pelo comportamento personalizado, escaneando cada ponto final do serviço e verificando se contêm elementos de ligação seguras.</span><span class="sxs-lookup"><span data-stu-id="a59cb-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="a59cb-105">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a59cb-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a59cb-106">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="a59cb-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="a59cb-107">Comportamento personalizado de validação de ponto final</span><span class="sxs-lookup"><span data-stu-id="a59cb-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="a59cb-108">Adicionando código de `Validate` usuário ao <xref:System.ServiceModel.Description.IServiceBehavior> método contido na interface, o comportamento personalizado pode ser dado a um serviço ou ponto final para executar ações definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="a59cb-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="a59cb-109">O código a seguir é usado para fazer loop através de cada ponto final contido em um serviço, que pesquisa através de suas coleções de vinculação para vinculações seguras.</span><span class="sxs-lookup"><span data-stu-id="a59cb-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```csharp
public void Validate(ServiceDescription serviceDescription,
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their
    // binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any
        // secure binding elements. Transport, Asymmetric, and Symmetric
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 <span data-ttu-id="a59cb-110">Adicionar o seguinte código ao arquivo `serviceValidate` Web.config adiciona a extensão de comportamento para que o serviço seja reconhecido.</span><span class="sxs-lookup"><span data-stu-id="a59cb-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="a59cb-111">Uma vez que a extensão de comportamento é `endpointValidate` adicionada ao serviço, agora é possível adicionar o comportamento à lista de comportamentos no arquivo Web.config e, assim, ao serviço.</span><span class="sxs-lookup"><span data-stu-id="a59cb-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="a59cb-112">Comportamentos e suas extensões adicionadas ao arquivo Web.config aplicam comportamento a serviços individuais, enquanto quando adicionados ao arquivo Machine.config aplicam comportamento a todos os serviços ativos no computador.</span><span class="sxs-lookup"><span data-stu-id="a59cb-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a59cb-113">Ao adicionar comportamento a todos os serviços, é sugerido fazer backup do arquivo Machine.config antes de fazer qualquer alteração.</span><span class="sxs-lookup"><span data-stu-id="a59cb-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="a59cb-114">Agora execute o cliente fornecido no diretório cliente\bin desta amostra.</span><span class="sxs-lookup"><span data-stu-id="a59cb-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="a59cb-115">Uma exceção ocorre com a seguinte mensagem:http://localhost/servicemodelsamples/service.svc"O serviço solicitado' não pôde ser ativado."</span><span class="sxs-lookup"><span data-stu-id="a59cb-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="a59cb-116">Isso é esperado porque um ponto final é considerado inseguro pelo ponto final validando o comportamento e impede que o serviço seja iniciado.</span><span class="sxs-lookup"><span data-stu-id="a59cb-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="a59cb-117">O comportamento também lança uma exceção interna que descreve qual ponto final é inseguro e grava uma mensagem para o sistema Event Viewer a fonte System.ServiceModel 4.0.0.0 e a categoria WebHost.</span><span class="sxs-lookup"><span data-stu-id="a59cb-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="a59cb-118">Também é possível ativar o rastreamento do serviço nesta amostra.</span><span class="sxs-lookup"><span data-stu-id="a59cb-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="a59cb-119">Isso permite que o usuário visualize as exceções lançadas pelo comportamento de validação de ponto final, abrindo os traços de serviço resultantes usando a ferramenta Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="a59cb-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="a59cb-120">Para exibir mensagens de exceção de validação de ponto final com falha no Visualizador de eventos</span><span class="sxs-lookup"><span data-stu-id="a59cb-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1. <span data-ttu-id="a59cb-121">Clique no menu **Iniciar** e selecione **Executar...**.</span><span class="sxs-lookup"><span data-stu-id="a59cb-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2. <span data-ttu-id="a59cb-122">Digite `eventvwr` e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="a59cb-122">Type `eventvwr` and click **OK**.</span></span>  
  
3. <span data-ttu-id="a59cb-123">Na janela Visualizador de eventos, clique **em Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="a59cb-123">In the Event Viewer window, click **Application**.</span></span>  
  
4. <span data-ttu-id="a59cb-124">Clique duas vezes no evento "System.ServiceModel 4.0.0.0" adicionado recentemente na categoria "WebHost" na janela **Aplicativo** para exibir mensagens de ponto final inseguras.</span><span class="sxs-lookup"><span data-stu-id="a59cb-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a59cb-125">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="a59cb-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a59cb-126">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a59cb-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a59cb-127">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a59cb-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a59cb-128">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a59cb-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a59cb-129">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a59cb-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a59cb-130">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a59cb-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a59cb-131">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="a59cb-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a59cb-132">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a59cb-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="a59cb-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="a59cb-133">See also</span></span>

- <span data-ttu-id="a59cb-134">[AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a59cb-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
