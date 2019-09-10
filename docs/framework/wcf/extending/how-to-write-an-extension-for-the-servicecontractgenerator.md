---
title: 'Como: escrever uma extensão para o ServiceContractGenerator'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: af23babd9255c45b9fa89b5c167de6960f0f690e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855728"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Como: escrever uma extensão para o ServiceContractGenerator
Este tópico descreve como gravar uma extensão para o <xref:System.ServiceModel.Description.ServiceContractGenerator>. Isso pode ser feito implementando a <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface em um comportamento de operação ou implementando a <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface em um comportamento de contrato. Este tópico mostra como implementar a <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface em um comportamento de contrato.  
  
 O <xref:System.ServiceModel.Description.ServiceContractGenerator> gera contratos de serviço, tipos de cliente e configurações de <xref:System.ServiceModel.Description.ServiceEndpoint>cliente <xref:System.ServiceModel.Description.ContractDescription>de instâncias <xref:System.ServiceModel.Channels.Binding> , e. Normalmente, você importa <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>e <xref:System.ServiceModel.Channels.Binding> instâncias de metadados de serviço e, em seguida, usa essas instâncias para gerar código para chamar o serviço. Neste exemplo, uma <xref:System.ServiceModel.Description.IWsdlImportExtension> implementação é usada para processar anotações WSDL e, em seguida, adicionar extensões de geração de código aos contratos importados para gerar comentários sobre o código gerado.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>Para gravar uma extensão para o ServiceContractGenerator  
  
1. Implementar <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Para modificar o contrato de serviço gerado, use <xref:System.ServiceModel.Description.ServiceContractGenerationContext> a instância passada para <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> o método.  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. Implemente <xref:System.ServiceModel.Description.IWsdlImportExtension> na mesma classe. O <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> método pode processar uma extensão WSDL específica (neste caso, anotações WSDL) adicionando uma extensão de geração de código à instância importada <xref:System.ServiceModel.Description.ContractDescription> .  
  
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
  
4. No código do cliente, crie uma `MetadataExchangeClient` chamada `GetMetadata`e.  
  
    ```csharp  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. Crie uma `WsdlImporter` chamada `ImportAllContracts`e.  
  
    ```csharp  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. Criar um `ServiceContractGenerator` e chamar `GenerateServiceContractType` para cada contrato.  
  
    ```csharp  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>é chamado automaticamente para cada comportamento de contrato em um determinado contrato que <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>implementa. Esse método pode, então, <xref:System.ServiceModel.Description.ServiceContractGenerationContext> modificar o passado. Neste exemplo, comentários são adicionados.  
  
## <a name="see-also"></a>Consulte também

- [Metadados](../feature-details/metadata.md)
- [Como: Importar WSDL personalizado](how-to-import-custom-wsdl.md)
