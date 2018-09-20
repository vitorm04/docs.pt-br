---
title: Comportamento de publicação de metadados
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: c3e26454cc9b29620d80a86df7d7aee131e18200
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743055"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="04717-102">Comportamento de publicação de metadados</span><span class="sxs-lookup"><span data-stu-id="04717-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="04717-103">O comportamento de publicação de metadados que demonstra como controlar os recursos de publicação de metadados de um serviço.</span><span class="sxs-lookup"><span data-stu-id="04717-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="04717-104">Para evitar a divulgação acidental de metadados de serviço potencialmente confidenciais, a configuração padrão para serviços Windows Communication Foundation (WCF) desabilita a publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="04717-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="04717-105">Esse comportamento é seguro por padrão, mas também significa que você não pode usar metadados importar ferramenta (como Svcutil.exe) para gerar o código de cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço é explicitamente habilitado na configuração.</span><span class="sxs-lookup"><span data-stu-id="04717-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="04717-106">Para maior clareza, este exemplo demonstra como criar um ponto de extremidade de publicação de metadados não segura.</span><span class="sxs-lookup"><span data-stu-id="04717-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="04717-107">Esses pontos de extremidade estão potencialmente disponíveis para os consumidores não autenticados anônimos e tome cuidado antes de implantar esses pontos de extremidade para garantir que publicamente divulga metadados de um serviço são apropriado.</span><span class="sxs-lookup"><span data-stu-id="04717-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="04717-108">Consulte a [ponto de extremidade do personalizado proteger metadados](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) exemplo para obter um exemplo que protege um ponto de extremidade de metadados.</span><span class="sxs-lookup"><span data-stu-id="04717-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="04717-109">O exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o `ICalculator` contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="04717-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="04717-110">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="04717-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04717-111">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="04717-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="04717-112">Para um serviço para expor metadados, o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> deve ser configurado no serviço.</span><span class="sxs-lookup"><span data-stu-id="04717-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="04717-113">Quando esse comportamento estiver presente, você pode publicar metadados por meio da configuração de um ponto de extremidade para expor o <xref:System.ServiceModel.Description.IMetadataExchange> contrato como uma implementação de um protocolo WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="04717-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="04717-114">Como uma conveniência, este contrato tem o nome abreviado de configuração de "IMetadataExchange".</span><span class="sxs-lookup"><span data-stu-id="04717-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="04717-115">Este exemplo usa o `mexHttpBinding`, que é uma conveniência padrão de associação que é equivalente de `wsHttpBinding` com o modo de segurança definido como `None`.</span><span class="sxs-lookup"><span data-stu-id="04717-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="04717-116">Um endereço relativo "mex" é usado no ponto de extremidade, que, quando resolvido nos serviços de base endereço resulta em um endereço de ponto de extremidade de http://localhost/servicemodelsamples/service.svc/mex.</span><span class="sxs-lookup"><span data-stu-id="04717-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of http://localhost/servicemodelsamples/service.svc/mex.</span></span> <span data-ttu-id="04717-117">O exemplo a seguir mostra a configuração de comportamento:</span><span class="sxs-lookup"><span data-stu-id="04717-117">The following shows the behavior configuration:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="04717-118">O exemplo a seguir mostra o ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="04717-118">The following shows the MEX endpoint.</span></span>  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="04717-119">Este exemplo define o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> propriedade para `true`, que também expõe metadados do serviço usando o HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="04717-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="04717-120">Para habilitar um ponto de extremidade de metadados HTTP GET, o serviço deve ter um endereço básico HTTP.</span><span class="sxs-lookup"><span data-stu-id="04717-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="04717-121">A cadeia de caracteres de consulta `?wsdl` é usado no endereço base do serviço para acessar os metadados.</span><span class="sxs-lookup"><span data-stu-id="04717-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="04717-122">Por exemplo, para ver o WSDL para o serviço em um navegador da Web você usaria o endereço http://localhost/servicemodelsamples/service.svc?wsdl.</span><span class="sxs-lookup"><span data-stu-id="04717-122">For example, to see the WSDL for the service in a Web browser you would use the address http://localhost/servicemodelsamples/service.svc?wsdl.</span></span> <span data-ttu-id="04717-123">Como alternativa, você pode usar esse comportamento para expor metadados via HTTPS, definindo <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> para `true`.</span><span class="sxs-lookup"><span data-stu-id="04717-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="04717-124">Isso requer um endereço base HTTPS.</span><span class="sxs-lookup"><span data-stu-id="04717-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="04717-125">Para acessar o uso de ponto de extremidade MEX do serviço do [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="04717-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="04717-126">Isso gera um cliente com base nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="04717-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="04717-127">Para acessar os metadados do serviço usando o HTTP GET, aponte seu navegador para http://localhost/servicemodelsamples/service.svc?wsdl.</span><span class="sxs-lookup"><span data-stu-id="04717-127">To access the service's metadata using HTTP GET, point your browser to http://localhost/servicemodelsamples/service.svc?wsdl.</span></span>  
  
 <span data-ttu-id="04717-128">Se você remove esse comportamento e tente abrir o serviço, você receberá uma exceção.</span><span class="sxs-lookup"><span data-stu-id="04717-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="04717-129">Esse erro ocorre porque sem o comportamento, o ponto de extremidade configurado com o `IMetadataExchange` contrato não tem nenhuma implementação.</span><span class="sxs-lookup"><span data-stu-id="04717-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="04717-130">Se você definir `HttpGetEnabled` para `false`, você verá a página de ajuda CalculatorService em vez de ver os metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="04717-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="04717-131">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="04717-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="04717-132">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="04717-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="04717-133">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="04717-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="04717-134">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="04717-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="04717-135">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="04717-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="04717-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="04717-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="04717-137">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="04717-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="04717-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="04717-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## <a name="see-also"></a><span data-ttu-id="04717-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04717-139">See Also</span></span>
