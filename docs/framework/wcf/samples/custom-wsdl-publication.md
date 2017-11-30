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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e390bf728cde703a967fcea954583f6e5f84002
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-wsdl-publication"></a>Publicação personalizada de WSDL
Este exemplo demonstra como:  
  
-   Implementar um <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> em um personalizado <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> atributo para exportar as propriedades de atributo como anotações de WSDL.  
  
-   Implementar <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> para importar as anotações de WSDL personalizadas.  
  
-   Implementar <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> e <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> em um personalizado contrato comportamento e o comportamento de uma operação personalizada, respectivamente, para gravar anotações importadas como comentários no CodeDom para o contrato importado e a operação.  
  
-   Use o <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> para baixar o WSDL, uma <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Importar WSDL usando o importador WSDL personalizado e o <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> para gerar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] código de cliente com as anotações de WSDL como / / / e ' ' comentários em c# e Visual Basic.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
## <a name="service"></a>Serviço  
 O serviço neste exemplo é marcado com dois atributos personalizados. Primeiro, o `WsdlDocumentationAttribute`, aceita uma cadeia de caracteres no construtor e podem ser aplicadas para fornecer uma interface de contrato ou operação com uma cadeia de caracteres que descreve seu uso. O segundo, `WsdlParamOrReturnDocumentationAttribute`, podem ser aplicadas para retornar valores ou parâmetros para descrever esses valores na operação. O exemplo a seguir mostra um contrato de serviço, `ICalculator`, descritas usando esses atributos.  
  
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
  
 O `WsdlDocumentationAttribute` implementa <xref:System.ServiceModel.Description.IContractBehavior> e <xref:System.ServiceModel.Description.IOperationBehavior>, portanto, as instâncias de atributo são adicionadas ao correspondente <xref:System.ServiceModel.Description.ContractDescription> ou <xref:System.ServiceModel.Description.OperationDescription> quando o serviço é aberto. O atributo também implementa <xref:System.ServiceModel.Description.IWsdlExportExtension>. Quando <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> é chamado, o <xref:System.ServiceModel.Description.WsdlExporter> que é usado para exportar os metadados e o <xref:System.ServiceModel.Description.WsdlContractConversionContext> que contém a descrição do serviço objetos são passados como parâmetros para habilitar a modificação dos metadados exportado.  
  
 Neste exemplo, dependendo se o objeto de contexto de exportação possui um <xref:System.ServiceModel.Description.ContractDescription> ou um <xref:System.ServiceModel.Description.OperationDescription>, um comentário é extraído do atributo usando a propriedade de texto e é adicionado ao elemento de anotação WSDL, conforme mostrado no código a seguir.  
  
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
  
 Se uma operação está sendo exportada, o exemplo usa reflexão para obter qualquer `WsdlParamOrReturnDocumentationAttribute` valores para parâmetros e valores de retorno e os adiciona aos elementos WSDL anotação para a operação da seguinte maneira.  
  
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
  
 O exemplo, em seguida, publica os metadados da maneira padrão, usando o seguinte arquivo de configuração.  
  
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
  
## <a name="svcutil-client"></a>Cliente svcutil  
 Este exemplo não usar o Svcutil.exe. O contrato é fornecido no generatedClient.cs arquivo de modo que, depois que o exemplo demonstra a importação WSDL personalizada e geração de código, o serviço pode ser invocado. Para usar o seguinte importador WSDL personalizado para este exemplo, você pode executar o Svcutil.exe e especificar o `/svcutilConfig` opção, fornecendo o caminho para o arquivo de configuração de cliente usado neste exemplo, o que faz referência a `WsdlDocumentation.dll` biblioteca. Para carregar o `WsdlDocumentationImporter`, no entanto, Svuctil.exe deve ser capaz de localizar e carregar o `WsdlDocumentation.dll` biblioteca, o que significa que o que ele está registrado no cache de assembly global, no caminho, ou está no mesmo diretório que o Svcutil.exe. Para obter um exemplo básico como este, o mais fácil fazer é copiar Svcutil.exe e o arquivo de configuração do cliente para o mesmo diretório que `WsdlDocumentation.dll` e executá-lo lá.  
  
## <a name="the-custom-wsdl-importer"></a>O importador WSDL personalizado  
 Personalizado <xref:System.ServiceModel.Description.IWsdlImportExtension> objeto `WsdlDocumentationImporter` também implementa <xref:System.ServiceModel.Description.IContractBehavior> e <xref:System.ServiceModel.Description.IOperationBehavior> a serem adicionadas ao ServiceEndpoints importados e <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> e <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> para ser chamado para modificar a geração de código quando a operação ou um contrato código está sendo criado.  
  
 Primeiro, do <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> método, o exemplo determina se a anotação de WSDL está no nível do contrato ou de operação e se adiciona como um comportamento no escopo apropriado, passando o texto da anotação importados para o construtor.  
  
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
  
 Em seguida, quando o código for gerado, o sistema invoca o <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> e <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> métodos, passando as informações de contexto apropriado. O exemplo formata as anotações de WSDL personalizadas e insere-los como comentários de CodeDom.  
  
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
  
## <a name="the-client-application"></a>O aplicativo cliente  
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
  
 Depois que o importador personalizado foi especificado, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metadados sistema carrega o importador personalizado em qualquer <xref:System.ServiceModel.Description.WsdlImporter> criado para essa finalidade. Este exemplo usa o <xref:System.ServiceModel.Description.MetadataExchangeClient> para baixar os metadados, o <xref:System.ServiceModel.Description.WsdlImporter> adequadamente configurado para importar os metadados usando o importador personalizado, o exemplo cria, e o <xref:System.ServiceModel.Description.ServiceContractGenerator> para compilar as informações de contrato modificado em ambos Visual Basic e o cliente código c# que pode ser usado no Visual Studio para dar suporte ao Intellisense ou compilado em documentação XML.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
  
## <a name="see-also"></a>Consulte também
