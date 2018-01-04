---
title: "Publicação personalizada de WSDL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba62c44ecf72df7faaed77f54f07ecd88157c6d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-wsdl-publication"></a><span data-ttu-id="cc310-102">Publicação personalizada de WSDL</span><span class="sxs-lookup"><span data-stu-id="cc310-102">Custom WSDL Publication</span></span>
<span data-ttu-id="cc310-103">Este exemplo demonstra como:</span><span class="sxs-lookup"><span data-stu-id="cc310-103">This sample demonstrates how to:</span></span>  
  
-   <span data-ttu-id="cc310-104">Implementar um <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> em um personalizado <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> atributo para exportar as propriedades de atributo como anotações de WSDL.</span><span class="sxs-lookup"><span data-stu-id="cc310-104">Implement a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> on a custom <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> attribute to export attribute properties as WSDL annotations.</span></span>  
  
-   <span data-ttu-id="cc310-105">Implementar <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> para importar as anotações de WSDL personalizadas.</span><span class="sxs-lookup"><span data-stu-id="cc310-105">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> to import the custom WSDL annotations.</span></span>  
  
-   <span data-ttu-id="cc310-106">Implementar <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> e <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> em um personalizado contrato comportamento e o comportamento de uma operação personalizada, respectivamente, para gravar anotações importadas como comentários no CodeDom para o contrato importado e a operação.</span><span class="sxs-lookup"><span data-stu-id="cc310-106">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> on a custom contract behavior and a custom operation behavior, respectively, to write imported annotations as comments in the CodeDom for the imported contract and operation.</span></span>  
  
-   <span data-ttu-id="cc310-107">Use o <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> para baixar o WSDL, uma <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Importar WSDL usando o importador WSDL personalizado e o <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> para gerar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] código de cliente com as anotações de WSDL como / / / e ' ' comentários em c# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cc310-107">Use the <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> to download the WSDL, a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> to import the WSDL using the custom WSDL importer, and the <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> to generate [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client code with the WSDL annotations as /// and ''' comments in C# and Visual Basic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc310-108">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="cc310-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="cc310-109">Serviço</span><span class="sxs-lookup"><span data-stu-id="cc310-109">Service</span></span>  
 <span data-ttu-id="cc310-110">O serviço neste exemplo é marcado com dois atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="cc310-110">The service in this sample is marked with two custom attributes.</span></span> <span data-ttu-id="cc310-111">Primeiro, o `WsdlDocumentationAttribute`, aceita uma cadeia de caracteres no construtor e podem ser aplicadas para fornecer uma interface de contrato ou operação com uma cadeia de caracteres que descreve seu uso.</span><span class="sxs-lookup"><span data-stu-id="cc310-111">The first, the `WsdlDocumentationAttribute`, accepts a string in the constructor and can be applied to provide a contract interface or operation with a string that describes its usage.</span></span> <span data-ttu-id="cc310-112">O segundo, `WsdlParamOrReturnDocumentationAttribute`, podem ser aplicadas para retornar valores ou parâmetros para descrever esses valores na operação.</span><span class="sxs-lookup"><span data-stu-id="cc310-112">The second, `WsdlParamOrReturnDocumentationAttribute`, can be applied to return values or parameters to describe those values in the operation.</span></span> <span data-ttu-id="cc310-113">O exemplo a seguir mostra um contrato de serviço, `ICalculator`, descritas usando esses atributos.</span><span class="sxs-lookup"><span data-stu-id="cc310-113">The following example shows a service contract, `ICalculator`, described using these attributes.</span></span>  
  
```  
// Define a service contract.      
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
// Document it.  
[WsdlDocumentation("The ICalculator contract performs basic calculation services.")]  
public interface ICalculator  
{  
    [OperationContract]  
    [WsdlDocumentation("The Add operation adds two numbers and returns the result.")]  
    [return:WsdlParamOrReturnDocumentation("The result of adding the two arguments together.")]  
    double Add(  
      [WsdlParamOrReturnDocumentation("The first value to add.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to add.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Subtract operation subtracts the second argument from the first.")]  
    [return:WsdlParamOrReturnDocumentation("The result of the second argument subtracted from the first.")]  
    double Subtract(  
      [WsdlParamOrReturnDocumentation("The value from which the second is subtracted.")]double n1,   
      [WsdlParamOrReturnDocumentation("The value that is subtracted from the first.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Multiply operation multiplies two values.")]  
    [return:WsdlParamOrReturnDocumentation("The result of multiplying the first and second arguments.")]  
    double Multiply(  
      [WsdlParamOrReturnDocumentation("The first value to multiply.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to multiply.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Divide operation returns the value of the first argument divided by the second argument.")]  
    [return:WsdlParamOrReturnDocumentation("The result of dividing the first argument by the second.")]  
    double Divide(  
      [WsdlParamOrReturnDocumentation("The numerator.")]double n1,   
      [WsdlParamOrReturnDocumentation("The denominator.")]double n2  
    );  
}  
```  
  
 <span data-ttu-id="cc310-114">O `WsdlDocumentationAttribute` implementa <xref:System.ServiceModel.Description.IContractBehavior> e <xref:System.ServiceModel.Description.IOperationBehavior>, portanto, as instâncias de atributo são adicionadas ao correspondente <xref:System.ServiceModel.Description.ContractDescription> ou <xref:System.ServiceModel.Description.OperationDescription> quando o serviço é aberto.</span><span class="sxs-lookup"><span data-stu-id="cc310-114">The `WsdlDocumentationAttribute` implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior>, so the attribute instances are added to the corresponding <xref:System.ServiceModel.Description.ContractDescription> or <xref:System.ServiceModel.Description.OperationDescription> when the service is opened.</span></span> <span data-ttu-id="cc310-115">O atributo também implementa <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span><span class="sxs-lookup"><span data-stu-id="cc310-115">The attribute also implements <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span></span> <span data-ttu-id="cc310-116">Quando <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> é chamado, o <xref:System.ServiceModel.Description.WsdlExporter> que é usado para exportar os metadados e o <xref:System.ServiceModel.Description.WsdlContractConversionContext> que contém a descrição do serviço objetos são passados como parâmetros para habilitar a modificação dos metadados exportado.</span><span class="sxs-lookup"><span data-stu-id="cc310-116">When <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> is called, the <xref:System.ServiceModel.Description.WsdlExporter> that is used to export the metadata and the <xref:System.ServiceModel.Description.WsdlContractConversionContext> that contains the service description objects are passed in as parameters enabling the modification of the exported metadata.</span></span>  
  
 <span data-ttu-id="cc310-117">Neste exemplo, dependendo se o objeto de contexto de exportação possui um <xref:System.ServiceModel.Description.ContractDescription> ou um <xref:System.ServiceModel.Description.OperationDescription>, um comentário é extraído do atributo usando a propriedade de texto e é adicionado ao elemento de anotação WSDL, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="cc310-117">In this sample, depending upon whether the export context object has a <xref:System.ServiceModel.Description.ContractDescription> or an <xref:System.ServiceModel.Description.OperationDescription>, a comment is extracted from the attribute using the text property and is added to the WSDL annotation element as shown in the following code.</span></span>  
  
```  
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (contractDescription != null)  
    {  
        // Inside this block it is the contract-level comment attribute.  
        // This.Text returns the string for the contract attribute.  
        // Set the doc element; if this isn't done first, there is no XmlElement in the   
        // DocumentElement property.  
        context.WsdlPortType.Documentation = string.Empty;  
        // Contract comments.  
        XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;  
        XmlElement summaryElement = owner.CreateElement("summary");  
        summaryElement.InnerText = this.Text;  
        context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);  
    }  
    else  
    {  
        Operation operation = context.GetOperation(operationDescription);  
        if (operation != null)  
        {  
            // We are dealing strictly with the operation here.  
            // This.Text returns the string for the operation-level attributes.  
            // Set the doc element; if this isn't done first, there is no XmlElement in the   
            // DocumentElement property.  
            operation.Documentation = String.Empty;  
  
            // Operation C# triple comments.  
            XmlDocument owner = operation.DocumentationElement.OwnerDocument;  
            XmlElement newSummaryElement = owner.CreateElement("summary");  
            newSummaryElement.InnerText = this.Text;  
            operation.DocumentationElement.AppendChild(newSummaryElement);  
```  
  
 <span data-ttu-id="cc310-118">Se uma operação está sendo exportada, o exemplo usa reflexão para obter qualquer `WsdlParamOrReturnDocumentationAttribute` valores para parâmetros e valores de retorno e os adiciona aos elementos WSDL anotação para a operação da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="cc310-118">If an operation is being exported, the sample uses reflection to obtain any `WsdlParamOrReturnDocumentationAttribute` values for parameters and return values and adds them to the WSDL annotation elements for that operation as follows.</span></span>  
  
```  
// Get returns information  
ParameterInfo returnValue = operationDescription.SyncMethod.ReturnParameter;  
object[] returnAttrs = returnValue.GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
if (returnAttrs.Length != 0)  
{  
    // <returns>text.</returns>  
    XmlElement returnsElement = owner.CreateElement("returns");  
    returnsElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)returnAttrs[0]).ParamComment;  
    operation.DocumentationElement.AppendChild(returnsElement);  
}  
  
// Get parameter information.  
ParameterInfo[] args = operationDescription.SyncMethod.GetParameters();  
for (int i = 0; i < args.Length; i++)  
{  
    object[] docAttrs = args[i].GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
    if (docAttrs.Length == 1)  
    {  
        // <param name="Int1">Text.</param>  
        XmlElement newParamElement = owner.CreateElement("param");  
        XmlAttribute paramName = owner.CreateAttribute("name");  
        paramName.Value = args[i].Name;  
        newParamElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)docAttrs[0]).ParamComment;  
        newParamElement.Attributes.Append(paramName);  
        operation.DocumentationElement.AppendChild(newParamElement);  
    }  
}  
```  
  
 <span data-ttu-id="cc310-119">O exemplo, em seguida, publica os metadados da maneira padrão, usando o seguinte arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="cc310-119">The sample then publishes metadata in the standard way, using the following configuration file.</span></span>  
  
```xml  
<services>  
  <service   
      name="Microsoft.ServiceModel.Samples.CalculatorService"  
      behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- ICalculator is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    <!-- the mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
    <endpoint address="mex"  
              binding="mexHttpBinding"  
              contract="IMetadataExchange" />  
  </service>  
</services>  
  
<!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="svcutil-client"></a><span data-ttu-id="cc310-120">Cliente svcutil</span><span class="sxs-lookup"><span data-stu-id="cc310-120">Svcutil client</span></span>  
 <span data-ttu-id="cc310-121">Este exemplo não usar o Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="cc310-121">This sample does not use Svcutil.exe.</span></span> <span data-ttu-id="cc310-122">O contrato é fornecido no generatedClient.cs arquivo de modo que, depois que o exemplo demonstra a importação WSDL personalizada e geração de código, o serviço pode ser invocado.</span><span class="sxs-lookup"><span data-stu-id="cc310-122">The contract is provided in the generatedClient.cs file so that after the sample demonstrates custom WSDL import and code generation, the service can be invoked.</span></span> <span data-ttu-id="cc310-123">Para usar o seguinte importador WSDL personalizado para este exemplo, você pode executar o Svcutil.exe e especificar o `/svcutilConfig` opção, fornecendo o caminho para o arquivo de configuração de cliente usado neste exemplo, o que faz referência a `WsdlDocumentation.dll` biblioteca.</span><span class="sxs-lookup"><span data-stu-id="cc310-123">To use the following custom WSDL importer for this example, you can run Svcutil.exe and specify the `/svcutilConfig` option, giving the path to the client configuration file used in this sample, which references the `WsdlDocumentation.dll` library.</span></span> <span data-ttu-id="cc310-124">Para carregar o `WsdlDocumentationImporter`, no entanto, Svuctil.exe deve ser capaz de localizar e carregar o `WsdlDocumentation.dll` biblioteca, o que significa que o que ele está registrado no cache de assembly global, no caminho, ou está no mesmo diretório que o Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="cc310-124">To load the `WsdlDocumentationImporter`, however, Svuctil.exe must be able to locate and load the `WsdlDocumentation.dll` library, which means either that it is registered in the global assembly cache, in the path, or is in the same directory as Svcutil.exe.</span></span> <span data-ttu-id="cc310-125">Para obter um exemplo básico como este, o mais fácil fazer é copiar Svcutil.exe e o arquivo de configuração do cliente para o mesmo diretório que `WsdlDocumentation.dll` e executá-lo lá.</span><span class="sxs-lookup"><span data-stu-id="cc310-125">For a basic sample such as this, the easiest thing to do is to copy Svcutil.exe and the client configuration file into the same directory as `WsdlDocumentation.dll` and run it from there.</span></span>  
  
## <a name="the-custom-wsdl-importer"></a><span data-ttu-id="cc310-126">O importador WSDL personalizado</span><span class="sxs-lookup"><span data-stu-id="cc310-126">The Custom WSDL Importer</span></span>  
 <span data-ttu-id="cc310-127">Personalizado <xref:System.ServiceModel.Description.IWsdlImportExtension> objeto `WsdlDocumentationImporter` também implementa <xref:System.ServiceModel.Description.IContractBehavior> e <xref:System.ServiceModel.Description.IOperationBehavior> a serem adicionadas ao ServiceEndpoints importados e <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> e <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> para ser chamado para modificar a geração de código quando a operação ou um contrato código está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="cc310-127">The custom <xref:System.ServiceModel.Description.IWsdlImportExtension> object `WsdlDocumentationImporter` also implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior> to be added to the imported ServiceEndpoints and <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> to be invoked to modify the code generation when the contract or operation code is being created.</span></span>  
  
 <span data-ttu-id="cc310-128">Primeiro, do <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> método, o exemplo determina se a anotação de WSDL está no nível do contrato ou de operação e se adiciona como um comportamento no escopo apropriado, passando o texto da anotação importados para o construtor.</span><span class="sxs-lookup"><span data-stu-id="cc310-128">First, in the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method, the sample determines whether the WSDL annotation is at the contract or operation level, and adds itself as a behavior at the appropriate scope, passing the imported annotation text to its constructor.</span></span>  
  
```  
public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
{  
    // Contract Documentation  
    if (context.WsdlPortType.Documentation != null)  
    {  
        // System examines the contract behaviors to see whether any implement IWsdlImportExtension.  
        context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
    }  
    // Operation Documentation  
    foreach (Operation operation in context.WsdlPortType.Operations)  
    {  
        if (operation.Documentation != null)  
        {  
            OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
            if (operationDescription != null)  
            {  
                // System examines the operation behaviors to see whether any implement IWsdlImportExtension.  
                operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="cc310-129">Em seguida, quando o código for gerado, o sistema invoca o <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> e <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> métodos, passando as informações de contexto apropriado.</span><span class="sxs-lookup"><span data-stu-id="cc310-129">Then, when the code is generated, the system invokes the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> methods, passing the appropriate context information.</span></span> <span data-ttu-id="cc310-130">O exemplo formata as anotações de WSDL personalizadas e insere-los como comentários de CodeDom.</span><span class="sxs-lookup"><span data-stu-id="cc310-130">The sample formats the custom WSDL annotations and inserts them as comments into the CodeDom.</span></span>  
  
```  
public void GenerateContract(ServiceContractGenerationContext context)  
{  
    Debug.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(FormatComments(text));  
}  
  
public void GenerateOperation(OperationContractGenerationContext context)  
{  
    context.SyncMethod.Comments.AddRange(FormatComments(text));  
    Debug.WriteLine("In generate operation.");  
}  
```  
  
## <a name="the-client-application"></a><span data-ttu-id="cc310-131">O aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="cc310-131">The Client Application</span></span>  
 <span data-ttu-id="cc310-132">O aplicativo cliente carrega o importador WSDL personalizado especificando-o no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cc310-132">The client application loads the custom WSDL importer by specifying it in the application configuration file.</span></span>  
  
```xml  
<client>  
  <endpoint address="http://localhost/servicemodelsamples/service.svc"   
  binding="wsHttpBinding"   
  contract="ICalculator" />  
  <metadata>  
    <wsdlImporters>  
      <extension type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
    </wsdlImporters>  
  </metadata>  
</client>  
```  
  
 <span data-ttu-id="cc310-133">Depois que o importador personalizado foi especificado, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metadados sistema carrega o importador personalizado em qualquer <xref:System.ServiceModel.Description.WsdlImporter> criado para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="cc310-133">Once the custom importer has been specified, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metadata system loads the custom importer into any <xref:System.ServiceModel.Description.WsdlImporter> created for that purpose.</span></span> <span data-ttu-id="cc310-134">Este exemplo usa o <xref:System.ServiceModel.Description.MetadataExchangeClient> para baixar os metadados, o <xref:System.ServiceModel.Description.WsdlImporter> adequadamente configurado para importar os metadados usando o importador personalizado, o exemplo cria, e o <xref:System.ServiceModel.Description.ServiceContractGenerator> para compilar as informações de contrato modificado em ambos Visual Basic e o cliente código c# que pode ser usado no Visual Studio para dar suporte ao Intellisense ou compilado em documentação XML.</span><span class="sxs-lookup"><span data-stu-id="cc310-134">This sample uses the <xref:System.ServiceModel.Description.MetadataExchangeClient> to download the metadata, the <xref:System.ServiceModel.Description.WsdlImporter> properly configured to import the metadata using the custom importer the sample creates, and the <xref:System.ServiceModel.Description.ServiceContractGenerator> to compile the modified contract information into both Visual Basic and C# client code that can be used in Visual Studio to support Intellisense or compiled into XML documentation.</span></span>  
  
```  
/// From WSDL Documentation:  
///   
/// <summary>The ICalculator contract performs basic calculation   
/// services.</summary>   
///   
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.ServiceModel.Samples", ConfigurationName="ICalculator")]  
public interface ICalculator  
{  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Add operation adds two numbers and returns the   
    /// result.</summary><returns>The result of adding the two arguments   
    /// together.</returns><param name="n1">The first value to add.</param><param   
    /// name="n2">The second value to add.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Add", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/AddResponse")]  
    double Add(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Subtract operation subtracts the second argument from the   
    /// first.</summary><returns>The result of the second argument subtracted from the   
    /// first.</returns><param name="n1">The value from which the second is   
    /// subtracted.</param><param name="n2">The value that is subtracted from the   
    /// first.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Subtract", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/SubtractResponse")]  
    double Subtract(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Multiply operation multiplies two values.</summary><returns>The   
    /// result of multiplying the first and second arguments.</returns><param   
    /// name="n1">The first value to multiply.</param><param name="n2">The second value   
    /// to multiply.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Multiply", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/MultiplyResponse")]  
    double Multiply(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Divide operation returns the value of the first argument divided   
    /// by the second argument.</summary><returns>The result of dividing the first   
    /// argument by the second.</returns><param name="n1">The numerator.</param><param   
    /// name="n2">The denominator.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Divide", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/DivideResponse")]  
    double Divide(double n1, double n2);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cc310-135">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="cc310-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cc310-136">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cc310-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cc310-137">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cc310-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="cc310-138">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cc310-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cc310-139">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cc310-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cc310-140">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cc310-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cc310-141">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="cc310-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cc310-142">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cc310-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
  
## <a name="see-also"></a><span data-ttu-id="cc310-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc310-143">See Also</span></span>
