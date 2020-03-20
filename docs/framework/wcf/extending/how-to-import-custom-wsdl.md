---
title: Como importar WSDL personalizado
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 614842f2d77d967e0a6d4841e5e5e4fcc8805580
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185544"
---
# <a name="how-to-import-custom-wsdl"></a>Como importar WSDL personalizado
Este tópico descreve como importar WSDL personalizado. Para lidar com o WSDL <xref:System.ServiceModel.Description.IWsdlImportExtension> personalizado, você deve implementar a interface.  
  
### <a name="to-import-custom-wsdl"></a>Para importar WSDL personalizado  
  
1. Implementar <xref:System.ServiceModel.Description.IWsdlImportExtension>. Implemente <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> o método para modificar os metadados antes de serem importados. Implementar <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> os <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> métodos para modificar contratos e pontos finais importados dos metadados. Para acessar o contrato ou ponto final importado,<xref:System.ServiceModel.Description.WsdlContractConversionContext> <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>use o objeto de contexto correspondente (ou ):  
  
    ```csharp
    public class WsdlDocumentationImporter : IWsdlImportExtension
    {
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
    }
    ```
  
2. Configure o aplicativo cliente para usar o importador WSDL personalizado. Observe que se você estiver usando Svcutil.exe, você deve adicionar esta configuração ao arquivo de configuração de Svcutil.exe (Svcutil.exe.config):  
  
    ```xml  
    <system.serviceModel>  
          <client>  
            <endpoint
              address="http://localhost:8000/Fibonacci"
              binding="wsHttpBinding"  
              contract="IFibonacci"  
            />  
            <metadata>  
              <wsdlImporters>  
                <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
              </wsdlImporters>  
            </metadata>  
          </client>  
        </system.serviceModel>  
    ```  
  
3. Crie uma <xref:System.ServiceModel.Description.WsdlImporter> nova instância <xref:System.ServiceModel.Description.MetadataSet> (passando na instância que contém os documentos WSDL que você deseja importar) e ligue para <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a>Confira também

- [Metadados](../feature-details/metadata.md)
- [Exportando e importando metadados](../feature-details/exporting-and-importing-metadata.md)
- [Publicação personalizada de WSDL](../samples/custom-wsdl-publication.md)
