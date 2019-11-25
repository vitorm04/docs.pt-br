---
title: Como escrever uma extensão para o ServiceContractGenerator
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: 68b380a40448f21ba770aa47c7188b818fa8f9e7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975873"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Como escrever uma extensão para o ServiceContractGenerator
Este tópico descreve como gravar uma extensão para o <xref:System.ServiceModel.Description.ServiceContractGenerator>. Isso pode ser feito pela implementação da interface <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> em um comportamento de operação ou na implementação da interface <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> em um comportamento de contrato. Este tópico mostra como implementar a interface <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> em um comportamento de contrato.  
  
 O <xref:System.ServiceModel.Description.ServiceContractGenerator> gera contratos de serviço, tipos de cliente e configurações de cliente das instâncias <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>e <xref:System.ServiceModel.Channels.Binding>. Normalmente, você importa as instâncias <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>e <xref:System.ServiceModel.Channels.Binding> de metadados de serviço e, em seguida, usa essas instâncias para gerar código para chamar o serviço. Neste exemplo, uma implementação de <xref:System.ServiceModel.Description.IWsdlImportExtension> é usada para processar anotações WSDL e, em seguida, adicionar extensões de geração de código aos contratos importados para gerar comentários sobre o código gerado.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>Para gravar uma extensão para o ServiceContractGenerator  
  
1. Implementar <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Para modificar o contrato de serviço gerado, use a instância <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passada para o método <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>.  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
        context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. Implemente <xref:System.ServiceModel.Description.IWsdlImportExtension> na mesma classe. O método <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> pode processar uma extensão WSDL específica (neste caso, anotações WSDL) adicionando uma extensão de geração de código à instância de <xref:System.ServiceModel.Description.ContractDescription> importada.  
  
    ```csharp
    public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)
    {
        // Contract documentation
        if (context.WsdlPortType.Documentation != null)
        {
            context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));
        }
        // Operation documentation
        foreach (Operation operation in context.WsdlPortType.Operations)
        {
            if (operation.Documentation != null)
            {
                OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);
                if (operationDescription != null)
                {
                    operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));
                }
            }
        }
    }
    public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)
    {
        Console.WriteLine("BeforeImport called.");
    }

    public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)
    {
        Console.WriteLine("ImportEndpoint called.");
    }
    ```  
  
3. Adicione o importador WSDL à sua configuração de cliente.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. No código do cliente, crie um `MetadataExchangeClient` e chame `GetMetadata`.  
  
    ```csharp
    var mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. Crie um `WsdlImporter` e chame `ImportAllContracts`.  
  
    ```csharp
    var importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. Crie um `ServiceContractGenerator` e chame `GenerateServiceContractType` para cada contrato.  
  
    ```csharp
    var generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> é chamado automaticamente para cada comportamento de contrato em um determinado contrato que implementa <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Esse método pode modificar o <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passado. Neste exemplo, comentários são adicionados.  
  
## <a name="see-also"></a>Consulte também

- [Metadados](../feature-details/metadata.md)
- [Como importar WSDL personalizado](how-to-import-custom-wsdl.md)
