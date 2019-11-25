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
# <a name="how-to-import-custom-wsdl"></a><span data-ttu-id="0e533-102">Como importar WSDL personalizado</span><span class="sxs-lookup"><span data-stu-id="0e533-102">How to: Import Custom WSDL</span></span>
<span data-ttu-id="0e533-103">Este tópico descreve como importar o WSDL personalizado.</span><span class="sxs-lookup"><span data-stu-id="0e533-103">This topic describes how to import custom WSDL.</span></span> <span data-ttu-id="0e533-104">Para lidar com o WSDL personalizado, você deve implementar a interface <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span><span class="sxs-lookup"><span data-stu-id="0e533-104">To handle the custom WSDL, you must implement the <xref:System.ServiceModel.Description.IWsdlImportExtension> interface.</span></span>  
  
### <a name="to-import-custom-wsdl"></a><span data-ttu-id="0e533-105">Para importar o WSDL personalizado</span><span class="sxs-lookup"><span data-stu-id="0e533-105">To import custom WSDL</span></span>  
  
1. <span data-ttu-id="0e533-106">Implementar <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span><span class="sxs-lookup"><span data-stu-id="0e533-106">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span></span> <span data-ttu-id="0e533-107">Implemente o método <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> para modificar os metadados antes que eles sejam importados.</span><span class="sxs-lookup"><span data-stu-id="0e533-107">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> method to modify the metadata before it is imported.</span></span> <span data-ttu-id="0e533-108">Implemente os métodos <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> e <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> para modificar os contratos e os pontos de extremidade importados dos metadados.</span><span class="sxs-lookup"><span data-stu-id="0e533-108">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> and <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> methods to modify contracts and endpoints imported from the metadata.</span></span> <span data-ttu-id="0e533-109">Para acessar o contrato ou ponto de extremidade importado, use o objeto de contexto correspondente (<xref:System.ServiceModel.Description.WsdlContractConversionContext> ou <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span><span class="sxs-lookup"><span data-stu-id="0e533-109">To access the imported contract or endpoint, use the corresponding context object (<xref:System.ServiceModel.Description.WsdlContractConversionContext> or <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span></span>  
  
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
  
2. <span data-ttu-id="0e533-110">Configure o aplicativo cliente para usar o importador WSDL personalizado.</span><span class="sxs-lookup"><span data-stu-id="0e533-110">Configure the client application to use the custom WSDL importer.</span></span> <span data-ttu-id="0e533-111">Observe que, se você estiver usando svcutil. exe, deverá adicionar essa configuração ao arquivo de configuração para SvcUtil. exe (svcutil. exe. config):</span><span class="sxs-lookup"><span data-stu-id="0e533-111">Note that if you are using Svcutil.exe, you should add this configuration to the configuration file for Svcutil.exe (Svcutil.exe.config):</span></span>  
  
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
  
3. <span data-ttu-id="0e533-112">Crie uma nova instância de <xref:System.ServiceModel.Description.WsdlImporter> (passando a instância de <xref:System.ServiceModel.Description.MetadataSet> que contém os documentos WSDL que você deseja importar) e chame <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span><span class="sxs-lookup"><span data-stu-id="0e533-112">Create a new <xref:System.ServiceModel.Description.WsdlImporter> instance (passing in the <xref:System.ServiceModel.Description.MetadataSet> instance that contains the WSDL documents that you want to import), and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0e533-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e533-113">See also</span></span>

- [<span data-ttu-id="0e533-114">Metadados</span><span class="sxs-lookup"><span data-stu-id="0e533-114">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="0e533-115">Exportando e importando metadados</span><span class="sxs-lookup"><span data-stu-id="0e533-115">Exporting and Importing Metadata</span></span>](../feature-details/exporting-and-importing-metadata.md)
- [<span data-ttu-id="0e533-116">Publicação de WSDL personalizada</span><span class="sxs-lookup"><span data-stu-id="0e533-116">Custom WSDL Publication</span></span>](../samples/custom-wsdl-publication.md)
