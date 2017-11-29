---
title: "Cliente ASMX com um serviço do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 11ccb40fb4c29678ce0552da2dd8eb29c1ae561e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="a7aac-102">Cliente ASMX com um serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="a7aac-102">ASMX Client with a WCF Service</span></span>
<span data-ttu-id="a7aac-103">Este exemplo demonstra como criar um serviço usando [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e, em seguida, acessar o serviço de não[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, como um cliente ASMX.</span><span class="sxs-lookup"><span data-stu-id="a7aac-103">This sample demonstrates how to create a service using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and then access the service from a non-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, such as an ASMX client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7aac-104">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="a7aac-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a7aac-105">Este exemplo consiste em um programa de console de cliente (.exe) e uma biblioteca de serviço (. dll) hospedada pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="a7aac-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="a7aac-106">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="a7aac-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="a7aac-107">O contrato é definido pelo `ICalculator` interface, que expõe operações matemáticas (`Add`, `Subtract`, `Multiply`, e `Divide`).</span><span class="sxs-lookup"><span data-stu-id="a7aac-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="a7aac-108">O cliente ASMX faz solicitações síncronas para uma operação matemática e as respostas do serviço com o resultado.</span><span class="sxs-lookup"><span data-stu-id="a7aac-108">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>  
  
 <span data-ttu-id="a7aac-109">O serviço implementa uma `ICalculator` contrato conforme definido no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a7aac-109">The service implements an `ICalculator` contract as defined in the following code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="a7aac-110">O <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Xml.Serialization.XmlSerializer> mapear tipos CLR para uma representação XML.</span><span class="sxs-lookup"><span data-stu-id="a7aac-110">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="a7aac-111">O <xref:System.Runtime.Serialization.DataContractSerializer> interpreta algumas representações XML diferente XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="a7aac-111">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="a7aac-112">Não[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] geradores de proxy como Wsdl.exe, geram uma interface mais utilizável quando o XmlSerializer está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="a7aac-112">Non-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="a7aac-113">O <xref:System.ServiceModel.XmlSerializerFormatAttribute> é aplicada para o `ICalculator` interface, para garantir que o XmlSerializer é usado para mapear os tipos CLR em XML.</span><span class="sxs-lookup"><span data-stu-id="a7aac-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="a7aac-114">A implementação do serviço calcula e retorna o resultado apropriado.</span><span class="sxs-lookup"><span data-stu-id="a7aac-114">The service implementation calculates and returns the appropriate result.</span></span>  
  
 <span data-ttu-id="a7aac-115">O serviço expõe um ponto de extremidade de comunicação com o serviço, definido usando um arquivo de configuração (Web. config).</span><span class="sxs-lookup"><span data-stu-id="a7aac-115">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="a7aac-116">O ponto de extremidade consiste em um endereço, uma ligação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="a7aac-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="a7aac-117">O serviço expõe o ponto de extremidade no endereço base fornecido pelo host do Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="a7aac-117">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="a7aac-118">O `binding` atributo é definido como basicHttpBinding que permite a comunicação HTTP usando SOAP 1.1, que é compatível com o WS-I Basic Profile 1.1 conforme mostrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="a7aac-118">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->  
    <endpoint address=""  
              binding="basicHttpBinding"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="a7aac-119">O cliente ASMX se comunica com o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço usando um proxy tipado que é gerado pelo utilitário de WSDL Web Services Description Language () (Wsdl.exe).</span><span class="sxs-lookup"><span data-stu-id="a7aac-119">The ASMX client communicates with the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="a7aac-120">O proxy digitado está contido no generatedClient.cs arquivo.</span><span class="sxs-lookup"><span data-stu-id="a7aac-120">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="a7aac-121">O utilitário WSDL recupera metadados para o serviço especificado e gera um proxy tipado para uso por um cliente para se comunicar.</span><span class="sxs-lookup"><span data-stu-id="a7aac-121">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="a7aac-122">Por padrão, a estrutura não expõem quaisquer metadados.</span><span class="sxs-lookup"><span data-stu-id="a7aac-122">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="a7aac-123">Para expor os metadados necessários para gerar o proxy, você deve adicionar um [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) e defina seu `httpGetEnabled` atributo `True` conforme mostrado na configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="a7aac-123">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- Setting httpGetEnabled to True on the serviceMetadata  
           behavior exposes the service's wsdl at <base address>?wsdl :  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="a7aac-124">Execute o seguinte comando em um prompt de comando no diretório do cliente para gerar o proxy digitado.</span><span class="sxs-lookup"><span data-stu-id="a7aac-124">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 <span data-ttu-id="a7aac-125">Usando o proxy com tipo gerado, o cliente pode acessar um ponto de extremidade do serviço em questão, configurando o endereço apropriado.</span><span class="sxs-lookup"><span data-stu-id="a7aac-125">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="a7aac-126">O cliente usa um arquivo de configuração (App. config) para especificar o ponto de extremidade para se comunicar com.</span><span class="sxs-lookup"><span data-stu-id="a7aac-126">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 <span data-ttu-id="a7aac-127">A implementação de cliente constrói uma instância do proxy com tipo para começar a se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="a7aac-127">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>  
  
```  
// Create a client to the CalculatorService.  
using (CalculatorService client = new CalculatorService())  
{  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
}  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="a7aac-128">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="a7aac-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a7aac-129">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="a7aac-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a7aac-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="a7aac-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a7aac-131">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a7aac-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a7aac-132">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a7aac-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a7aac-133">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a7aac-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a7aac-134">passando e retornando dados complexos tipos consulte: [associação de dados em um cliente de formulários do Windows](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [associação de dados em um cliente do Windows Presentation Foundation](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), e [associação de dados em um ASP.NET Cliente](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span><span class="sxs-lookup"><span data-stu-id="a7aac-134"> passing and returning complex data types see: [Data Binding in a Windows Forms Client](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a7aac-135">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a7aac-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a7aac-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a7aac-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a7aac-137">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="a7aac-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a7aac-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a7aac-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
  
## <a name="see-also"></a><span data-ttu-id="a7aac-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7aac-139">See Also</span></span>
