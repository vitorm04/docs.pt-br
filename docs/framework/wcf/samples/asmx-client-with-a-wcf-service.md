---
title: Cliente ASMX com um serviço do WCF
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: 3c4728eae56a46c620499a1c0ba709e50c255d6c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925288"
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="5939b-102">Cliente ASMX com um serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="5939b-102">ASMX Client with a WCF Service</span></span>
<span data-ttu-id="5939b-103">Este exemplo demonstra como criar um serviço usando Windows Communication Foundation (WCF) e, em seguida, acessar o serviço de um cliente não WCF, como um cliente ASMX.</span><span class="sxs-lookup"><span data-stu-id="5939b-103">This sample demonstrates how to create a service using Windows Communication Foundation (WCF) and then access the service from a non-WCF client, such as an ASMX client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5939b-104">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5939b-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5939b-105">Este exemplo consiste em um programa de console do cliente (. exe) e uma biblioteca de serviços (. dll) hospedados pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="5939b-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="5939b-106">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="5939b-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="5939b-107">O contrato é definido pela `ICalculator` interface, que expõe operações matemáticas (`Add`, `Subtract`, `Multiply`e `Divide`).</span><span class="sxs-lookup"><span data-stu-id="5939b-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="5939b-108">O cliente ASMX faz solicitações síncronas para uma operação matemática e o serviço responde com o resultado.</span><span class="sxs-lookup"><span data-stu-id="5939b-108">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>  
  
 <span data-ttu-id="5939b-109">O serviço implementa um `ICalculator` contrato, conforme definido no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5939b-109">The service implements an `ICalculator` contract as defined in the following code.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="5939b-110">O <xref:System.Runtime.Serialization.DataContractSerializer> e<xref:System.Xml.Serialization.XmlSerializer> mapeiam os tipos CLR para uma representação XML.</span><span class="sxs-lookup"><span data-stu-id="5939b-110">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="5939b-111">O <xref:System.Runtime.Serialization.DataContractSerializer> interpreta algumas representações XML de forma diferente do XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="5939b-111">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="5939b-112">Geradores de proxy não WCF, como WSDL. exe, geram uma interface mais utilizável quando o XmlSerializer está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="5939b-112">Non-WCF proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="5939b-113">O <xref:System.ServiceModel.XmlSerializerFormatAttribute> é aplicado `ICalculator` à interface do, para garantir que o XmlSerializer seja usado para mapear tipos CLR para XML.</span><span class="sxs-lookup"><span data-stu-id="5939b-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="5939b-114">A implementação do serviço calcula e retorna o resultado apropriado.</span><span class="sxs-lookup"><span data-stu-id="5939b-114">The service implementation calculates and returns the appropriate result.</span></span>  
  
 <span data-ttu-id="5939b-115">O serviço expõe um único ponto de extremidade para se comunicar com o serviço, definido usando um arquivo de configuração (Web. config).</span><span class="sxs-lookup"><span data-stu-id="5939b-115">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="5939b-116">O ponto de extremidade consiste em um endereço, uma associação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="5939b-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="5939b-117">O serviço expõe o ponto de extremidade no endereço base fornecido pelo host do Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="5939b-117">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="5939b-118">O `binding` atributo é definido como BasicHttpBinding que fornece comunicações http usando SOAP 1,1, que é compatível com WS-I BasicProfile 1,1, conforme mostrado na configuração de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5939b-118">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="5939b-119">O cliente ASMX se comunica com o serviço WCF usando um proxy tipado que é gerado pelo utilitário WSDL (Web Services Description Language) (WSDL. exe).</span><span class="sxs-lookup"><span data-stu-id="5939b-119">The ASMX client communicates with the WCF service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="5939b-120">O proxy tipado está contido no arquivo generatedClient.cs.</span><span class="sxs-lookup"><span data-stu-id="5939b-120">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="5939b-121">O utilitário WSDL recupera metadados para o serviço especificado e gera um proxy de tipo para ser usado por um cliente para se comunicar.</span><span class="sxs-lookup"><span data-stu-id="5939b-121">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="5939b-122">Por padrão, a estrutura não expõe nenhum metadado.</span><span class="sxs-lookup"><span data-stu-id="5939b-122">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="5939b-123">Para expor os metadados necessários para gerar o proxy, você deve adicionar um [ \<> de metadados](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) e `True` definir seu `httpGetEnabled` atributo como, conforme mostrado na configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="5939b-123">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>  
  
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
  
 <span data-ttu-id="5939b-124">Execute o comando a seguir em um prompt de comando no diretório do cliente para gerar o proxy de tipo.</span><span class="sxs-lookup"><span data-stu-id="5939b-124">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 <span data-ttu-id="5939b-125">Usando o proxy de tipo gerado, o cliente pode acessar um determinado ponto de extremidade de serviço Configurando o endereço apropriado.</span><span class="sxs-lookup"><span data-stu-id="5939b-125">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="5939b-126">O cliente usa um arquivo de configuração (App. config) para especificar o ponto de extremidade com o qual se comunicar.</span><span class="sxs-lookup"><span data-stu-id="5939b-126">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 <span data-ttu-id="5939b-127">A implementação do cliente constrói uma instância do proxy digitado para começar a se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="5939b-127">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="5939b-128">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="5939b-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5939b-129">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="5939b-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```console 
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5939b-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5939b-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5939b-131">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5939b-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5939b-132">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5939b-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5939b-133">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5939b-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5939b-134">Para obter mais informações sobre como passar e retornar tipos de dados complexos, consulte: [Associação de dados em um cliente Windows Forms](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [Associação de dados em um cliente Windows Presentation Foundation](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md)e [Associação de dados em um cliente ASP.net](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span><span class="sxs-lookup"><span data-stu-id="5939b-134">For more information about passing and returning complex data types see: [Data Binding in a Windows Forms Client](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5939b-135">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5939b-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5939b-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5939b-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5939b-137">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="5939b-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5939b-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5939b-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
