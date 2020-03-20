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
# <a name="custom-wsdl-publication"></a>Publicação personalizada de WSDL
Este exemplo demonstra como:  
  
- Implementar <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> um atributo personalizado <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> para exportar propriedades de atributos como anotações WSDL.  
  
- Implementar <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> para importar as anotações personalizadas do WSDL.  
  
- Implementar <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> e em um comportamento de contrato personalizado e um comportamento de operação personalizado, respectivamente, para escrever anotações importadas como comentários no CodeDom para o contrato e operação importados.  
  
- Use <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> o para baixar o WSDL, um <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> para importar o WSDL <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> usando o importador WSDL personalizado, e para gerar o código cliente da Windows Communication Foundation (WCF) com as anotações WSDL como /// e ''' comentários em C# e Visual Basic.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
## <a name="service"></a>Serviço  
 O serviço nesta amostra é marcado com dois atributos personalizados. O primeiro, `WsdlDocumentationAttribute`o , aceita uma corda no construtor e pode ser aplicado para fornecer uma interface de contrato ou operação com uma string que descreve seu uso. O segundo, `WsdlParamOrReturnDocumentationAttribute`pode ser aplicado para devolver valores ou parâmetros para descrever esses valores na operação. O exemplo a seguir `ICalculator`mostra um contrato de serviço, descrito usando esses atributos.  
  
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
  
 Os `WsdlDocumentationAttribute` <xref:System.ServiceModel.Description.IContractBehavior> implementos <xref:System.ServiceModel.Description.IOperationBehavior>e , assim, as instâncias de atributo são adicionadas ao correspondente <xref:System.ServiceModel.Description.ContractDescription> ou <xref:System.ServiceModel.Description.OperationDescription> quando o serviço é aberto. O atributo <xref:System.ServiceModel.Description.IWsdlExportExtension>também implementa . Quando <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> é chamado, o <xref:System.ServiceModel.Description.WsdlExporter> que é usado <xref:System.ServiceModel.Description.WsdlContractConversionContext> para exportar os metadados e o que contém os objetos de descrição do serviço são passados como parâmetros que permitem a modificação dos metadados exportados.  
  
 Nesta amostra, dependendo se o objeto <xref:System.ServiceModel.Description.ContractDescription> de <xref:System.ServiceModel.Description.OperationDescription>contexto de exportação tiver um ou um , um comentário é extraído do atributo usando a propriedade de texto e é adicionado ao elemento de anotação WSDL, conforme mostrado no código a seguir.  
  
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
  
 Se uma operação estiver sendo exportada, `WsdlParamOrReturnDocumentationAttribute` a amostra utiliza a reflexão para obter quaisquer valores para parâmetros e valores de retorno e os adiciona aos elementos de anotação WSDL para essa operação da seguinte forma.  
  
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
  
 Em seguida, a amostra publica metadados da maneira padrão, usando o seguinte arquivo de configuração.  
  
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
  
## <a name="svcutil-client"></a>Cliente Svcutil  
 Esta amostra não usa Svcutil.exe. O contrato é fornecido no arquivo generatedClient.cs para que após a amostra demonstre importação e geração de código personalizados de WSDL, o serviço possa ser invocado. Para usar o seguinte importador de WSDL personalizado para este exemplo, você `/svcutilConfig` pode executar Svcutil.exe e especificar a `WsdlDocumentation.dll` opção, dando o caminho para o arquivo de configuração do cliente usado nesta amostra, que faz referência à biblioteca. No entanto, o `WsdlDocumentationImporter`Svuctil.exe deve ser capaz `WsdlDocumentation.dll` de localizar e carregar a biblioteca, o que significa que ela está registrada no cache de montagem global, no caminho, ou está no mesmo diretório que Svcutil.exe. Para uma amostra básica como esta, a coisa mais fácil a fazer é copiar Svcutil.exe e o arquivo de configuração do cliente no mesmo diretório `WsdlDocumentation.dll` e executá-lo a partir daí.  
  
## <a name="the-custom-wsdl-importer"></a>O importador personalizado wsdl  
 O <xref:System.ServiceModel.Description.IWsdlImportExtension> objeto `WsdlDocumentationImporter` personalizado <xref:System.ServiceModel.Description.IContractBehavior> também <xref:System.ServiceModel.Description.IOperationBehavior> implementa e deve ser adicionado <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> aos ServiceEndpoints importados e a ser invocado para modificar a geração de código quando o contrato ou código de operação estiver sendo criado.  
  
 Primeiro, no <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> método, a amostra determina se a anotação WSDL está no nível de contrato ou operação, e adiciona-se como um comportamento no escopo apropriado, passando o texto de anotação importado para o seu construtor.  
  
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
  
 Então, quando o código é gerado, <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> o sistema invoca os métodos, passando as informações de contexto apropriadas. A amostra formata as anotações WSDL personalizadas e as insere como comentários no CodeDom.  
  
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
  
## <a name="the-client-application"></a>O Aplicativo cliente  
 O aplicativo cliente carrega o importador WSDL personalizado especificando-o no arquivo de configuração do aplicativo.  
  
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
  
 Uma vez especificado o importador personalizado, o sistema de metadados <xref:System.ServiceModel.Description.WsdlImporter> WCF carrega o importador personalizado em qualquer criado para esse fim. Esta amostra <xref:System.ServiceModel.Description.MetadataExchangeClient> usa o para baixar <xref:System.ServiceModel.Description.WsdlImporter> os metadados, os devidamente configurados para importar <xref:System.ServiceModel.Description.ServiceContractGenerator> os metadados usando o importador personalizado que a amostra cria e para compilar as informações de contrato modificadas em código cliente Visual Basic e C# que podem ser usados no Visual Studio para suportar o Intellisense ou compilados na documentação XML.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
