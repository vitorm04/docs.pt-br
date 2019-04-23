---
title: 'Como: importar o WSDL personalizado'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: d9a4609f08a95bbecca81aa6667102a0e4a73c67
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303785"
---
# <a name="how-to-import-custom-wsdl"></a><span data-ttu-id="29aac-102">Como: importar o WSDL personalizado</span><span class="sxs-lookup"><span data-stu-id="29aac-102">How to: Import Custom WSDL</span></span>
<span data-ttu-id="29aac-103">Este tópico descreve como importar WSDL personalizado.</span><span class="sxs-lookup"><span data-stu-id="29aac-103">This topic describes how to import custom WSDL.</span></span> <span data-ttu-id="29aac-104">Para lidar com o WSDL personalizado, você deve implementar o <xref:System.ServiceModel.Description.IWsdlImportExtension> interface.</span><span class="sxs-lookup"><span data-stu-id="29aac-104">To handle the custom WSDL, you must implement the <xref:System.ServiceModel.Description.IWsdlImportExtension> interface.</span></span>  
  
### <a name="to-import-custom-wsdl"></a><span data-ttu-id="29aac-105">Para importar WSDL personalizado</span><span class="sxs-lookup"><span data-stu-id="29aac-105">To import custom WSDL</span></span>  
  
1. <span data-ttu-id="29aac-106">Implementar <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span><span class="sxs-lookup"><span data-stu-id="29aac-106">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span></span> <span data-ttu-id="29aac-107">Implementar o <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> método para modificar os metadados, antes que sejam importados.</span><span class="sxs-lookup"><span data-stu-id="29aac-107">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> method to modify the metadata before it is imported.</span></span> <span data-ttu-id="29aac-108">Implemente a <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> e <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> métodos para modificar os contratos e pontos de extremidade importados dos metadados.</span><span class="sxs-lookup"><span data-stu-id="29aac-108">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> and <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> methods to modify contracts and endpoints imported from the metadata.</span></span> <span data-ttu-id="29aac-109">Para acessar o contrato importado ou ponto de extremidade, use o objeto de contexto correspondente (<xref:System.ServiceModel.Description.WsdlContractConversionContext> ou <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span><span class="sxs-lookup"><span data-stu-id="29aac-109">To access the imported contract or endpoint, use the corresponding context object (<xref:System.ServiceModel.Description.WsdlContractConversionContext> or <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span></span>  
  
    ```  
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
  
2. <span data-ttu-id="29aac-110">Configure o aplicativo de cliente para usar o importador WSDL personalizado.</span><span class="sxs-lookup"><span data-stu-id="29aac-110">Configure the client application to use the custom WSDL importer.</span></span> <span data-ttu-id="29aac-111">Observe que se você estiver usando Svcutil.exe, você deve adicionar essa configuração ao arquivo de configuração para Svcutil.exe (svcutil):</span><span class="sxs-lookup"><span data-stu-id="29aac-111">Note that if you are using Svcutil.exe, you should add this configuration to the configuration file for Svcutil.exe (Svcutil.exe.config):</span></span>  
  
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
  
3. <span data-ttu-id="29aac-112">Criar um novo <xref:System.ServiceModel.Description.WsdlImporter> instância (passando a <xref:System.ServiceModel.Description.MetadataSet> instância que contém os documentos WSDL que você deseja importar) e chamar <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span><span class="sxs-lookup"><span data-stu-id="29aac-112">Create a new <xref:System.ServiceModel.Description.WsdlImporter> instance (passing in the <xref:System.ServiceModel.Description.MetadataSet> instance that contains the WSDL documents that you want to import), and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="29aac-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29aac-113">See also</span></span>

- [<span data-ttu-id="29aac-114">Metadados</span><span class="sxs-lookup"><span data-stu-id="29aac-114">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="29aac-115">Exportando e importando metadados</span><span class="sxs-lookup"><span data-stu-id="29aac-115">Exporting and Importing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
- [<span data-ttu-id="29aac-116">Publicação de WSDL personalizada</span><span class="sxs-lookup"><span data-stu-id="29aac-116">Custom WSDL Publication</span></span>](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
