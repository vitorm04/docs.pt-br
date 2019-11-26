---
title: Como importar WSDL personalizado
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 10fc3282560d35e61044a367f8172571096d76bd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975895"
---
# <a name="how-to-import-custom-wsdl"></a>Como importar WSDL personalizado
Este tópico descreve como importar o WSDL personalizado. Para lidar com o WSDL personalizado, você deve implementar a interface <xref:System.ServiceModel.Description.IWsdlImportExtension>.  
  
### <a name="to-import-custom-wsdl"></a>Para importar o WSDL personalizado  
  
1. Implementar <xref:System.ServiceModel.Description.IWsdlImportExtension>. Implemente o método <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> para modificar os metadados antes que eles sejam importados. Implemente os métodos <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> e <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> para modificar os contratos e os pontos de extremidade importados dos metadados. Para acessar o contrato ou ponto de extremidade importado, use o objeto de contexto correspondente (<xref:System.ServiceModel.Description.WsdlContractConversionContext> ou <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):  
  
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
  
2. Configure o aplicativo cliente para usar o importador WSDL personalizado. Observe que, se você estiver usando svcutil. exe, deverá adicionar essa configuração ao arquivo de configuração para SvcUtil. exe (svcutil. exe. config):  
  
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
  
3. Crie uma nova instância de <xref:System.ServiceModel.Description.WsdlImporter> (passando a instância de <xref:System.ServiceModel.Description.MetadataSet> que contém os documentos WSDL que você deseja importar) e chame <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Metadados](../feature-details/metadata.md)
- [Exportando e importando metadados](../feature-details/exporting-and-importing-metadata.md)
- [Publicação de WSDL personalizada](../samples/custom-wsdl-publication.md)
