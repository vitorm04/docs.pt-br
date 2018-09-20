---
title: Validação de segurança
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0aaa88268959561cabe4613d51feb0f219275634
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45989638"
---
# <a name="security-validation"></a><span data-ttu-id="f4ba7-102">Validação de segurança</span><span class="sxs-lookup"><span data-stu-id="f4ba7-102">Security Validation</span></span>
<span data-ttu-id="f4ba7-103">Este exemplo demonstra como usar um comportamento personalizado para validar os serviços em um computador para garantir que eles atendam a critérios específicos.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="f4ba7-104">Neste exemplo, os serviços são validados pelo comportamento personalizado de verificação por meio de cada ponto de extremidade no serviço e verificando para ver se eles contêm elementos de associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="f4ba7-105">Este exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f4ba7-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4ba7-106">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="f4ba7-107">Comportamento personalizado de validação de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="f4ba7-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="f4ba7-108">Adicionando o código de usuário para o `Validate` método contido no <xref:System.ServiceModel.Description.IServiceBehavior> interface, comportamento personalizado pode ser fornecido para um serviço ou um ponto de extremidade para executar ações definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="f4ba7-109">O código a seguir é usado para executar loop em cada ponto de extremidade contido em um serviço, que procura por meio de suas coleções de associação para associações seguras.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```  
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually gathering their    
       binding elements.  
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
  
 <span data-ttu-id="f4ba7-110">Adicionando o seguinte código ao arquivo Web. config adiciona o `serviceValidate` extensão de comportamento para o serviço reconhecer.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="f4ba7-111">Depois que a extensão de comportamento é adicionada ao serviço, agora é possível adicionar o `endpointValidate` comportamento à lista de comportamentos no arquivo Web. config e, assim, para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
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
  
 <span data-ttu-id="f4ba7-112">Aplicam comportamentos e suas extensões que são adicionados ao arquivo Web. config do comportamento para serviços individuais, enquanto quando adicionado ao arquivo Machine. config aplicar o comportamento para cada serviço ativo no computador.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4ba7-113">Ao adicionar o comportamento para todos os serviços, é recomendável fazer backup do arquivo Machine. config antes de fazer qualquer alteração.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="f4ba7-114">Agora execute o cliente fornecido no diretório client\bin deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="f4ba7-115">Tem uma exceção ocorre com a seguinte mensagem: "o serviço solicitado, 'http://localhost/servicemodelsamples/service.svc' não pôde ser ativado."</span><span class="sxs-lookup"><span data-stu-id="f4ba7-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="f4ba7-116">Isso é esperado, pois um ponto de extremidade é considerado inseguro pelo ponto de extremidade de validar o comportamento e impede que o serviço seja iniciado.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="f4ba7-117">O comportamento também gera uma exceção interna que descreve qual ponto de extremidade não é seguro e grava uma mensagem no Visualizador de eventos do sistema com a origem de "System. ServiceModel 4.0.0.0" e a categoria "WebHost".</span><span class="sxs-lookup"><span data-stu-id="f4ba7-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="f4ba7-118">Também é possível ativar o rastreamento no serviço neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="f4ba7-119">Isso permite que o usuário exibir as exceções geradas pelo comportamento de validação de ponto de extremidade, abrindo os rastreamentos resultante do serviço usando a ferramenta Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="f4ba7-120">Para exibir mensagens de exceção de validação de ponto de extremidade no Visualizador de eventos de falha</span><span class="sxs-lookup"><span data-stu-id="f4ba7-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1.  <span data-ttu-id="f4ba7-121">Clique o **inicie** menu e selecione **executar...** .</span><span class="sxs-lookup"><span data-stu-id="f4ba7-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2.  <span data-ttu-id="f4ba7-122">Tipo de `eventvwr` e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-122">Type `eventvwr` and click **OK**.</span></span>  
  
3.  <span data-ttu-id="f4ba7-123">Na janela do Visualizador de eventos, clique em **aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-123">In the Event Viewer window, click **Application**.</span></span>  
  
4.  <span data-ttu-id="f4ba7-124">Duas vezes no evento adicionado recentemente "System. ServiceModel 4.0.0.0" sob a categoria "WebHost" na **aplicativo** janela para exibir mensagens de ponto de extremidade inseguro.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f4ba7-125">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ba7-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f4ba7-126">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f4ba7-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f4ba7-127">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f4ba7-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f4ba7-128">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f4ba7-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f4ba7-129">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f4ba7-130">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f4ba7-131">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f4ba7-132">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f4ba7-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="f4ba7-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4ba7-133">See Also</span></span>  
 [<span data-ttu-id="f4ba7-134">AppFabric que monitora exemplos</span><span class="sxs-lookup"><span data-stu-id="f4ba7-134">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
