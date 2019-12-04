---
title: Comportamento de publicação de metadados
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 3b3057d845ac37280ff46e6e15415758f1f0ba77
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714789"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="4b5b8-102">Comportamento de publicação de metadados</span><span class="sxs-lookup"><span data-stu-id="4b5b8-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="4b5b8-103">O exemplo de comportamento de publicação de metadados demonstra como controlar os recursos de publicação de metadados de um serviço.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="4b5b8-104">Para evitar a divulgação não intencional de metadados de serviço potencialmente confidenciais, a configuração padrão para Windows Communication Foundation (WCF) Services desabilita a publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="4b5b8-105">Esse comportamento é seguro por padrão, mas também significa que você não pode usar uma ferramenta de importação de metadados (como SvcUtil. exe) para gerar o código do cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço esteja explicitamente habilitado na configuração.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4b5b8-106">Para maior clareza, este exemplo demonstra como criar um ponto de extremidade de publicação de metadados não seguro.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="4b5b8-107">Esses pontos de extremidade estão potencialmente disponíveis para consumidores anônimos não autenticados e devem ser levados em vida antes da implantação desses pontos de extremidade para garantir que os metadados de um serviço sejam desmarcados publicamente.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="4b5b8-108">Consulte o exemplo de [ponto de extremidade de metadados seguro personalizado](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) para obter um exemplo que protege um ponto de extremidade de metadados.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="4b5b8-109">O exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o contrato de serviço `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="4b5b8-110">Neste exemplo, o cliente é um aplicativo de console (. exe) e o serviço é hospedado pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="4b5b8-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b5b8-111">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4b5b8-112">Para que um serviço exponha metadados, o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> deve ser configurado no serviço.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="4b5b8-113">Quando esse comportamento está presente, você pode publicar metadados Configurando um ponto de extremidade para expor o contrato de <xref:System.ServiceModel.Description.IMetadataExchange> como uma implementação de um protocolo de WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="4b5b8-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="4b5b8-114">Como uma conveniência, esse contrato recebeu o nome abreviado da configuração "IMetadataExchange".</span><span class="sxs-lookup"><span data-stu-id="4b5b8-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="4b5b8-115">Este exemplo usa o `mexHttpBinding`, que é uma associação padrão de conveniência equivalente ao `wsHttpBinding` com o modo de segurança definido como `None`.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="4b5b8-116">Um endereço relativo de "MEX" é usado no ponto de extremidade, que, quando resolvido em relação ao endereço base de serviços, resulta em um endereço de ponto de extremidade de `http://localhost/servicemodelsamples/service.svc/mex`.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="4b5b8-117">O seguinte mostra a configuração de comportamento:</span><span class="sxs-lookup"><span data-stu-id="4b5b8-117">The following shows the behavior configuration:</span></span>  
  
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
  
 <span data-ttu-id="4b5b8-118">O ponto de extremidade MEX é mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-118">The following shows the MEX endpoint.</span></span>  
  
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
  
 <span data-ttu-id="4b5b8-119">Este exemplo define a propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> como `true`, que também expõe os metadados do serviço usando HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="4b5b8-120">Para habilitar um ponto de extremidade de metadados GET de HTTP, o serviço deve ter um endereço base HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="4b5b8-121">A cadeia de caracteres de consulta `?wsdl` é usada no endereço base do serviço para acessar os metadados.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="4b5b8-122">Por exemplo, para ver o WSDL do serviço em um navegador da Web, você usaria o endereço `http://localhost/servicemodelsamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-122">For example, to see the WSDL for the service in a Web browser you would use the address `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span> <span data-ttu-id="4b5b8-123">Como alternativa, você pode usar esse comportamento para expor metadados por HTTPS, definindo <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="4b5b8-124">Isso requer um endereço base HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="4b5b8-125">Para acessar o ponto de extremidade MEX do serviço, use a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4b5b8-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="4b5b8-126">Isso gera um cliente com base nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="4b5b8-127">Para acessar os metadados do serviço usando HTTP GET, aponte seu navegador para `http://localhost/servicemodelsamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-127">To access the service's metadata using HTTP GET, point your browser to `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span>  
  
 <span data-ttu-id="4b5b8-128">Se você remover esse comportamento e tentar abrir o serviço, receberá uma exceção.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="4b5b8-129">Esse erro ocorre porque, sem o comportamento, o ponto de extremidade configurado com o contrato de `IMetadataExchange` não tem implementação.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="4b5b8-130">Se você definir `HttpGetEnabled` como `false`, verá a página de ajuda do CalculatorService em vez de ver os metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4b5b8-131">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4b5b8-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4b5b8-132">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b5b8-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4b5b8-133">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b5b8-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4b5b8-134">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b5b8-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4b5b8-135">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4b5b8-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-136">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="4b5b8-137">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4b5b8-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4b5b8-138">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
