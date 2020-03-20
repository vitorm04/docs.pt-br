---
title: Comportamento de publicação de metadados
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: dade6d1a53fd99b994fb3c027db4e51392bfdcda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144390"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="1851c-102">Comportamento de publicação de metadados</span><span class="sxs-lookup"><span data-stu-id="1851c-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="1851c-103">A amostra Comportamento de publicação de metadados demonstra como controlar os recursos de publicação de metadados de um serviço.</span><span class="sxs-lookup"><span data-stu-id="1851c-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="1851c-104">Para evitar a divulgação não intencional de metadados de serviços potencialmente sensíveis, a configuração padrão dos serviços do Windows Communication Foundation (WCF) desativa a publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="1851c-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="1851c-105">Esse comportamento é seguro por padrão, mas também significa que você não pode usar uma ferramenta de importação de metadados (como svcutil.exe) para gerar o código do cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço esteja explicitamente ativado na configuração.</span><span class="sxs-lookup"><span data-stu-id="1851c-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1851c-106">Para obter clareza, esta amostra demonstra como criar um ponto final de publicação de metadados não seguro.</span><span class="sxs-lookup"><span data-stu-id="1851c-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="1851c-107">Esses pontos finais estão potencialmente disponíveis para consumidores anônimos não autenticados e os cuidados devem ser tomados antes de implantar tais pontos finais para garantir que a divulgação pública dos metadados de um serviço seja apropriada.</span><span class="sxs-lookup"><span data-stu-id="1851c-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="1851c-108">Consulte a amostra [Deponto de Metadados Personalizados para](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) obter uma amostra que proteja um ponto final de metadados.</span><span class="sxs-lookup"><span data-stu-id="1851c-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="1851c-109">A amostra é baseada no [Getting](../../../../docs/framework/wcf/samples/getting-started-sample.md)Started `ICalculator` , que implementa o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="1851c-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="1851c-110">Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="1851c-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1851c-111">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="1851c-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1851c-112">Para que um serviço exponha metadados, o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> deve ser configurado no serviço.</span><span class="sxs-lookup"><span data-stu-id="1851c-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="1851c-113">Quando esse comportamento estiver presente, você pode publicar metadados <xref:System.ServiceModel.Description.IMetadataExchange> configurando um ponto final para expor o contrato como uma implementação de um protocolo WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="1851c-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="1851c-114">Como conveniência, este contrato recebeu o nome de configuração abreviado de "IMetadataExchange".</span><span class="sxs-lookup"><span data-stu-id="1851c-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="1851c-115">Esta amostra `mexHttpBinding`usa o , que é uma `wsHttpBinding` vinculação padrão de `None`conveniência que é equivalente ao com o modo de segurança definido para .</span><span class="sxs-lookup"><span data-stu-id="1851c-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="1851c-116">Um endereço relativo de "mex" é usado no ponto final, que quando resolvido `http://localhost/servicemodelsamples/service.svc/mex`contra o endereço base de serviços resulta em um endereço de ponto final de .</span><span class="sxs-lookup"><span data-stu-id="1851c-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="1851c-117">A seguir, mostra a configuração de comportamento:</span><span class="sxs-lookup"><span data-stu-id="1851c-117">The following shows the behavior configuration:</span></span>  
  
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
  
 <span data-ttu-id="1851c-118">O seguinte mostra o ponto final do MEX.</span><span class="sxs-lookup"><span data-stu-id="1851c-118">The following shows the MEX endpoint.</span></span>  
  
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
  
 <span data-ttu-id="1851c-119">Esta amostra <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> define `true`a propriedade para , que também expõe os metadados do serviço usando HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="1851c-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="1851c-120">Para habilitar um ponto final de metadados HTTP GET, o serviço deve ter um endereço base HTTP.</span><span class="sxs-lookup"><span data-stu-id="1851c-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="1851c-121">A seqüência de consultas `?wsdl` é usada no endereço base do serviço para acessar os metadados.</span><span class="sxs-lookup"><span data-stu-id="1851c-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="1851c-122">Por exemplo, para ver o WSDL para o serviço `http://localhost/servicemodelsamples/service.svc?wsdl`em um navegador da Web, você usaria o endereço .</span><span class="sxs-lookup"><span data-stu-id="1851c-122">For example, to see the WSDL for the service in a Web browser you would use the address `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span> <span data-ttu-id="1851c-123">Alternativamente, você pode usar esse comportamento para <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> expor `true`metadados sobre HTTPS, configurando para .</span><span class="sxs-lookup"><span data-stu-id="1851c-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="1851c-124">Isso requer um endereço base HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1851c-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="1851c-125">Para acessar o ponto final do serviço, use a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1851c-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="1851c-126">Isso gera um cliente com base nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="1851c-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="1851c-127">Para acessar os metadados do serviço usando HTTP `http://localhost/servicemodelsamples/service.svc?wsdl`GET, aponte seu navegador para .</span><span class="sxs-lookup"><span data-stu-id="1851c-127">To access the service's metadata using HTTP GET, point your browser to `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span>  
  
 <span data-ttu-id="1851c-128">Se você remover esse comportamento e tentar abrir o serviço, você terá uma exceção.</span><span class="sxs-lookup"><span data-stu-id="1851c-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="1851c-129">Esse erro ocorre porque, sem o comportamento, o ponto final configurado com o `IMetadataExchange` contrato não tem implementação.</span><span class="sxs-lookup"><span data-stu-id="1851c-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="1851c-130">Se você `HttpGetEnabled` `false`definir, verá a página de ajuda CalculadoraService em vez de ver os metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="1851c-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1851c-131">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1851c-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1851c-132">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1851c-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1851c-133">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1851c-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1851c-134">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1851c-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1851c-135">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1851c-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1851c-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1851c-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1851c-137">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="1851c-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1851c-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="1851c-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
