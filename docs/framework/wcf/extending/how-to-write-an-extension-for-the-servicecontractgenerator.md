---
title: "Como escrever uma extensão para o ServiceContractGenerator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 39fb7fde2d293ae96e11b7c77b4a16d18ee3cac9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Como escrever uma extensão para o ServiceContractGenerator
Este tópico descreve como escrever uma extensão para o <xref:System.ServiceModel.Description.ServiceContractGenerator>. Isso pode ser feito através da implementação de <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> um comportamento de operação de interface ou implementar o <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface em um comportamento de contrato. Este tópico mostra como implementar a <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface em um comportamento de contrato.  
  
 O <xref:System.ServiceModel.Description.ServiceContractGenerator> gera contratos de serviço, tipos de cliente e as configurações de cliente de <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, e <xref:System.ServiceModel.Channels.Binding> instâncias. Normalmente, você importa <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, e <xref:System.ServiceModel.Channels.Binding> instâncias dos metadados do serviço e, em seguida, use essas instâncias para gerar código para chamar o serviço. Neste exemplo, um <xref:System.ServiceModel.Description.IWsdlImportExtension> implementação é usada para processar as anotações de WSDL e, em seguida, adicionar extensões de geração de código para os contratos importados para gerar comentários no código gerado.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>Para escrever uma extensão para o ServiceContractGenerator  
  
1.  Implementar <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Para modificar o contrato de serviço gerado, use o <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instância passada para o <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> método.  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2.  Implementar <xref:System.ServiceModel.Description.IWsdlImportExtension> na mesma classe. O <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> método pode processar uma extensão WSDL específica (anotações de WSDL neste caso), adicionando uma extensão de geração de código para importado <xref:System.ServiceModel.Description.ContractDescription> instância.  
  
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
  
3.  Adicione o importador WSDL para a configuração do cliente.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4.  O código de cliente, crie um `MetadataExchangeClient` e chame `GetMetadata`.  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5.  Criar um `WsdlImporter` e chame `ImportAllContracts`.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6.  Criar um `ServiceContractGenerator` e chame `GenerateServiceContractType` para cada contrato.  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7.  <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>é chamado automaticamente para cada comportamento de contrato em um dado contrato que implementa <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Esse método pode modificar o <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passado. Neste exemplo, eles são acrescentados.  
  
## <a name="see-also"></a>Consulte também  
 [Metadados](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Como: Importar WSDL personalizado](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
