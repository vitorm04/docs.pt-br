---
title: Publicação personalizada de WSDL
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: ae6d5fdf243d5000090e993bd3353c6180d0ccaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145053"
---
# <a name="custom-wsdl-publication"></a><span data-ttu-id="91fd5-102">Publicação personalizada de WSDL</span><span class="sxs-lookup"><span data-stu-id="91fd5-102">Custom WSDL Publication</span></span>
<span data-ttu-id="91fd5-103">Este exemplo demonstra como:</span><span class="sxs-lookup"><span data-stu-id="91fd5-103">This sample demonstrates how to:</span></span>  
  
- <span data-ttu-id="91fd5-104">Implementar <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> um atributo personalizado <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> para exportar propriedades de atributos como anotações WSDL.</span><span class="sxs-lookup"><span data-stu-id="91fd5-104">Implement a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> on a custom <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> attribute to export attribute properties as WSDL annotations.</span></span>  
  
- <span data-ttu-id="91fd5-105">Implementar <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> para importar as anotações personalizadas do WSDL.</span><span class="sxs-lookup"><span data-stu-id="91fd5-105">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> to import the custom WSDL annotations.</span></span>  
  
- <span data-ttu-id="91fd5-106">Implementar <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> e em um comportamento de contrato personalizado e um comportamento de operação personalizado, respectivamente, para escrever anotações importadas como comentários no CodeDom para o contrato e operação importados.</span><span class="sxs-lookup"><span data-stu-id="91fd5-106">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> on a custom contract behavior and a custom operation behavior, respectively, to write imported annotations as comments in the CodeDom for the imported contract and operation.</span></span>  
  
- <span data-ttu-id="91fd5-107">Use <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> o para baixar o WSDL, um <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> para importar o WSDL <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> usando o importador WSDL personalizado, e para gerar o código cliente da Windows Communication Foundation (WCF) com as anotações WSDL como /// e ''' comentários em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="91fd5-107">Use the <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> to download the WSDL, a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> to import the WSDL using the custom WSDL importer, and the <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> to generate Windows Communication Foundation (WCF) client code with the WSDL annotations as /// and ''' comments in C# and Visual Basic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91fd5-108">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="91fd5-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="91fd5-109">Serviço</span><span class="sxs-lookup"><span data-stu-id="91fd5-109">Service</span></span>  
 <span data-ttu-id="91fd5-110">O serviço nesta amostra é marcado com dois atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="91fd5-110">The service in this sample is marked with two custom attributes.</span></span> <span data-ttu-id="91fd5-111">O primeiro, `WsdlDocumentationAttribute`o , aceita uma corda no construtor e pode ser aplicado para fornecer uma interface de contrato ou operação com uma string que descreve seu uso.</span><span class="sxs-lookup"><span data-stu-id="91fd5-111">The first, the `WsdlDocumentationAttribute`, accepts a string in the constructor and can be applied to provide a contract interface or operation with a string that describes its usage.</span></span> <span data-ttu-id="91fd5-112">O segundo, `WsdlParamOrReturnDocumentationAttribute`pode ser aplicado para devolver valores ou parâmetros para descrever esses valores na operação.</span><span class="sxs-lookup"><span data-stu-id="91fd5-112">The second, `WsdlParamOrReturnDocumentationAttribute`, can be applied to return values or parameters to describe those values in the operation.</span></span> <span data-ttu-id="91fd5-113">O exemplo a seguir `ICalculator`mostra um contrato de serviço, descrito usando esses atributos.</span><span class="sxs-lookup"><span data-stu-id="91fd5-113">The following example shows a service contract, `ICalculator`, described using these attributes.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="91fd5-114">Os `WsdlDocumentationAttribute` <xref:System.ServiceModel.Description.IContractBehavior> implementos <xref:System.ServiceModel.Description.IOperationBehavior>e , assim, as instâncias de atributo são adicionadas ao correspondente <xref:System.ServiceModel.Description.ContractDescription> ou <xref:System.ServiceModel.Description.OperationDescription> quando o serviço é aberto.</span><span class="sxs-lookup"><span data-stu-id="91fd5-114">The `WsdlDocumentationAttribute` implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior>, so the attribute instances are added to the corresponding <xref:System.ServiceModel.Description.ContractDescription> or <xref:System.ServiceModel.Description.OperationDescription> when the service is opened.</span></span> <span data-ttu-id="91fd5-115">O atributo <xref:System.ServiceModel.Description.IWsdlExportExtension>também implementa .</span><span class="sxs-lookup"><span data-stu-id="91fd5-115">The attribute also implements <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span></span> <span data-ttu-id="91fd5-116">Quando <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> é chamado, o <xref:System.ServiceModel.Description.WsdlExporter> que é usado <xref:System.ServiceModel.Description.WsdlContractConversionContext> para exportar os metadados e o que contém os objetos de descrição do serviço são passados como parâmetros que permitem a modificação dos metadados exportados.</span><span class="sxs-lookup"><span data-stu-id="91fd5-116">When <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> is called, the <xref:System.ServiceModel.Description.WsdlExporter> that is used to export the metadata and the <xref:System.ServiceModel.Description.WsdlContractConversionContext> that contains the service description objects are passed in as parameters enabling the modification of the exported metadata.</span></span>  
  
 <span data-ttu-id="91fd5-117">Nesta amostra, dependendo se o objeto <xref:System.ServiceModel.Description.ContractDescription> de <xref:System.ServiceModel.Description.OperationDescription>contexto de exportação tiver um ou um , um comentário é extraído do atributo usando a propriedade de texto e é adicionado ao elemento de anotação WSDL, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="91fd5-117">In this sample, depending upon whether the export context object has a <xref:System.ServiceModel.Description.ContractDescription> or an <xref:System.ServiceModel.Description.OperationDescription>, a comment is extracted from the attribute using the text property and is added to the WSDL annotation element as shown in the following code.</span></span>  
  
```csharp
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
        }
    }
}
```  
  
 <span data-ttu-id="91fd5-118">Se uma operação estiver sendo exportada, `WsdlParamOrReturnDocumentationAttribute` a amostra utiliza a reflexão para obter quaisquer valores para parâmetros e valores de retorno e os adiciona aos elementos de anotação WSDL para essa operação da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="91fd5-118">If an operation is being exported, the sample uses reflection to obtain any `WsdlParamOrReturnDocumentationAttribute` values for parameters and return values and adds them to the WSDL annotation elements for that operation as follows.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="91fd5-119">Em seguida, a amostra publica metadados da maneira padrão, usando o seguinte arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="91fd5-119">The sample then publishes metadata in the standard way, using the following configuration file.</span></span>  
  
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
  
## <a name="svcutil-client"></a><span data-ttu-id="91fd5-120">Cliente Svcutil</span><span class="sxs-lookup"><span data-stu-id="91fd5-120">Svcutil client</span></span>  
 <span data-ttu-id="91fd5-121">Esta amostra não usa Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="91fd5-121">This sample does not use Svcutil.exe.</span></span> <span data-ttu-id="91fd5-122">O contrato é fornecido no arquivo generatedClient.cs para que após a amostra demonstre importação e geração de código personalizados de WSDL, o serviço possa ser invocado.</span><span class="sxs-lookup"><span data-stu-id="91fd5-122">The contract is provided in the generatedClient.cs file so that after the sample demonstrates custom WSDL import and code generation, the service can be invoked.</span></span> <span data-ttu-id="91fd5-123">Para usar o seguinte importador de WSDL personalizado para este exemplo, você `/svcutilConfig` pode executar Svcutil.exe e especificar a `WsdlDocumentation.dll` opção, dando o caminho para o arquivo de configuração do cliente usado nesta amostra, que faz referência à biblioteca.</span><span class="sxs-lookup"><span data-stu-id="91fd5-123">To use the following custom WSDL importer for this example, you can run Svcutil.exe and specify the `/svcutilConfig` option, giving the path to the client configuration file used in this sample, which references the `WsdlDocumentation.dll` library.</span></span> <span data-ttu-id="91fd5-124">No entanto, o `WsdlDocumentationImporter`Svuctil.exe deve ser capaz `WsdlDocumentation.dll` de localizar e carregar a biblioteca, o que significa que ela está registrada no cache de montagem global, no caminho, ou está no mesmo diretório que Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="91fd5-124">To load the `WsdlDocumentationImporter`, however, Svuctil.exe must be able to locate and load the `WsdlDocumentation.dll` library, which means either that it is registered in the global assembly cache, in the path, or is in the same directory as Svcutil.exe.</span></span> <span data-ttu-id="91fd5-125">Para uma amostra básica como esta, a coisa mais fácil a fazer é copiar Svcutil.exe e o arquivo de configuração do cliente no mesmo diretório `WsdlDocumentation.dll` e executá-lo a partir daí.</span><span class="sxs-lookup"><span data-stu-id="91fd5-125">For a basic sample such as this, the easiest thing to do is to copy Svcutil.exe and the client configuration file into the same directory as `WsdlDocumentation.dll` and run it from there.</span></span>  
  
## <a name="the-custom-wsdl-importer"></a><span data-ttu-id="91fd5-126">O importador personalizado wsdl</span><span class="sxs-lookup"><span data-stu-id="91fd5-126">The Custom WSDL Importer</span></span>  
 <span data-ttu-id="91fd5-127">O <xref:System.ServiceModel.Description.IWsdlImportExtension> objeto `WsdlDocumentationImporter` personalizado <xref:System.ServiceModel.Description.IContractBehavior> também <xref:System.ServiceModel.Description.IOperationBehavior> implementa e deve ser adicionado <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> aos ServiceEndpoints importados e a ser invocado para modificar a geração de código quando o contrato ou código de operação estiver sendo criado.</span><span class="sxs-lookup"><span data-stu-id="91fd5-127">The custom <xref:System.ServiceModel.Description.IWsdlImportExtension> object `WsdlDocumentationImporter` also implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior> to be added to the imported ServiceEndpoints and <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> to be invoked to modify the code generation when the contract or operation code is being created.</span></span>  
  
 <span data-ttu-id="91fd5-128">Primeiro, no <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> método, a amostra determina se a anotação WSDL está no nível de contrato ou operação, e adiciona-se como um comportamento no escopo apropriado, passando o texto de anotação importado para o seu construtor.</span><span class="sxs-lookup"><span data-stu-id="91fd5-128">First, in the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method, the sample determines whether the WSDL annotation is at the contract or operation level, and adds itself as a behavior at the appropriate scope, passing the imported annotation text to its constructor.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="91fd5-129">Então, quando o código é gerado, <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> o sistema invoca os métodos, passando as informações de contexto apropriadas.</span><span class="sxs-lookup"><span data-stu-id="91fd5-129">Then, when the code is generated, the system invokes the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> methods, passing the appropriate context information.</span></span> <span data-ttu-id="91fd5-130">A amostra formata as anotações WSDL personalizadas e as insere como comentários no CodeDom.</span><span class="sxs-lookup"><span data-stu-id="91fd5-130">The sample formats the custom WSDL annotations and inserts them as comments into the CodeDom.</span></span>  
  
```csharp
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
  
## <a name="the-client-application"></a><span data-ttu-id="91fd5-131">O Aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="91fd5-131">The Client Application</span></span>  
 <span data-ttu-id="91fd5-132">O aplicativo cliente carrega o importador WSDL personalizado especificando-o no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91fd5-132">The client application loads the custom WSDL importer by specifying it in the application configuration file.</span></span>  
  
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
  
 <span data-ttu-id="91fd5-133">Uma vez especificado o importador personalizado, o sistema de metadados <xref:System.ServiceModel.Description.WsdlImporter> WCF carrega o importador personalizado em qualquer criado para esse fim.</span><span class="sxs-lookup"><span data-stu-id="91fd5-133">Once the custom importer has been specified, the WCF metadata system loads the custom importer into any <xref:System.ServiceModel.Description.WsdlImporter> created for that purpose.</span></span> <span data-ttu-id="91fd5-134">Esta amostra <xref:System.ServiceModel.Description.MetadataExchangeClient> usa o para baixar <xref:System.ServiceModel.Description.WsdlImporter> os metadados, os devidamente configurados para importar <xref:System.ServiceModel.Description.ServiceContractGenerator> os metadados usando o importador personalizado que a amostra cria e para compilar as informações de contrato modificadas em código cliente Visual Basic e C# que podem ser usados no Visual Studio para suportar o Intellisense ou compilados na documentação XML.</span><span class="sxs-lookup"><span data-stu-id="91fd5-134">This sample uses the <xref:System.ServiceModel.Description.MetadataExchangeClient> to download the metadata, the <xref:System.ServiceModel.Description.WsdlImporter> properly configured to import the metadata using the custom importer the sample creates, and the <xref:System.ServiceModel.Description.ServiceContractGenerator> to compile the modified contract information into both Visual Basic and C# client code that can be used in Visual Studio to support Intellisense or compiled into XML documentation.</span></span>  
  
```csharp
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="91fd5-135">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="91fd5-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="91fd5-136">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="91fd5-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="91fd5-137">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="91fd5-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="91fd5-138">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="91fd5-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="91fd5-139">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="91fd5-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="91fd5-140">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="91fd5-140">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="91fd5-141">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="91fd5-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="91fd5-142">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="91fd5-142">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
