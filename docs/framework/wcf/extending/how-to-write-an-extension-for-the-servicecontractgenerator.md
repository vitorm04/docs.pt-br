---
title: 'Como: escrever uma extensão para o ServiceContractGenerator'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: c9e10efccf0d51e6b78aace1296d227a78a9f91d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340614"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Como: escrever uma extensão para o ServiceContractGenerator
Este tópico descreve como escrever uma extensão para o <xref:System.ServiceModel.Description.ServiceContractGenerator>. Isso pode ser feito com a implementação de <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> um comportamento de operação de interface ou implementar o <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface em um comportamento de contrato. Este tópico mostra como implementar o <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface em um comportamento de contrato.  
  
 O <xref:System.ServiceModel.Description.ServiceContractGenerator> gera os contratos de serviço, os tipos de cliente e as configurações de cliente do <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, e <xref:System.ServiceModel.Channels.Binding> instâncias. Normalmente, você importa <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, e <xref:System.ServiceModel.Channels.Binding> instâncias de metadados de serviço e, em seguida, use essas instâncias para gerar código para chamar o serviço. Neste exemplo, um <xref:System.ServiceModel.Description.IWsdlImportExtension> implementação é usada para processar as anotações de WSDL e, em seguida, adicione as extensões de geração de código para os contratos importados para gerar comentários no código gerado.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>Para gravar uma extensão para o ServiceContractGenerator  
  
1. Implementar <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Para modificar o contrato de serviço gerado, use o <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instância passada para o <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> método.  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. Implemente <xref:System.ServiceModel.Description.IWsdlImportExtension> na mesma classe. O <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> método pode processar uma extensão específica da WSDL (anotações WSDL neste caso), adicionando uma extensão de geração de código para o importados <xref:System.ServiceModel.Description.ContractDescription> instância.  
  
    ```  
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
  
3. Adicione o importador WSDL para sua configuração de cliente.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. No código do cliente, criar uma `MetadataExchangeClient` e chamar `GetMetadata`.  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. Criar uma `WsdlImporter` e chamar `ImportAllContracts`.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. Criar uma `ServiceContractGenerator` e chamar `GenerateServiceContractType` para cada contrato.  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> é chamado automaticamente para cada comportamento de contrato em um determinado contrato que implementa <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Esse método pode modificar o <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passado. Neste exemplo, eles são acrescentados.  
  
## <a name="see-also"></a>Consulte também

- [Metadados](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Como: importar o WSDL personalizado](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
